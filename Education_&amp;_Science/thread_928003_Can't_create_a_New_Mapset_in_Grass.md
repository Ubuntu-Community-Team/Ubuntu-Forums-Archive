---
title: "Can't create a New Mapset in Grass"
date: 2008-09-23
forum: Education &amp; Science
---

### Post by FiReSTaRT on 2008-09-23
So, I decided to give it a shot as a supplement to Arc... When I try to create a new mapset, I get the following message:
couldn't change working directory to "/home/dlyh/grassdata/grassdata": no such file or directory
couldn't change working directory to "/home/dlyh/grassdata/grassdata": no such file or directory
    while executing
"cd $dir"
    (procedure "CheckLocation" line 9)
    invoked from within
"CheckLocation"
    invoked from within
".frame0.frameNMS.third.button invoke"
    ("uplevel" body line 1)
    invoked from within
"uplevel #0 [list $w invoke]"
    (procedure "tk::ButtonUp" line 22)
    invoked from within
"tk::ButtonUp .frame0.frameNMS.third.button"
    (command bound to event)


Any help would be appreciated

---

### Post by Nick Lake on 2008-10-01
I assume the location /home/dlyh/grassdata/grassdata actually exists right?

Are you creating a new mapset using the gis.m GUI? or via command line? Try starting grass in command line...

> grass -text

And follow the instructions to create a completely new GISDBASE/LOCATION and MAPSET - see if that works.

I started mucking around with GRASS as a way of de-stressing from using ESRI. I find that it kills ArcGIS for raster processing and the cool thing is you can write bash scripts that call grass commands - which just craps on using VBS or Python to create geoprocessing tasks. :) Reminds me of the days we ran ArcInfo on Solaris.

I've even started introducing GRASS at work for certain tasks that are just annoying in ArcGIS.

I've got a GRASS book here at home which is the best reference I've found (not very good references on the internet) - So if you need me to thumb through it on occassion let me know (send email)).

Good luck,
- Nick

---

### Post by FiReSTaRT on 2008-10-02
Thanks a lot Nick. I'll give it a shot tomorrow and take you up on your offer in the future. I am learning to use ESRI and it can be a bit frustrating. Ofcourse I wish the Grass GUI worked better in Ubuntu, but maybe it'll work better with Intrepid.
By the way I heard that it doesn't do much for vector data. How does it perform and is there an Open Source GIS that has decent vector-handling capabilities?

---

### Post by Nick Lake on 2008-10-03
Yeah it's more of a raster-oriented GIS - but it can handle vector data. Although I haven't got it working on Ubuntu you could have a look at QGIS (Quantum GIS) - it has a GUI similar to ArcMap and is probably happier with vector data. I only played around with it on Windows out of curiosity.

Good luck.
- Nick

---

### Post by FiReSTaRT on 2008-10-03
I checked it out. It worked without any issues (8.04), but I didn't like the user interface. 
What sort of GIS work do you do?

---

### Post by FiReSTaRT on 2008-10-09
Update.. I finally got around to installing the qgis-grass plugin and now it's working when I'm using qgis as a front end. This weekend I'll finally have some free time to play with it.

---

### Post by Nick Lake on 2008-10-15
Great!

QGIS is definitely more familiar if you're used to ArcMap. I'm a GeoInformatics consultant - so GIS is a major tool in my arsenal. We also do quite a bit of custom and ground-up software development and analytical work. I've just written some command line tools in C++ on Ubuntu that perform translations and analysis on ESRI ASCII Raster GRIDs. Performance absolutely kills ESRI's own tool sets.

I'm also personally interested in developing parallel algorithms for geo-computation problems (applying high-performance computing techniques to GIS). This is what really got me looking at Linux again.

If you do pick up GRASS again - and need some help - let me know.
I never had any luck installing QGIS on 8.04 - perhaps need to give it a go again :)

- Nick

---

### Post by FiReSTaRT on 2008-10-17
That's what I'm hoping to bring to the family business in the future (minus the code-writing). As for Qgis, I think it even installed straight through Synaptic.

---

### Post by nlion on 2008-10-19
> **Nick Lake said:**
> 

I've got a GRASS book here at home which is the best reference I've found (not very good references on the internet) - So if you need me to thumb through it on occassion let me know (send email)).

Good luck,
- Nick

What is the title of the book?  If it's that good I think I may want to buy it for myself. I'm trying to get more familiar with qgis and GRASS after using ESRI software for so long.

And on another note:

I'm running Ibex and qgis has been removed from the repository. Anyone know why?

---

### Post by FiReSTaRT on 2008-10-21
I hope it's only been done for the beta. QGIS 0.11 has a few stability issues on my machine, especially when doing georeferencing of raster datasets. I hope there will be updates to correct that.

---

### Post by FiReSTaRT on 2008-10-22
I just noticed that QGIS 1.0 is about to come out. Maybe they are waiting for it to come out and then include it in the repos?

---

### Post by nlion on 2008-10-27
> **FiReSTaRT said:**
> I just noticed that QGIS 1.0 is about to come out. Maybe they are waiting for it to come out and then include it in the repos?

That would be nice, although this 4 day wait is agonizing if that is the case.

---

### Post by Amator on 2008-10-28
> **Nick Lake said:**
> I've got a GRASS book here at home which is the best reference I've found (not very good references on the internet) - So if you need me to thumb through it on occassion let me know (send email)).

Good luck,
- Nick

Could you please post the title and details of the book? I know Nlion also asked this also, but I can't see an answer. I am trying to get familiar with GRASS as a replacement for ESRI, but I am having a lot of trouble, amongst others with creating a new location. My problem is that I cannot find a decent manual or anything, so a good book would be great!

(btw, a good basic tutorial can be found at [http://www.ing.unitn.it/~grass/docs/tutorial_62_en/index.html](http://www.ing.unitn.it/~grass/docs/tutorial_62_en/index.html))

---

### Post by tom.db on 2008-11-03
Open Source GIS: A GRASS GIS Approach

[http://www.grassbook.org/](http://www.grassbook.org/)

Many pages are also on google book
;)

---

### Post by Amator on 2008-11-13
Thanks! 
I was able to download the complete book using my universty library account!

---

