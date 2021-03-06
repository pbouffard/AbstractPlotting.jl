# Plotting Functions

On this page, the basic plotting functions are listed together with examples of their usage and available attributes.

## `arrows`

```@docs
arrows
```

### Examples

```@example
using GLMakie
AbstractPlotting.inline!(true) # hide

xs = LinRange(1, 10, 20)
ys = LinRange(1, 15, 20)
us = [cos(x) for x in xs, y in ys]
vs = [sin(y) for x in xs, y in ys]

arrows(xs, ys, us, vs, arrowsize = 0.2, lengthscale = 0.3)
```

## `band`

```@docs
band
```

### Examples

```@example
using GLMakie
AbstractPlotting.inline!(true) # hide

xs = 1:0.2:10
ys_low = -0.2 .* sin.(xs) .- 0.25
ys_high = 0.2 .* sin.(xs) .+ 0.25

band(xs, ys_low, ys_high)
band!(xs, ys_low .- 1, ys_high .-1, color = :red)
current_figure()
```

## `barplot`

```@docs
barplot
```

### Examples

```@example
using GLMakie
AbstractPlotting.inline!(true) # hide

xs = 1:0.2:10
ys = 0.5 .* sin.(xs)

barplot(xs, ys, color = :red, strokecolor = :black, strokewidth = 1)
barplot!(xs, ys .- 1, fillto = -1, color = xs, strokecolor = :black, strokewidth = 1)
current_figure()
```

## `contour`

```@docs
contour
```

### Examples

```@example
using GLMakie
AbstractPlotting.inline!(true) # hide

xs = LinRange(0, 10, 100)
ys = LinRange(0, 15, 100)
zs = [cos(x) * sin(y) for x in xs, y in ys]

contour(xs, ys, zs)
```

## `contourf`

```@docs
contourf
```

```@example
using GLMakie
AbstractPlotting.inline!(true) # hide

xs = LinRange(0, 10, 100)
ys = LinRange(0, 10, 100)
zs = [cos(x) * sin(y) for x in xs, y in ys]

contourf(xs, ys, zs, levels = 10)
```


## `errorbars`

```@docs
errorbars
```

### Examples

```@example
using GLMakie
AbstractPlotting.inline!(true) # hide

xs = 0:0.5:10
ys1 = 0.5 .* sin.(xs)
ys2 = ys1 .- 1
ys3 = ys1 .- 2

lowerrors = fill(0.1, length(xs))
higherrors = LinRange(0.1, 0.4, length(xs))


errorbars(xs, ys1, higherrors, color = :red) # same low and high error
errorbars!(xs, ys2, lowerrors, higherrors, color = LinRange(0, 1, length(xs)))
errorbars!(xs, ys3, lowerrors, higherrors, whiskerwidth = 3, direction = :x)

# plot position scatters so low and high errors can be discriminated
scatter!(xs, ys1, markersize = 3, color = :black)
scatter!(xs, ys2, markersize = 3, color = :black)
scatter!(xs, ys3, markersize = 3, color = :black)
current_figure()
```

## `heatmap`

```@docs
heatmap
```

### Examples

```@example
using GLMakie
AbstractPlotting.inline!(true) # hide

xs = LinRange(0, 10, 100)
ys = LinRange(0, 15, 100)
zs = [cos(x) * sin(y) for x in xs, y in ys]

heatmap(xs, ys, zs)
```

## `image`

```@docs
image
```

### Examples

```@example
using GLMakie
AbstractPlotting.inline!(true) # hide
using FileIO

img = rotr90(load("assets/cow.png"))

image(img)
```


## `lines`

```@docs
lines
```

### Examples

```@example
using GLMakie
AbstractPlotting.inline!(true) # hide

xs = 0:0.01:10
ys = 0.5 .* sin.(xs)

lines(xs, ys)
lines!(xs, ys .- 1, linewidth = 5)
lines!(xs, ys .- 2, linewidth = 5, color = ys)
lines!(xs, ys .- 3, linestyle = :dash)
current_figure()
```

## `linesegments`

```@docs
linesegments
```

### Examples

