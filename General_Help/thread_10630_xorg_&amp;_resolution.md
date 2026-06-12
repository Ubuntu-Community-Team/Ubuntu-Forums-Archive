---
title: "xorg &amp; resolution"
date: 2005-01-09
forum: General Help
---

### Post by lee_connell on 2005-01-09
Hi everyone,

i have one machine that is a desktop and has a radeon 7000 video card.  when i was using xfree86 the resolution was fine, 1024x768.  Now i upgraded to hoary and xorg and it will not take my resolution set in xorg.conf.  It only uses 800x640.  Within gnome resolution changing app it only displays available option 800x640, though my xorg.conf for every color depth has 1024x768.

Any ideas?

lee

---

### Post by JackDog on 2005-01-13
post the relavent parts of your xorg conf file and the xorg log file. If your conf file is configured to run higher resolutions, and it doesnt, the log file will tell you why.

---

### Post by daniels on 2005-01-13
You might need to grab your HorizSync and VertRefresh lines from /etc/X11/XF86Config-4 and add them to the Device section of xorg.conf.  If this works, please send the output of running 'sudo ddcprobe'.

---

### Post by lee_connell on 2005-01-13
Hi guys thanks for the info, posted is my xorg.log and xorg.conf files.  I noticed that the horz sync vert sync seem to be screwing things up in the log.

---

### Post by lee_connell on 2005-01-13
sudo ddcprobe
Password:
vbe: VESA 2.0 detected.
oem: ATI RADEON VE
memory: 65536kb
mode: 800x600x16
mode: 1024x768x16
mode: 320x200x32k
mode: 320x200x64k
mode: 320x200x16m
mode: 1600x1200x256
mode: 640x400x256
mode: 640x480x256
mode: 640x480x32k
mode: 640x480x64k
mode: 640x480x16m
mode: 1600x1200x32k
mode: 800x600x256
mode: 800x600x32k
mode: 800x600x64k
mode: 800x600x16m
mode: 1600x1200x64k
mode: 1024x768x256
mode: 1024x768x32k
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x256
mode: 1280x1024x32k
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 132x25 (text)
mode: 132x43 (text)
edidfail

I tried adding modelines in which i seen from my XFree86.0.log and use the "UseModes' in monitor section, but it didn't work either.  I purged XFree86 so my conf file is gone :(

---

### Post by daniels on 2005-01-14
Can someone who has an XF86Config-4 with the HorizSync and VertRefresh for 1024x768 please post it here?

---

### Post by lee_connell on 2005-01-15
anyone???

---

### Post by daniels on 2005-01-16
[http://www.ubuntuforums.org/showthread.php?p=49530](http://www.ubuntuforums.org/showthread.php?p=49530)

---

