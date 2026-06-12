---
title: "GIS and GeoServer"
date: 2007-05-22
forum: Education &amp; Science
---

### Post by mwacky on 2007-05-22
Anyone out there using GeoServer with ubuntu?  I've been looking around the [UbuntuGIS Wiki]("https://wiki.ubuntu.com") and it does not mention it.

---

### Post by Gus-O-Matic on 2007-06-10
I've been running Geoserver on a dapper server for quite a while now, I seem to remember it didn't work with the ubuntu version of tomcat for some reason so I had to manually install both.

---

### Post by shivantha17 on 2008-06-09
> **Gus-O-Matic said:**
> I've been running Geoserver on a dapper server for quite a while now, I seem to remember it didn't work with the ubuntu version of tomcat for some reason so I had to manually install both.

no need to install TomCat.
Just install geoserver and Java 1.5
set JAVA_HOME variable and 
just run as sudo ./startup.sh


have fun with geoserver
:lolflag:

---

### Post by gsknaidu-pg7 on 2009-02-03
Hi,
i am new to GIS stuff, currently doing project on "Vehicle Fleet Tracking System".
I am planning to use wireless module XT65, from this device we will get the track details about vehicle that details to show on the map...what i have to do(GIS stuff)?
I am planning to use Geoserver+googlemap(wms)+postgresql...but i am not able to do.
i confused, how the gps stuff will integrate with googlemap through geoserver.
If any other choice please suggest to me.........


thanks in advance,


with sincerely,t
gudivada

---

### Post by blastus on 2009-02-20
> **gsknaidu-pg7 said:**
> Hi,
i am new to GIS stuff, currently doing project on "Vehicle Fleet Tracking System".
I am planning to use wireless module XT65, from this device we will get the track details about vehicle that details to show on the map...what i have to do(GIS stuff)?
I am planning to use Geoserver+googlemap(wms)+postgresql...but i am not able to do.
i confused, how the gps stuff will integrate with googlemap through geoserver.
If any other choice please suggest to me.........


thanks in advance,


with sincerely,t
gudivada

A WMS server provides images, specifically map images. With a WMS server you can overlay map tiles on any map client that supports custom tile layers. This includes OpenLayers, Virtual Earth, Google Maps etc...

In Google Maps, you override the getTileUrl method in GTileLayer to convert the x, y, and zoom to a WMS request to GeoServer. If you look in the GeoServer installation directory you'll find a Google maps example along with a supporting JavaScript file that does the math.

---

### Post by anitagraser on 2009-10-13
Hi all!

I'm having problems starting geoserver. I installed geoserver2.0 and tomcat6 (only read afterwards that it wasn't needed). 
Then, I added the following two lines to startup.sh and shutdown.sh:

anita@anita-desktop:/etc/geoserver-2.0-RC1/bin$ head startup.sh
JAVA_HOME="/usr/lib/jvm/java-6-sun";
GEOSERVER_HOME="/etc/geoserver-2.0-RC1";

But when trying to start geoserver I get the following error messages:

