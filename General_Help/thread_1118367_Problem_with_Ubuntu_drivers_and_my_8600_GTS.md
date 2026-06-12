---
title: "Problem with Ubuntu drivers and my 8600 GTS"
date: 2009-04-06
forum: General Help
---

### Post by Jpoppyz on 2009-04-06
I recently made the switch to ubuntu and i'm enjoying it, but I'm having with some problems with the video card drivers and my video card. I installed the NVIDIA accelerated graphics driver(version 177) so i could enable desktop effects, and ubuntu is not letting me. When i try to enable them i get the error "desktop effects could not be enabled." I want a more aesthetically pleasing OS considering my GPU can handle it and ubuntu won't let me.

What do i do?

---

### Post by cariboo on 2009-04-06
Are you sure the driver is installed correctly? Check your /etc/X11/xorg.conf, the device section should look like this:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

Jim

---

