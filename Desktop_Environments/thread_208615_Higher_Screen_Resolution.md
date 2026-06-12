---
title: "Higher Screen Resolution"
date: 2006-07-03
forum: Desktop Environments
---

### Post by Loomy on 2006-07-03
Alright good news I finally got my video card to show up!!

But I still only have the three ?default? screen resolutions.  How do I change my screen to a higher resolution? :|

---

### Post by 23meg on 2006-07-03
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by Loomy on 2006-07-03
I am very new to Linux is this the simplest way?  I'm sure I can figure it out just wondering if there is an easier route. ;)

---

### Post by jvictor on 2006-07-04
**IF** u r using a CRT then ...

1) Get to know the monitors horizontal and vertical refresh rates
(Ur monitor manual will have it ..or search for the specs in google)

2) Know the resolutions your monitor supports

Follow these steps by opening a terminal and typing in these commands

```
sudo gedit /etc/X11/xorg.conf
```

locate the section that looks like (i've given mine as eg here)

```
Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-120
EndSection
```


**REPLACE YOUR MONITORS VALUE in place of  HorizSync and VertRefresh ; IF NOT YOU RUN A RISK OF DAMAGING YOUR MONITOR**

Go to section screen and look for the default depth you are using , mostly it will be 24 bit, but plz be sure of this

and modify the correct bit-depth subsection by adding the resolution u know that ur monitor can support

again i'm giving my example


 SubSection "Display"
                Depth           24
                Modes           "1152x864" "1024x768" "800x600" "640x480"
 EndSubSection


once you are done , double check the value of the VertRefresh & horizsync save the file , log out , type control + alt + backspace and login hopefully u will get the desired resolution

There are plenty of threads that talk of the same thing , I suggest u do a proper search b4 u post , yes you are new to Linux and so were we at a time :) 

Cheers and HTH

---