anita@anita-desktop:/etc/geoserver-2.0-RC1/bin$ sudo ./startup.sh
GEOSERVER DATA DIR is /etc/geoserver-2.0-RC1/data_dir
0 [main] INFO org.mortbay.log - Logging to org.slf4j.impl.SimpleLogger@63415de6 via org.mortbay.log.Slf4jLog
161 [main] WARN org.mortbay.log - Deprecated configuration used for /etc/geoserver-2.0-RC1/webapps
182 [main] INFO org.mortbay.log - jetty-6.1.8
Oct 13, 2009 10:13:54 AM it.geosolutions.imageio.gdalframework.GDALUtilities loadGDAL
WARNING: Native library load failed.java.lang.UnsatisfiedLinkError: no gdaljni in java.library.path
log4j:WARN File option not set for appender [geoserverlogfile].
log4j:WARN Are you using FileAppender instead of ConsoleAppender?
1268 [main] INFO /geoserver - Initializing Spring root WebApplicationContext
13 Oct 10:13:55 ERROR [geoserver.global] - 
----------------------------------
- GEOSERVER_DATA_DIR: /etc/geoserver-2.0-RC1/data_dir
----------------------------------
13 Oct 10:13:55 INFO [org.geoserver] - Loaded style 'tiger_roads'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded style 'poly_landmarks'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded style 'dem'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded style 'pophatch'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded style 'poi'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded style 'capitals'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded style 'cite_lakes'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded style 'green'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded style 'population'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded style 'rain'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded style 'polygon'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded style 'grass'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded style 'simple_roads'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded style 'line'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded style 'giant_polygon'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded style 'restricted'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded style 'simple_streams'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded style 'concat'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded style 'burg'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded style 'raster'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded style 'point'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded style 'flags'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded workspace 'sde'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded workspace 'topp'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded store 'taz_shapes', enabled
13 Oct 10:13:55 INFO [org.geoserver] - Loaded data store 'taz_shapes'
13 Oct 10:13:55 WARN [referencing.factory] - Axis elements found in a wkt definition, the force longitude first axis order hint might not be respected:
PROJCS["WGS84 / Simple Mercator", GEOGCS["WGS 84", DATUM["WGS_1984", SPHEROID["WGS_1984", 6378137.0, 298.257223563]], PRIMEM["Greenwich", 0.0], UNIT["degree", 0.017453292519943295]], PROJECTION["Mercator_1SP_Google"], PARAMETER["latitude_of_origin", 0.0], PARAMETER["central_meridian", 0.0], PARAMETER["scale_factor", 1.0], PARAMETER["false_easting", 0.0], PARAMETER["false_northing", 0.0], UNIT["m", 1.0], AXIS["x", EAST], AXIS["y", NORTH], AUTHORITY["EPSG","54004"]]
13 Oct 10:13:55 INFO [org.geoserver] - Loaded feature type 'tasmania_water_bodies', enabled
13 Oct 10:13:55 INFO [org.geoserver] - Loaded feature type 'taz_shapes'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded layer 'tasmania_water_bodies'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded feature type 'tasmania_roads', enabled
13 Oct 10:13:55 INFO [org.geoserver] - Loaded feature type 'taz_shapes'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded layer 'tasmania_roads'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded feature type 'tasmania_state_boundaries', enabled
13 Oct 10:13:55 INFO [org.geoserver] - Loaded feature type 'taz_shapes'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded layer 'tasmania_state_boundaries'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded feature type 'tasmania_cities', enabled
13 Oct 10:13:55 INFO [org.geoserver] - Loaded feature type 'taz_shapes'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded layer 'tasmania_cities'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded store 'states_shapefile', enabled
13 Oct 10:13:55 INFO [org.geoserver] - Loaded data store 'states_shapefile'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded feature type 'states', enabled
13 Oct 10:13:55 INFO [org.geoserver] - Loaded feature type 'states_shapefile'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded layer 'states'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded workspace 'cite'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded workspace 'it.geosolutions'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded workspace 'sf'
13 Oct 10:13:55 INFO [org.geoserver] - Loaded store 'sf', enabled
13 Oct 10:13:55 INFO [org.geoserver] - Loaded data store 'sf'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded feature type 'bugsites', enabled
13 Oct 10:13:56 INFO [org.geoserver] - Loaded feature type 'sf'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded layer 'bugsites'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded feature type 'archsites', enabled
13 Oct 10:13:56 INFO [org.geoserver] - Loaded feature type 'sf'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded layer 'archsites'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded feature type 'roads', enabled
13 Oct 10:13:56 INFO [org.geoserver] - Loaded feature type 'sf'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded layer 'roads'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded feature type 'streams', enabled
13 Oct 10:13:56 INFO [org.geoserver] - Loaded feature type 'sf'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded layer 'streams'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded feature type 'restricted', enabled
13 Oct 10:13:56 INFO [org.geoserver] - Loaded feature type 'sf'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded layer 'restricted'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded store 'sfdem', enabled
13 Oct 10:13:56 INFO [org.geoserver] - Loaded coverage store 'sfdem'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded coverage 'sfdem', enabled
13 Oct 10:13:56 INFO [org.geoserver] - Loaded coverage 'sfdem'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded layer 'sfdem'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded workspace 'tiger'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded store 'nyc', enabled
13 Oct 10:13:56 INFO [org.geoserver] - Loaded data store 'nyc'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded feature type 'poly_landmarks', enabled
13 Oct 10:13:56 INFO [org.geoserver] - Loaded feature type 'nyc'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded layer 'poly_landmarks'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded feature type 'poi', enabled
13 Oct 10:13:56 INFO [org.geoserver] - Loaded feature type 'nyc'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded layer 'poi'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded feature type 'tiger_roads', enabled
13 Oct 10:13:56 INFO [org.geoserver] - Loaded feature type 'nyc'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded layer 'tiger_roads'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded feature type 'giant_polygon', enabled
13 Oct 10:13:56 INFO [org.geoserver] - Loaded feature type 'nyc'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded layer 'giant_polygon'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded workspace 'nurc'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded store 'mosaic', enabled
13 Oct 10:13:56 INFO [org.geoserver] - Loaded coverage store 'mosaic'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded coverage 'mosaic', enabled
13 Oct 10:13:56 INFO [org.geoserver] - Loaded coverage 'mosaic'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded layer 'mosaic'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded store 'arcGridSample', enabled
13 Oct 10:13:56 INFO [org.geoserver] - Loaded coverage store 'arcGridSample'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded coverage 'Arc_Sample', enabled
13 Oct 10:13:56 INFO [org.geoserver] - Loaded coverage 'arcGridSample'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded layer 'Arc_Sample'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded store 'worldImageSample', enabled
13 Oct 10:13:56 INFO [org.geoserver] - Loaded coverage store 'worldImageSample'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded coverage 'Img_Sample', enabled
13 Oct 10:13:56 INFO [org.geoserver] - Loaded coverage 'worldImageSample'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded layer 'Img_Sample'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded store 'img_sample2', enabled
13 Oct 10:13:56 INFO [org.geoserver] - Loaded coverage store 'img_sample2'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded coverage 'Pk50095', enabled
13 Oct 10:13:56 INFO [org.geoserver] - Loaded coverage 'img_sample2'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded layer 'Pk50095'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded layer group 'tasmania'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded layer group 'tiger-ny'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded layer group 'spearfish'
13 Oct 10:13:56 INFO [org.geoserver] - Loaded service 'wms', enabled
13 Oct 10:13:56 INFO [org.geoserver] - Loaded service 'wcs', enabled
13 Oct 10:13:56 INFO [org.geoserver] - Loaded service 'wfs', enabled
13 Oct 10:13:56 INFO [util.ApplicationContextProvider] - No context parameter, system or Java environment variables found for GEOSERVER_WMS_URL
13 Oct 10:13:56 INFO [util.ApplicationContextProvider] - Reverting to [http://localhost:8080/geoserver/wms](http://localhost:8080/geoserver/wms)
13 Oct 10:13:56 INFO [storage.DefaultStorageFinder] - **********************************************************************************************************************************
13 Oct 10:13:56 INFO [storage.DefaultStorageFinder] - *** Found Servlet context parameter GEOSERVER_DATA_DIR set to /etc/geoserver-2.0-RC1/data_dir, using it as the default prefix. ***
13 Oct 10:13:56 INFO [storage.DefaultStorageFinder] - **********************************************************************************************************************************
13 Oct 10:13:57 INFO [geowebcache.GeoWebCacheDispatcher] - set TileLayerDispatcher
13 Oct 10:13:57 INFO [geowebcache.GeoWebCacheDispatcher] - Invoked setServletPrefix(gwc)
13 Oct 10:13:57 INFO [wms.WMSService] - Will proxy requests to backend that are not getmap or getcapabilities.
13 Oct 10:13:57 INFO [util.ApplicationContextProvider] - No context parameter, system or Java environment variables found for GEOSERVER_WFS_URL
13 Oct 10:13:57 INFO [util.ApplicationContextProvider] - Reverting to null
13 Oct 10:13:57 INFO [util.ApplicationContextProvider] - No context parameter, system or Java environment variables found for GEOWEBCACHE_WFS_FILTER
13 Oct 10:13:57 INFO [util.ApplicationContextProvider] - Reverting to null
13 Oct 10:13:57 INFO [wfs.WFSService] - Configured to forward to [http://localhost:8080/geoserver/wfs](http://localhost:8080/geoserver/wfs) , timeout is 600000ms, regex filter 
13 Oct 10:13:57 INFO [rest.RESTDispatcher] - Created RESTDispatcher with 6 paths
3855 [main] INFO org.mortbay.log - Opened /etc/geoserver-2.0-RC1/logs/2009_10_13.request.log
3862 [main] WARN org.mortbay.log - failed SelectChannelConnector@0.0.0.0:8080
java.net.BindException: Address already in use
	at sun.nio.ch.Net.bind(Native Method)
	at sun.nio.ch.ServerSocketChannelImpl.bind(ServerSocketChannelImpl.java:119)
	at sun.nio.ch.ServerSocketAdaptor.bind(ServerSocketAdaptor.java:59)
	at org.mortbay.jetty.nio.SelectChannelConnector.open(SelectChannelConnector.java:205)
	at org.mortbay.jetty.nio.SelectChannelConnector.doStart(SelectChannelConnector.java:304)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:39)
	at org.mortbay.jetty.Server.doStart(Server.java:233)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:39)
	at org.mortbay.xml.XmlConfiguration.main(XmlConfiguration.java:977)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.mortbay.start.Main.invokeMain(Main.java:183)
	at org.mortbay.start.Main.start(Main.java:497)
	at org.mortbay.start.Main.main(Main.java:115)
