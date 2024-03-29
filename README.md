This repository contains various resources and an instruction to generate the `ValYou`
Ecological data points based on Orchid sighting from raw data / source.

Instructions
------------
The source file (CSV) is available for download on [The Orchid Atlas of Western Australia](http://biocache.ala.org.au/occurrence/search?q=data_resource_uid:dr669)
entry on the [Atlas of Living Australia](http://www.ala.org.au) website.

*** Steps to reproduce ***
  1. CSV preparation:
    1. Trim the CSV to select a subset of columns
    2. Clean the CSV for empty entries
  2. Schema preparation:
    1. Ensure PostGIS is enabled by running `CREATE EXTENSION postgis;` 
    2. Run `sql/1.sql` to setup the `orchid` table
    3. Import the Orchids sighting data via pgAdmin import tool
    4. Run `sql/2.sql` to create and setup the Geometry column
    5. Run `sql/3.sql` to create the required category code entries
  3. Pre-process the `category_values` for Orchid sightings
    1. Run the `py/process.py` script, it will generate a `4.sql`
    2. Run the `sql/4.sql` to populate the `category_values` table with the data