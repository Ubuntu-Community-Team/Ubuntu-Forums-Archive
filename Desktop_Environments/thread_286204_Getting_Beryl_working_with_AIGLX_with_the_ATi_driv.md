---
title: "Getting Beryl working with AIGLX with the ATi driver"
date: 2006-10-27
forum: Desktop Environments
---

### Post by wolphin on 2006-10-27
Hi,

I first followed [this](http://paste.ubuntu-nl.org/28639/) and downloaded the ATi driver mentioned there. I then found the [BerylOnEdgy](https://wiki.ubuntu.com/BerylOnEdgy#head-51ebf4450aca8da36670c603441db9fed0a3868e) wiki page, but that says that I need the 'open source radeon driver' - is the driver I downloaded the open source one?

I installed Beryl by following this wiki page: [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

When my xorg.conf was like this, X locked up whenever I started beryl-manager):
> Section "Device"
 	Identifier	"ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option 		"DRI" "true" 
	Option 		"ColorTiling" "on"
	Option 		"EnablePageFlip" "true"
	Option 		"AccelMethod" "EXA"
	Option 		"XAANoOffscreenPixmaps"
	Option 		"RenderAccel" "true"
	Option 		"AGPFastWrite" "on"
EndSection
I then got told to change it to this:
> Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"VideoOverlay" "on"
	Option 		"OpenGLOverlay" "off"
EndSection

Section "Extensions"
	Option		"Composite" "false"
EndSection
I understand why the composite extension is disabled ([http://felipe-alfaro.org/blog/2006/09/06/ubuntu-edgy-ati-fglrx-dri-3d-acceleration-and-xorg-composite-extension)](http://felipe-alfaro.org/blog/2006/09/06/ubuntu-edgy-ati-fglrx-dri-3d-acceleration-and-xorg-composite-extension)), but not why OpenGLOverlay is. With this xorg.conf, beryl-manager does not work, but neither do the 3D effects.

What can I do to make Beryl work with AIGLX? If you need any more details, please let me know.

Thanks in advance.

---

### Post by davec64 on 2006-10-28
I'm suffering with Beryl as well, have a loo at this [thread ]("http://ubuntuforums.org/showthread.php?t=286965&highlight=edgy+aiglx+beryl")as well!
They haven't solved it either, but your not alone!

---

### Post by MattJ100 on 2006-10-28
[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

That blog post, combined with the Bery wiki page helped me get it working.

---

### Post by chaosgeisterchen on 2006-10-28
You know that that blog entry shows a how-to for **XGL** and not for **AIGLX**?

In fact you're completly heading in the false directory. **AIGLX** only works with the **radeon** driver. **fglrx** will not work as it does not support the Extension needed for running AIGLX.

---

### Post by MattJ100 on 2006-10-30
Sorry, AIGLX, XGL, whatever :) Sorry. Just note that XGL worked fine for me and I'm happy (for once).

---

### Post by mrfuzzemz on 2006-10-30
AIGLX is different and integrated better than XGL as it is a plug-in rather than a hack.  What I'd love to have is a nice easy howto to get AIGLX running on a fresh install of Edgy.

---

### Post by MattJ100 on 2006-10-30
> **mrfuzzemz said:**
> AIGLX is different and integrated better than XGL as it is a plug-in rather than a hack.  What I'd love to have is a nice easy howto to get AIGLX running on a fresh install of Edgy.
I know, but I had no luck with it with my ATI card. You're right, a howto would be nice :)

---

### Post by blitzer on 2006-10-30
> **MattJ100 said:**
> [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

That blog post, combined with the Bery wiki page helped me get it working.


[COLOR="Red"]Thanks for the great link MattJ100[/COLOR]  8)   I am currently typing from beryl and wobbly windows  :-D 

[COLOR="Blue"][SIZE="4"]And again a great thank you goes to Lennart Hansen for his graphical How To

[/SIZE][/COLOR]

---

### Post by mrfuzzemz on 2006-10-30
Hmmmm... I'm just curious.  What cards have people gotten AIGLX to work with?

---

### Post by MattJ100 on 2006-11-01
> **blitzer said:**
> [COLOR="Red"]Thanks for the great link MattJ100[/COLOR]  8)   I am currently typing from beryl and wobbly windows  :-D 

[COLOR="Blue"][SIZE="4"]And again a great thank you goes to Lennart Hansen for his graphical How To

[/SIZE][/COLOR]
Hey, np :P Glad it worked out.

---

