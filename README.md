# Single File STAC Extension Specification

- **Title:** Single File STAC
- **Identifier:** <https://stac-extensions.github.io/single-file-stac/v1.0.0/schema.json>
- **Field Name Prefix:** -
- **Scope:** Item, Collection
- **Extension [Maturity Classification](https://github.com/radiantearth/stac-spec/tree/master/extensions/README.md#extension-maturity):** Proposal
- **Owner**: @matthewhanson

An extension to provide a set of Collections and Items within a single file catalog. The single file is a STAC catalog that contains everything
that would normally be in a linked set of STAC files. This format is useful to save a portion of a catalog, or when creating a small catalog 
from derived data that should remain portable. It is most useful for saving the results of a search from a STAC API, as the 
Items, Collections, and optionally the search parameters are all saved within the single file. Hierarchical links have no meaning in a 
single file STAC, and so, if present, should be removed when creating a single file catalog.

- Examples:
  - [STAC example](examples/item-collection.json): Shows the basic usage of the extension in a STAC ItemCollection
- [JSON Schema](json-schema/schema.json)
- [Changelog](./CHANGELOG.md)

## Item Properties and Collection Fields

A Single File STAC is a set of Items and their Collections presented as a [GeoJSON FeatureCollection](https://tools.ietf.org/html/rfc7946#section-3.3) 
contained in a single file.

| Field Name         | Type   | Description                                                  |
| ------------------ | ------ | ------------------------------------------------------------ |
| type               | string | **REQUIRED.** Type of the GeoJSON Object. MUST be set to `FeatureCollection`. |
| collections | \[[Collection](https://github.com/radiantearth/stac-spec/tree/master/collection-spec/collection-spec.md#collection-fields)] | An array of STAC Collections that are used by any of the Items in the catalog. |
| features    | **REQUIRED.** \[[Item](https://github.com/radiantearth/stac-spec/tree/master/item-spec/item-spec.md#item-fields)] | An array of STAC Items |
