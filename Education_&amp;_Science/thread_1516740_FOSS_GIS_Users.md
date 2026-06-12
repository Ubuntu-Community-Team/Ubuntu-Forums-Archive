---
title: "FOSS GIS Users?"
date: 2010-06-24
forum: Education &amp; Science
---

### Post by sidzen on 2010-06-24
Is there anyone in this Community using Free Open Source Geographic Information Systems software?

Specifically, raster-based GIS comparable to ERDAS Imagine/Leica Geosystems -- is it available and from what source?
Unless GRASS has come a long ways, I'm looking for somethng a little more powerfull for Landscape Ecololgy analyses as well as baseline data geocorrection and mapping.
Would a platform such as HostGIS be required; how would one set up a workstation; and what are the minimal requirements (especially for the GPU) for a high performance system?  3-D flyby capability would be nice, but not required initially.

I've been out of the loop for a number of years, but would like to freelance my skills for non-profits and the like if it is feasible.  Your help and ideas are appreciated.

Mother Earth is my concern -- always has been, always will be.

---

### Post by earlycj5 on 2010-06-24
> **sidzen said:**
> Is there anyone in this Community using Free Open Source Geographic Information Systems software?

Specifically, raster-based GIS comparable to ERDAS Imagine/Leica Geosystems -- is it available and from what source?
Unless GRASS has come a long ways, I'm looking for somethng a little more powerfull for Landscape Ecololgy analyses as well as baseline data geocorrection and mapping.
Would a platform such as HostGIS be required; how would one set up a workstation; and what are the minimal requirements (especially for the GPU) for a high performance system?  3-D flyby capability would be nice, but not required initially.

I've been out of the loop for a number of years, but would like to freelance my skills for non-profits and the like if it is feasible.  Your help and ideas are appreciated.

Mother Earth is my concern -- always has been, always will be.

*disclaimer* I'm an R user, but have a grad certificate in GIS, so my suggestions are based on that.

Combination of GRASS+R or R+SAGA for analysis?

I did all my PhD (modeling and GIS work) work in R, the landscape ecology course here at K-State is taught using R.

I'd start by checking the packages here: [https://wiki.ubuntu.com/UbuntuGIS](https://wiki.ubuntu.com/UbuntuGIS), it is free after all.  :)

---

### Post by Pynalysis on 2011-10-04
Quantum GIS is a nice replacement for Arc...

---

### Post by LTVCA on 2011-10-07
I don't work with Landscape Ecology, so I can't contribute directly to that discussion.  I do know that some of my former colleagues also used GRASS and R for Landscape Ecology.  I tend to use QuantumGIS (QGIS) as a user friendly GIS for daily use.  With the GRASS interface installed, QGIS can also be used as a front end for GRASS when I need to do more intensive computing.  When I need other tools I tend to look towards OSGeo.  It's kind of an umbrella for various FOSS GIS projects.  [www.osgeo.org]("http://www.osgeo.org")

---

### Post by civetta on 2011-10-12
Qgis is nice and has a grass plugin so the programs can interface. Also lots of nice python plugins. It doesn't have 3d though. Kind of a nice desktop gis, and takes care of some annoying tasks easily for you (e.g. has on-the-fly raster projection). Look at the [ubuntugis ppa]("https://launchpad.net/~ubuntugis/+archive/ubuntugis-unstable") as they have more up-to-date packages than those available in ubuntu's repositories.

---

### Post by moldaviax on 2011-10-19
QGIS is quite good and wraps GRASS functions. I'd also have a look at GV-SIG and the sextante extension for geoprocessing. 

Have a look at the OS Geo web site for a comprehensive list of related foss tools [http://www.osgeo.org/](http://www.osgeo.org/) and you might also be interested in their live dvd project [http://live.osgeo.org/en/index.html](http://live.osgeo.org/en/index.html) which if it is still the same as demonstrated at the 2011 UK Open Source GIS conference was ubuntu based :)

M.

---

