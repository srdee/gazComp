# gazComp
gazComp is a web application used to compare gazetteers with a human brain.
Currently two gazetteer sources can be compared, Pleiades and Geonames.

gazComp's architecture allows for other gazetteer sources to be defined.
See the following classes in src/js/gazComp.js

* gazComp.Data
* gazComp.GeonamesData
* gazComp.PleiadesData

# Requirements
* jQuery
* Google Maps API

# Installation
Create an HTML document with an empty &lt;body&gt; tag pair.
Include the required Javascript and CSS files.

	<link href="gazComp/src/css/gazComp.css" rel="stylesheet" type="text/css" />
	<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.10.2/jquery.min.js"></script>
	<script type="text/javascript" src="gazComp/src/js/gazComp.js"></script>
	<script type="text/javascript" src="https://maps.googleapis.com/maps/api/js?key=#{API_Key}&sensor=false"></script>

# Use
Initialize gazComp.App passing along the URL to the server-side script which will receive data generated by gazComp.

	var gaz = new gazComp.App( '#{path_to_your_server_script}' );

Call the compare method passing along two data sources.
Data sources are instances of classes that extend gazComp.Data.

	gaz.compare( new gazComp.GeonamesData( '2343234' ), new gazComp.PleiadesData( '83473298' ) );


# Define a new gazComp collection class.
gazComp collection classes extend gazComp.Data.
Collection classes are interfaces to retrieve data from specific gazetteer collections, for example Geonames http://www.geonames.org/ and Pleiades http://pleiades.stoa.org/.

Each class must defined a custom get() method to retrieve data from the collection.
The class must also defined a custom convert() method to change retrieved data into a standardized gazComp data object.