3862 [main] WARN org.mortbay.log - failed Server@a431693
java.net.BindException: Address already in use
	at sun.nio.ch.Net.bind(Native Method)
	at sun.nio.ch.ServerSocketChannelImpl.bind(ServerSocketChannelImpl.java:119)
	at sun.nio.ch.ServerSocketAdaptor.bind(ServerSocketAdaptor.java:59)
	at org.mortbay.jetty.nio.SelectChannelConnector.open(SelectChannelConnector.java:205)
	at org.mortbay.jetty.nio.SelectChannelConnector.doStart(SelectChannelConnector.java:304)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:39)
	at org.mortbay.jetty.Server.doStart(Server.java:233)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:39)
	at org.mortbay.xml.XmlConfiguration.main(XmlConfiguration.java:977)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.mortbay.start.Main.invokeMain(Main.java:183)
	at org.mortbay.start.Main.start(Main.java:497)
	at org.mortbay.start.Main.main(Main.java:115)
3863 [main] WARN org.mortbay.log - EXCEPTION 
java.net.BindException: Address already in use
	at sun.nio.ch.Net.bind(Native Method)
	at sun.nio.ch.ServerSocketChannelImpl.bind(ServerSocketChannelImpl.java:119)
	at sun.nio.ch.ServerSocketAdaptor.bind(ServerSocketAdaptor.java:59)
	at org.mortbay.jetty.nio.SelectChannelConnector.open(SelectChannelConnector.java:205)
	at org.mortbay.jetty.nio.SelectChannelConnector.doStart(SelectChannelConnector.java:304)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:39)
	at org.mortbay.jetty.Server.doStart(Server.java:233)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:39)
	at org.mortbay.xml.XmlConfiguration.main(XmlConfiguration.java:977)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.mortbay.start.Main.invokeMain(Main.java:183)
	at org.mortbay.start.Main.start(Main.java:497)
	at org.mortbay.start.Main.main(Main.java:115)

