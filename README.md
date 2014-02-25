# Mathematica CountryPlot and CountryPlot3D

## Usage

* `CountryPlot3D[{{c1, h1}, {c2, h2}, ...}]`    
   Show countries ci with height hi

* `CountryPlot3D[{c1, c2, ...}, prop]`     
  Use heights corresponding to CountryData[ci, prop]

* `CountryPlot3D[prop]`    
  Plot a CountryData property for the whole world

* `CountryPlot[...]`

## Examples

Plot a `CountryData` property for the whole world:

    CountryPlot3D["Population"]

![world population](http://simonschmidt.github.io/Mathematica-CountryPlot/population.png)

Or only for parts of the world:

    CountryPlot3D[{"Europe", "Africa", "Turkey"}, "Population"]

![subset population](http://simonschmidt.github.io/Mathematica-CountryPlot/subsetPopulation.png)

Provide your own data:

    CountryPlot3D[{
      {"Scandinavia", 4},
      {"Germany", 3},
      {"France", 1}},
      "ExtraCountries" -> "Europe",
      "ScaleHeight" -> False]

![custom data](http://simonschmidt.github.io/Mathematica-CountryPlot/custom.png)

Change projection:

    CountryPlot["PovertyFraction", 
      "CartographicProperty" -> {"SchematicPolygon", "LambertConic"}]

![projection](http://simonschmidt.github.io/Mathematica-CountryPlot/projection.png)

## Options

Same as Graphics/Graphics3D with the following additions:

#### ColorFunction
  - Arguments: `height, country,  provided`  where provided is False if it is one of the extra countries
  - Default: `If[#3, ColorData["ThermometerColors"][#2], Gray] &`

#### ColorFunctionScaling

#### "ExtraCountries"    
  Additional countries to plot.
  - `All` make sure all countries are in the plot
  - `country` country or region of countries to include
  - `{country1, country2, ...}`
  - `None`

#### "ExtraHeight"    
  Height for extra countries, default 0

#### "CartographicProperty"    
  Cartographic display property, see `CountryData` documentation for more information, default "SchematicPolygon"

#### "ScaleHeight"    
  Rescale height values
  - `False` do no rescaling
  - `h` rescale heights to between 0 and h
  - `Scaled[h]` Default Scaled[0.1] corresponding to maximum height of 10% of longest side.
