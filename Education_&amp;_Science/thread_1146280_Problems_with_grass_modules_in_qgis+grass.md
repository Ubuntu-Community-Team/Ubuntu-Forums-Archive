---
title: "Problems with grass modules in qgis+grass"
date: 2009-05-02
forum: Education &amp; Science
---

### Post by santiagogaitan@gmail.com on 2009-05-02
Good day to everyone.

I've been trying, for a lot of time, to use the plugin of GRASS in QGIS. However, When i use the r.in.gdal or r.in.gdal.loc modules to import a GeoTIFF or a MrSID images the system gives me the next message:

[COLOR="Red"][COLOR="RoyalBlue"]Cannot start module r.in.gdal
/usr/lib/grass/bin/r.in.gdal --interface-description

GRASS_INFO_ERROR(22688,1): MAPSET PERMANENT - permission denied GRASS_INFO_END(22688,1) [/COLOR][/COLOR]

I would be happy to use qgis+grass power, but it seems to be, at this time, so hard.

Another problem that i want to solve is the decode of .sid images (Orthorectified Landsat mosaic from NASA) to GeoTIFF formats. Rather than the use of qgis+grass, i've been trying with the tool recommended from NASA to do that: "Mrsidgeodecoder" (available at [http://www.lizardtech.com/download/dl_download.php?detail=geo_mrsiddecode&platform=lin](http://www.lizardtech.com/download/dl_download.php?detail=geo_mrsiddecode&platform=lin)). I've unpacked it and change the permissions but when i give the next command in a terminal:

[COLOR="RoyalBlue"]mrsidgeodecode -i example.sid -o example.tif -of tifg[/COLOR]

The system gives me the next message:

[COLOR="RoyalBlue"]bash: mrsidgeodecode: command not found[/COLOR]

By the way, i'm on a ubuntu 8.04.1 64bits system.

I would appreciate your help to solve this.

Thanks,

Santiago.

---

### Post by santiagogaitan@gmail.com on 2009-06-07
Seems like the problem was about permissions on the disk where i have the grass data base and the raster image. The disk has permissions only for root.

The solution:

Open a terminal and type [COLOR="RoyalBlue"]sudo qgis[/COLOR]

Bye!

---

