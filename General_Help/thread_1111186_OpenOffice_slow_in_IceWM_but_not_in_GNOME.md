---
title: "OpenOffice slow in IceWM but not in GNOME"
date: 2009-03-30
forum: General Help
---

### Post by oinkl on 2009-03-30
I'm currently using Linux Mint Felicia.

As per title, when navigating menus and dragging taskbars around in OpenOffice in IceWM, the menus and taskbars take half a second to redraw. When I drag taskbars around, it leaves trails of windows behind it. The whole experience is generally very very laggy, as if my graphics drivers were not installed.

This is not an issue in GNOME(my graphics card drivers work fine in GNOME).

What could be the cause? Is it because of IceWM, or is IceWM not detecting my graphics card drivers, or could it be something else entirely? How do I check if IceWM has detected my graphics card drivers?

These are the contents of xorg.conf

```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

```

---

### Post by kerry_s on 2009-03-30
gedit ~/.bashrc

put> export OOO_FORCE_DESKTOP=gnome

log out and back in.

---

