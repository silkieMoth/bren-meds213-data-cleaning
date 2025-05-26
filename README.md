# Cleaning the shorebird survey data 


## The data set

ARCTIC SHOREBIRD DEMOGRAPHICS NETWORK [https://doi.org/10.18739/A2222R68W](https://doi.org/10.18739/A2222R68W)

Data set hosted by the [NSF Arctic Data Center](https://arcticdata.io) data repository 

Field data on shorebird ecology and environmental conditions were collected from 1993-2014 at 16 field sites in Alaska, Canada, and Russia.

This project aims to clean the Snow_cover dataset.

![Shorebird, copyright NYT](https://static01.nyt.com/images/2017/09/10/nyregion/10NATURE1/10NATURE1-superJumbo.jpg?quality=75&auto=webp)

Data were not collected every year at all sites. Studies of the population ecology of these birds included nest-monitoring to determine the timing of reproduction and reproductive success; live capture of birds to collect blood samples, feathers, and fecal samples for investigations of population structure and pathogens; banding of birds to determine annual survival rates; resighting of color-banded birds to determine space use and site fidelity; and use of light-sensitive geolocators to investigate migratory movements. 

Data on climatic conditions, prey abundance, and predators were also collected. Environmental data included weather stations that recorded daily climatic conditions, surveys of seasonal snowmelt, weekly sampling of terrestrial and aquatic invertebrates that are prey of shorebirds, live trapping of small mammals (alternate prey for shorebird predators), and daily counts of potential predators (jaegers, falcons, foxes). Detailed field methods for each year are available in the `ASDN_protocol_201X.pdf` files. All research was conducted under permits from relevant federal, state, and university authorities.



## File List and Overview

    shorebird-data-cleaning
    │
    ├── data/ 
    │   └── land_cover.csv   # cleaned land cover data by site/date/plot
    ├── qmds/ 
    │   ├── eds213_data_cleaning_assign_JOSHUAPAULCOHEN_revision.qmd  # produce clean land_cover.csv
    │   ├── data-cleaning_4_hw.qmd  # initial cleaning of the data
    │   └── data-cleaning_empty.qmd  # another variation of above
    │
    ├── eds213_data_cleaning_assign_JOSHUAPAULCOHEN.html # describes data cleaning process
    │
    │
    │
    ├── bren-meds213-data-cleaning.Rproj
    ├── README.md 
    └── .gitignore 

> This dataset contains only a cleaned subset of the data it originates from (Arctic Shorbird Demographics Network). It was not included in this repository.


## Metadata for land_cover.csv
* \# of variables
  + 11 variables in total
* \# of observations
  + 40632 observations
* Variables list and descriptions
  + Site
    - 4 letter code representing a particular study site
    - Limitations: string, required length 4
    - value examples
      + barr
      + nome
  + Year
    - year of observation
    - Limitations: int, required length 4
    - value examples
      + 2013
  + Date 
    - m/d/y date of observation
    - Limitations: required date format
    - value examples
      + 7-Jun-11
  + Plot
    - code representing the plot of a given observation in a study site
    - Limitations: string, required length 4
    - value examples
      + brw6
      + 5b
      + 22
  + Location
    - code for a particular location within a plot for the roughly 8cm<sup>2</sup> malaise traps. separated by a space of 20m.
    - Limitations: string, no other restrictions. see metadata for details
    - value examples
      + b12
      + j8
      + 11
  + Snow_cover, Water_cover, Land_cover
    - total cover of snow, water an land in a given trap location respectively. Should sum to 100 except in cases of error.
    - Limitations: int, must be > 0 and < 100
    - units: %
    - value examples
      + 10, 40, 50
      + 0, 100, 0
  + Total_cover
    - the sum of all covers variables. Should be 100 in all circumstances, except in cases of error
    - Limitations: int, must be > 0 and < 100 
    - units: %
    - value examples
      + 100
  + Observer
    - abbreviation representing the scientist recording data for a given observation
    - Limitations: string
    - Value examples
      + jwebber
      + lrensel
  + Notes
    - any added comments
* Cleaning process
  + Cover columns were recalculated to equal 100, or were removed if ther was no way to mediate this error
  + Total cover was forced to be within 0-100 if the erroneous value was within 50 of the accepted range. Else, it was removed.
  + Missing data values that were not NA were shifted to be such.
  + Rows were still faulty after these corrections, they were removed.

* some missing data values were recorded as "unk" or "n/a". 

## Licensing and Sharing

The Arctic Shorebird Demographics Network is licensed under the Creative Commons Attribution 4.0 International License.

This dataset is hosted by the [Arctic Data Center: https://arcticdata.io/](https://arcticdata.io/)

[Link to data access: https://arcticdata.io/catalog/view/doi:10.18739/A2222R68W](https://arcticdata.io/catalog/view/doi:10.18739/A2222R68W)

**Citing this project**: Include name of repository owner and link to repository or Github profile. Otherwise, citation format is at user's discretion.