---
title: "anyone installed Yo Frankie! 1.1 on ubuntu 9.04?"
date: 2009-08-09
forum: Gaming &amp; Leisure
---

### Post by legolas_w on 2009-08-09
Hi
Thank you for reading my post.
I was trying to install the Yo Frankie! 1.1. and I get the following error message, please let me know if you have some knowledge about fixing the error:
```

(Reading database ... 207759 files and directories currently installed.)
Preparing to replace blender 2.49a-1~getdeb1 (using blender_2.49a-1~getdeb1_i386.deb) ...
Unpacking replacement blender ...
Preparing to replace yofrankie 1.1b-1~getdeb1 (using yofrankie_1.1b-1~getdeb1_all.deb) ...
Unpacking replacement yofrankie ...
dpkg: dependency problems prevent configuration of blender:
 blender depends on libalut0 (>= 1.1.0-1); however:
  Package libalut0 is not installed.
 blender depends on libavdevice52 (>= 3:0.svn20090303-1) | libavdevice-unstripped-52 (>= 3:0.svn20090303-1); however:
  Package libavdevice52 is not installed.
  Package libavdevice-unstripped-52 is not installed.
 blender depends on libftgl2 (>= 2.1.3~rc5); however:
  Package libftgl2 is not installed.
 blender depends on libopenjpeg2; however:
  Package libopenjpeg2 is not installed.
dpkg: error processing blender (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of yofrankie:
 yofrankie depends on blender (>= 2.49a); however:
  Package blender is not configured yet.
dpkg: error processing yofrankie (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 blender
 yofrankie


```

---

### Post by Perfect Storm on 2009-08-09
Guide; [http://gwos.org/doku.php/guides:64bit](http://gwos.org/doku.php/guides:64bit)

Note if you're using 32-bit change this when following the guide;

yofrankie-linux-x86_64.bin

to 

yofrankie-linux-i386.bin


You don't need Blender anymore - I just ran mine without.

---

### Post by gradinaruvasile on 2009-08-09
YoFrankie 1.1 needs Blender version 2.49a.
Here:

[http://www.getdeb.net/download/4659/0](http://www.getdeb.net/download/4659/0)

Install it then install YoFrankie. One thing though: it may not work well on or poorly supported cards (Ati with the opensource drivers, intel integrated etc). Should work well on Nvidia cards.

And it seems u need to instal libalut0, libavdevice52, libavdevice-unstripped-52 (this might be replacing the  libavdevice52), libftgl2, libopenjpeg2 packages....

Use the graphical installer for installing blender, it should pull the necessary packages from the repos.


I played on a Nvidia 8200 integrated card and got a playable performance - not excellent i mean 15-20 fps@1280x1024.

---

### Post by Perfect Storm on 2009-08-09
Strange...I just grab Yo Frankie unpacked it and ran it. And I don't have Blender installed. :confused:

---

### Post by gradinaruvasile on 2009-08-09
> **Artificial Intelligence said:**
> Strange...I just grab Yo Frankie unpacked it and ran it. And I don't have Blender installed. :confused:

You talk about a generic package that probably has blender bundled in. 
I think legolas_w talks about the .deb file from getdeb.

---

### Post by Perfect Storm on 2009-08-09
ah, okay.

---

