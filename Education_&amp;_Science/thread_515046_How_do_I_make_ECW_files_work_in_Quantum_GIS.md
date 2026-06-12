---
title: "How do I make ECW files work in Quantum GIS?"
date: 2007-08-01
forum: Education &amp; Science
---

### Post by whoopn on 2007-08-01
I would really like to understand how to make ECW files (they are images files that can be terabytes in size but easily opened) viewable in Quantum GIS.

I found this on the QGIS forums:
[http://forum.qgis.org/viewtopic.php?p=283]("http://forum.qgis.org/viewtopic.php?p=283")
> You have to download the ECW SDK from [http://www.ermapper.com/](http://www.ermapper.com/)
Then apt-get source gdal
Then edit debian/rules and add the following configure switch:
--with-ecw=ARG Include ECW support (ARG=ECW SDK Path, yes or no)

Then rebuild the package with dpkg-buildpackage -rfakeroot
You may find the apt-build package useful for this.

I don't quite understand what they are talking about...  Can anyone explain (in more complete instructions) what is going on and how I accomplish this?

Thank you so much!  If we get this stuff working in Ubuntu then my office will most likely switch to Ubuntu! :)

---

### Post by Nick Lake on 2008-08-03
I know this is an old thread... but thought I'd reply anyway.

ECW - Enhanced Compression Wavelet format was created by ER Mapper (now Leica Geosystems). Products like ER Mapper can export to ECW (not sure if they support Linux - but all of their software used to run on UNIX). There are also a number of free compressors but these are usually limited in the size of the data they can compress.

Other compression formats you may want to look at are:
1] MrSID from LizardTech (also uses wavelet compression).
2] JPEG2000

- Nick Lake

---

### Post by lutra on 2008-10-05
> **whoopn said:**
> I would really like to understand how to make ECW files (they are images files that can be terabytes in size but easily opened) viewable in Quantum GIS.

I found this on the QGIS forums:
[http://forum.qgis.org/viewtopic.php?p=283]("http://forum.qgis.org/viewtopic.php?p=283")


I don't quite understand what they are talking about...  Can anyone explain (in more complete instructions) what is going on and how I accomplish this?

Thank you so much!  If we get this stuff working in Ubuntu then my office will most likely switch to Ubuntu! :)



you need to compile from source, including the SDK you need. I wrote a guide for the local GFOSS community, so it is in Portuguese, but you should understand quite well the steps.

I wrote the guide for Qgis 0.10 but you can apply it also to the 0.11 version and even the upcoming 1.0


[http://wiki.osgeo.org/wiki/Instalar_Grass_e_Qgis_em_Ubuntu_8.04_(com_ECW_e_MrSID](http://wiki.osgeo.org/wiki/Instalar_Grass_e_Qgis_em_Ubuntu_8.04_(com_ECW_e_MrSID))


take care

---

