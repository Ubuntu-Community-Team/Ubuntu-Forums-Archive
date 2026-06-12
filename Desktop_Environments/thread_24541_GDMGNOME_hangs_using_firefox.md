---
title: "GDM/GNOME hangs using firefox"
date: 2005-04-07
forum: Desktop Environments
---

### Post by johneboy on 2005-04-07
Hi All,

This morning I updated my desktop and laptop when the update notifier informed me of changes. Since then I am having random occurrences where when following a hyperlink in firefox the entire gnome desktop hangs, the mouse cursor moves but clicking has no effect and the keyboard is unresponsive (so can't ALT+TAB between applications).  The only way out of this situation is to hit the reset button on the machine, using CTRL+ALT+BACKSPACE or CTRL+ALT+Fx is unresponsive.  If I have rhythmbox playing music the music continues when the UI locks up.

Does anybody have an idea what's going on?

Thanks in advance

John

---

### Post by wolovids on 2005-04-07
Maybe you are having the [same problems](http://ubuntuforums.org/showthread.php?t=24279) we are with the nvidia drivers?  Hopefully the problem will be resolved very soon.

---

### Post by PMO6022 on 2005-04-07
I have been having the exact same problem as the original poster, but I haven't found a solution. I am using the nvidia driver, so maybe that is it. I'm off to read the other thread.

---

### Post by Knome_fan on 2005-04-07
[QUOTE=PMO6022]I have been having the exact same problem as the original poster, but I haven't found a solution. I am using the nvidia driver, so maybe that is it. I'm off to read the other thread.[/QUOTE]

Disableing RenderAccel as suggested in the other thread worked for me.

---

### Post by johneboy on 2005-04-07
Thanks for the advice folks.  Both of my machines have NVidia cards.

I'll try the things recommended and see if that fixes the problem and post the results here.

Regards

John

---

### Post by PMO6022 on 2005-04-07
[QUOTE=Knome_fan]Disableing RenderAccel as suggested in the other thread worked for me.[/QUOTE]

I am trying this out, but it is hard to prove something _isn't_ happening.  I'll give it a few days and see.  Hopefully it works out.  Thanks.

---

### Post by danpre on 2005-05-04
[QUOTE=Knome_fan]Disableing RenderAccel as suggested in the other thread worked for me.[/QUOTE]

Hi guys...
but where I can turn this RenderAccel off?

DANIeL

---

### Post by johneboy on 2005-05-04
[QUOTE=danpre]Hi guys...
but where I can turn this RenderAccel off?

DANIeL[/QUOTE]
 Hi Danpre,

Look in the "Device" section of the configuration file 

/etc/X11/xorg.conf

This section looks like so on my machine:

```
Section "Device"
        Identifier      "NVIDIA Corporation NV17 [GeForce4 MX 440]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel"           "false"
        Option          "NoLogo"
EndSection
``` 

Regards

John

---

### Post by danpre on 2005-05-04
[QUOTE=johneboy]Hi Danpre,

Look in the "Device" section of the configuration file 

/etc/X11/xorg.conf

This section looks like so on my machine:

```
Section "Device"
        Identifier      "NVIDIA Corporation NV17 [GeForce4 MX 440]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel"           "false"
        Option          "NoLogo"
EndSection
``` 

Regards

John[/QUOTE]

Hmmm... strange

my section is:

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

so I will just copy a:
        Option          "RenderAccel"           "false"

from yours - mayby it will work

DANIeL

---

