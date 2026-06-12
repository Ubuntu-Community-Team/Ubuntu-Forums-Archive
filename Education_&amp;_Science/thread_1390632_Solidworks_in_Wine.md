---
title: "Solidworks in Wine ?"
date: 2010-01-25
forum: Education &amp; Science
---

### Post by gabo.cr on 2010-01-25
Did anybody tried running Solidworks with Wine?
I think this program is too much for Virtualbox, but I want to know anyone's opinion about that.
Thanks!

---

### Post by wolfmanjack on 2010-02-01
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=318](http://appdb.winehq.org/objectManager.php?sClass=application&iId=318)
doesn't look like it really works

[http://ubuntuforums.org/showthread.php?t=753622&highlight=solidworks&page=2](http://ubuntuforums.org/showthread.php?t=753622&highlight=solidworks&page=2)
might be interesting for you as well

---

### Post by Gemnoc on 2010-02-02
If you want to get a kick, install the latest v3.1 of GraphiteOne 3D Basic or 3D Design. It's a CAD 2D/3D package for Linux. There are Ubuntu packages available.
[http://www.graphiteone-cad.com/page_download.php](http://www.graphiteone-cad.com/page_download.php)

GraphiteOne v1.3 used to be free for personal use and was based on OpenCASCADE. Starting with v2 it integrated the commercial Parasolid kernel instead, and was not free anymore.

Now v3.1 retains the same Parasolid kernel, which is also used in Solidworks and Solid Edge (and a few others). But with this release, the author has totally cloned the Solidworks UI.

Mind you, this is NOT Solidworks, and it doesn't open SW files. It does open and save in Parasolid (.X_T and .X_B) format. Although it mimicks SW, it is not as user friendly.

The 3D Design version is free for personal use, with heavy limitations: part design only (no assembly), and up to 20 features.

[Just to be clear: if all you're interested in is running Solidworks in Ubuntu, simply disregard what I said. Ditto if you are expecting a true SW alternative. This will NOT be the case. But if, like me, you're curious about CAD on Linux, and don't mind wasting your time on trying apps that may or may not be that good, then go ahead and try it. :mrgreen:]

---

### Post by Gemnoc on 2010-02-03
I tried to install Solid Edge V20 and ST. The installer seems to be working, but the application doesn't launch.

Some people report success running Catia V5R19.

If you go to the WineHQ AppDB page, you'll see someone gave SW 2009 SP0 a Bronze rating with some cosmetic glitches, but saving sometimes crashes the app.

---

### Post by Lubelaczek on 2010-05-07
> **prabaz said:**
> Anyone here tried running *Solidworks* or any other windbloat native 3d modeling software through *WINE?*

I did. No success. It installs somehow but when I try go to "file/open file" it all gets crazy after pointing any type of file: stp, igs, dxf. Also I did try MastercamX. Same thing - no success, however it doesn't crash but nothing happens when I try to open existing file.

---

