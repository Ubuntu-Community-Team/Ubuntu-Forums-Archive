---
title: "Going crazy trying to get widescreen"
date: 2006-11-17
forum: Desktop Environments
---

### Post by Vorticon on 2006-11-17
Hello.

First off i'll say i tried practically everything there is to do to get a widescreen resolution. I tried all the posts all over this forum and many others but i just can't get it to work.

I think it has something to do with the nvidia x server settings since they are a pain in the buttocks. 

I want a 1440x900 resolution on my monitor which is the specified resolution (Samsung SyncMaster 940BW).

I am using nvidia drivers 1.0-9626 on AMD64 ubunty edgy.

I'm also using beryl, but i don't guess that has much to do with it.

Here is my xorg.conf:

```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    Modeline "1440x900_75.00"  136.49  1440 1536 1688 1936  900 901 904 940  -HSync +Vsync
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
    Option         "TripleBuffer" "true"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option          "MonitorLayout" "CRT"
SubSection "Display"
Depth 1
Modes "1440x900" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 4
Modes "1440x900" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 8
Modes "1440x900" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 15
Modes "1440x900" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 16
Modes "1440x900" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 24
Modes "1440x900" "1024x768" "800x600"
EndSubSection
    Option "AddARGBGLXVisuals" "True"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

I added the modeline using the ```
gtf 1440 900 75
``` command.

I am seriously driving crazy now trying to get it to work since i can't select the 1440x900 resolution either in the nvidia x server configuration tool or in the regular ubuntu resolution picker. Whatever i do i always end up in 1024x768 after x restart or total reboot :( :(
I have been trying to fix this for about 2 weeks now (just once in a while i give it a new try) and still, just can't get it to work.

Please help this desperate newbie.
Thanks.

---

### Post by MetalMusicAddict on 2006-11-17
Did you try to **sudo dpkg-reconfigure xserver-xorg** from a terminal? Follow the prompts and pick the right GFX card, res and refresh.

---

### Post by Vorticon on 2006-11-17
Ok i have tried that, but it didn´t work. I still can select practically any resolution below 1280x1024 in the nivida x server settings program and only some stuff below 1024x768 in the regular res settings tool.

---

### Post by JayTee on 2006-11-17
I see you have a Modeline statement so that's a good start. Hopefully it won't take you 10 hours to get this working like it did me. 1 minute for Vista, 5 minutes for XP (had to download new drivers) and 10 hours for Ubuntu. Pathetic.

Try changing this:

Depth 24
Modes "1440x900" "1024x768" "800x600"
EndSubSection

to this:
Depth 24
Modes "1440x900_75.00" "1024x768" "800x600"
EndSubSection
 and repeat for all your other Color Depth settings. Save and do a reboot.

---

### Post by MetalMusicAddict on 2006-11-17
> **JayTee said:**
> 1 minute for Vista, 5 minutes for XP (had to download new drivers) and 10 hours for Ubuntu. Pathetic.

Yes. 10hrs for you to get your nvidia drivers working, pathetic.

---

### Post by JayTee on 2006-11-17
> **MetalMusicAddict said:**
> Yes. 10hrs for you to get your nvidia drivers working, pathetic.

OK, MetalMusicAddict! First off, my nvidia drivers worked great with my old 17" LCD. It was when I bought the new 19" widescreen that I ran into problems. It had NOTHING to do with my nvidia drivers, genius! The 10 hours included reading through several hundred threads on here and a couple other forums and trying suggested solutions. Pardon me for being a noob. Wish we could all have been born Linux Gods like you were.

How about contributing something more to help this guy with his problem or are you only really good at making personal slights? At least I'm trying to help him get his problem resolved, little old pathetic me. I've seen so many "know-it-all" elitists on here that seem to think that sudo dpkg-reconfigure xserver-xorg solves every video problem and just mentioning it makes them look smart.

---

### Post by John.Michael.Kane on 2006-11-17
Here's a sample xorg with your lcd specs in it.This should get you up and going.

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync      30.0-81.0
    VertRefresh    56.0-75.0
    # 1440x900 @ 75.00 Hz (GTF) hsync: 70.50 kHz; pclk: 136.49 MHz
  Modeline "1440x900_75.00"  136.49  1440 1536 1688 1936  900 901 904 940  -HSync +Vsync
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
    Option         "TripleBuffer" "true"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option          "MonitorLayout" "CRT"
SubSection "Display"
Depth 1
Modes "1440x900_75.00"
EndSubSection
SubSection "Display"
Depth 4
Modes "1440x900_75.00"
EndSubSection
SubSection "Display"
Depth 8
Modes "1440x900_75.00"
EndSubSection
SubSection "Display"
Depth 15
Modes "1440x900_75.00"
EndSubSection
SubSection "Display"
Depth 16
Modes "1440x900_75.00"
EndSubSection
SubSection "Display"
Depth 24
Modes "1440x900_75.00"
EndSubSection
    Option "AddARGBGLXVisuals" "True"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

Sidenote: Another option is after configuring your xorg to match you can try pressing the [AUTO] button on the front of your panel to see if the monitor picks up the new config

Also Here's a modeline generator [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php) if anyone else needs it.

---

### Post by Vorticon on 2006-11-18
Thanks for the help but seriously. I did everything exactly as you guys said and it still doesnt work. It seems like both resolution setups seem to totally disregard what my xorg.conf file says. :( :(

I've looked up my logfile and i see this:

```
(WW) NVIDIA(0): No valid modes for "1440x900_75.00"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
```

I just found out that if i change in Section "Device"
Driver "nvidia" to Driver "nv" i can get the right resolution, but then beryl doesn't work anymore :\

---

### Post by Vorticon on 2006-11-20
Can someone please help :(

---

### Post by Maikun on 2006-11-21
Hi,

it seems to be a problem with the nvidia proprietary drivers since version 8something. I had a working nvidia driver with 3D and my TFT Hyundai monitor in Breezy. With dapper, it only worked up to 1024x768, but not with my native 1280x1024. Now I use Edgy with latests nvidia 9* drivers and the same happens. I can only use the 2D nv driver.

I've already tried a lot of workarounds to no avail. Modelines don't work (No valid modes for "1280x1024_60.00"). Disabling EDID (Option "UseEDID" "False") gives me 640x480 resolution!. Don't know what to do. It seems to be an old problem, that my monitor "Hyundai ImageQuest L70A" doesn't give the correct data. But at some point the nvidia drivers worked. Anybody help us?

---

### Post by Vorticon on 2006-11-22
Then i'm not alone in this. I am now using the "nv" driver since i obviously want to use my widescreen 1440x900 resolution that this monitor is capable of ... I would like to see it work with the "nvidia" driver too :\

I call upon the linux-gods of this forum to help us :cry: :cry: :cry:

---

### Post by Zamboniman on 2006-11-22
Looks like you have the wrong modeline in your Screen section.

I notice that in your Monitor Section you have:

> **Vorticon said:**
> 
    Modeline "1440x900_75.00"  136.49  1440 1536 1688 1936  900 901 904 940  -HSync +Vsync
EndSection


but in your Device Section you have:

> **Vorticon said:**
> 

Depth 24
Modes "1440x900" "1024x768" "800x600"


This should read:

Modes "1440x900_75.00" "1024x768" "800x600"

to match your above modeline.  I suspect this will fix things up for you.  Just a typo.

---

### Post by Zamboniman on 2006-11-22
Woops, I see now that my suggestion above has already been made by others and you say it didn't work.  I'm guessing your modeline is wrong.  You could try Colas Modeline Generator at [http://koala.ilog.fr/cgi-bin/nph-colas-modelines](http://koala.ilog.fr/cgi-bin/nph-colas-modelines)
to see if you can get something working.

---

### Post by Vorticon on 2006-11-23
It doesn't seem to be a problem with the modelines, more a problem with the driver since i can run the resolution i want with the "nv" driver and not with the "nvidia" driver

---

### Post by sciurus on 2006-11-24
For reference, here is what works for me on a Samsung SyncMaster 931BW with the "ati" driver.

```

Section "Monitor"
	Identifier	"Samsung 931BW"
	Option		"DPMS"
	#HorizSync	30-81
	#VertRefresh	56-75
	Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON 9800 AIW"
	Monitor		"Samsung 931BW"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900_60.00"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900_60.00"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900_60.00"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900_60.00"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900_60.00"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900_60.00"
	EndSubSection
EndSection

```

---

### Post by not_cool on 2006-11-25
I had the same problem of having to set my driver to nv to get the resolution correct, but beryl wouldn't work. First uninstall the nVidia drivers that you installed from Synaptic. Then go to [http://www.nzone.com/object/nzone_downloads_linux_display_x86_64_1.0-9742.html]("here") and download the driver. Follow the directions on installing it. Make sure to configure it. nVidia should have changed the driver in xorg.conf to "nvidia." If it didn't, change it. Restart X. Beryl should be working after you.

**I don't know if this matters but I installed the drivers from a terminal, not X.**

---

