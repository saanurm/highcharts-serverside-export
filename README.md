Highcharts Serverside Export
============================

The primary goal of the Highcharts Serverside Export framework (HSE) is to provide a java API for Highcharts including image generation capabilities.

Solution features
* Java API mapping the Highcharts model,
* Rhino-Apache Batik based renderer : java ChartOptions ==> Rhino ==> Highcharts ==> SVG ==> image (png, JPEG, etc...),


Getting Help
------------

To start to use it, you need to know Highcharts API.

## Highcharts
* See [Highcharts](http://www.highcharts.com/)
* See [Highcharts API Reference](http://www.highcharts.com/ref/)

## Highcharts Serverside Export java doc
* See embeded java doc (./doc)

## Rhino
* See [Rhino](http://www.mozilla.org/rhino/)

## Batik SVG Toolkit
* See [Apache Batik SVG Toolkit](http://xmlgraphics.apache.org/batik/)

Quick Start
-----------

## A java sample : SimpleExport (test/examples/SimpleExport.java)

	public static void main (String[] args) {
		
		// This executable expects an export directory as input
		File exportDirectory = new File (args [0]);
		
		// ====================================================================
		// ChartOptions creation
		// ----------------------
		//  The createHighchartsDemoColumnBasic method describes the creation of 
		//   a java chartOption. It is a java equivalent to javascript Highcharts sample
		//   (see http://highcharts.com/demo/column-basic)
		ChartOptions chartOptions1 = SamplesFactory.getSingleton ().createColumnBasic ();

		// ====================================================================
		// Chart export
		// ----------------
		// Inputs :
		//    1. chartOptions : the java ChartOptions to be exported,
		//    2. exportFile  : file to export to.
		HighchartsExporter pngExporter = ExportType.png.createExporter ();
		pngExporter.export (chartOptions1, null, new File (exportDirectory, "column-basic.png"));
		...
  }

* export directory
You can choose the export directory by changing the java line :
  * windows :  File exportDirectory = new File ("D:\\");
  * linux : File exportDirectory = new File ("/home/myself/export-dir");
  * ...
 
SamplesFactory contains three methods that generate equivalent of Highcharts demo gallery examples :
* SamplesFactory.createColumnBasic : [Basic column](http://highcharts.com/demo/column-basic)
* SamplesFactory.createPieChart : [Pie chart](http://highcharts.com/demo/pie-basic)
* SamplesFactory.createTimeDataWithIrregularIntervals : [Time data with irregular intervals](http://highcharts.com/demo/spline-irregular-time)

## Running the sample
  
* jars
All the dependencies files are provided in ./lib/

* Eclipse :
  The framework is eclipse ready.
   * open the project in eclipse,
   * run SimpleExport
   
* other IDE
   * open the project in your favorite IDE,
   * declare all the ./lib jars as dependencies in your project,
   * run SimpleExport