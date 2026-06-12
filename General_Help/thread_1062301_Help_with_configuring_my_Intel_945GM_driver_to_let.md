---
title: "Help with configuring my Intel 945GM driver to let me get desktop effects"
date: 2009-02-06
forum: General Help
---

### Post by Ghostnik11 on 2009-02-06
Hi I have been trying for the last 2 weeks how to configure or set up my driver which is an intel 945GM driver to allow me to get desktop effects such as the famous cube and other things but I don't know how.  I have been searching all over but seem to can't find out how to set up my intel driver properly.  I am a noob and am fairly new to ubuntu so any help would be much appreciated.  thank you in advance.

---

### Post by Ghostnik11 on 2009-02-06
When I perform compiz check this is what I get.
```
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 
```

---

### Post by MarblePanther on 2009-02-06
This thread might help you:

[http://ubuntuforums.org/showthread.php?t=966733](http://ubuntuforums.org/showthread.php?t=966733)

---

### Post by Ghostnik11 on 2009-02-06
Didn't help but thanks I don't get it I did what they said which was uninstall all the files containing fglrx. then ran compiz-check and I still got the same thing

---

### Post by Ghostnik11 on 2009-02-06
thanks I got it to work I just had to restart my laptop after doing what they said about removing the nvidia and flgrx

---

### Post by MarblePanther on 2009-02-06
Glad you got it working

Have fun with the wobbly windows and spinning cubes!

---

