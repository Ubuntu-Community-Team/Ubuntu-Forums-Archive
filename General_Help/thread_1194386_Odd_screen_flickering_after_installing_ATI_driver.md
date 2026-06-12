---
title: "Odd screen flickering after installing ATI driver"
date: 2009-06-22
forum: General Help
---

### Post by Kamaria on 2009-06-22
Specs:
Kubuntu 9.04
AMD Phenom II 810 2.6 ghz
OCZ 6 GB Ram
ATI Radeon HD 4850 

I just installed Kubuntu 9.04 on my brand new computer. The screen was fine until I activated and installed the proprietary driver...then, upon restarting, I noticed this odd occasional weird flickering on my screen when the OS started...these black translucent bands across the screen flashing at regular intervals. It cause my mouse clicks to lag for some reason, and would go away after a while...but when I start certain applications, like Steam running in Wine, it'll come back...

Any idea on how to fix this?

---

### Post by HavocXphere on 2009-06-22
If its a CRT screen then switch off the RandR service...its somewhere in the menus.

I had the some thing on 8.10. Intervals were ~1 sec and it was ~ 1cm think line, mostly towards the top of the screen.

---

### Post by Kamaria on 2009-06-22
Can't seem to find it. >.<

---

### Post by sedawk on 2009-06-22
What happens if you replace compiz with a more classic window manager?
```

nohup metacity --replace &

```

Something I had to do to make video playback work properly (/etc/X11/xorg.conf) is the TexturedVideo option:

```

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	BusID       "PCI:1:5:0"
	Option "TexturedVideo" "On"
	Driver	"fglrx"
EndSection

```

---

