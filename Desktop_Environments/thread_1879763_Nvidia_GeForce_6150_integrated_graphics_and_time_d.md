---
title: "Nvidia GeForce 6150 integrated graphics and time delays on dash"
date: 2011-11-12
forum: Desktop Environments
---

### Post by keithpeter on 2011-11-12
Hello All

My Asus Pundit uses Nvidia GeForce 6150 integrated graphics which is blacklisted for Unity. The lspci string with the exact hardware description is below...

```
VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2)
```

I've found the following work arounds...

1) In file /etc/environment add

```
UNITY_FORCE_START=1
```

to overcome the blacklisting. No issues so far, but Fedora 15 used to freeze on this same hardware so watching out for freezes.

2) The responsiveness of Unity 3d improves using the work around mentioned in bug #92599, so that the xorg.conf file looks like this (line added to the default xorg.conf file is bold)

```
Section "Screen"
	Identifier	"Default Screen"
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
	**Option "DynamicTwinView" "False"**
EndSection
```

**[SIZE="3"]Question[/SIZE]**

Is the time delay in appearance of the launcher and in the appearance of the dash configurable? Or is that delay governed by the time to read the search index or the graphics speed?

On this hardware, dash takes about half a second to appear.

Super-W and Super-S work at the same speed as they used to under Compiz on 10.10, and significantly faster than the dash. The animation is less smooth than with 10.10 but I suppose that is progress :twisted:

---

### Post by ademey on 2011-12-13
I have the same card and noticed the delay when hitting the dash button as well. Also, the first time in every session I right-click a program icon on the unity panel, options are not highlighted and I cannot select them. Instead the mouse pointer is active on the what's underneath the panel.

---

