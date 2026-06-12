---
title: "black over the desktop"
date: 2010-03-08
forum: Desktop Environments
---

### Post by pyrat on 2010-03-08
I installed 9.10 yesterday and my desktop background does not show up.  It appears to be under a black screen.  The panels at the top and bottom are normal, and I can open windows normally over the black screen, but I can't see the background.  When I log out or shut down, the black goes off first, then I see the background just before the shut down.   Nothing in System -> Preferences seems to have any effect.  Any suggestions??

---

### Post by ajgreeny on 2010-03-08
ATI graphics card using the open source driver, running compiz and at resolution above 1024x768?  I suspect so.  To get your desktop back for now use Alt+F2 and enter ```
metacity --replace
``` or go to System -Preferences -Appearance and set the system to use none in the effects tab.

The simple way is to run without desktop effects, but if you really want to use compiz and have that eye candy, you will need either to run at a lower resolution, or use 16 bit colour.

The easiest way to do that is to manually edit your /etc/X11/xorg.conf file.  You may not even have such a file in your system, but if you make one it will be used, so in terminal use the command ```
gksudo gedit /etc/X11/xorg.conf
``` and in that put something along the lines of
```
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "ati"
EndSection 

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    16
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```but using your own figures for resolution and refresh rates

---

### Post by pyrat on 2010-03-08
Thank you so much!!  How do you get so smart!??  Setting Visual effects to None solved the problem.  I'm really don't understand the rest of your answert but intend to learn.  I'm a mainframe Unix user for many years but a complete newbies to Ubuntu but I am loving every minute.  Again, Thank you so much for your help!.

---

### Post by ajgreeny on 2010-03-09
Like everyone else here, I was once a new user and felt as much at sea as you feel at the moment.  Over my 5 years of Ubuntu use, I have gradually learned about linux and Ubuntu in particular, having searched and used this forum a great deal to solve my problems which were not generally huge, but just annoying.  I'm now doing my bit to payback for all the help I received when I started, so am delighted to be able to help you by answering your question.

Unfortunately ATI are not very good with linux in general, and older cards like mine (9200SE) are not fully supported any more, though it was up to jaunty 9.04, and like you, I started with a black screen wallpaper and no icons in 9.10, but a search showed that it was an incompatibility of compiz with the open source driver that caused the problem, and experimentation showed me that running 16 bit colour could solve it.  There are still a few minor display artifacts in videos when using compiz, but if I need to I just disable compiz with the compiz-switch application and icon from Forlong, [http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

---

