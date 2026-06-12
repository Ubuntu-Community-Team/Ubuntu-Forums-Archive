---
title: "When visual effects on, cannot see menu headings in open office."
date: 2009-04-02
forum: Desktop Environments
---

### Post by newonlinux on 2009-04-02
Hi, I've searched but not been able to find a solution to my problem.

I have an Nvidia graphics card, and the proprietary drivers for it, and I assume that it is causing the problem.

When I go to Appearence and change Visual Effects from off to Normal or Extra, when I open an Open Office program, the words are missing from the clickable buttons, like the menu tabs at the top (File, Edit, View etc.) like you can see in the screenshots attached. 

They are there for a split second when the programs start, but then disappear, and if I hover the mouse over the button they reappear for another split second but then disappear again.

But other programs like Evolution or Gedit work fine with no missing words.

Any help will be appreciated, thanks.

---

### Post by newonlinux on 2009-04-03
Anybody know anything to help?
(bump)

---

### Post by binbash on 2009-04-03
It is a nvidia bug if i am not wrong.There are huge amount of topics about this.Please search the forums.

---

### Post by newonlinux on 2009-04-03
Yep, with a little harder searching I found a solution.

Many fixes found on:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/294076](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/294076)
[http://ubuntuforums.org/showthread.php?t=974493](http://ubuntuforums.org/showthread.php?t=974493)
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/297836](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/297836)

Thanks.

---

### Post by ffahog on 2009-04-03
To the poster who simply replied "Just go search", that's not helpful. It took me a little while to find even this thread with searching, so it's better if these specific concerns can be addressed in the thread.

In one of the links above I found this advice, which worked for OOo:

> Same here. Running Ubuntu 8.10 Gnome / Compiz. I found a way to make the menus appear. Set effects to none, open any OpenOffice application (I opened Spreadsheet). Go to Tools->Options. Expand OpenOffice.org and select "View" and de-select Screen Font Antialiasing. Then activate your effects again; the fonts stay.

I still have the same problem with WINE. But at least for now I can keep my effects on (and, hence, run Cairo-Dock normally) and still have OOo work.

---

### Post by newonlinux on 2009-04-03
ffahog I found a solution for WINE aswell.

It's on here: [http://www.nvnews.net/vbulletin/showthread.php?t=122695](http://www.nvnews.net/vbulletin/showthread.php?t=122695)

But first your method for getting the fonts to work isn't the best because they will be a bit fuzzy.
I reccomend reactivating antialiasing and instead following the method on that link, which is:

from terminal.
1. Update the xorg.conf

> sudo gedit /etc/X11/xorg.conf

Make it look like this:

> Section "Monitor"
    Identifier "Monitor0"
    VendorName "Unknown"
    ModelName "Unknown"
    HorizSync 30.0 - 110.0
    VertRefresh 50.0 - 150.0
    Option "DPMS"
EndSection

[B]Section "Device"
    Identifier "Device0"
    Driver "nvidia"
    VendorName "NVIDIA Corporation"
EndSection[/B]

Section "Screen"
    Identifier "Screen0"
    Device "Device0"
    Monitor "Monitor0"
    DefaultDepth 24
[B]    Option "AllowGLXWithComposite" "True"
    Option "AddARGBGLXVisuals" "True"[/B]
    SubSection "Display"
        Depth 24
        Modes "1600x1200" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
[B]
Section "Extensions"
    Option "Composite" "Enabled"
EndSection[/B]

My own one actually looks like:> Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	Option "RenderAccel" "0"
EndSection

Section "Extensions"
    Option "Composite" "Enabled"
EndSection


You can manually add more resolutions to this line:
Modes "1600x1200" "1280x800" "1024x768" "800x600" "640x480"

2. Go to System > Preferences > Appearence > Fonts
Select Subpixel

*that last subpixel bit I was able to disable and the fonts still worked.*

**but to make WINE work:**

Type in terminal:
> sudo gedit /home/settings.txt

and paste in the following text then save

> [HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"ClientSideWithRender"="N"

Go to a terminal window and write:

> regedit settings.txt

Remember to reboot your system after installing the driver.

Hope this works for you too

PS: There will be a driver update that fixes the problem itself, but for now, this seems to be working just fine.

---

