---
title: "Mapping Software"
date: 2009-01-20
forum: Education &amp; Science
---

### Post by irockonguitar on 2009-01-20
Hi

I'm in need of a program that can draw a map of any given part of the world, and be given coordinates of points to draw boundary lines, and place symbols on the map. This is for a university project, I need to be able to show the paths of various troops along major water bodies and other significant landscape features. I know the new version of Matlab can do this, but Octave can't (unless the command is different) and I don't feel like buying software for this.

Thanks

---

### Post by ssam on 2009-01-20
you could have a look at marble.
[http://edu.kde.org/marble/](http://edu.kde.org/marble/)
i think you can use it as a widget, and customise it.

---

### Post by seatopia on 2009-01-20
Take a look at GMT ([http://gmt.soest.hawaii.edu/](http://gmt.soest.hawaii.edu/)).  It's command line oriented and has a bit of a learning curve, but it's one of the best mapping programs out there.

---

### Post by irockonguitar on 2009-01-20
Thanks, guys! I'll try both of them, but from the websites, it looks like GMT is more like what I'm after.

Cheers!

---

### Post by samden on 2009-01-21
There is also QGIS, you'd need to obtain GIS data for the area you are interested in but there is free data available around the net for different areas.
[http://www.qgis.org]("http://www.qgis.org")

---

### Post by irockonguitar on 2009-01-21
> **samden said:**
> There is also QGIS, you'd need to obtain GIS data for the area you are interested in but there is free data available around the net for different areas.
[http://www.qgis.org]("http://www.qgis.org")

Thanks, is that like ArcGIS? I just started taking a course in GIS (I'm taking Geomatics Engineering, in case you're wondering) so I know virtually nothing about any of the software out there, except that I'll be using ArcGIS in that course, on the school's M$ computers.

I'll give it a try though. I haven't tried the other two suggestions yet, because I'm having internet troubles, so I can't actually download anything at the moment, but I've got an IT guy coming to help me in a few minutes. Hopefully I have a steady connection again soon!

Thanks again for the suggestion!

---

### Post by samden on 2009-01-22
Yes, it is like ArcGIS. QGIS is a lot simpler than ArcGIS, it is mainly designed to view shapefiles and do some basic editing - it is probably all you need. But it has a plugin that lets it act as a graphical front-end to GRASS GIS, a far more powerful package that will let you do pretty well anything. So it is very powerful if you want it to be.

I don't know much about GIS myself, I've just done a 1-day course in ArcGIS and have as a result managed to use QGIS to do the basic mapping I needed for my thesis, so I am pretty happy with it. The interface is similar to ArcGIS.

For free GIS data, check out [http://www.geocomm.com/]("http://www.geocomm.com/")

---

### Post by irockonguitar on 2009-01-22
Ok, that's awesome. Thanks!

---

### Post by earlycj5 on 2009-01-22
QGIS can also tie into PostGIS as well which I've found useful.

---

### Post by irockonguitar on 2009-01-22
> **earlycj5 said:**
> QGIS can also tie into PostGIS as well which I've found useful.

Oh really? What is PostGIS? How is it useful? Sorry, I'm incredibly new to this, but I'm also really fascinated with it, so I want to know as much as possible.

---

### Post by Joshuwa on 2009-01-22
QGIS is pretty nice. 

Being so used to ArcGIS, I also find the uDig project to be very worth looking at: [http://udig.refractions.net/](http://udig.refractions.net/)

It also has a link to JGrass, which uses the uDig framework to provide a more usable GUI for Grass.

Grass is quite powerful - even more so than ArcMap in some regards - but can be a real pain to set up and get working, so I would try out the alternatives before going that route. But if you find you like GIS, it's definitely worth fiddling with over a weekend.

Unfortunately, I've not heard of ArcMap being successfully ran via wine, or else I would suggest trying that.

Also, if you're not strictly tied to a *nix environment, it may be worth checking with your university's Geography or Engineering department and asking if they have either 1) labs with ArcMap on them or 2) Student-use CD's so you can install ArcGIS on your home PC.

Even though ArcGIS is a $15,000+ suite, ESRI is extremely generous with universities, and gives it to them free of charge (including CD's for students to use).

Best of luck to you and your project - I hope you find a solution that works for you.

---

### Post by FiReSTaRT on 2009-01-24
I have been using Quantum (QGIS). Just like any other major GIS package, its main strength lies in plugins. It has a built-in plugin installer. Before you do anything with the package (download the new version), make sure you update the installer. For some stuff I find it easier to use than ESRI, which I got for a $25 licensing fee. As for PostGIS, it adds a strong database component to Quantum, comparable to ArcSDE for some uses.

---

### Post by irockonguitar on 2009-01-24
Awesome, thanks! I'm sure it'll take awhile for me to figure out how to actually build a map with QGIS, but at least I have a starting point now.

---

### Post by earlycj5 on 2009-01-24
> **irockonguitar said:**
> Oh really? What is PostGIS? How is it useful? Sorry, I'm incredibly new to this, but I'm also really fascinated with it, so I want to know as much as possible.

From the PostGIS wiki:
> 
What is PostGIS

PostGIS is an extension to the PostgreSQL object-relational database system that allows GIS (Geographic Information System) objects to be stored in the database. PostGIS does for PostgreSQL what Oracle Spatial does for Oracle, ArcSDE does for Microsoft SQL Server/Oracle.


This guide is helpful in setting it up.
[http://postgis.refractions.net/support/wiki/index.php?PostgisOnUbuntu](http://postgis.refractions.net/support/wiki/index.php?PostgisOnUbuntu)

---

### Post by skatetokil on 2009-02-23
> **earlycj5 said:**
> From the PostGIS wiki:


This guide is helpful in setting it up.
[http://postgis.refractions.net/support/wiki/index.php?PostgisOnUbuntu](http://postgis.refractions.net/support/wiki/index.php?PostgisOnUbuntu)

Alright so I'd been having trouble myself, and I followed the tutorial here.  However, did the import as shown and it returned an error:

```
postgres@LinBox:/home/clay$ shp2pgsql -D midatl_50mwind.shp windtable windproject | psql windproject
midatl_50mwind.shp: shape (.shp) or index files (.shx) can not be opened, will just import attribute data.
midatl_50mwind.shp: dbf file (.dbf) can not be opened.

```

What am I doing wrong here?  When I try to use SPIT in Qgis, it asks for a password (which I haven't created and don't know how to set up) and I'm not sure how to configure things in the terminal so I can connect using QGIS.

---

