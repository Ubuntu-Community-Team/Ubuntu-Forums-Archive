---
title: "How do you increase the default Resolution?"
date: 2009-01-07
forum: General Help
---

### Post by Drezliok on 2009-01-07
How do you increase the default Resolution?

I turn down the default in the xorg.conf before upgrading to Ibex. Now that I am with Ibex I went to the xorg.conf and there are no resolution settings in it.

I am using Nvidia's driver. Not the Ubuntu Restricted, I havn't figured out how to uninstall the driver to use the Ubuntu provided restricted driver.


Thankyou for all the help.
Drezliok.

---

### Post by 2hot6ft2 on 2009-01-07
envy has the uninstall option you can find it in the repos.
System>Administration>Synaptic Package Manager

and
System>Preferences>Screen Resolution
for the screen resolution

Also I believe that if you go to install the driver in
System>Administration>Hardware Drivers
that it will uninstall the other driver before installing the new one.

---

### Post by ajgreeny on 2009-01-07
Even though ibex's xorg.conf is more or less an empty file, you can still add resolution information to it and get a resolution that suits you.  As an example here is my xorg.conf which I manually edited to this after ibex got my resolution wrong and wouldn't let me see the bottom panel; it was below the screen base priginally.  Luckily I had a backup of an old xorg.conf from Dapper Drake, so I just copied and pasted the parts that I needed and all was well again.
My xorg.conf for 8.10, (without all the unwanted stuff at the top):-

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

---

### Post by Drezliok on 2009-01-08
Ok I tried the adding the info into xorg.conf file.
Like so:
```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
SubSection "Display"
Modes "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"False"
EndSection

```

It didn't work. I want to try 1400x1050.

I have the Ubuntu provided Nvidia driver now, I was able to remove the offcial.

---

