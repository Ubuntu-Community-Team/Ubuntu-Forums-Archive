---
title: "Metacity doesn't start after login"
date: 2009-04-25
forum: Desktop Environments
---

### Post by mimetist on 2009-04-25
Hi all, and thank you for your help :D

My problem is exactly what the title says... Metacity doesn't start after login therefore I can't see window borders. But if I activate visual effects (Compiz) and then deactivate them, metacity starts and works fine for the rest of my session.

I've been changing options trying to find a solution with CompizConfig and Compiz Fusion Icon... and if I set Effects as default, it starts correctly after login (even with metacity as window manager!!).

My temporal solution is to use a script to change between them by clicking on an icon. The Script is this (maybe useful for someone):
```
#!/bin/sh

# click to start, click to stop
if pidof compiz.real; then
 exec metacity --replace
else
 exec compiz --replace
fi
```
which is a modification of this one:
[http://ubuntuforums.org/showthread.php?t=495528](http://ubuntuforums.org/showthread.php?t=495528)

Oh, I'm using Ubuntu 9.04

---

### Post by HDave on 2009-04-27
Any update on this?  I have the exact same problem after upgrading to Jaunty.

---

### Post by OnSite511 on 2009-04-29
Anyone?
My wife is having the exact same problem 9.04 w/ Nvidia chipset G4 6100 & driver version 180.44

---

### Post by martywd on 2009-04-29
@mimetist: >  My temporal solution is to use a script to change between them by clicking on an icon. The Script is this (maybe useful for someone)...

Thanks for that script as a temporary fix for this issue.

I started noticing this issue in 8.10, but it's definitely more of an issue in my 9.04 upgrade.

VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1) and 180.44-0ubuntu1 .

---

