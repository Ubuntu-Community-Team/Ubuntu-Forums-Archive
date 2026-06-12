---
title: "Systems Settings-&gt;Display Busted after getting Twinview working"
date: 2006-06-05
forum: Desktop Environments
---

### Post by Geshtar on 2006-06-05
So I got Twinview working pretty well on my dual monitor box with Kubuntu 6.06 but after I did, I went to the System Settings->Display menu where stuff like the resolution slider is, and was greeted with this:
```
The module Display could not be loaded.

The diagnostics is:

Possible reasons:
-An error occurred during your last KDE upgrade leaving and orphaned control module.
-You have old third party modules lying around.
```

I've never used Kubuntu/Ubuntu extensively so I don't really understand what that means or how I might go about solving it.  Any information would be appreciated.

Thanks,

-Geshtar

---

### Post by msak007 on 2006-06-05
[QUOTE=Geshtar]
```
The module Display could not be loaded.

The diagnostics is:

Possible reasons:
-An error occurred during your last KDE upgrade leaving and orphaned control module.
-You have old third party modules lying around.
```
[/QUOTE]

I'm having the same problem, and I'm not sure if it's a KDE or Kubuntu bug. I've seen a couple other threads in the Dapper development forum that are now closed with the same problem (various modules), but nobody seems to have provided a solution or workaround. I'm pretty sure that the module was working on a brand new install, but broke some time later (maybe after I installed the xorg fglrx package?) Are you using ATI or Nvidia?

---

### Post by Geshtar on 2006-06-05
I am using Nvidia drivers.  I believe the System Settings->Display was still working after my initial isntall of the Nvidia drivers, since I think went there to make sure that my screen was indeed doing 1600x1200.  I believe it stopped once I got Twinview up and running for my dual monitors.

-Geshtar

---

### Post by msak007 on 2006-06-06
Well, I somehow fixed (not sure if this is a fix) my Display module and it came back. I'm using an ATI card though (X850 XT), so I can't help you out. 

In my case, after I installed the xorg fglrx driver from the repositories and ran "aticonfig --initial", it created some entries for card, monitor, etc., in xorg.conf. The problem I had with it is that all the devices had generic names ("aticonfig-Monitor[0]", "aticonfig-Device[0]", "aticonfig-Screen[0]") instead of what was originally there (Dell 2005 FPW, ATI Radeon X850XT, etc.). For my "Section "ServerLayout"" entry in xorg.conf, I changed the line "Screen" (which after the config had "aticonfig-Screen[0]") to reflect the "Screen" section that had the devices with the names I preferred ("Default Screen"), and changed the "Driver" in the "Device" section from "ati" to "fglrx" to get the 3D acceleration. Once I restarted X, I believe that's when I lost the module. Just to test it, I changed "Screen" back to "aticonfig-Screen[0]" (the entry created by the ATI setup which had the generic "ati" names stated above), restarted, and voila! The Display module now works. :-k It loads and I can make the changes, but the hardware names are generic. Is this a bug, or the way it was designed to work? I know ATI cards don't have the greatest support, but what in those entries could have caused the module to stop loading. I can post my xorg.conf for anybody that wants to take a look at it to tell me where it may have been wrong.

---

### Post by msak007 on 2006-06-06
Well I never know when to leave things alone, so I messed with my xorg.conf file again and broke the Display module, again. After restoring my xorg.conf to the default, running "aticonfig --initial" to insert the ATI configuration lines, and restarting X, the Display module broke again. After messing with it for an hour and changing all sorts of settings and restarting numerous times, I finally decided to restore the default configuration and manually change the driver from "vesa" to "fglrx". All is good now, and the Display module is working as it should. Conclusion: "aticonfig --initial" added some entries to xorg.conf that the Display module didn't like, and it wouldn't load. What's the deal? I have the drivers from the repositories, so I'm intersted to see if anybody else is having the same issue, and whether or not it has anything to do with whether the driver was manually installed from ATI's installer or the repositories. The OP has an Nvidia card and I don't know much about how they work in Linux, but is there an equivalent command that adds lines / parameters for those cards?

---

### Post by Geshtar on 2006-06-06
Well I have found the source of the problem, but still no idea on how to fix it.

After playing with the nvidia-xconfig and comparing what it generated with various flags, to what I had, the System Settings->Display tab is broken anytime I have Xinerama disabled.  If Xinerama is enabled, the Display tab works, although it cannot determine the resolution and the slider for changing the resolution is grayed out.

Unfortunately, having Xinerama on is not an option because it makes it so that windows do not know where screen borders are and makes maximizing windows impossible.  I tried the --no-xinerama-info-in-twinview option and that had no effect on anything it seems.

I'm beginning to think this is a bug.

---

### Post by mlord on 2006-06-10
I had this problem today on a fresh install of Dapper, with just the default x.org configuration / drivers, and the  latest KDE 3.5.3.

So I looked in ~/.xsession-errors to see what was wrong, and it had a traceback from some python code.   After poking around in there for a bit, I found the part that was failing for me:  a line that invoked "which xset" from within python.

The problem is, I have my own version of "which", that returns multiple matches (and aliases) by default, instead of just a single line.  So, I renamed my /usr/local/bin/which to /usr/local/bin/which.mine, and.. now it all works.

