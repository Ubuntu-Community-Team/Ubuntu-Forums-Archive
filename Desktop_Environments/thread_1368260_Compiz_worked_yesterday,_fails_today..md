---
title: "Compiz worked yesterday, fails today."
date: 2009-12-30
forum: Desktop Environments
---

### Post by samthurston on 2009-12-30
I rebooted my machine last night as I often do, only to discover this morning that desktop effects were disabled.  I attempted to re-enable them thusly:


```
system > preferences > appearance (visual effects tab > normal)
```

the screen flickers for a bit and then says "desktop effects could not be enabled"

Odd. Worked fine yesterday.

well, I have a custom kernel maybe something is hokey: 

```
$ lsmod | grep nvidia
nvidia              10310364  26 
```

No, that looks ok.  Anything in the logs?

```
$ cat /var/log/Xorg.0.log | grep [EW][EW]
Current Operating System: Linux kestrel 2.6.32-kestrel1 #1 SMP PREEMPT Mon Dec 7 00:41:30 CST 2009 x86_64
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(II) Loading extension MIT-SCREEN-SAVER
```

No show stoppers there. what about 
```
$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: GeForce 8600 GT/PCI/SSE2
    GL_NV_depth_buffer_float, GL_NV_conditional_render, GL_NV_depth_clamp, 
    GL_NV_vertex_program3, GL_NVX_conditional_render,
```

Ok, everything's set up right, is there something I'm missing?

```
compiz --replace &
aborting and using fallback: /usr/bin/metacity
```

FOR SERIOUS?!

I'm out of ideas... any suggestions?

---

### Post by samthurston on 2009-12-30
just for fun I downloaded and ran the compiz-check
```
$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G84 [GeForce 8600 GT] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]
```

Is there someplace that compiz should be logging why it won't run?  I tried /var/log/user.log, nothing there, and I can't find any options for command line compiz execution for verbosity control.

---

### Post by samthurston on 2010-01-03
Why has this thread gotten no response?  It it the wrong forum? Did I fail to make the title bold and red?  Is more information required?

Bump.

---

### Post by samthurston on 2010-01-04
There are more symptoms and I think that this is all related somehow, but I'm at a bit of a loss as to how and how to fix it.

Compiz will successfully run for another user.
All the icons from my notification area have disappeared.  
I cannot mount a partition, it fails with the message "Authentication is Required."
I tried to edit my user permissions when trying to fix these issues and found that although all my permissions are checked, when I click the "click here to make changes" nothing happens.

sudo and gksudo work fine from the command line.

I'm convinced this has something to do with policykit but policykit is completely foreign to me.


Solution: the entire set of symptoms went away when I switched the user session type from "GNOME Failsafe" to "GNOME" in gdm.

---

