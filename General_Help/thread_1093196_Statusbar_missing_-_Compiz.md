---
title: "Statusbar missing - Compiz"
date: 2009-03-11
forum: General Help
---

### Post by prkos on 2009-03-11
When window is maximized statusbar is hidden, it looks like it's behind the gnome panel, like the window is vertically too big and extends downwards. 

When window is unmaximized the statusbar is there. 

It happens in every application I tried to maximize (Firefox, thunderbird, nautilus, gedit, inkscape). 

It doesn't happen when using Metacity, only when using Compiz. I tried to play with the Workaround options but it doesn't seem to affect it. 

This started happening today when I booted the comp, I don't know what's causing it but I installed OpenOffice 3 yesterday through their own launchpad repository, some java packages were in there. I've noticed compiz/openoffice problems before (flickering window borders).

---

### Post by binbash on 2009-03-11
Are you sure you unticked legacy fullscreen support at workarounds section at compizconfig settings manager?

---

### Post by prkos on 2009-03-11
Yes, I'm sure. I tried various combinations, ticked, unticked, then options for specific applications like Firefox and OpenOffice, no change. 

I also tried disabling the whole Workarounds section. Maybe it needs reboot to catch it on? Although when I had the "weird Firefox fullscreen" problem a while ago the changes in Workarounds were instant. 

I'll try reboot now with Workarounds disabled. 

btw could it be edgeresistance? I have Wobbly windows enabled and apparently this is an option there. Maybe the snapping occurs at the bottom edge of the screen instead of the gnome panel when in full screen. 
I also have one gnome panel on the left side of the screen and snapping seems to work as expected there.

---

### Post by prkos on 2009-03-11
I got the statusbar back, I think the issue was in nVidia settings (System > Administration > NVIDIA X server settings). The day before I changed the panning size of the TV output. I set it to 1000x1000 but today when I checked it it was 800x600. So I saved it again (sudo) as 800x600 and rebooted, it's working ok now. 

I'm not sure but there may be one other thing that influenced this - setting the TV output as primary output for X screen. I changed it back to monitor.

---

