---
title: "Screen Resolution"
date: 2005-04-25
forum: Desktop Environments
---

### Post by Consumer on 2005-04-25
Hi,

I've just installed Hoary Hedgehog. All went smoothe except that in gnome I cannot change my resolution to anything better than 640x480 nor can I change my refresh rate. Is this a gnome glitch or something I've overlooked ?

---

### Post by heimo on 2005-04-25
Welcome to Ubuntu.

You're not alone with that problem. It can be fixed and this is good place to start:
[http://ubuntuforums.org/showthread.php?t=21984](http://ubuntuforums.org/showthread.php?t=21984)

Please provide more information about your hardware: monitor and graphics card. Also relevant parts of xorg.conf and xorg log would be useful. (see the thread abowe)

If something there's unclear, I'm willing to help as far as I can.

Cheers!

---

### Post by Consumer on 2005-04-25
[QUOTE=heimo]Welcome to Ubuntu.

You're not alone with that problem. It can be fixed and this is good place to start:
[http://ubuntuforums.org/showthread.php?t=21984](http://ubuntuforums.org/showthread.php?t=21984)

Please provide more information about your hardware: monitor and graphics card. Also relevant parts of xorg.conf and xorg log would be useful. (see the thread abowe)

If something there's unclear, I'm willing to help as far as I can.

Cheers![/QUOTE]


Hey,

Thanks for the prompt reply. I haven't had much luck with the tutorial ... could this be  a problem with gnome ?

---

### Post by Consumer on 2005-04-25
Hardware: GFORCE 2 MX 400
Relisys TE55 screen

I can't find any logs :s

---

### Post by heimo on 2005-04-25
Relevant log is in:
/var/log/Xorg.0.log

Please do NOT copy paste it to this forum. It's a long one. If you can make it an attachment or give a link to it, that'd be great. The other file that is essential for solving this problem is /etc/X11/xorg.log

From there you could copy-paste Monitor section, Device Section and the beginning (~20 lines) from Screen section. Put them inside code tags (with [ ] brackets) to get this kind of
 ```














nice scrollable window
which will not break the
layout of forum and will be
easier to read, and will not annoy
so many people






 
 
 
 
 
 



``` 

Or you can just attach that file too.

Thanks!

EDIT:

Your monitors specification
[http://www.eserviceinfo.com/download.php?fileid=13475]("http://www.eserviceinfo.com/download.php?fileid=13475")

Supported resolutions: 1024x768 800x600 640x480 (to Screen section)
Maximum dotclock: 80MHz

To Monitor section:
```
HorizSync   30-54
 VertRefresh 50-120

# couple modelines which should work on TE555 (15" CRT)
# 66Hz
Modeline "1024x768"      72.65  1024 1056 1328 1360    768  783  792  807
# 85Hz
Modeline "800x600"       58.20   800  832 1048 1080    600  611  620  631

```

---

### Post by Consumer on 2005-04-25
That worked a treat, thank you so much!  :razz:

---