Then it gets stuck and doesn't load any further. So I have to cancel it all of the time.

WARNING: Native library load failed.java.lang.UnsatisfiedLinkError: no gdaljni in java.library.path
... where would this gdaljni be found?

Thanks for your help.

---

### Post by vanill on 2011-04-11
Hi,
I have a problem with GeoServer and Ubuntu. I need to install GeoServer as localhost in ubuntu 10.10 installed in virtualbox. So I downloaded geoserver files, unziped them in Documents and tried to start startup.sh but nothing happend. I'm just beginner in linux, this is my first experience. I found few tutorials, but I'm not so smart from it. Can you anyone help me with this?

Thanks a lot, I'm lost, Dan

P.S. I allready downloaded java-6-openjdk

---

### Post by mwacky on 2011-04-15
startup.sh is the script that will start geoserver.

What is your output?

You'll need to setup your JAVA_HOME and GEOSERVER_HOME environment variables.  Generally startup will fail if those are not set but it will let you know.

---

### Post by vanill on 2011-04-15
Hi,
I wrote:

JAVA_HOME="/usr/lib/jvm/java-6-sun"
GEOSERVER_HOME="/home/danek/software/geoserver/bin"

at the beginning of startup.sh and shutdown.sh (next line is: #!/bin/sh). When I double click on startup.sh and I choose Run (or Run in Terminal) terminal just open for a while (about one second) and that is all. The same with shutdown.sh. So this is the reason, why I asking here, cause I can't figure it out with tutorials I found :(

---

### Post by vanill on 2011-04-15
hurray! problem was wrong written GEOSERVER_HOME (it should end with /geoserver, but I have written /geoserver/bin) and missing semicolons :D

So sorry for spaming this topic :oops:

---

