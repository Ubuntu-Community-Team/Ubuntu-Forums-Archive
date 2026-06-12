---
title: "Keyboard and mouse don't work after I start X"
date: 2009-03-12
forum: General Help
---

### Post by kahlil88 on 2009-03-12
I'm trying to reconfigure X.org because it stopped working a few days ago. I can now start X, but my keyboard and mouse (both are USB) don't work at all afterward. The keyboard obviously works, as I need it to start X in the first place, and I have verified that the mouse works with **cat /dev/input/mouse0**

---

### Post by MaxIBoy on 2009-03-12
Can we see your xorg.conf?

---

### Post by kahlil88 on 2009-03-12
I should probably mention I'm running Gentoo x86-64

---

### Post by MaxIBoy on 2009-03-12
Try giving your mouse its own "inputdevice" section. That's what it looks like in mine.

You've probably already read this, but just to be sure:
[http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html)

---

### Post by Yellow Pasque on 2009-03-12
In X Server 1.5.x, configuration of input devices is done automatically by HAL to take advantage of input device hotplugging. HAL doesn't like the kbd or mouse drivers (it wants evdev), so you can either use "evdev" intead of kbd/mouse or you specify this option in xorg.conf to disable HAL for input devices (also disables input hotplugging):
```
Section "ServerFlags"
     Option "AutoAddDevices" "False"
EndSection
```

See this for more detail: [http://wiki.archlinux.org/index.php/Xorg_input_hotplugging](http://wiki.archlinux.org/index.php/Xorg_input_hotplugging)

---

### Post by kahlil88 on 2009-03-12
Thank you, Temüjin! Gnome is now up and running, but the mouse still isn't working (oddly enough, I still get junk output with **cat /dev/input/mouse0**).

---

### Post by Yellow Pasque on 2009-03-12
So what did you opt for, installing evdev or using Option "AutoAddDevices" "False"?
BTW, why are you trying to cat a block device file?

A /var/log/Xorg.0.log might be helpful here...

---

### Post by kahlil88 on 2009-03-12
> **Temüjin said:**
> So what did you opt for, installing evdev or using Option "AutoAddDevices" "False"?
BTW, why are you trying to cat a block device file?

A /var/log/Xorg.0.log might be helpful here...
I added the **Option "AudoAddDevices" "False"** bit to my xorg.conf, and I was using the **cat /dev/input/mouse0** to test that it saw my mouse (someone suggested it on another forum).

---

### Post by Yellow Pasque on 2009-03-12
I see this:
```
(II) Loading /usr/lib64/xorg/modules/input//mouse_drv.so
dlopen: /usr/lib64/xorg/modules/input//mouse_drv.so: undefined symbol: miPointerGetMotionEvents
(EE) Failed to load /usr/lib64/xorg/modules/input//mouse_drv.so
(II) UnloadModule: "mouse"
(EE) Failed to load module "mouse" (loader failed, 7)
```
Make sure that file exists and has the proper permissions (644). You may need to recompile that module (xf86-input-mouse).

Also, you'll probably want to add this to your xorg.conf Device section:
```
Option "DRI"
Option "AccelMethod" "EXA"
```

---

### Post by kahlil88 on 2009-03-12
Where would I be without you, Temüjin? I re-emerged the mouse driver like you suggested and it's working again! I'm curious though...what will the DRI and EXA options do?

---

### Post by Yellow Pasque on 2009-03-12
DRI will allow video hardware acceleration (fast), instead of CPU-accelerated video (slow).

Long Answer: [http://en.wikipedia.org/wiki/Direct_Rendering_Infrastructure](http://en.wikipedia.org/wiki/Direct_Rendering_Infrastructure)

---

