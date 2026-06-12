---
title: "KDE apps slow since upgrade"
date: 2007-10-21
forum: Desktop Environments
---

### Post by darundal on 2007-10-21
Just upgraded from Feisty to Gutsy this morning. For the most part, everything went perfectly well. However, since the upgrade, any KDE apps I try to run (specifically, Amarok and K3b) are really slow. I can literally watch and distinguish elements being drawn on the screen. Now, looking at some related threads, I have found that this is somehow related to XGL (which is disabled because I use the FGLRX driver). I tried uninstalling XGL, which was a suggested solution, and it helped nothing. Anyone have any other ideas as to what I could do to get Amarok and K3b running as they should? None of the other threads really seemed to have a solution posted. Thx.

---

### Post by doundounba on 2007-12-02
From [another thread]("http://ubuntuforums.org/showthread.php?t=558731"):

> Create a file at "~/.config/xserver-xgl/disable" - in my case I put a simple line like "##comment", although I suspect the only important issue is that the file exists. After restarting X, xgl is no longer running, instead I have good old Xorg again.

This did the trick for me. (EDIT: I'm running Kubuntu, so YMMV...)

---

### Post by ferd on 2007-12-03
> **doundounba said:**
> From [another thread]("http://ubuntuforums.org/showthread.php?t=558731"):



This did the trick for me. (EDIT: I'm running Kubuntu, so YMMV...)

Thank you so much. This was driving me nuts.:guitar:

---

### Post by bostonvaulter on 2007-12-17
Is there any way to disable this only when choosing the kde session?

---