They really should hardcode /usr/bin/which into scripts like that.

Cheers

---

### Post by Geshtar on 2006-06-10
Well, I never messed around with X much aside from xorg.conf, so looking in .xsession-errors was a good idea that I had not done.

My error is also in a python script...the error is below:
> adding Display /usr/share/applications/kde/displayconfig.desktop
open /dev/mem: Permission denied
VESA BIOS Extensions not detected.


Pythonize constructor -- pid = 6456
Python interpreter initialized!



Pythonize constructor -- pid = 6456
Traceback (most recent call last):
  File "<string>", line 8, in kcontrol_bridge_create_displayconfig
  File "/usr/lib/python2.4/site-packages/displayconfig.py", line 1677, in create_displayconfig
    return DisplayApp(parent, name)
  File "/usr/lib/python2.4/site-packages/displayconfig.py", line 443, in __init__
    self.xsetup = XSetup(self.xconfigpath)
  File "/usr/lib/python2.4/site-packages/displayconfigabstraction.py", line 368, in __init__
    self._finalizeInit()
  File "/usr/lib/python2.4/site-packages/displayconfigabstraction.py", line 373, in _finalizeInit
    gfxcard._finalizeInit()
  File "/usr/lib/python2.4/site-packages/displayconfigabstraction.py", line 1082, in _finalizeInit
    screen._finalizeInit()
  File "/usr/lib/python2.4/site-packages/displayconfigabstraction.py", line 1632, in _finalizeInit
    self.original_size = self.getAvailableResolutions()[self.currentsizeindex]
IndexError: list index out of range


I unfortunately do not know python (on my list of things to learn), I took a peek at line 1632 where it appears to be dying, and I do not understand the code...it looks like they are calling a method with an array subscript tacked on to the end.......something I have never seen before with the languages that I have worked with.  I also do not konw what that /dev/mem/ permission denied is about.....

Anyone able to shed some light on this?

Thanks,
   Geshtar

---

### Post by mlord on 2006-06-10
[QUOTE=Geshtar]I also do not konw what that /dev/mem/ permission denied is about.....
[/QUOTE]
[QUOTE=mlord]
Mmmm.. let's check out the /dev/mem thing, and see if it really matters here or not.   Try this, in a konsole (terminal) window:[/QUOTE]

Nevermind.. I just tried things here, and *that* is not the issue (/dev/mem is fine).

Must be something wrong elsewhere..

---

### Post by mlord on 2006-06-10
Mmm.. I'm no python guru, but it looks as if the code probably failed to parse the mode lines from your xorg.conf file, which could happen if you have manually edited the file, or if some other tool has mucked with it.

I think it is looking for a line in the "Display" subsection of the "Screen" section, that resembles this (one big long line}:

modes "1920x1200@60" "2560x1600@60" "1920x1200@75" "1680x1050@75" "1680x1050@60" "1600x1024@60" "1440x900@60" "1440x900@75" "1280x800@60" "1280x720@50" "1280x768@75" "1280x800@75" "1280x720@60" "1280x768@60" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "720x400@85" "640x350@85" "640x400@85"

Or it could be some other problem.  :)

It might be looking for the individual "modeline" lines from the "Monitor" section instead..  They look like this (specific to my machine):

  modeline  "640x400@85" 31.5 640 672 736 832 400 401 404 445 -hsync +vsync
  modeline  "640x350@85" 31.5 640 672 736 832 350 382 385 445 +hsync -vsync
  modeline  "720x400@85" 35.5 720 756 828 936 400 401 404 446 -hsync +vsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
...
  modeline  "1920x1200@75" 246.59 1920 2064 2272 2624 1200 1201 1204 1253 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync

---

### Post by mlord on 2006-06-10
> 
File "/usr/lib/python2.4/site-packages/displayconfigabstraction.py", line 1632, in _finalizeInit
self.original_size = self.getAvailableResolutions()[self.currentsizeindex]
IndexError: list index out of range


Try editing that file, and comment out line 1632 (just stick a # character in front of it), and then add this line just above or below the original line 1632:

self.original_size = (800, 600)

And then see if it comes to life (ugly hack, I know, but just to see if it gets us further).

Then restore the original file again (undo those changes).

---

### Post by tkman on 2006-06-14
Is anyone posting these issues as bugs so they can be fixed?

---

### Post by hedgey504 on 2006-08-08
This turns out to be an easy fix.  Edit this file as root (sudo):

/usr/lib/python2.4/site-packages/displayconfigabstraction.py

Change line 1648 as follows:

```
            if (size[0],size[1]) in self.standard_sizes]
```

to
```
            if (1) ] #(size[0],size[1]) in self.standard_sizes] 
``` (commenting out the remainder of the line)

Basically the function  _computeSizesFromXorg() gets the available sizes from  self.x_live_screen.getAvailableSizes() and then promptly discards any that are not in self.standard_sizes.  TwinView resolutions are generally not standard.  Woops.

Original block:
```

    def _computeSizesFromXorg(self):
        self.available_sizes = [
            (size[0],size[1]) \
            for size in self.x_live_screen.getAvailableSizes() \
            if (size[0],size[1]) in self.standard_sizes]

```

---

