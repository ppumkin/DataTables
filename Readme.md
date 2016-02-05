# DataTables tbody colspan patch

This is a fork of the main DataTables repository that has a patch applied in the column/cell parser engine to allow rows with colspan in the tbody to be loaded.

This is a very basic patch that was created to prevent inititialisastion blow up caused by missing number '<td>` in rows. The engine is built in such a way that the td must be equal or more than in the header. Since colspan takes up visual space of these cells but in the markup you use one less td, then parsing engine fails because it cannot build a consistent data object. Funnily enough, when you have more td than expected, they get ignored.

# What does this patch mean then? 

Simply put.

 - Any shortfall in '<td>' when parsing from DOM, will get initialised with a default value of "" (Empty String)
 - Visually, your colspan row will span as youd expect it. 
 - Searching will return expected results for remainder of rows as expected
 - Sorting the "empty" column will show empty cells at top (A->Z) or bottom (Z->A)
 - DOM structure is not affected
 - 
# Maintanence

The original creator of the script has done a magnificient job with DataTables. He has expressed great concern with supporting colspan and rowspan in tbody. So in short, there is no maintanence of this patch. It comes as it is and if you feel like creating an issue, maybe ill fix it maybe not. 

I will try and keep this fork with the latest head

These changes may impact stability within other parts of this script. 
No regression tests have been done so use at your own risk.

--Original Readme--

# DataTables plug-in for jQuery

DataTables is a table enhancing plug-in for the [jQuery](//jquery.com) Javascript library, adding sorting, paging and filtering abilities to plain HTML tables with minimal effort. The stated goal of DataTables is:

> To enhance the accessibility of data in HTML tables.

To meet this goal, DataTables is developed with two distinct groups of users in mind:

* You the developers using DataTables. For developers DataTables provides a wide array of options for how data should be obtained, displayed and acted upon, along with an extensive API for accessing and manipulating the table.

* End users. For those using the interface DataTables presents, actions to get the most from the information contained in tables, such as sorting and filtering, along with paging and scrolling of the data in table, are easy to use, intuitive and fast.


## Installation

In most cases, to use DataTables all you need to do is include jQuery, the DataTables Javascript and DataTables CSS files in your HTML page. See the [DataTables manual](http://datatables.net/manual/installation#Including-Javascript-/-CSS) for details on how to do this using the latest version of DataTables.


## Usage

In its simplest case, DataTables can be initialised with a single line of Javascript:

```js
$('table').dataTable();
```

where the jQuery selector is used to obtain a reference to the table you want to enhance with DataTables. Optional configuration parameters can be passed in to DataTables to have it perform certain actions by using a configuration object as the parameter passed in to the DataTables constructor. For example:

```js
$('table').dataTable( {
  paginate: false,
  scrollY: 300
} );
```

will disable paging and enable scrolling.

A full list of the options available for DataTables are available in the [documentation](//datatables.net).


## Documentation

Full documentation of the DataTables options, API and plug-in interface are available on the [DataTables web-site](//datatables.net). The site also contains information on the wide variety of plug-ins that are available for DataTables, which can be used to enhance and customise your table even further.


## Support

Support for DataTables is available through the [DataTables forums](//datatables.net/forums) and [commercial support options](//datatables.net/support) are available.


## License

DataTables is release under the [MIT license](//datatables.net/license). You are free to use, modify and distribute this software, as long as the copyright header is left intact (specifically the comment block which starts with `/*!`.
