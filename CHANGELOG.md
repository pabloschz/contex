# ContEx Change Log

## v0.4.1: Quick patch from doofinder

- Make some function publics to work with the API at lower level and add come customization.

## v0.4.0 : In progress

- Add target option when setting `BarChart` event handler.
- Refactor `BarChart` to honour all options passed in `new`.
- Refactor `PointPlot` to honour all options passed in `new`.
- Refactor `GanttChart` to honour all options passed in `new`.
- Provide minimal default style so labels don't disappear unexpectedly if no CSS is set. Thanks @srowley.
- XML declaration added to generated SVG so the output can be served as an image. Thanks @srowley.
- Custom tick formatting enabled for PointPlot
- Added `:custom_value_scale` to `BarChart` to allow overriding of the automatically generated scale
- Added `:custom_x_scale` and `:custom_y_scale` to `PointPlot` to allow overriding of the automatically generated scales
- Added `LinePlot` (finally)
- Make stroke width for `LinePlot` adjustable through options. Thanks @littleStudent.
- Handle nil values in `LinePlot` by creating gaps in line.
- Stop crash on timescales when interval clashes with days in month resulting in invalid date. Thanks @imsoulfly. 

### Deprecated
- Most of the options set via functions, e.g. `BarChart.colours/2`. Use the options in the relevant `new` functions instead.

## v0.3.0 : 2020-06-08
- Allow Dataset to be created from a list of Maps (previously lists of lists and list of tuples were supported)
- Implement a data mapping mechanism to provide a consistent way of mapping data into required plot elements. Thanks 
@srowley for breaking the back of this.
- Added simplified chart creation API. Thanks @srowley. The existing API remains as-is
- Added test coverage for some components. Thanks @srowley
- Refactored SVG generation to minimise, or at least isolate, messy string interpolation, as per @elcritch suggestion. More to do on code tidy up.
- Improved Timescale code. Thanks for suggestions from [Eiji](https://elixirforum.com/u/eiji/)
- Replaced Enum with Stream in (as yet to be activated) line generation code in PointPlot as per @elcritch suggestion.
- Fixed up some typespecs to stop Elixir 1.10 complaining. More to do to make the module struct specs right.
- Removed Timex dependency.
- A number of bug fixes in TimeScales, plus additional type guards
- Added basic sanitization of possible user inputs (titles, axis labels, category names from data). Sanitization approach is somewhat naive - basically any text is run through a copy of the `Plug.HTML.html_escape`.
- Fixed scaling bug in sparkline when data range was small
- Added axis_label_rotation option to PointPlot and BarChart. Thanks @srowley.
- Allow plot margins to be optionally specified and override default calcs. Thanks @axelson.

## v0.2.0 : 2020-01-28
- Documentation for all modules
- Created type specs for the public API
- Renamed :data to :dataset in various plot types to avoid ambiguity
- ** BREAKING ** Renamed BarPlot to BarChart
- ** POTENTIALLY BREAKING ** Renamed ContinuousScale to ContinuousLinearScale, renamed constructor from new_linear() to new(). Used internally, so shouldn't cause any issues.
- ** POTENTIALLY BREAKING ** Made a number of margin calculation functions in Plot private. Shouldn't have been used externally anyway.
- ** POTENTIALLY BREAKING ** Removed set_x_range and set_y_range from PointPlot. No longer used as range is set by Plot size calcs.
- Fixed incorrect closed path in sparkline
- Allowed forcing of value range in `BarChart` (`BarChart.force_value_range\2`)
- Changed `BarChart` colour handling to pass through to `ColourCategoryScale`
- Changed `new\3` to `new\1` on various plots as width & height are now set by `Plot`
- Prevented infinite loop in `ColourCategoryScale` when setting palette to `nil` (turns out `nil` is an atom)
- Fixed divide by zero error in `ContinuousLinearScale` (needed to test for float as well as integer)
- Enabled legend for point plot
- Added multiple series for point plot (note - must share a common x value at this stage)


## v0.1.0 : 2020-01-15
Initial version extracted from bigger project