---
title: "Install problem GDAL MrSid on 10.04 LTS"
date: 2010-05-31
forum: Education &amp; Science
---

### Post by LTVCA on 2010-05-31
[SIZE=2]Has anyone been able to successfully compile the MrSid plugin for GDAL on 10.04?[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]I've been trying on a fresh install of 10.04. I got GDAL 1.7.2 and libgdal-mrsid-src 1.7.2 from deb [/SIZE][[SIZE=2][COLOR=#0033aa]http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu[/COLOR][/SIZE]]("http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu")[SIZE=2] lucid main[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]The GDAL alone appears to be working fine.[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]From LizardTech I got and used Geo_DSDK-7.0.0.2167.linux.x86.gcc41.tar.gz described as: [/SIZE]
[COLOR=#cc0000][SIZE=1][COLOR=black]GeoExpress Raster SDK for MG3/MG2 for Linux (x86) - gcc 4.1 32-bit[/COLOR][/SIZE]
[/COLOR][COLOR=#cc0000][SIZE=1][COLOR=#000000]Supported Processor: 32-bit x86[/COLOR][/SIZE]
[SIZE=1][COLOR=black]Supported Systems: Linux 2.6.9+ / glibc 2.3.4 / libstdc++ 6[/COLOR][/SIZE]
[/COLOR][SIZE=1][COLOR=black]Supported Compiler: gcc 4.1[/COLOR][/SIZE]
 
 
[SIZE=2]Compiling the src with *gdal-mrsid-build* (provided by the package) doesn't appear to produce any errors. But afterwards GDAL no longer works. For example the command *gdalinfo --format* produces a illegal operation error. QGIS will just crash on startup. Removing the newly created gdal_MrSID.so from /usr/lib/gdal17plugins/ resolves the errors.[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]I know that 10.04 installs with gcc 4.4 so I installed 4.1, reset my gcc, g++ and cpp links to the 4.1 versions and tried that. No luck. gcc 4.4 still uses libstdc++6 so I didn't do anything there. That left glibc 2.3.4 as a potential problem. Since I couldn't find a package to install that on 10.04, I tried to compile it from source. But that gave me just a mess of errors I'm not prepared to resolve at this point.[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]So has anyone out there had success with this? Any help would be appreciated. All our imagery is in MrSID format . [/SIZE]

---

### Post by BigBaka on 2010-06-09
No luck here either I'm afraid. Have had to revert to using a PC! Waiting for lizardtech to update GDAL for 10.04 seems to be all there is to do. Please post if / when there is an update, or you managed to get Mr Sid files working in QGIS.

---

### Post by BigBaka on 2010-08-19
By way of Update, have just installed QGIS 1.5 Tethys on Ubuntu 10.04, but it seems there is still no fix for the Mr Sid problem.

---

### Post by BigBaka on 2010-08-20
Correction: MrSID formats can now be used with QGIS 1.5.0 Tethys. After much googling, I found a tutorial on how to do set up for MrSID. QGIS is now in the main repositories for Ubuntu 10.04. You can follow the directions in the link below to for a tutorial on how install MrSID plugins for QGIS.
[http://trac.osgeo.org/ubuntugis/wiki/TutorialMrSid](http://trac.osgeo.org/ubuntugis/wiki/TutorialMrSid)

---

### Post by LTVCA on 2010-08-24
Thanks for letting me know that it's now fixed. I had been using that same set of directions you linked to. I'm not sure what has changed, the versions and date stamps on GDAL and libgdal-mrsid appear to be the same as my previous failed attempts. There must have been a change in one of the build libraries.
 
Working Now!

---

### Post by jurgenachilles on 2011-03-18
[SIZE=2]The Geo_DSDK-7.0.0.2167.linux.x86.gcc41.tar.gz is no longer available 
Only Redhat is listed under Linux on the LizardTech site [http://www.lizardtech.com/developer/members/downloads.php](http://www.lizardtech.com/developer/members/downloads.php)
Unified_DSDK_8.0_linux.x86.gcc41.tgz

As a result I can't display MrSid with Quantum Gis 1.6.0 'Copiapo'

:(
[/SIZE]

---

### Post by LTVCA on 2011-03-21
Have you tried using the new Unified SDK listed under Red Hat?  If so, what kind of errors did it give you?

---

### Post by comeisl on 2011-08-09
I'm sorry but seems that MrSid is not compiled for gdal-1.8.1 with Lizardtech DSDK-8 I try to do with your instructions, and also with explained at [http://www.wildsong.biz/index.php?title=Building_GDAL_on_Linux](http://www.wildsong.biz/index.php?title=Building_GDAL_on_Linux), changing your filenames with Raster_DSDK as the new DSDK, but without success.

I've tried with gcc3.4 and gcc4.1 :( on Ubuntu_Natty with [http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu](http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu)

Any idea?

Thanks

---

### Post by LTVCA on 2011-08-15
I don't have any ideas.  Nor am I set up as a test environment to try and figure it out.  The only thing I could suggest is to try asking on one of the mailing lists at [http://lists.osgeo.org/mailman/listinfo](http://lists.osgeo.org/mailman/listinfo)

---

### Post by JamesCEddy on 2011-10-05
Not sure why it's marked solved.

But this might be the solution:
[http://ubuntuforums.org/showthread.php?p=11313263#post11313263]("http://ubuntuforums.org/showthread.php?p=11313263#post11313263")

---

### Post by LTVCA on 2011-10-07
The forum was marked solved because the thread was started back with GDAL 1.7.2 and QuantumGIS 1.5.  At one point those installation problems were solved.  
 
Then somebody added to this old thread when similar problems reoccurred in GDAL 1.8 and QuantumGIS 1.6.

---

