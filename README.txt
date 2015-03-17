--------------------------------------------------------------------------------
CytoscapeWeb revision 29261 (June 5, 2012 - 11:50 am) was used to base network
visualization component for cBio portal! To reproduce necessary executable: portal/web/swf/CytoscapeWeb.swf 
you need to check this revision and make the changes listed below.The changes below enables CytoscapeWeb to support SBGN( Systems Biological Graphical Notation ) for cBio portal.

- src folder includes modified  and newly added classes.
- lib folder includes resultant .swf file after the changes indicated below performed.

Author: Ýstemi Bahçeci<istemi.bahceci@gmail.com>
--------------------------------------------------------------------------------

Modified classes
----------------

/html-template/js/cytoscapeweb.js
- method profileDataAlwaysShown added

/org/cytoscapeweb/view/ExternalMediator.as
- wiring necessary to toggle whether or not profile data should always be shown.

/src/org/cytoscapeweb/ApplicationFacade.as
Modification is done on
- use CBioHandleHoverCommand for the mouse rollover and rollout events.
- use ShowProfileDataCommand to toggle whether or not profile data should always be shown.

/src/org/cytoscapeweb/controller/SelectCommand.as
Modification is done between lines 55~60 & 76 gives support to show detail discs of the selected nodes.

/src/org/cytoscapeweb/controller/DeselectCommand.as
Modification is done between lines 55~60 & 76 gives support to hide detail discs of the deselected nodes.

/src/org/cytoscapeweb/util/Nodes.as
Line 40 - SBGNNodeRenderer is imported. Line 93 - SBGNNodeRenderer is set.

/src/org/cytoscapeweb/util/Edges.as
Line 41 - CBioEdgeRenderer is imported. Line 78 - CBioEdgeRenderer is set.

/src/org/cytoscapeweb/model/GraphProxy.as
Line 796 - New cases is added to method loadGraph to load sbgn-ml graphs.

/src/org/cytoscapeweb/view/GraphMediator.as
Line 875 - "State Variable" and "Unit of Information" glyphs' coordinates also updated 
when their container node is moved.

/src/org/cytoscapeweb/view/render/CBioEdgeRenderer.as
Line 442 - New case "T-ARROW" is added for rendering "necessary stimulation" arc type of SBGN

/src/org/cytoscapeweb/view/render/CompoundNodeRenderer.as
Line 95 - Line width adjusted according to compartment glyphs

/src/org/cytoscapeweb/util/ArrowShapes.as
Line 46 - New string "T_ARROW" is added to support "T-ARROW" ( for necessary stimulation arc type ) through Javascript API

/src/org/cytoscapeweb/view/render/NodeRenderer.as
Line 203 - New case is added for "complex" type glyphs
Line 216 - New function is added for rendering "complex" type glyphs

/src/org/cytoscapeweb/util/CompoundNodes.as
Line 124 - "Complex" shape is added for compound nodes.

/src/org/cytoscapeweb/util/NodeShapes.as
Line 124 - "Complex" shape is added for compound nodes.

New classes
-----------

/src/org/cytoscapeweb/model/converters/SBGNMLConverter.as
Provides necessary functions for manupulating sbgn-ml data

/src/org/cytoscapeweb/view/render/CBioNodeRenderer.as
Extends NodeRenderer, changes render method to be able to draw the detail discs.

/src/org/cytoscapeweb/view/render/CBioEdgeRenderer.as
Extends EdgeRenderer, changes render method to be able to color merged edges.

/src/org/cytoscapeweb/controller/CBioHandleHoverCommand.as
Extends HandleHoverCommand, gives support to show details when a node is highlighted.

/src/org/cytoscapeweb/controller/ShowProfileDataCommand.as
Provides support to enable/disable whether or not profile data should always be shown.

/src/org/cytoscapeweb/view/render/SBGNNodeRenderer.as
Extends NodeRenderer, includes necessary functions to support rendering SBGN specific shapes
