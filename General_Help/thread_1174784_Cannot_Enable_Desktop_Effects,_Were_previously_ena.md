---
title: "Cannot Enable Desktop Effects, Were previously enabled."
date: 2009-05-31
forum: General Help
---

### Post by gx_hanson on 2009-05-31
Good morning everyone. 

I'm aware that you've all probably seen this before, but I've been searching for a while and I haven't managed to find any parallels between similar problems and the one I've been experiencing. 

I Installed Intrepid over a month ago, and from day one Desktop Effects have been enabled, no problems. Compiz has been performing excellently, and I haven't had to fiddle with anything. Just a few days ago, I installed google earth 4.3, and in an attempt to get it (the program) to stop crashing I turned off all desktop effects. 

Now I can't turn them back on. I'm 99% nothing else was changed at all in the meantime. I've been searching around online the past few days, and I managed to track down the compiz-check script, but running that doesn't seem to help. 

As I previously stated, I'm running Ubuntu Intrepid Ibex 8.10, fully updated (to my knowledge). I'm running it on a Sony Vaio VGN-CR220E, which has an Intel GMA 965, with an X3100 card (I think?) I'm relatively new to linux, but this past month has been a bit of a crash-course, and I know enough to get around. 

I've posted the compiz-check output below, as well as the /etc/X11/xorg.conf contents. I hope someone here can help me with this. 

This is the output of the compiz-check script, the first time around:

```
graham@little-buddy-II:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Another compositing manager in use. 

Would you like to know more? (Y/n) y

 It has been detected, that you are currently running xcompmgr, which is a
 standalone compositing manager.
 If this one is in use, Compiz will not be able to run. 

Do you want to disable xcompmgr? (Y/n) y
```I followed the suggestion, disabled xcompmgr, and ran the script again, and this is what I get now:

```
graham@little-buddy-II:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
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
```Here is the output for typing compiz into the terminal (after disabling xcompmgr):
```
graham@little-buddy-II:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: glXCreateContext failed
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
/home/graham/.gtkrc-2.0:14: error: invalid string constant "my_color", expected valid string constant
Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
```And lastly, here is my xorg.conf file:

Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Again, any help anyone has to offer would really be appreciated, this has been driving me up the wall the past few days.

---

### Post by Lunx on 2009-05-31
Might be too simplistic for it to be the answer, but have you checked that the Extra Effects button is checked under System--> Preferences--> Appearance--> Visual Effects?

---

### Post by rainwalker on 2009-05-31
Just for kicks, try ```
SKIP_CHECKS=yes compiz
```That will skip straight to trying to force compiz to start, (hopefully) bypassing any checks for blacklisted videocards, which yours may have become.

---

### Post by CatKiller on 2009-05-31
Another thing to check would be to make sure that the ```
/apps/metacity/general/compositing_manager
``` key is **un**ticked.

---

