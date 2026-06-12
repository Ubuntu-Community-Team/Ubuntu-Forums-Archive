---
title: "xrandr add screen resolution"
date: 2009-03-31
forum: General Help
---

### Post by max_power on 2009-03-31
when i go System -> Preferences -> Display 

I'm only offered :

1360x768 (16:9)
1152x864 (4:3)

How do i add more screen resolutions?

I tried adding more to /etc/X11/xorg.conf but its not showing up in the options box.

Thanks

---

### Post by calmario on 2009-04-11
Hey man. This will help:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by max_power on 2009-04-13
Here are the steps

[LIST=1]
[*]Use xrandr to make sure that the new mode can fit within the maximum framebuffer size ```
xrandr | grep maximum
```

[*]Use gtf to create a mode line ```
gtf 1440 900 59.9
```

[*]Add new mode using xrandr ```
xrandr --newmode "1440x900_59.90"  106.29  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
```

[*]Add this newly added mode to the desired output (VGA/LVDS etc) ```
xrandr --addmode VGA 1440x900_59.90 
```

[*]Choose the new mode ```
xrandr --output VGA --mode 1440x900_59.90
```
[/LIST]


**TO MAKE THE CHANGES PERSISTENT**
```
sudo gedit /etc/X11/xorg.conf
```

Find this: (yours might look different than from below)
Section "Screen"
    Identifier      "Primary Screen"
    Device          "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
EndSection

and add this to it

    DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes   "1280x1024" "1024x768" "640x480"
    EndSubSection

so it should all look similar to this:

Section "Screen"
    Identifier      "Primary Screen"
    Device          "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
    DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes   "1280x1024" "1024x768" "640x480"
    EndSubSection
EndSection


**MAKE SURE YOU ADD YOUR NEW RESOLUTION TO THE MODES LINE**
        Modes   "1280x1024" "1024x768" "640x480"


Thanks to:
[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions)

