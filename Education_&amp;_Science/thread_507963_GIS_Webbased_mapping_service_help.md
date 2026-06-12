---
title: "GIS Webbased mapping service help?"
date: 2007-07-23
forum: Education &amp; Science
---

### Post by whoopn on 2007-07-23
Does anyone know how or know where to read how to go from fresh Ubuntu install (preferably) to a webbased GIS mapping service?  

I don't know how to:

Get a map to be published and available for a PHP website to use as its content.

What I mean is this:

I need a map on a PHP website that I am able to zoom in and out of (map caching would be awesome b/c speed is a concern).  So I need to understand how to (using ESRI terms here):

* publish a map
* Call that map in a PHP website
* Cache that map for a speed increase greater than what ESRI can deliver

I need to know the steps is all really.  I don't understand how all of the different packages (Mapserver, GRASS, QGIS, APACHE, etc...) interact with one another.

Any help is appreciated!

---

### Post by taslinux on 2007-07-26
A related question: why do I do everything except GIS on my Ubuntu machine? Because (a) there isn't an open-source GIS that's as easy to use as those in the ESRI line and (b) ESRI isn't interested in porting its GIS programs to Unix/Linux. Hopefully the new Java-based GIS programs will soon offer what even the earliest ArcView versions had. I was told there are excellent Unix-based and cross-platform GIS programs available for a price, and the first one I looked at was US$6000 for a single-user licence. Urk.

---

### Post by timmie on 2007-07-30
Hello,
I guess you are a beginner in webampping - just like me.

See a good introduction by Crschmidt from OpenLayers at:
[http://trac.openlayers.org/wiki/MappingYourData](http://trac.openlayers.org/wiki/MappingYourData)

For a feature comparison look at this table (German, but obvious...Google translate can help):
[http://swm.wald.intevation.org/index_13.html](http://swm.wald.intevation.org/index_13.html)

Mapserver only provides the infrastructure. For PHP mapping use clients on that page.

---

### Post by TomFumb on 2008-03-15
> **taslinux said:**
> ... and (b) ESRI isn't interested in porting its GIS programs to Unix/Linux...

Erm, wasn't Arc/Info originally developed for unix?

A lot of what ArcMap does is just Arc/Info functionality with a nicer interface, and Arc/Info is a lot more powerful.

---

### Post by Greyfox67 on 2008-04-01
I realize this post is turning 'old' but I'd like to keep this post going if there is no objection.

As a GIS Technician I've been exploring quite a few OpenSource packages as it applies to both Linux and Windows. Working in a municipality I to A) Find ways of saving money and B) ensure my solution(s) are compatible with my users who are mostly Windows Users.

Some solutions I've started looking into for the past couple of months:

A) MS4W Mapserver for Windows. Coupled with Quantum GIS for windows, I've got the core packages I need but now need to learn how get Mapserver to publish my map files to the internet.

B) On the Linux side I've looked at Mapserver and Geoserver. Although the functionality is there, I need something that is both user-friendly to the public and gives a professional look. Given the latter equation is why I DON'T like Openlayers. I just feel it looks to "cheap" (forgive the ironic remark there as we are calling a free program "cheap")

At any rate, I am interested in hearing others solutions or even problems and very interested in opening some collaboration. 

On a final note; I have looked into GIS Knoppix and HostGIS but have yet to test either.

---

### Post by Nick Lake on 2008-08-03
I'd like to keep this thread alive too...

It seems strange to me that ESRI haven't embraced (or should I say re-embraced) UNIX / Linux for the desktop earlier. It was born on UNIX and continues to move away from Linux (despite a few fairly pathetic attempts to provide some of their client end software on Linux via Java).

In the old days we used to run ArcInfo on Solaris and it worked beautifully. Why hasn't ESRI continued to support their flagship products on these platforms?

In my working environment most of the interpretive and analytical work is done on Linux (RH) and Solaris (even SGI in some cases). Our everyday users now have both Linux, XP64 and Win2K boxes just so that they can use all of the software they require! It's insane because globally we have several thousand users! If ESRI provided a decent solution on Linux we could dramatically reduce the number of computers we use and integration would be a lot easier.

We run Oracle Spatial and ArcSDE on both Linux and Solaris platforms. It'd be great to see better support for these spatial RDBMS on Linux platforms in something like ESRI's ArcMap product suite.

- Over

---

### Post by Nick Lake on 2008-08-03
Just another idea...

If the very rich ESRI libraries were available for Linux (and I don't want some crappy Java version) - It'd be relatively easy to enable parallel processing for more complex problems over a cluster without having to implement geo-processing logic ourselves.

Partition data... and processing tasks...
Migrate geo-processing tasks to other compute nodes... Merge data back... Done.

Wow! - I'm getting really out of topic here.

- Over and Out

---

