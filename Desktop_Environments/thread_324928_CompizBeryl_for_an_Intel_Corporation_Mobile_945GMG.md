---
title: "Compiz/Beryl for an Intel Corporation Mobile 945GM/GMS/940GML video card"
date: 2006-12-24
forum: Desktop Environments
---

### Post by jenigmat429 on 2006-12-24
I've been trying to get beryl/compiz with an Intel Corporation Mobile 945GM/GMS/940GML video card, and each time I've had to go back to one of the backup copies of the xorg.conf file that I've made. I've used several different tutorials, and none of them have worked. Does anyone have any tips?

---

### Post by robgill on 2006-12-24
> **jenigmat429 said:**
> I've been trying to get beryl/compiz with an Intel Corporation Mobile 945GM/GMS/940GML video card, and each time I've had to go back to one of the backup copies of the xorg.conf file that I've made. I've used several different tutorials, and none of them have worked. Does anyone have any tips?

This one worked for me:

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX)

---

### Post by jenigmat429 on 2006-12-24
Sorry, I probably should have specified, but I've tried the guides for edgy, because I'm using edgy.

Sorry, forgot about this part: So is there anything that might help for Edgy? When I use the guides it tells me "beryl: no composite extension" when I've modified the xorg.conf to add a composite extension.

---

### Post by d3v1ant_0n3 on 2006-12-24
I have an 845 chipset, the xorg setup is pretty much the same ...

My "Device" section
```
Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	65536 #forces memory to 64mb
	Option "XAANoOffscreenPixmaps" "true" #I added this line for beryl
EndSection
```

I added to comments to highlight what I changed

You'll also need this section

```
Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
Option "Composite" "true"
EndSection
```

Hope that's of some help.

---

### Post by jenigmat429 on 2006-12-24
Nope. I changed my conf as you said and I'm getting the same thing. Do I need anything for my graphics card?

---

### Post by jenigmat429 on 2006-12-24
Actually, I noticed something. On the Beryl wiki, I read that Intel drivers should have all of the drivers and stuff by default.  However, when I input "$ glxinfo | grep direct", I get a no, instead of a yes. Since it says that there's no driver's for Intel video cards, I don't know what to do to install XGL.

---

### Post by d3v1ant_0n3 on 2006-12-24
If you're using Edgy, you don't need XGL- AIGLX is already installed.

The DRI section in Xorg.conf should enable direct rendering for you.

---

### Post by jenigmat429 on 2006-12-25
My DRI section is the same as yours, but I'm still getting a no for direct rendering

---

