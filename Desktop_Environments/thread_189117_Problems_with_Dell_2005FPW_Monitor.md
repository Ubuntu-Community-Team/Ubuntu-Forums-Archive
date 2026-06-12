---
title: "Problems with Dell 2005FPW Monitor"
date: 2006-06-04
forum: Desktop Environments
---

### Post by jessecollins on 2006-06-04
Hello All.  This is nothing too big but it is annoying.  

I am dual booting with Windows XP Pro (that might be my first problem, hehe, :) ) and everytime I switch OS's I have to go to the 2005FPW monitor menu and select "Image Settings" and then "Auto-Adjust" so that the screen is correctly aligned.  

If I don't auto adjust the monitor, Ubuntu is shifted over to the right (so that there is a black space on the left side) and Windows XP is shifted over to the left (so that there is a black space on the right side).  Now say if I have the monitor auto adjusted so that in Ubuntu everything is centered and I DON'T auto adjust the next time I am in Windows, then when I boot back into Ubuntu everything is still centered.

I have installed the Nvidia driver and edited the xorg.conf file to get 1680x1050 resolution but, I am guessing that I need to edit the Modeline numbers.  Any help would be greatly appreciated.  

Here is a snippet from my xorg.conf file:

```
Section "Monitor"
        Identifier      "DELL 2005FPW"
        Option          "DPMS"
        HorizSync       30-81
        VertRefresh     56-75
        Modeline "1680x1050@60" 154.20 1680 1712 2296 2328 1050 1071 1081 1103 -hsync -vsync
EndSection
```

Thank you!

---

### Post by MetalMusicAddict on 2006-06-04
Heres mine for my 2405, should help.

[HTML]Section "Monitor"
	Identifier	"DELL 2405FPW"
	Option		"DPMS"
	HorizSync	30-75
	VertRefresh	30-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800]"
	Monitor		"DELL 2405FPW"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection[/HTML]

You could also type in a terminal: **sudo dpkg-reconfigure xserver-xorg** then reboot. This option might be better.

---

### Post by pdc303 on 2006-06-04
I also dual boot WinXP/Ubuntu with a GeForce/FPW2005 setup.

As I understand it, you do not need to specify all that information.

My xorg.conf reads:
```

Section "Monitor"
    Identifier     "DELL 2005FPW"
    Option         "DPMS"
EndSection
```

It is a GeForce 6800.

I am no expert by any means - this just works ;)

---

### Post by tha_rainman on 2006-06-04
Have you guys tried using a DVI connection instead of VGA? AFAIK DVI always adjusts that automatically. Seems to be the case with my setup...

---

### Post by jessecollins on 2006-06-04
[QUOTE=pdc303]I also dual boot WinXP/Ubuntu with a GeForce/FPW2005 setup.

As I understand it, you do not need to specify all that information.

My xorg.conf reads:
```

Section "Monitor"
    Identifier     "DELL 2005FPW"
    Option         "DPMS"
EndSection
```

It is a GeForce 6800.

I am no expert by any means - this just works ;)[/QUOTE]

The only thing that I am worried about is the specs of 2005fpw and 2405fpw say that you are only supposed to run 1680x1050 or 1920x1200 with a vertical scan range of 60Hz.  I guess I am being too cautious.

[http://www.dell.com/content/products/productdetails.aspx/monitor_2005fpw?c=us&cs=22&l=en&s=dfh&~tab=specstab#tabtop]("http://www.dell.com/content/products/productdetails.aspx/monitor_2005fpw?c=us&cs=22&l=en&s=dfh&~tab=specstab#tabtop")

---

### Post by jessecollins on 2006-06-04
[QUOTE=tha_rainman]Have you guys tried using a DVI connection instead of VGA? AFAIK DVI always adjusts that automatically. Seems to be the case with my setup...[/QUOTE]

That could definitely be my problem.  I am using DVI but I run it to a KVM switch that has VGA output.  I didn't even think of that.  Ooops.  :D

---

### Post by MetalMusicAddict on 2006-06-04
I run mine through DVI, 1920x1200@60hz on a nVidia 6800OC.

I do think running **sudo dpkg-reconfigure xserver-xorg** will do you right. It will let you pick your resolution, refresh, monitor and video driver.

---

