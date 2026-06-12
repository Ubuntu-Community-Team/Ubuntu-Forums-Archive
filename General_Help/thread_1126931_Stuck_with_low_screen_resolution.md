---
title: "Stuck with low screen resolution"
date: 2009-04-15
forum: General Help
---

### Post by mamboze on 2009-04-15
Hi,
I've just installed Intrepid on an ACER Aspire 4520, Athlon X2, Nvidia Geforce 7000M, without any big issues, except only low screen resolutions, 640x480 and 800x600, are available. I went to Administration>Hardware Drivers, selected the Nvidia accelerated graphics driver version 177, clicked Activate, rebooted. During reboot, a nvidia logo flashed very briefly, so I guess something is installed, but still only low resolutions. 

I've run Ubuntu on a desktop since 7.04 with no problems setting screen resolution. This is my first go with a laptop.

Any help would be much appreciated.

---

### Post by techturkey on 2009-04-15
hi can you go to system-preferences-screen resolution and change your resolution there, unless that is what you were doing...

---

### Post by mamboze on 2009-04-16
Thanks, techturkey

I should have mentioned that I tried to change the screen resolution using Preferences>Screen Resolution but there were no options above 800x600. I know the hardware can do better because it was higher when Windows XP was installed.

As I say, I seemed to have installed something using the Hardware Drivers window but I'm not sure what.

---

### Post by mamboze on 2009-04-16
Thanks, techturkey

I should have mentioned that I tried to change the screen resolution using Preferences>Screen Resolution but there were no options above 800x600. I know the hardware can do better because it was higher when Windows XP was installed.

As I say, I seemed to have installed something using the Hardware Drivers window but I'm not sure what.

---

### Post by CatKiller on 2009-04-16
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
```Bear in mind that these are the values for **my** monitor. You'll need to put in the values for **your** monitor, otherwise you could well permanently damage your monitor.

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       30-95
        VertRefresh     50-160
EndSection

```

---

### Post by DJonsson2008 on 2009-04-16
That seems to work for me even using the Vesa drivers. 

On my Acer AL1916w I used the following

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Acer"
	Modelname	"Acer AL1916W"
	Horizsync	30.0-82.0
	Vertrefresh	56.0-76.0
EndSection

I also updated the modeline  "modeline  "1024x768@76" 76.0...
to reflect the refresh rate.

I'm wondering though how can one verify other than using displayconfig-gtk, perhaps via the command line or via
another utility the actual refresh rate, HorizSync, 
VertRefresh currently in use?

---

### Post by mamboze on 2009-04-16
Excellent advice from both of you, DJonsson2008 and CatKiller. 

I used 

Section "Monitor"
Identifier "Configured Monitor"
Vendorname "Acer"
Modelname "Acer AL1916W"
Horizsync 30.0-82.0
Vertrefresh 56.0-76.0
EndSection

and the screen displays at 1024x786@76

I didn't know where to put - "modeline "1024x768@76" 76.0...  so I left it out, any pointers on that? 

Thanks very much :D

---

### Post by DJonsson2008 on 2009-04-17
On xorg.conf this works for me, be sure though to backup your xorg.conf and be ready to manually restore it before trying. 

NOTE: Width limitations of this may wrap the continious modes lines in this post. 

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Acer"
	Modelname	"Acer AL1916W"
	Horizsync	30.0-82.0
	Vertrefresh	56.0-76.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@76" 76.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

---

### Post by mexicanganster on 2009-08-05
i think the graphic driver is not active to enable the graphic go to system>administration>hardware drivers
it will show you a list of drivers you should find yours and enable the graphic driver then restart sometimes you have to install the driver software like nvidia 7000m ask you to install its software in order to change the resoulution

---

### Post by soapBAR2 on 2009-08-05
Nvidia proprietary drivers have a very nice (and necessary) GUI control panel -

```
sudo apt-get install nvidia-settings ; sudo nvidia-settings
```

And you're away! Remember to hit "save to X configuration file" (which is why you need to run it with sudo) or your settings will be lost the next time you reset your X-server/computer. Also, if you want, you can get rid of the nvidia logo if you edit your /etc/X11/xorg.conf and put in the Option "NoLogo" "True" under device. Mine looks like this:

```

Section "Device"
    Identifier     "Default Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

```

---

### Post by 3rdalbum on 2009-08-05
> **soapBAR2 said:**
> Nvidia proprietary drivers have a very nice (and necessary) GUI control panel -

```
sudo apt-get install nvidia-settings ; sudo nvidia-settings
```

And you're away! Remember to hit "save to X configuration file" (which is why you need to run it with sudo) or your settings will be lost the next time you reset your X-server/computer.

Better to put the modes into the xorg.conf file yourself; otherwise it doesn't seem to work.

But anyway, the thread is months old, let it die.

---

