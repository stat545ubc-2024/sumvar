
<!-- README.md is generated from README.Rmd. Please edit that file -->

# easyicer

<!-- badges: start -->
<!-- badges: end -->

This R package is designed as an integrated pipeline with multiple
interconnected functions that can take raw health economic data to
create cost-effectiveness analyses. The functions can be used cohesively
in a step-wise manner or deployed standalone depending on the data
structures used. It contains the `summed_output()` function which takes
a column as a character string storing a vector of numeric values within
a dataframe and calculates the sum of the vector. The `icercalc()` and
`icerplot()` functions can be used to calculate and plot ICER values
based on inputs obtained from `summed_output()`. It is designed to help
users automate repetitive sum operations based on user-defined variable
groupings and filter conditions, and create ICER analyses. An integrated
dataset is included in the source files for this package that was used
to demonstrate package functionality in the package vignette. The raw
dataset can be located in this package’s repository on GitHub. This
package contains multiple dependencies to support syntax compatibility
and plotting with ggplot2.

## Installation

You can install the latest version of easyicer with:

    install.packages("devtools")
    devtools::install_github("stat545ubc-2024/easyicer", ref = "2.0.1")

## Usage

Here is a basic example of using the `summed_output()` function written
in this package with the `palmerpenguins::penguins` dataset:

``` r
library(easyicer)
library(palmerpenguins)

# Create a filter condition and store as an object
sex_male_year_2007 <- palmerpenguins::penguins$sex == "male" & palmerpenguins::penguins$year == 2007

summed_output(data = palmerpenguins::penguins,
              group_vars = c("island", "species"),
              sum_var = "bill_depth_mm",
              filter_vars = sex_male_year_2007,
              na.rm = TRUE)
#> # A tibble: 5 × 3
#> # Groups:   island [3]
#>   island    species   cumulative
#>   <fct>     <fct>          <dbl>
#> 1 Biscoe    Adelie          91.5
#> 2 Biscoe    Gentoo         261. 
#> 3 Dream     Adelie         194. 
#> 4 Dream     Chinstrap      249. 
#> 5 Torgersen Adelie         143.
```

\*For more detailed usage of this package, please refer to the vignette
for this package.
