<!-- .slide: data-background="./images/bg-1.png" -->

<h2 style="font-size: 2em;">BIM/Revit and Building Scene Layer</h2>

By &Ouml;zg&uuml;r Ertac &amp; Yannik Messerli

---

<!-- .slide: data-background="./images/bg-2.png" -->

# Agenda

- Introduction to BIM and Revit
- Revit-as-a-service
- Introduction to ArcGIS Javascript API
- Using the BuildingSceneLayer
- Go beyond (the walls)

---

<!-- .slide: data-background="./images/bg-2.png" -->

## Building Information Modeling


***BIM is a process not an application!***


---

<!-- .slide: data-background="./images/bg-2.png" -->

### Building Information Modeling

<div style="text-align: justify;">
A 3D model-based process that provides professionals info and tools to efficiently plan, design, construct and manage buildings and structures.

A BIM object is a combination of:
- Design
- Geometry for physical chracteristics
- Relations and attributes (Meta Data)
- Intelligent 2D- & 3D-Objects
</div>

---

<!-- .slide: data-background="./images/bg-2.png" -->

## Revit Data

<div style="text-align: left;">
Revit is not BIM, Revit is built for BIM

- design with parametric modeling and drafting elements
- mutliple views of same geometry
- a change anywhere is a change everywhere

</div>

---

<!-- .slide: data-background="./images/bg-2.png" -->

## Revit Data

<div style="text-align: left;">

