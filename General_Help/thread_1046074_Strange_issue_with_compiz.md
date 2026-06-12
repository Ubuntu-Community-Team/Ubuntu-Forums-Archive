---
title: "Strange issue with compiz"
date: 2009-01-21
forum: General Help
---

### Post by yeleek on 2009-01-21
Hi,

Last night shutting down my lappy took longer than usual.  Today when I boot it I just get a blank screen.  Run xfce4-panel, xfce4-session, xfdesktop, xfwm4 and i get my desktop back but without compiz/emerald.  Reboot and the laptop comes up as normal but without compiz.  Try to run the below and compiz/emerald do not start.  And obviously I have to restart xdwm4 afterwards.  Any ideas please?

ben@ben-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

### Post by yeleek on 2009-01-21
Fixed it.  Disabled Compositing in Windows Manager Tweaks and tried compiz --replace again.  Worked fine.

---

### Post by tiagovicentao on 2009-01-21
Hello Guys I have a very strange situation with my Compiz + Emerald, I downloaded several Emerald themes but they never worked, I used the command replace but no change.
Yesterday it worked the window borders were like they had to be and this morning it worked again but after rebooting the lap top it didn't work anymore :( have already reinstalled both Compiz and Emerald and tried to use different themes.

Please someone!!!!

---

### Post by gjoellee on 2009-01-21
> **tiagovicentao said:**
> Hello Guys I have a very strange situation with my Compiz + Emerald, I downloaded several Emerald themes but they never worked, I used the command replace but no change.
Yesterday it worked the window borders were like they had to be and this morning it worked again but after rebooting the lap top it didn't work anymore :( have already reinstalled both Compiz and Emerald and tried to use different themes.

Please someone!!!!

What is your output when doing those commands?
```
compiz --replace
``````
emerald --replace
```

---

### Post by tiagovicentao on 2009-01-21
In compiz > window manager I used emerald --replace

did not try in terminal to have output

---

### Post by tiagovicentao on 2009-01-22
Well I tried emerald --replace on terminal as suggested, IT WORKED!!! but when I close terminal session the windows borders are gone :( then I have to go back to compiz and unmark then mark the window decorator option again so I have mu windows borders back (without emerald effects).

---

