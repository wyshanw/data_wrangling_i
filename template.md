Simple document
================

## Import data

I want to import ‘FAS\_litters.csv’

``` r
litters_df = read_csv("data/FAS_litters.csv")
```

    ## Rows: 49 Columns: 8

    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (2): Group, Litter Number
    ## dbl (6): GD0 weight, GD18 weight, GD of Birth, Pups born alive, Pups dead @ ...

    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

I imported the dataset. Now I want better names

``` r
names(litters_df)
```

    ## [1] "Group"             "Litter Number"     "GD0 weight"       
    ## [4] "GD18 weight"       "GD of Birth"       "Pups born alive"  
    ## [7] "Pups dead @ birth" "Pups survive"

``` r
litters_df = janitor::clean_names(litters_df)
```

Here’s skimr

``` r
skimr::skim(litters_df)
```

|                                                  |             |
|:-------------------------------------------------|:------------|
| Name                                             | litters\_df |
| Number of rows                                   | 49          |
| Number of columns                                | 8           |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |             |
| Column type frequency:                           |             |
| character                                        | 2           |
| numeric                                          | 6           |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |             |
| Group variables                                  | None        |

Data summary

**Variable type: character**

| skim\_variable | n\_missing | complete\_rate | min | max | empty | n\_unique | whitespace |
|:---------------|-----------:|---------------:|----:|----:|------:|----------:|-----------:|
| group          |          0 |              1 |   4 |   4 |     0 |         6 |          0 |
| litter\_number |          0 |              1 |   3 |  15 |     0 |        49 |          0 |

**Variable type: numeric**

| skim\_variable    | n\_missing | complete\_rate |  mean |   sd |   p0 |   p25 |   p50 |   p75 | p100 | hist  |
|:------------------|-----------:|---------------:|------:|-----:|-----:|------:|------:|------:|-----:|:------|
| gd0\_weight       |         15 |           0.69 | 24.38 | 3.28 | 17.0 | 22.30 | 24.10 | 26.67 | 33.4 | ▃▇▇▆▁ |
| gd18\_weight      |         17 |           0.65 | 41.52 | 4.05 | 33.4 | 38.88 | 42.25 | 43.80 | 52.7 | ▃▃▇▂▁ |
| gd\_of\_birth     |          0 |           1.00 | 19.65 | 0.48 | 19.0 | 19.00 | 20.00 | 20.00 | 20.0 | ▅▁▁▁▇ |
| pups\_born\_alive |          0 |           1.00 |  7.35 | 1.76 |  3.0 |  6.00 |  8.00 |  8.00 | 11.0 | ▁▃▂▇▁ |
| pups\_dead\_birth |          0 |           1.00 |  0.33 | 0.75 |  0.0 |  0.00 |  0.00 |  0.00 |  4.0 | ▇▂▁▁▁ |
| pups\_survive     |          0 |           1.00 |  6.41 | 2.05 |  1.0 |  5.00 |  7.00 |  8.00 |  9.0 | ▁▃▂▇▇ |

## Arguments in ‘read\_csv’

``` r
litters_df = read_csv("data/FAS_litters.csv",
                      skip = 5,
                      col_names = F,
                      na = "low8")
```

    ## Rows: 45 Columns: 8

    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (4): X1, X2, X3, X4
    ## dbl (4): X5, X6, X7, X8

    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

## Parsing columns

``` r
litters_data = read_csv(file = "./data/FAS_litters.csv",
  col_types = cols(
    Group = col_character(),
    `Litter Number` = col_character(),
    `GD0 weight` = col_double(),
    `GD18 weight` = col_double(),
    `GD of Birth` = col_integer(),
    `Pups born alive` = col_integer(),
    `Pups dead @ birth` = col_integer(),
    `Pups survive` = col_integer()
  )
)
tail(litters_data)
```

    ## # A tibble: 6 × 8
    ##   Group `Litter Number` `GD0 weight` `GD18 weight` `GD of Birth`
    ##   <chr> <chr>                  <dbl>         <dbl>         <int>
    ## 1 Low8  #79                     25.4          43.8            19
    ## 2 Low8  #100                    20            39.2            20
    ## 3 Low8  #4/84                   21.8          35.2            20
    ## 4 Low8  #108                    25.6          47.5            20
    ## 5 Low8  #99                     23.5          39              20
    ## 6 Low8  #110                    25.5          42.7            20
    ## # … with 3 more variables: Pups born alive <int>, Pups dead @ birth <int>,
    ## #   Pups survive <int>

## Reading fron excel

REading mlb data

``` r
mlb11_df = read_excel("data/mlb11.xlsx")
```

LotR words is next

``` r
fellow_df = read_excel("data/LotR_Words.xlsx", range = "B3:D6")
```

## Read SAS file

Try to read sas file but failed

``` r
#pulse_df = read_sas("data/public_pulse_data.sas7bdat")
```

## why not read.csv

‘read.csv’ does not give ‘tibble’ and that is bad

## how do i export data

there is a good way!

``` r
write_csv(fellow_df, "data/fellowship_words.csv")
```

I’m an R Markdown document!

# Section 1

Here’s a **code chunk** that samples from a *normal distribution*:

``` r
samp = rnorm(100)
length(samp)
```

    ## [1] 100

# Section 2

I can take the mean of the sample, too! The mean is -0.0268652.
