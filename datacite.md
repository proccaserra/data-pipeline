# DataCite

The CSV file [datacite.csv](https://github.com/biocaddie/data-pipeline/blob/master/datacite.csv) contains a list of DataCite data repositories in the life sciences. This list is manually curated.

* To get more information about the data repository, use `re3data_id: `http://service.re3data.org/repository/RE3DATA_ID`
* To see all datasets in the repository, use `symbol`: `http://search.datacite.org/data-centers/SYMBOL`
* To retrieve the metadata in DATS format via API call, use `http://api.datacite.org/dats?publisher-id=SYMBOL`

## API

General information about the DataCite API is available at [https://api.datacite.org](https://api.datacite.org). The `/dats` API endpoint is work in progress and feedback is appreciated. The source code is at [https://github.com/datacite/spinone/blob/master/app/models/dataset.rb](https://github.com/datacite/spinone/blob/master/app/models/dataset.rb).

### Lists

Lists results can contain multiple entries. Searching or filtering typically returns a list result. A list has two parts:

* **meta**, which includes information about the query, e.g. number of results returned.
* **data**, which will will contain the items matching the query or filter.

### Sort order

If the API call includes a query, then the sort order will be by the relevance score. If no query is included, then the sort order will be by DOI deposit date. Results can be sorted by `deposited`, `published`, `updated` and `score`.

### Parameters

Parameters can be used to query, filter and control the results returned by the DataCite API. They can be passed as normal URI parameters or as JSON in the body of the request.

| Parameter                    | Description                 |
|:-----------------------------|:----------------------------|
| `query`                      | limited [DisMax](https://wiki.apache.org/solr/DisMax) query terms |
| `rows`                       | results per per page |
| `offset`                     | result offset |
| `sort`                       | sort results by a certain field |
| `order`                      | set the sort order to `asc` or `desc` |

### Examples

* [http://api.datacite.org/dats?publisher-id=osti.nimh](http://api.datacite.org/dats?publisher-id=osti.nimh)
* [http://api.datacite.org/dats?publisher-id=cdl.tcia&sort=updated](http://api.datacite.org/dats?publisher-id=cdl.tcia&sort=updated)
* [http://api.datacite.org/dats?publisher-id=cdl.broad&sort=deposited&offset=2000](http://api.datacite.org/dats?publisher-id=cdl.broad&sort=deposited&offset=2000)
* [http://api.datacite.org/dats?publisher-id=bl.lshtm&resource-type-id=dataset](http://api.datacite.org/dats?publisher-id=bl.lshtm&resource-type-id=dataset)