```@example
using GLMakie
AbstractPlotting.inline!(true) # hide

xs = 1:0.2:10
ys = sin.(xs)

linesegments(xs, ys)
linesegments!(xs, ys .- 1, linewidth = 5)
linesegments!(xs, ys .- 2, linewidth = LinRange(1, 10, length(xs)))
linesegments!(xs, ys .- 3, linewidth = 5, color = LinRange(1, 5, length(xs)))
current_figure()
```


## `mesh`

```@docs
mesh
```

```@example
using GLMakie
AbstractPlotting.inline!(true) # hide

vertices = [
    0.0 0.0;
    1.0 0.0;
    1.0 1.0;
    0.0 1.0;
]

faces = [
    1 2 3;
    3 4 1;
]

colors = [:red, :green, :blue, :orange]

scene = mesh(vertices, faces, color = colors, shading = false)
```

## `meshscatter`

```@docs
meshscatter
```

### Examples

```@example
using GLMakie
AbstractPlotting.inline!(true) # hide

xs = cos.(1:0.5:20)
ys = sin.(1:0.5:20)
zs = LinRange(0, 3, length(xs))

meshscatter(xs, ys, zs, markersize = 0.1, color = zs)
```


## `poly`

```@docs
poly
```

### Examples

```@example
using GLMakie
AbstractPlotting.inline!(true) # hide

p1 = Point2f0(0, 0)
p2 = Point2f0(2, 0)
p3 = Point2f0(3, 1)
p4 = Point2f0(1, 1)

poly([p1, p2, p3, p4], color = :red, strokecolor = :black, strokewidth = 1)
```

## `rangebars`

```@docs
rangebars
```

### Examples

```@example
using GLMakie
AbstractPlotting.inline!(true) # hide

vals = -1:0.1:1

lows = zeros(length(vals))
highs = LinRange(0.1, 0.4, length(vals))


rangebars(vals, lows, highs, color = :red)
rangebars!(vals, lows, highs, color = LinRange(0, 1, length(vals)),
    whiskerwidth = 3, direction = :x)
current_figure()
```

## `scatter`

```@docs
scatter
```

### Examples

```@example
using GLMakie
AbstractPlotting.inline!(true) # hide

xs = LinRange(0, 10, 20)
ys = 0.5 .* sin.(xs)

scatter(xs, ys, color = :red)
scatter!(xs, ys .- 1, color = xs)
scatter!(xs, ys .- 2, markersize = LinRange(5, 30, 20))
scatter!(xs, ys .- 3, marker = 'a':'t', strokewidth = 0, color = :black)
current_figure()
```


## `surface`

```@docs
surface
```

### Examples

```@example
using GLMakie
AbstractPlotting.inline!(true) # hide

xs = LinRange(0, 10, 100)
ys = LinRange(0, 15, 100)
zs = [cos(x) * sin(y) for x in xs, y in ys]

surface(xs, ys, zs)
```

## `text`

```@docs
text
```

### Examples

```@example
using GLMakie
AbstractPlotting.inline!(true) # hide

scene = Scene(camera = campixel!, show_axis = false, resolution = (600, 600))

text!(scene, "AbstractPlotting", position = Point2f0(300, 500),
    textsize = 30, align = (:left, :bottom), show_axis = false)
text!(scene, "AbstractPlotting", position = Point2f0(300, 400),
    color = :red, textsize = 30, align = (:right, :center), show_axis = false)
text!(scene, "AbstractPlotting\nMakie", position = Point2f0(300, 300),
    color = :blue, textsize = 30, align = (:center, :center), show_axis = false)
text!(scene, "AbstractPlotting\nMakie", position = Point2f0(300, 200),
    color = :green, textsize = 30, align = (:center, :top), rotation = pi/4, show_axis = false)
```

## `volume`

```@docs
volume
```

### Examples

```@example
using GLMakie
AbstractPlotting.inline!(true) # hide

r = LinRange(-1, 1, 100)
cube = [(x.^2 + y.^2 + z.^2) for x = r, y = r, z = r]
cube_with_holes = cube .* (cube .> 1.4)

volume(cube_with_holes, algorithm = :iso, isorange = 0.05, isovalue = 1.7)
```