Other BIM standards / software
- IFC
- Bentley Arch
- Allplan
- BricsCAD and [many more](https://financesonline.com/building-information-modeling/)
</div>

---

<!-- .slide: data-background="./images/bg-2.png" -->

## Georeference a Revit Data

<div style="text-align: left;">
ArcGIS Pro can display Revit in correct location!
Requirements:

- Projection file (name.prj)
- World file (name.wld3)
- Revit control points (Project Base Point, Survey Point)

</div>

---

<!-- .slide: data-background="./images/bg-2.png" -->

### Georeference a Revit Data

<img class="plain" src="./images/revit_prj_base.png" background=none>


---

<!-- .slide: data-background="./images/bg-2.png" -->

### Revit in ArcGIS Pro

<img class="plain" src="./images/revit_in_pro_s.png" background=none>

---

<!-- .slide: data-background="./images/bg-2.png" -->

### Revit in ArcGIS Pro

<img class="plain" src="./images/read_revit_s.png" background=none>

---

<!-- .slide: data-background="./images/bg-2.png" -->

### Sharing Revit as a Service

<div style="text-align: left;">
Introducing a new I3S layer for buildings

- Building Scene Layer (Pro 2.3, Enterprise 10.7) 
- Model categories in Revit data structure
- Load Revit in ArcGIS Pro -> Share as SLPK -> Upload to Portal
- Visual filtering, saved filters & levels, categories

</div>

---

<!-- .slide: data-background="./images/bg-2.png" -->

### Sharing Revit as a Service

<div style="text-align: left;">
Limitations

- one revit file -> one building scene layer
- not updatable from source directly
- no materials / textures

</div>

---

<!-- .slide: data-background="./images/bg-2.png" -->

### <b>Consuming a Service</b>

<img class="plain" src="./images/recap-5.png" background=none>

---

<!-- .slide: data-background="./images/bg-2.png" -->

## ArcGIS Javascript API

   
- Visual mapping (2D & 3D), components and widgets
- Support for various different layer types (data sources)
- Integration with the ArcGIS platform (security, sign-in, premium services, …)

<div style="font-size: 75%" class="twos">

> Find doc & samples to get started at [https://developers.arcgis.com/javascript](https://developers.arcgis.com/javascript)

<blockquote>
<h4 style="padding: 0 40px;">ArcGIS API for JavaScript Programming Patterns and API Fundamentals with version 4.x</h4>
<div style="text-align: center;">Mon, 2:00 p.m. — 2:45 p.m | Ballroom ABC</div>

</blockquote>

</div>

---

<!-- .slide: data-background="./images/bg-2.png" -->

<div class="code-snippet" style="max-width: 600px; font-size: 130%; float: none; margin: auto;">
    <pre><code style="margin-bottom: -30px;" class="lang-html">
    &lt;!DOCTYPE html&gt;
    &lt;html&gt;
    &lt;head&gt;
      &lt;meta charset=&quot;utf-8&quot;&gt;
    </code>
    <code style="margin-bottom: -30px;" class="lang-html">
      &lt;link rel=&quot;stylesheet&quot; href=&quot;//js.arcgis.com/4.13/esri/css/main.css&quot;&gt;
      &lt;script src=&quot;//js.arcgis.com/4.13/&quot;&gt;&lt;/script&gt;
    </code>
    <code style="margin-bottom: -30px;" class="lang-js">
      &lt;title&gt;Create a 3D map&lt;/title&gt;
    &lt;/head&gt;
    &lt;body&gt;
      &lt;script&gt;
    </code>
    <code style="margin-bottom: -30px;" class="lang-js">
        require([
          "esri/WebScene",
          "esri/views/SceneView",
          "dojo/domReady!"
        ], function(WebScene, SceneView) {
          var scene = new WebScene();
          var view = new SceneView({
            container: "viewDiv",
            map: scene
          });
        });
    </code>
    <code class="lang-html">
      &lt;/script&gt;
      &lt;div id=&quot;viewDiv&quot;&gt;&lt;/div&gt;
    &lt;/body&gt;
    &lt;/html&gt;
    </code><div style="clear: both; height: 30px;"></div></pre>
</div>

---

<!-- .slide: data-background="./images/bg-2.png" -->

<iframe id="scene-view-map-view" data-src="./snippets/setup-snippet-1.html" scrolling="no" style="overflow: hidden;padding: 0; width: 685px;height:592px;"></iframe>

---

<!-- .slide: data-background="./images/bg-2.png" -->

## Architecture
<br/>
<img src="./images/concepts-architecture2.png" width="60%" style="border: none; background: none; box-shadow: none"/>

---

<!-- .slide: data-background="./images/bg-2.png" -->

## Layers

- GIS information (features of same type)
- Related properties (shape, etc...) 

---

<!-- .slide: data-background="./images/bg-2.png" -->

## Layers

<table>
<tbody><tr>
<td><code>FeatureLayer</code></td>
<td><small>2D &amp; 3D</small></td>
</tr>
<tr>
<td><code>CSVLayer</code></td>
<td><small>2D &amp; 3D</small></td>
</tr>
<tr>
<td><code>MapImageLayer</code></td>
<td><small>2D &amp; 3D</small></td>
</tr>
<tr>
<td><code>ImageryLayer</code></td>
<td><small>2D &amp; 3D</small></td>
</tr>
<tr>
<td><code>WMSLayer</code></td>
<td><small>2D &amp; 3D</small></td>
</tr>
<tr>
<td><code>TileLayer</code></td>
<td><small>2D &amp; 3D</small></td>
</tr>
<tr>
<td><code>WMTSLayer</code></td>
<td><small>2D &amp; 3D</small></td>
</tr>
<tr>
<td><code>VectorTileLayer</code></td>
<td><small>2D &amp; 3D</small></td>
</tr>
<tr>
<td><code>ElevationLayer</code></td>
<td><small> 3D only</small></td>
</tr>
<tr>
<td><code>SceneLayer</code></td>
<td><small> 3D only</small></td>
</tr>
<tr>
<td><code>BuildingSceneLayer</code></td>
<td><small> 3D only</small></td>
</tr>
</tbody></table>

---

<!-- .slide: data-background="./images/bg-2.png" -->

## [`SceneLayer`](https://developers.arcgis.com/javascript/latest/api-reference/esri-layers-SceneLayer.html)

- Optimized for large data
- [`BuildingSceneLayer`](https://developers.arcgis.com/javascript/latest/api-reference/esri-layers-BuildingSceneLayer.html) is a variation of it for BIM data.

---

<!-- .slide: data-background="./images/bg-2.png" -->

<div class="code-snippet" style="max-width: 600px; font-size: 200%; float: none; margin: auto;">
<pre>
<code style="margin-bottom: -40px;" class="lang-js">
var layer = new BuildingSceneLayer({
  portalItem: {
    url: "https://..." // Url of service
  }
});
scene.add(layer);
</code><div style="clear: both; height: 30px;"></div>
</pre>
</div>

---

<!-- .slide: data-background="./images/bg-2.png" -->

<iframe id="setup-snippet-2" data-src="./snippets/setup-snippet-2.html" scrolling="no" style="overflow: hidden;padding: 0;"></iframe>

---

<!-- .slide: data-background="./images/bg-2.png" -->

## `BuildingSceneLayer` 

- Same properties than `SceneLayer`, with additions:
- `filters` and the `activeFilterId`
- `sublayers`

<blockquote style="padding: 30px;"><small style="line-height: 1.9em;">
Additional fields from <code style="vertical-align: middle;">SceneLayer</code>: <code style="vertical-align: middle;">renderer</code>, <code style="vertical-align: middle;">definitionExpression</code>, <code style="vertical-align: middle;">popupTemplate</code>, ...
</small>
</blockquote>

---

<!-- .slide: data-background="./images/bg-2.png" -->

### Building Sublayers

`BuildingComponentSublayer` or `BuildingGroupSublayer`

<br>

- `ModelName` is a standard name for each sublayer
- `visible` if the sublayer is visible in the view 
- `opacity` of the sublayers individually
- `sublayers` if `BuildingGroupSublayer`


---

<!-- .slide: data-background="./images/bg-2.png" -->

## Building Sublayers

<div class="twos">
  <div>
    <br>    <br>
    <h4>First level of sublayers:<h4>
    <img src="./images/shellvsfull.png" alt="">
  </div>
  <div class="snippet-preview">
    <iframe id="code-snippet-3" data-src="./snippets/setup-snippet-3.html" scrolling="no" style="overflow: hidden;padding: 0; min-width: 400px;" frameborder="0"></iframe>
  </div>
</div>

---

<!-- .slide: data-background="./images/bg-2.png" -->

## Disciplines

<h4>Second level of sublayers<h4>
<img src="./images/sublayers.png" style="margin-left: -200px; width: 850px;" alt="" />

---

<!-- .slide: data-background="./images/bg-2.png" -->

## Disciplines

<h4>Second level of sublayers<h4>

<iframe id="code-snippet-3" data-src="./snippets/setup-snippet-3.html" scrolling="no" style="overflow: hidden;padding: 0; width: 700px; min-height: 261px;height: 400px;" frameborder="0"></iframe>

---

<!-- .slide: data-background="./images/bg-4.png" -->
## Filtering

---

<!-- .slide: data-background="./images/bg-2.png" -->

-  Multiple `BuildingFilter` can be added to `BuildingSceneLayer.filters[]`
-  Only one active through `BuildingSceneLayer.activeFilterId`

---

<!-- .slide: data-background="./images/bg-2.png" -->

### [`BuildingFilter`](https://developers.arcgis.com/javascript/latest/api-reference/esri-layers-support-BuildingFilter.html#filterBlocks)

<div class="code-snippet" style="font-size: 200%;"><pre ><code style="padding: 0px 50px;" class="lang-js">
const buildingFilter = new BuildingFilter({
  filterBlocks: [{
    // an SQL expression that filters using the BldgLevel field
    filterExpression: "BldgLevel = 3",
    filterMode: {
      type: "solid" // "wire-frame" !!
    }
  }]
});
// set the filter in the filters array on the layer
buildingLayer.filters = [buildingFilter];
// specify which filter is the one that should be applied
buildingLayer.activeFilterId = buildingFilter.id;
</code></pre></div>

---

<!-- .slide: data-background="./images/bg-2.png" -->

### [`BuildingFilter`](https://developers.arcgis.com/javascript/latest/api-reference/esri-layers-support-BuildingFilter.html#filterBlocks)

<iframe id="setup-snippet-2" data-src="./snippets/filters.html" scrolling="no" style="overflow: hidden;padding: 0;"></iframe>

---

<!-- .slide: data-background="./images/bg-2.png" -->

### Attribute to Filter

- `Discipline` (Architectural, Plumbing, ...)
- `Category` (Furniture, Door, Panel, ...)
- `Family` ("basic wall", "panels", ...)
- `FamilyType` (e.g. "Glass 4")
- `BldgLevel`
- `CreatedPhase` / `DemolishedPhase`
- `RoomType`

<blockquote>
<small>
  More at <a href="https://pro.arcgis.com/en/pro-app/help/mapping/layer-properties/filter-a-building-scene-layer.htm">pro.arcgis.com/en/pro-app/help/mapping/layer-properties/filter-a-building-scene-layer.htm</a>
</small>
</blockquote>

---

<!-- .slide: data-background="./images/bg-1.png" -->

## Demo

<small style="margin: auto; margin-top: -30px; margin-bottom: -30px; text-align: center;">
  <a href="https://github.com/Esri/building-viewer/">https://github.com/Esri/building-viewer</a>
</small>

<a href="https://esri.github.io/building-viewer"><img src="./images/building-viewer.png" alt="https://github.com/Esri/building-viewer/" style="margin-top: -30px;"></a>

---

<!-- .slide: data-background="./images/bg-1.png" -->


<div style="text-align: left;">
  <h2>Thank you!</h2>
  <br>
<h4>&Ouml;zg&uuml;r Ertac</h4>
<div style="margin-top: -30px; margin-bottom: 20px;font-size: 0.7em;">@Oertac_gis</div>
<h4>Yannik Messerli</h4>
<div style="margin-top: -30px; margin-bottom: 20px;font-size: 0.7em;">
linkedin.com/in/yannikmesserli</div>
</div>

---

<!-- .slide: data-background="./images/bg-2.png" -->

### Please Take Our Survey on the App

<img class="plain" src="./images/survey.png" background=none>

---

<!-- .slide: data-background="images/bg-final.png" -->