[http://www.arunviswanathan.com/node/53](http://www.arunviswanathan.com/node/53)

---

### Post by unutbu on 2009-04-13
Thank you for the nice write-up. =D>

---

### Post by nacho_dh on 2009-06-08
In case the frame buffer size is a limitation for the resolution you want to add (it happened to me), just modify/create the "Virtual" parameter in the "Display" subsection of your xorg.conf. Here's how mine looks after configuring the frame buffer size to use my 22' widescreen (resol: 1680x1050)...

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2960 1050
		Depth 24
		Modes "1680x1050" "1280x800"
	EndSubSection
EndSection
```

---

### Post by Alhenry on 2010-10-14
I am extremely confused right now. I want my screen resolution
To be 1280x1024 on 60.00mhz and I have an hp vs17e screen
Any help would be appreciated

---

### Post by max_power on 2010-10-14
> **Alhenry said:**
> I am extremely confused right now. I want my screen resolution
To be 1280x1024 on 60.00mhz and I have an hp vs17e screen
Any help would be appreciated



This is an old thread and the xrandr info might be out dated. I would suggest you start a new thread and mark it as a karmic question.

---

### Post by Cloink on 2011-03-30
I would just like to add that these instructions worked for me with U10.10, after many attempts reading other posts.

DO NOT, if using an NVidia 8400 GS graphics card, install the nvidia driver.

I'm a little confused because my xorg.conf file does not exist.  It did before I uninstalled the nvid driver, I need to see what happens when I reboot...

-----------
Rebooted
-----------

I found a backup, xorg.conf.backup (in /etc/X11).  I'm guessing here but I think multiple installs/uninstalls of the nvidia driver must have lost the original xorg.conf that the ubuntu install would have created.  Anyway, using the backup as a model, I tried my best to change it to match what max_power originally suggested.  It hung at the  . . u b u n t u . .  splash screen so I obviously got that wrong.  I've now removed the xorg.conf file (using recovery mode), allowing it to boot up without it, and have added the xrandr commands to a startup.sh shellscript which I already had anyway.  This reports some errors/warnings but I get 1680x1050 so I'm happy for now.

----------
Update
Don't miss my comments re D-SUB cable that have tripped over onto page 2 of this thread...
[http://ubuntuforums.org/showthread.php?t=1112186&page=2](http://ubuntuforums.org/showthread.php?t=1112186&page=2)
----------

But.

Does anyone know how to generate the xorg.conf file, as per the ubuntu install?

Thanks,
Cloink.

---

### Post by Cloink on 2011-03-31
Bump.

Does anyone know how to generate the xorg.conf file, as per the ubuntu install?

Mine has gone missing, probably owing to hoping an install of the nvidia driver would give me a native screen resolution option, which of course it didn't.

---

### Post by fnaaijkens on 2011-04-12
> **max_power said:**
> Here are the steps

[LIST=1]
[*]Use xrandr to make sure that the new mode can fit within the maximum framebuffer size ```
xrandr | grep maximum
```

[*]Use gtf to create a mode line ```
gtf 1440 900 59.9
```

[*]Add new mode using xrandr ```
xrandr --newmode "1440x900_59.90"  106.29  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
```

[*]Add this newly added mode to the desired output (VGA/LVDS etc) ```
xrandr --addmode VGA 1440x900_59.90 
```

[*]Choose the new mode ```
xrandr --output VGA --mode 1440x900_59.90
```
[/LIST]


**TO MAKE THE CHANGES PERSISTENT**
```
sudo gedit /etc/X11/xorg.conf
```

Find this: (yours might look different than from below)
Section "Screen"
    Identifier      "Primary Screen"
    Device          "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
EndSection

and add this to it

    DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes   "1280x1024" "1024x768" "640x480"
    EndSubSection

so it should all look similar to this:

Section "Screen"
    Identifier      "Primary Screen"
    Device          "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
    DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes   "1280x1024" "1024x768" "640x480"
    EndSubSection
EndSection


**MAKE SURE YOU ADD YOUR NEW RESOLUTION TO THE MODES LINE**
        Modes   "1280x1024" "1024x768" "640x480"


Thanks to:
[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions)

[http://www.arunviswanathan.com/node/53](http://www.arunviswanathan.com/node/53)
Sir, you're the first to lay out so nicely how to work the mysterious xrandr option of adding a mode.

Althoug using OpenSuSE myself, you helped me a lot.  And then to realize you wrote this 2 years ago!!

Wonder why there is so little out there about the new setup. It almost made me go back a few versions to be able to use the infamous SaX  XOrg configurator...
You saved me from that horror!  I had to use CRT1 instead of  VGA, but one finds that out pretty quickly...

Thanks a bunch.

---

### Post by Cloink on 2011-04-12
What might make things a lot easier for you (everyone) is to make sure your monitor D-SUB cable has all the pins intact.  I changed mine for a completely separate reason but lo and behold then ubuntu picks up the monitor res through the cable and sets it appropriately without me having to do a thing.

Checking the pins on the cables, the nasty old grey one is missing a pin that is present on the nice new(er) blue-ended cable.

Live and learn I suppose...

---

### Post by sirdicholas on 2011-07-11
Awesome... Thank you much.

---

### Post by artemgab on 2011-10-03
thank you very much, [max_power]("http://ubuntuforums.org/member.php?u=91736"). your solution with xrandr helped me on natty.
what I had before I tried your solution:
I installed latest nvidia drivers. in nvidia settings I generated and saved new xorg.conf. Edited one line at   Section "Screen" like this: ```
Option         "metamodes" "1440x900_75 +0+0"
```After that the default refresh rate at the login screen and in user session "Ubuntu classic (no efffects)" was 75. But when I switched to Unity or "Ubuntu classic" (with compiz) the refresh rate was falling back to 60. I had to manually switch to 75 in nvidia settings every session.

I applied your xrandr solutions steps 1-5 and now 75Hz is persistent.

---

### Post by Grim_reaper10 on 2011-10-31
hey, I tried to add a new screen resolution, but whenever I type in sudo gedit /etc/X11/xorg.conf in my terminal the message that the text editor only display is this 


Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection


I'm new in ubuntu, I tried copying those previous codes and replace the ones in the text editor, but it only ruined the display so I have to install ubuntu again.. My videocard is nvidia 7300gt.

all available resolutions are below 1280x720.. help me please..

---

### Post by max_power on 2011-11-01
> **Grim_reaper10 said:**
> hey, I tried to add a new screen resolution, but whenever I type in sudo gedit /etc/X11/xorg.conf in my terminal the message that the text editor only display is this 


Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection


I'm new in ubuntu, I tried copying those previous codes and replace the ones in the text editor, but it only ruined the display so I have to install ubuntu again.. My videocard is nvidia 7300gt.

all available resolutions are below 1280x720.. help me please..

This is an old old thread but I can try to help you.

What kind of video card do you have? Nvidia? ATI? Intel?

---

### Post by Grim_reaper10 on 2011-11-01
@max_power I was trying to find a solution, this thread is most similar, so i posted it in here.. 

my graphics card is Nvidia GeForce 7300 GT..

---

### Post by max_power on 2011-11-01
Do you have the nvidia drivers installed?

open a terminal and type 

```
sudo nvidia-settings
```

---

### Post by Grim_reaper10 on 2011-11-01
yes, I have the nvidia drivers installed.. 

I typed in sudo nvidia-settings.

after i entered my password, the Nvidia X server settings came out..

---

### Post by A4Skyhawk on 2011-11-03
> **max_power said:**
> Do you have the nvidia drivers installed?

open a terminal and type 

```
sudo nvidia-settings
```
**********************************************************************
      Please excuse my interruption of this thread as I have a similar problem: I cannot change the default setting in Xrandr that resets on every bootup.
         I have Nvidia GeForce 6150SE nForce 430, using Ubuntu 10.04 LTS.  After entering the above command in terminal, I get the Nvidia GUI.  When I select X Screen 0, the information that displays indicates that the screen dimensions are 1152x864 pixels (325x228 millimeters), which is the default setting that resets on every bootup.  However, when I select X Server Display Configuration in the GUI, the options for layout/resolution show the option for 1280x1024x75, which is also shown in the monitor's user manual.  If I select 1280x1024x75, the monitor operates satisfactorily.  If I select 'Save to X Configuration File' in the GUI, the default setting is changed in the xrandr file, but resets to 1152x864 on the next bootup.
     Here is the response to '$ xrandr -q' after bootup:
Screen 0: minimum 320 x 175, current 1152 x 864, maximum 1280 x 1024
default connected 1152x864+0+0 0mm x 0mm
   1280x1024      50.0     51.0     52.0     53.0  
   1280x960       54.0     55.0  
   1152x864       56.0*    57.0     58.0     59.0     60.0     61.0  
   1024x768       62.0     63.0     64.0     65.0     66.0  
   960x600        67.0  
   960x540        68.0  
   928x696        69.0  
   896x672        70.0  
   840x525        71.0     72.0     73.0     74.0  
   832x624        75.0  
   800x600        76.0     77.0     78.0     79.0     80.0     81.0     82.0     83.0     84.0  
   800x512        85.0  
   720x450        86.0  
   720x400        87.0  
   680x384        88.0     89.0  
   640x512        90.0     91.0  
   640x480        92.0     93.0     94.0     95.0     96.0     97.0     98.0  
   640x400        99.0  
   640x350       100.0  
   576x432       101.0    102.0    103.0    104.0    105.0    106.0  
   512x384       107.0    108.0    109.0    110.0    111.0  
   416x312       112.0  
   400x300       113.0    114.0    115.0    116.0    117.0  
   360x200       118.0  
   320x240       119.0    120.0    121.0    122.0  
   320x200       123.0  
   320x175       124.0 
     In the last 2 days I have tried many suggestions from the forum w/ no success.  Hope you can help.
TIA,
Bill

---

### Post by morbidyogi on 2012-12-25
> **max_power said:**
> Here are the steps

[LIST=1]
[*]Use xrandr to make sure that the new mode can fit within the maximum framebuffer size ```
xrandr | grep maximum
```

[*]Use gtf to create a mode line ```
gtf 1440 900 59.9
```

[*]Add new mode using xrandr ```
xrandr --newmode "1440x900_59.90"  106.29  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
```

[*]Add this newly added mode to the desired output (VGA/LVDS etc) ```
xrandr --addmode VGA 1440x900_59.90 
```

[*]Choose the new mode ```
xrandr --output VGA --mode 1440x900_59.90
```
[/LIST]


**TO MAKE THE CHANGES PERSISTENT**
```
sudo gedit /etc/X11/xorg.conf
```

Find this: (yours might look different than from below)
Section "Screen"
    Identifier      "Primary Screen"
    Device          "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
EndSection

and add this to it

    DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes   "1280x1024" "1024x768" "640x480"
    EndSubSection

so it should all look similar to this:

Section "Screen"
    Identifier      "Primary Screen"
    Device          "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
    DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes   "1280x1024" "1024x768" "640x480"
    EndSubSection
EndSection


**MAKE SURE YOU ADD YOUR NEW RESOLUTION TO THE MODES LINE**
        Modes   "1280x1024" "1024x768" "640x480"


Thanks to:
[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions)

[http://www.arunviswanathan.com/node/53](http://www.arunviswanathan.com/node/53)


I followed accordingly the only problem I got is, I have a DVI port on my motherboard (which is intel dh67cl) and VGA on my 17" LCD monitor. I am using DVI to VGA converter to be able to use the VGA cable, since I don't have any other port on my monitor. Now what do I type where in the code "VGA" is written? I tried VGA and DVI both. Didn't work.

I am myself having screen resolution issue which shows as maximum 1024x768 (4:3) even though I have a widescreen (16:9) and does not detect any other display except 800x600 or something.

---

### Post by oldos2er on 2012-12-25
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

