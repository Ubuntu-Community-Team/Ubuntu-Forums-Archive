---
title: "Strange UT2004 Error"
date: 2007-03-17
forum: Gaming &amp; Leisure
---

### Post by MasterRex on 2007-03-17
Okay, first off:

Installing UT2004 was simple. Quite a breeze, other than the fact that I kept pressing Shift+Backspace while using Gaim. [Annoying, but no problem to anything other than my time and peace of mind.] 
[[Thank -insert deity here- for Session Restore. I did it while composing this thread.]]

I'm running Edgy, however it's not the most 'up-to-date' version. I *did* update at one point, but with the death of my wireless drivers (which were a pain on their own..) and the concurrent death of my ATi drivers, I just continued to select my older version of Edgy in the boot menu. 

Now, to my specific problem --

```

**##The UT2004 Error**

rex@rex-desktop:~$ ut2004
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
WARNING: ALC_EXT_capture is subject to change!
Either GL_EXT_bgra or glDrawRangeElements not supported- bailing out.

History: 

Exiting due to error

```
```

**##Notice the frame rate. **

rex@rex-desktop:~$ glxgears -printfps
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
52039 frames in 5.0 seconds = 10387.169 FPS
57604 frames in 5.0 seconds = 11520.782 FPS
57148 frames in 5.0 seconds = 11424.954 FPS
57131 frames in 5.0 seconds = 11417.148 FPS
57490 frames in 5.0 seconds = 11486.946 FPS


```

Everything appears to be working fine, in fact the only error that I can physically find appears while opening ATi Control. The error reads:

'Driver does not provide the FireGL X11 extensions! Panel components will only operate partially!'

The it correctly shows that my driver/renderer is in fact NOT 'mesa' -- nor does it say 'indirect' as it has done in past installs and ATi driver complications. 

As noted with the frame rate printed in the glxgears session, the rest of my 3D accelerated applications[Enemy Territories, WorldForge:Sear, Torcs, X-Moto, SupertuxKart, etc etc.] work flawlessly. Also noted; there does seem to be a driver conflict. 

EDIT: Is Ubuntu confused?
```

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
   	Option       "no_accel" "no"
   	Option       "no_dri" "no"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

```

Alright, 'vesa'. My heart sank when I realized that section was still in my Xorg.conf file. In a moment, I'll attempt to either comment the section out, or instead rename 'vesa' to 'fglrx'. Sadly, I'm nearly certain that a destiny slugging through nano in the recovery kernal awaits me. I'll try this, and report back. [The only reason I believe it may work, is because my drivers have been installed quite properly, and there's nothing else I can think of to fix it, so why not? :) ]

 Sorry for the long read, and thank you for your time. 
[I'm not too new to Ubuntu/different Linux Distros, but do excuse me if I seem nubbish.] 

--MasterRex @ [www.GigaYetti.com](www.GigaYetti.com)

---

### Post by MasterRex on 2007-03-18
Bump. Any answers or suggestions would be helpful.

---

### Post by Darknet on 2007-03-18
i'm getting something similar. 

"WARNING: ALC_EXT_capture is subject to change!

Couldn't set video mode: Couldn't find matching GLX visual"

any ideas?

EDIT - 

"Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0"."
"Couldn't set video mode: Couldn't find matching GLX visual"

these two also show up in my terminal.

---

### Post by daller on 2007-06-28
In gameplay, ut2004 suddenly crashes...

This is the output:

```
daniel@daller:~$ ut2004
WARNING: ALC_EXT_capture is subject to change!
Signal: SIGSEGV [segmentation fault]
Aborting.
Crash information will be saved to your logfile.
```

And sometimes this:

```
daniel@daller:~$ ut2004
WARNING: ALC_EXT_capture is subject to change!
center pointSignal: SIGSEGV [segmentation fault]
Aborting.
Crash information will be saved to your logfile.
```

I'm running a 64-bit PC - If that changes anything!

---

### Post by chaser.nl on 2009-05-22
i am getting the same error on jaunty 9.04 (2.6.28-12-generic)

---

