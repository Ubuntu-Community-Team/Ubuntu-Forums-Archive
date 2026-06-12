---
title: "Geoserver or another mapserver?"
date: 2011-02-08
forum: Education &amp; Science
---

### Post by gazz1982 on 2011-02-08
Hi all,

I have been using GIS for a few years now, I am currently working with a disperced team who are not all too techy, well we are archaeologists!

Anyway, I have been looking at ways to but our excavation data online I have installed GeoServer on ubuntu... in initially I was very happy, I had a map on our website and i styled it nicely (thanks to uDig) i installed it using this code [http://sproke.blogspot.com/2010/12/install-script-for-geoserver-on-ubuntu.html](http://sproke.blogspot.com/2010/12/install-script-for-geoserver-on-ubuntu.html)

Anyway, every day it seems to stop working, both the map being displayed and the geoserver admin area, well the layers area to be specific, so now the thrustration is setting in... does anyone have experience with this?

I am using apache2, Tomcat 6 was installed with the geoserver quick install script (see above)

I'm running Ubuntu lynx on a decent desktop, the internet connection is on the University network, so no problems with speed.

Is GeoServer the way to go? I only want to display shp files, although the query tool is very useful.

Thanks for any help

Gary

---

### Post by kerrykuta12 on 2011-02-11
Its nice, thanks to share with us.

---

### Post by mwacky on 2011-04-23
GeoServer is a good way to go.  Do you have any details about your error, what version of GeoServer are you using?

---

### Post by cwarner7_11 on 2011-04-23
I have just started playing around with GIS, but have found several applications that may be of interest to you.  The one I find most useful for my uses is [GeomapApp]("http://www.geomapapp.org/").  Others of interest might include:

[QuantumGIS]("http://www.qgis.org/") 

[GrassGIS]("http://grass.fbk.eu/")

[iGMT]("http://geodynamics.usc.edu/~becker/igmt/")

The real issue for me is finding the appropriate database with adequate resolution for my "projects"...

---

### Post by mwacky on 2011-04-25
> **cwarner7_11 said:**
> I have just started playing around with GIS, but have found several applications that may be of interest to you.  The one I find most useful for my uses is [GeomapApp]("http://www.geomapapp.org/").  Others of interest might include:

[QuantumGIS]("http://www.qgis.org/") 

[GrassGIS]("http://grass.fbk.eu/")

[iGMT]("http://geodynamics.usc.edu/~becker/igmt/")

The real issue for me is finding the appropriate database with adequate resolution for my "projects"...

Try PostGIS

---

### Post by gunksta on 2011-04-26
> **mwacky said:**
> Try PostGIS

I think cwarner7_11is looking for shapefiles, not a database.

---

