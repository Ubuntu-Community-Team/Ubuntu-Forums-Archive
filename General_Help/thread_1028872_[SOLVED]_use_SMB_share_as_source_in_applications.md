---
title: "[SOLVED] use SMB share as source in applications"
date: 2009-01-02
forum: General Help
---

### Post by HOLLYW00D on 2009-01-02
howdy,  i have my SMB shares mounted and bookmarked (using "Connect to server" applet) and can read/write to them.  however, when i try to open a file on the shares from within a program, the shares aren't even listed as a source.  for example, in DeVeDe, i try to add a video file to convert to DVD, but SMB shares aren't showing up in the folder hierarchy within the "Add file" window.  They show up just fine in Nautilus.  Any help would be much appreciated.

i am using Ubuntu 8.10

---

### Post by dcstar on 2009-01-02
> **HOLLYW00D said:**
> howdy,  i have my SMB shares mounted and bookmarked (using "Connect to server" applet) and can read/write to them.  however, when i try to open a file on the shares from within a program, the shares aren't even listed as a source.  for example, in DeVeDe, i try to add a video file to convert to DVD, but SMB shares aren't showing up in the folder hierarchy within the "Add file" window.  They show up just fine in Nautilus.  Any help would be much appreciated.

i am using Ubuntu 8.10

See if this helps:

[http://ubuntuforums.org/showthread.php?t=1028338](http://ubuntuforums.org/showthread.php?t=1028338)

---

### Post by HOLLYW00D on 2009-01-03
thanks dcstar, but unfortunately i already have all the gvfs packages installed. :(  anything else i could try?

---

### Post by HOLLYW00D on 2009-01-04
problem solved by mounting the shares manually using cifs:  [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

