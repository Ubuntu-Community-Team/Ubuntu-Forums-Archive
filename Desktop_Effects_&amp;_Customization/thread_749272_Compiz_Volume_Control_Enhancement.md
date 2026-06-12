---
title: "Compiz Volume Control Enhancement"
date: 2008-04-08
forum: Desktop Effects &amp; Customization
---

### Post by PattonPending on 2008-04-08
Hi everyone,
I've dug through the forums and googled incessantly, but can't seem to find a good solution.

I'm looking for a way to disable the Compiz enhancements that override the default gnome volume enhancements.

Curiously the popup for screen brightness is unaffected, but the volume control is now a semi-transparent box that occupies too much of my screen for my liking.

Any help would be greatly appreciated.

Thanks.

---

### Post by PattonPending on 2008-04-15
Bump.

Any ideas?  If anyone has any ideas, needs more information from me, or has the same issue I'd greatly appreciate hearing from them.

Thanks in advance.

---

### Post by Half-Left on 2008-04-15
Not sure what you mean, can you post a screenshot?

---

### Post by strabes on 2008-04-15
I believe the attached screenshot is what he means. No idea how to disable it; I really like it, but it is very similar to that of OS X.

---

### Post by PattonPending on 2008-04-15
> **strabes said:**
> I believe the attached screenshot is what he means. No idea how to disable it; I really like it, but it is very similar to that of OS X.

Yes, that's exactly it.  Thanks for taking the screenshot. 

I wouldn't mind it so much if the effect were consistently applied, but other OSD's (like screen brightness, for example) aren't styled the same way, and retain the standard appearance from Gnome.

I'm thinking it has to be buried in Compiz somewhere (though that's an absolute blind guess) as it only adopts that style after the rest of the visual effects on the machine are fully loaded.  So if I adjust the volume while the system is still loading I get the standard Gnome OSD, and then shortly after it turns into the stylized one.

---

### Post by Zorael on 2008-04-15
It's likely possible to exempt the volume control OSD from receiving effects from Compiz. You either need to know the "name" of it, or its class.

Try opening a terminal and running xwininfo.
```
$ xwininfo
```

This should change your cursor to a cross. Now change your volume via whatever you were using earlier (special keyboard keys, mouse buttons, etc), and while the OSD is displayed, click it. The terminal should be flooded with some information about the window, including name and class.

Then it's just a matter of finding where in Compiz's settings (in ccsm, naturally) to exclude it.

[See this thread.](http://forum.compiz-fusion.org/showthread.php?t=558)

---

### Post by PattonPending on 2008-04-16
> **Zorael said:**
> It's likely possible to exempt the volume control OSD from receiving effects from Compiz. You either need to know the "name" of it, or its class.
...
Try opening a terminal and running xwininfo.
```
$ xwininfo
```



Thanks Zorael, good idea.  FYI the xwininfo output is:

```

xwininfo: Window id: 0xa00006 "gnome-settings-daemon"
  Absolute upper-left X:  558
  Absolute upper-left Y:  645
  Relative upper-left X:  558
  Relative upper-left Y:  645
  Width: 284
  Height: 284
  Depth: 32
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0xa00005 (not installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: yes
  Map State: IsViewable
  Override Redirect State: yes
  Corners:  +558+645  -558+645  -558-121  +558-121
  -geometry 284x284+558+645

```

I can't find anywhere in Compiz that seems to recognize any of the info generated either through this command or the "grab" option for selecting window parameters.  

I've tried disabling/affecting the OSD through settings in "Window Rules", "Place Windows", and "Window Decoration".  No effects seemed to work.

I also disabled most plugins I had active, to no effect.  The volume control remained candy coated.  

I have the feeling that this is more "under the hood" somehow, but I'm having trouble guessing where that could be.

Any comments given this information or other places to look would be great

Thanks again for the help.

---

### Post by PattonPending on 2008-04-17
Doing some more research, according to this thread: [cool new volume control]("http://ubuntuforums.org/showthread.php?t=376537&highlight=Cool+new+volume+control") it appears to actually be a feature of Gnome that kicks in when there is a compositing window manager present.

 I'm going to dig around in gconfeditor and see what shows up.

Anybody know of any way to force Gnome to default to the old controls?

---

### Post by PattonPending on 2008-04-19
I found the controls in gconf-editor that allow for the resizing of the default on screen displays, as well as adjusting the size of the volume steps and key bindings, (apps->gnome_settings_daemon).  However there doesn't seem to be any keys that would make the daemon default to the non-composited display.

Anyone have any good ideas for where to look?  Seeming now like it might be a limitation of Gnome?

---

### Post by PattonPending on 2008-04-21
A couple of days ago I posted a request for information over on [ the Gnome Desktop Forums ]("http://gnomesupport.org/forums/viewtopic.php?t=13273"), but thus far don't seem to be getting a lot of traffic.  

Those forums don't seem to be as active as the Ubuntu ones ;)

I'm going to try going through CCSM and removing different plugins again, this time with a more thorough full restarting of X instead of just reloading Compiz.  Hopefully something will click and help narrow down the *part* of the compositing engine that the Gnome OSD's are latching onto.

---

### Post by PattonPending on 2008-04-24
I'm still mucking about in CCSM trying to see if there's a way to impact the display of the volume meter from the gnome-settings-daemon.  No luck yet, so I went to the extreme.

Just to confirm that the issue is directly related to compositing and Gnome, I added the following section to my /etc/X11/xorg.conf:

```

#Section "Extensions"
#       Option "Composite" "Disable"
#EndSection

```

I then restarted X.  When I logged back in, the displays had defaulted to the standard Gnome OSD for volume.

The only response I've received on the Gnome forums indicated that they weren't sure if there were any controls in gconf to enable/disable the old behavior, so it looks like I'm limited to trying to figure out how to disable the compositing, rather than getting Gnome to "just work". 

Does anyone know of any way to disable *all* compositing but only for a specific application/daemon?

---

### Post by dspiteri on 2008-06-11
I'm with you. Besides looking like ***, the new gnome OSD fadeout effect uses some bodge which causes the display to stutter. Even on a high-end system. :confused:

---

### Post by macduy on 2008-06-17
Hi,

I got the same problem, I don't like the composited volume OSD and besides, it controls a different slider other than the one I set in the Volume Control. 

Hope they get this fixed soon-

---

### Post by brainkilla on 2008-07-15
> **dspiteri said:**
> I'm with you. Besides looking like ***, the new gnome OSD fadeout effect uses some bodge which causes the display to stutter. Even on a high-end system. :confused:

You must be using an nVidia card, right? Since I experience the same stuttering on a Athlon64 X2@3GHz with 2GB RAM and 9600GT 512MB, a system I daresay should be sufficient for proper acceleration of measly volume control widget... check out official nV forums, they are filled with similar complaints...

---

### Post by dspiteri on 2008-07-20
> **brainkilla said:**
> You must be using an nVidia card, right?

Yeah my system is a similar build to yours. This wasn't a problem with GG...

---

### Post by reacocard on 2008-07-20
sorry to burst everyone's bubble, but there's not any way to get rid of it. the volume dialog now just uses that mode whenever compositing is available, which can be provided by compiz, xfwm4 or other compositors. the only way to disabel ti would be by recompiling te program responsible for that popup with that bit of code removed/disabled, which is likely not easy to do.

---

