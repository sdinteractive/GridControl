#GridControl

Upstream has been abandoned so SD is maintaining this fork as this is still our preferred solution for updating admin grids.

### Features
- Add columns
- Remove columns
- Change columns
- Move columns
- Add new attributes
- Join new attributes

### Usage
First install this module. Next, create a separate module. Initially, you really only need one file which should be named, gridcontrol.xml and should be stored in the the etc folder. Eventually, you main wind up needing to create additional files such as renderers or models to fetch option arrays.

### XML Syntax
Refer to `app/code/community/FireGento/GridControl/etc/gridcontrol.xml.dist` for sample XML

### Add strategies

There are several strategies that can be employed for adding columns to a grid. You can view how these strategies are implemented in `FireGento_GridControl_Model_Observer::eavCollectionAbstractLoadBefore()`

##### `<index>`
The value in contained in the `<index>` node will be passed to `$event->getCollection()->addAttributeToSelect()`
Necessary for proper filtering and sort. 

##### `<joinAttribute>`
Expects 5 pipe delimited arguments which will be passed to `$event->getCollection()->joinAttribute()`

##### `<joinField>`
Expects 6 pipe delimited arguments which will be passed to `$event->getCollection()->joinField()`

##### `<join>`
Expects an XML node with a `table`, `condition` and `field` attribute, which will be passed to `$event->getCollection()->join()`. `{{table}}` will be replaced with the actual table name. It's a mess how this is in no way consistent with the others. This was inherited from upstream.

### Todo
- Configuration GUI (or just a system config that takes arbitrary XML and is merged with the modules gridcontrol.xml files?)

