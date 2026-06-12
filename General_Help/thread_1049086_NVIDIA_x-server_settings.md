---
title: "NVIDIA x-server settings"
date: 2009-01-24
forum: General Help
---

### Post by YigalB on 2009-01-24
When I run NVIDIA x-server settings, I get the following error message:
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

The problem is that when I run nvidia-xconfig, i get the "no such command".

---

### Post by dcstar on 2009-01-24
> **YigalB said:**
> When I run NVIDIA x-server settings, I get the following error message:
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

The problem is that when I run nvidia-xconfig, i get the "no such command".

nvidia-xconfig is part of the nvidia driver package that you are supposed have installed, which one do you have installed?

---

### Post by YigalB on 2009-01-24
> **dcstar said:**
> nvidia-xconfig is part of the nvidia driver package that you are supposed have installed, which one do you have installed?

Sorry - I have a correction: I can run nvidia-xconfig. Previously I tried it with space (nvidia -xconfig), assuning xconfig is a flag.

Now I can run it, but nothing happens. The highest resolution is 800*600, although the NVIDIA card supports higher, and so the CRT screen.

---

### Post by dcstar on 2009-01-24
> **YigalB said:**
> Sorry - I have a correction: I can run nvidia-xconfig. Previously I tried it with space (nvidia -xconfig), assuning xconfig is a flag.

Now I can run it, but nothing happens. The highest resolution is 800*600, although the NVIDIA card supports higher, and so the CRT screen.

It is just a command that changes xorg.conf.

Again, what nvidia driver are you running.

---

### Post by YigalB on 2009-01-24
> **dcstar said:**
> what nvidia driver are you running.

The card is FX 5200
the driver version is 173 (it says recommended. There is also version 96 which I didn't try)

---

### Post by wsscott on 2009-01-24
I have the same issue with the same video card.  Stupid question......how do you "run nvidia-xconfig"?

Thanks

---

### Post by YigalB on 2009-01-24
1- you open terminal window at aplications->accessories
2- you change to root (type sudo -s)
3- you write the command nvidia-xconfig

If you don't get error - it was done (the output is a file, not typed on screen, which I think is a bad practice)

---

### Post by wsscott on 2009-01-24
It worked!  You are right, nothing appears on the screen to let you know that the configuration was successful.

Thanks!

---

### Post by YigalB on 2009-01-24
> **wsscott said:**
> It worked!  You are right, nothing appears on the screen to let you know that the configuration was successful.

Thanks!

Do you het better resolution now?
I don't.

---

### Post by dcstar on 2009-01-24
> **wsscott said:**
> It worked!  You are right, nothing appears on the screen to let you know that the configuration was successful.

Thanks!

As I stated before, it is just a program that changes xorg.conf - but you have to tell it the commands to make the changes. If there is no xorg.conf file it will create a basic one.

```
man nvidia-xconfig
sudo nvidia-xconfig --options-and-changes-that-you-want
```

---

### Post by YigalB on 2009-01-25
> **dcstar said:**
> As I stated before, it is just a program that changes xorg.conf - but you have to tell it the commands to make the changes. If there is no xorg.conf file it will create a basic one.

```
man nvidia-xconfig
sudo nvidia-xconfig --options-and-changes-that-you-want
```

I will try learning the switches and do it. 
I don't like editing config files - because of the risk. I prefer using GUI, which deliver same value with no risk.

There must be a bug somewhere - the OS should have detected the possible resolutions and let me chose the best for me. How come it doesn't work? is that the driver or the OS?

---

### Post by dcstar on 2009-01-25
> **YigalB said:**
> 
.........
There must be a bug somewhere - the OS should have detected the possible resolutions and let me chose the best for me. How come it doesn't work? is that the driver or the OS?

Usually it works, sometimes it doesn't. Post the contents of your /etc/X11/xorg.conf file.

---

### Post by YigalB on 2009-01-25
> **dcstar said:**
> Usually it works, sometimes it doesn't. Post the contents of your /etc/X11/xorg.conf file.

I dont know how to specify what I want. Nor the screen model, nor the resolution. Editing system files is not something to be done by users. 

I assume it's a bug, if sometimes it works, sometimes not.
How can I report it? I assume there is bug reporting mechanism. 

It's a showstopper for using Ubuntu - I can't see the whole screen while using old graphical card from a well known company.

---

### Post by YigalB on 2009-01-25
I went through man nvidia-xconfig, and found the example: 
nvidia-xconfig --mode=1280x1024

I got an error that --mode is  the only parameter allowed is not recognized, and the only parameter allowed is another destintion file.

What did I do wrong?
Is it possible to get xorg.conf example file which includes several resolutions?

---

### Post by dcstar on 2009-01-25
> **YigalB said:**
> I dont know how to specify what I want. Nor the screen model, nor the resolution. Editing system files is not something to be done by users. 

I assume it's a bug, if sometimes it works, sometimes not.
How can I report it? I assume there is bug reporting mechanism. 

It's a showstopper for using Ubuntu - I can't see the whole screen while using old graphical card from a well known company.

Unless you comply with specific requests for information people cannot assist you.

Now that you have finally provided some useful information - that you are using an old Nvidia card - you can now get an answer to your problem:

8.10 does not support older Nvidia hardware (this is in the release notes), if you want a Ubuntu version that does, install 8.04.

---

### Post by YigalB on 2009-01-26
> **dcstar said:**
> 
8.10 does not support older Nvidia hardware (this is in the release notes), if you want a Ubuntu version that does, install 8.04.

I downloaded 8.04-2, and installed it.
After fresh install - the resolution was 800x600.
After loading NVIDIA drivers - it went down to 640x480
After removing the NVIDIA driver I got the 800*600.

Now that I have 8.04 - how can I convince Ubuntu to let me use higher resolution?

---

### Post by darksidedude on 2009-01-26
I would IMO us envy it uses the Nvida.com drivers without all the messy configs:popcorn:

I would do a google search for "envyNG" and just install the .DEB

---

### Post by YigalB on 2009-01-26
> **darksidedude said:**
> I would IMO us envy it uses the Nvida.com drivers without all the messy configs:popcorn:

I would do a google search for "envyNG" and just install the .DEB

I searched and found this link:
[http://linux.softpedia.com/progDownload/EnvyNG-Download-36961.html](http://linux.softpedia.com/progDownload/EnvyNG-Download-36961.html)

Is that what you meant?

In addition, I don't know what to do with DEB file. I always add programs using the GUI.

---

### Post by DeMus on 2009-01-26
> **darksidedude said:**
> I would IMO us envy it uses the Nvida.com drivers without all the messy configs:popcorn:

I would do a google search for "envyNG" and just install the .DEB

Envyng is in the Synaptic Package Manager:
System | Administration | Synaptic Package Manager
Type your password
Let the program list all the available software
Click on the search-button
type envyng and click on search
Click on the little square in front of envyng-core and the one in front of envyng gtk. In both cases choose Mark for installation
Then in the toolbar click Apply.

You find envyng in Applications | System tools
Start it, type your password, choose nvidia on the left and install recommended driver. Sit back, relax and at the end reboot your machine.
Success

---

### Post by SnakeHips on 2009-01-26
> **dcstar said:**
> Usually it works, sometimes it doesn't. Post the contents of your /etc/X11/xorg.conf file.

OP - The most helpful thing right now would be to post your xorg me thinks *before* you embark on trying to re-configure with envy.

---

### Post by Kevbert on 2009-01-26
> **YigalB said:**
> I downloaded 8.04-2, and installed it.
After fresh install - the resolution was 800x600.
After loading NVIDIA drivers - it went down to 640x480
After removing the NVIDIA driver I got the 800*600.

Now that I have 8.04 - how can I convince Ubuntu to let me use higher resolution?

Here's a copy of my xorg.conf file which may help. Display resolution is up to 1280x1024. I'm using a 7600GS adapter:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
[COLOR="Red"]	Driver		"nvidia"
	Option		"NoLogo"	"True"[/COLOR]
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
[COLOR="Red"]	Defaultdepth	24[/COLOR]
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
[COLOR="Red"]Section "Module"
	Load		"glx"
EndSection
```[/COLOR]

---

### Post by YigalB on 2009-01-26
> **SnakeHips said:**
> OP - The most helpful thing right now would be to post your xorg me thinks *before* you embark on trying to re-configure with envy.

Here is my XORG file:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

### Post by SnakeHips on 2009-01-26
Does it say configured by nvidia-settings at the  top ?

---

### Post by YigalB on 2009-01-26
comparing the above 2 XORGs, it seems mine has no "Defaultdepth" line.
Shall I add Defaultdepth 24 ?
If yes - so I need to restart? or run something to reactivate it?

---

### Post by YigalB on 2009-01-26
> **SnakeHips said:**
> Does it say configured by nvidia-settings at the  top ?

# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#

---

### Post by Kevbert on 2009-01-26
> **YigalB said:**
> comparing the above 2 XORGs, it seems mine has no "Defaultdepth" line.
Shall I add Defaultdepth 24 ?
If yes - so I need to restart? or run something to reactivate it?

Yes, but you also have several other things missing - I'll highlight them in my previous post.  A reboot is probably best and also it would be worth backing the old xorg.conf in case things go wrong.

---

### Post by YigalB on 2009-01-26
After updfaing the XORF, I restarted the PC.
At shhutdown, I was asked to test the resolution.
Adfter restart, it came with the 800x600 - nothing higher.
I looked at the XORF - it looks diferent than what I edited.
see below.
Could it be that the FX2500 is limited with Linux?
This PC used to be XP, where it was delivering higher resolutions.

here is the file:
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by SnakeHips on 2009-01-26
Correct me if i'm wrong but it appears your xorg.conf is not showing the nvidia drive . I would expect to see 'nv' or maybe "nvidia" - maybe i'm wrong on this.

**Driver "vesa"**

from terminal
firstly please take a backup of your xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.mybackup
```

then again from terminal
```
sudo nvidia-settings
```

This will launch the graphical tool. I'm interested in what resolution is available in the X Server Display Configuration menu.

hope you find thids helpful.

---

### Post by YigalB on 2009-01-26
> **SnakeHips said:**
> Correct me if i'm wrong but it appears your xorg.conf is not showing the nvidia drive . I would expect to see 'nv' or maybe "nvidia" - maybe i'm wrong on this.

**Driver "vesa"**

from terminal
firstly please take a backup of your xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.mybackup
```

then again from terminal
```
sudo nvidia-settings
```

This will launch the graphical tool. I'm interested in what resolution is available in the X Server Display Configuration menu.

hope you find thids helpful.

I run and got the immediate message:
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

I tried running the nvidia-sconfig and got:
The program 'nvidia-xconfig' can be found in the following packages:
 * nvidia-xconfig
 * nvidia-glx
 * nvidia-glx-new
Try: apt-get install <selected package>
bash: nvidia-xconfig: command not found

---

### Post by SnakeHips on 2009-01-26
How did you install your 'nvidia' packages ?

---

### Post by YigalB on 2009-01-26
> **SnakeHips said:**
> How did you install your 'nvidia' packages ?

Now I didnt.
Previously I installed 8.10 and I was told that 8.10 doesnt support my NVIDIA FX5200. 
I understood that 8.04 supports it.

Should I install or is it being detected and installed by the OS?

---

### Post by SnakeHips on 2009-01-26
Does this exist in your menu's ?

System/Administration/Hardware Drivers

and does it give you any options? there should be one marked recommended ,if this is the case then accept that and install.

do not reboot yet come back and let me know

---

### Post by YigalB on 2009-01-26
> **SnakeHips said:**
> Does this exist in your menu's ?

System/Administration/Hardware Drivers

and does it give you any options? there should be one marked recommended ,if this is the case then accept that and install.

do not reboot yet come back and let me know

Yes - I have it.
I am installing it right now,no rebooting yet.

it finished, saying changes applied, and that I need to restart.

---

### Post by SnakeHips on 2009-01-26
Ok thats cool. close that window and what we need to do now is update your xorg.conf with the new driver. you did make that backup earlier - right ;-)

first we need to check whats been installed ,open synaptic package manager and in the search box type "nvidia". you should have nvidia-glx ,nvdia-settings ,some others and one that says kernel-restricted modules. 

All in place? great.

from terminal 

```
sudo nvidia-settings
``` 

to open graphical GUI ,this must be done by sudo!. hopefully you'll have all your settings and your new resolution too.
look for X Server Display configuration and if all looks ok to you then in the bottom right hand corner click on "save to X configuration" and i would advise you to "merge" with existing. save or accept whatever it says.

Have a liveCD to hand and reboot ,it should be ok now ,fingers crossed.

---

### Post by YigalB on 2009-01-26
> **SnakeHips said:**
> Ok thats cool. close that window and what we need to do now is update your xorg.conf with the new driver. you did make that backup earlier - right ;-)

first we need to check whats been installed ,open synaptic package manager and in the search box type "nvidia". you should have nvidia-glx ,nvdia-settings ,some others and one that says kernel-restricted modules. 

All in place? great.

from terminal 

```
sudo nvidia-settings
``` 

to open graphical GUI ,this must be done by sudo!. hopefully you'll have all your settings and your new resolution too.
look for X Server Display configuration and if all looks ok to you then in the bottom right hand corner click on "save to X configuration" and i would advise you to "merge" with existing. save or accept whatever it says.

Have a liveCD to hand and reboot ,it should be ok now ,fingers crossed.

- Yes: I have backup
- I have NVIDIA-glx-new, nvidia setting, and Linux-restricted-modules (and now nvidia-restricted-modules)
- the "" still tells me I dont have the drivers installed .....

So should I reboot or not? 

Is there a way for you to remotely VNC this PC? I admire your support, but I may crack soon.

---

### Post by SnakeHips on 2009-01-26
If you followed this step

"save to X configuration" and i would advise you to "merge" with existing. save or accept whatever it says. 

then you can check by looking at you *new* xorg.conf before rebooting 
terminal
```
cat /etc/X11/xorg.conf
``` 

If it starts nvidia-settings at the top your home n dry - scroll down and check what is says against driver - should be "nvidia"

If that looks right then your good to reboot

---

### Post by YigalB on 2009-01-27
Last night, just before bed time, I did a mistake and used the rm comand istead of mv, and deleted the XORG file and the backups I had.
I re-installed the whole OS (8.04), since I lost tracking.
- After fresh install I had 800x600
- After adding the recommended NVIDIA driver the resolution was downgraded to 640x480.

This is the current status.
What should I do now? 
Should I keep fighting it?
Is it true that 8.10 doesnt support the NVIDIA FX2500 card? (doesnt make sense to me that OS will not support harware that was supported before) 
Should I buy another graphic card? new PC? go back to XP?

---

### Post by Kevbert on 2009-01-27
> **YigalB said:**
> Last night, just before bed time, I did a mistake and used the rm comand istead of mv, and deleted the XORG file and the backups I had.
I re-installed the whole OS (8.04), since I lost tracking.
- After fresh install I had 800x600
- After adding the recommended NVIDIA driver the resolution was downgraded to 640x480.

This is the current status.
What should I do now? 
Should I keep fighting it?
Is it true that 8.10 doesnt support the NVIDIA FX2500 card? (doesnt make sense to me that OS will not support harware that was supported before) 
Should I buy another graphic card? new PC? go back to XP?

I noticed in some of your posts you say you have an FX5200 and in others a FX2500, which one is it ?
If it's an FX5200 take a look at [this]("http://www.nvidia.com/object/linux_display_ia32_173.14.12.html").  This driver is for your card (amongst others).
If it's a Quadro FX2500 then you may be out of luck.

---

### Post by Tomatz on 2009-01-27
The problem is that you are installing **_nvidia-glx-new_**. This is for newer cards.

You need **_nvidia-glx_** ;)

I suggest you reinstall and then install **nvidia-glx**.

---

### Post by YigalB on 2009-01-27
> **Tomatz said:**
> The problem is that you are installing **_nvidia-glx-new_**. This is for newer cards.

You need **_nvidia-glx_** ;)

I suggest you reinstall and then install **nvidia-glx**.

First - my card is Nvidia 5200.

I added the GLX, and the synaptic already knew to uninstall the "new glx" (which btw - I didn't ask to install it). 

After reboot - I am still with 640*480.
But I have something new: I cant see the top of the line, where I can minimize/close the window. In addition, I opened terminal window - and here I see only blank page. No header, footer, or prompt. Just nothing.
If I open Firefox, I ant see the top line (the one above the File/Edit/View...)

---

### Post by Tomatz on 2009-01-27
> **YigalB said:**
> First - my card is Nvidia 5200.

I added the GLX, and the synaptic already knew to uninstall the "new glx" (which btw - I didn't ask to install it). 

After reboot - I am still with 640*480.
But I have something new: I cant see the top of the line, where I can minimize/close the window. In addition, I opened terminal window - and here I see only blank page. No header, footer, or prompt. Just nothing.
If I open Firefox, I ant see the top line (the one above the File/Edit/View...)

> - Yes: I have backup
- I have NVIDIA-glx-new, nvidia setting, and Linux-restricted-modules (and now nvidia-restricted-modules)
- the "" still tells me I dont have the drivers installed .....

?

---

### Post by YigalB on 2009-01-27
Each of these two statements is true, but at different times.
The 2nd quote was true yesterday. Since then I re-installed Ubuntu again(the 3rd tume). 

At this moment - the first quote is true. After installing the glx, removing the glx-new, I am left with 640*480 resolution, with strange windows behavior, and no ability to see terminal.

I am confued -  shouldn't the OS detect the hardware (FX 5200 card), select the suitable drivers and install them?

---

### Post by Tomatz on 2009-01-27
> **YigalB said:**
> Each of these two statements is true, but at different times.
The 2nd quote was true yesterday. Since then I re-installed Ubuntu again(the 3rd tume). 

At this moment - the first quote is true. After installing the glx, removing the glx-new, I am left with 640*480 resolution, with strange windows behavior, and no ability to see terminal.

I am confued -  shouldn't the OS detect the hardware (FX 5200 card), select the suitable drivers and install them?

Id say 95 percent of the time GPU drivers just work. TBH that card is getting old now so it is not as well supported. 

Have you tried envyng?

---

### Post by YigalB on 2009-01-27
> **Tomatz said:**
> Id say 95 percent of the time GPU drivers just work. TBH that card is getting old now so it is not as well supported. 

Have you tried envyng?


Getting old? It's just 5 years old! 
Ubuntu should put "we support oldies" as a moto. 

envyng? not yet. I will try that now.

---

### Post by Tomatz on 2009-01-27
> **YigalB said:**
> Getting old? It's just 5 years old! 
Ubuntu should put "we support oldies" as a moto. 

envyng? not yet. I will try that now.

Well its nvidia really, they dont support the older cards now :(

Remember not to use the newest driver in envy.

---

### Post by YigalB on 2009-01-27
> **Tomatz said:**
> Well its nvidia really, they dont support the older cards now :(

Remember not to use the newest driver in envy.

Nvidia? I dont think so. If they supported once for Ubuntu - it should last for ever. No one is expecting Nvidia to change driver when ever Ubuntu goes from 8.04 to 8.10.

As for envyng:
I installed and got two identical entries in applications-system tools.
I tried them both and they behave similar, meaning I am still with 640*480
But now I could open the nvidia software, unlike before.
However, I cant change the resolution into higher.
Another strange behavior is with the mouse: sometimes I click on a button and it seems like the click was elsewhere, wlthough te button was gra[phically shown as selected prior to the click.

Maybe my pc is hunted by ghost? 
Maybe it's the spirit of the XP that used to live there just few days ago?

---

### Post by Tomatz on 2009-01-27
> Nvidia? I dont think so. If they supported once for Ubuntu - it should last for ever. No one is expecting Nvidia to change driver when ever Ubuntu goes from 8.04 to 8.10.

No new nvidia drivers for older cards are being made so as the OS progresses, the driver becomes more incompatible.

> As for envyng:
I installed and got two identical entries in applications-system tools.
I tried them both and they behave similar, meaning I am still with 640*480
But now I could open the nvidia software, unlike before.
However, I cant change the resolution into higher.
Another strange behavior is with the mouse: sometimes I click on a button and it seems like the click was elsewhere, wlthough te button was gra[phically shown as selected prior to the click.

Maybe my pc is hunted by ghost? 
Maybe it's the spirit of the XP that used to live there just few days ago?

Post your new **xorg.conf**. and the **model number and name** of your monitor. I think your H+V refresh rates are wrong ;)

---

### Post by YigalB on 2009-01-27
> **Tomatz said:**
> No new nvidia drivers for older cards are being made so as the OS progresses, the driver becomes more incompatible.



Post your new **xorg.conf**. and the **model number and name** of your monitor. I think your H+V refresh rates are wrong ;)

See file below.
Screen is CTX 1792 UA CRT

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

---

### Post by Tomatz on 2009-01-27
> **YigalB said:**
> See file below.
Screen is CTX 1792 UA CRT

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection


Hmmm, what you will need to do is open nvidia settings (again :() and set it to the resolution you want. Then when you select ***"save to x configuration file"*** **_DO NOT_** save click **preview** instead. Then post the preview here.

```
Make sure you wrap the text in code tags by highlighting the text and 
clicking the # button in the reply box.
```

---

### Post by YigalB on 2009-01-27
> **Tomatz said:**
> Hmmm, what you will need to do is open nvidia settings (again :() and set it to the resolution you want. Then when you select ***"save to x configuration file"*** **_DO NOT_** save click **preview** instead. Then post the preview here.


I have Nvidia X server setting. is that the same as Nvidid setting?

I wish I could set the reolution I want. It just want let me!
There is a discrepensy between the point I click with the mouse and the place that clicks hits. 
Is there a command line I can run instead?

---

### Post by Tomatz on 2009-01-27
> **YigalB said:**
> I have Nvidia X server setting. is that the same as Nvidid setting?

I wish I could set the reolution I want. It just want let me!
There is a discrepensy between the point I click with the mouse and the place that clicks hits. 
Is there a command line I can run instead?

Nvidia X server settings **is** nvidia-settings. I think the problem is your h+v refresh rates aren't set correctly in xorg (haven't been detected properly during the driver installation). Causing you to have a low resolution.

If you can do as i said above (my last post) then we can try to fix the resolution problem.

;)

---

### Post by Binny88 on 2009-01-27
I  used the graphical interface for saving the nvidia x server settings.The default screen resolution was 800x480 but i wanted 1024x768. I applied the settings & they were applied  but i couldnt save the settings. I did mange to save them after visiting the forum by launching the program as root(sudo).
But when i restart i still go back to the default value 800x480. What could be wrong?

---

### Post by Tomatz on 2009-01-27
> **Binny88 said:**
> I  used the graphical interface for saving the nvidia x server settings.The default screen resolution was 800x480 but i wanted 1024x768. I applied the settings & they were applied  but i couldnt save the settings. I did mange to save them after visiting the forum by launching the program as root(sudo).
But when i restart i still go back to the default value 800x480. What could be wrong?

Please start a new thread as this is a different issue ;)

PM me the URL if you like.

---

### Post by Binny88 on 2009-01-27
> **Tomatz said:**
> Please start a new thread as this is a different issue ;)

PM me the URL if you like.

Oops Sorry, first time in the forum .This one is huge & very quick in response too.

tHIS IS THE URL OF THE THREAD
[http://ubuntuforums.org/showthread.php?t=1052070](http://ubuntuforums.org/showthread.php?t=1052070)

---

### Post by YigalB on 2009-01-27
> **Tomatz said:**
> Hmmm, what you will need to do is open nvidia settings (again :() and set it to the resolution you want. 

I can't do that. It want let me select it. It just says auto resolution.

I guess this brings us to the end of the options.
As in the ER, after 3 installations (one 8.10,  two 8.04), 54 threads, 6 pages, good people that tried helping me, one desperate guy(that's me), I declare the PC is non-Ubuntu compatible. It must have done something very bad in previous life.

By tomorrow it will join again the hell's forces, running XP.

Thank you all!

Y.

PS
Unless I will buy a new VGA card and do it all over again.......

---

### Post by Tomatz on 2009-01-27
> **YigalB said:**
> I can't do that. It want let me select it. It just says auto resolution.


Click the ***advanced*** button, then you can enter the resolution manually. Like this:

```
1280x1024
```

Or whatever resolution you want.



Stick with it and im sure we can fix the issue ;)

---

### Post by YigalB on 2009-01-27
> **Tomatz said:**
> Click the ***advanced*** button, then you can enter the resolution manually. Like this:

```
1280x1024
```

Or whatever resolution you want.



Stick with it and im sure we can fix the issue ;)

I don't believe in after life, but let's give it a chance....
Here is a short status:
- if i remove NVIDIA driver i can use it with 800x600.
In that case, I can't access the Nvidia settings.

- If I install the drivers, I have another problem: not only I have to work with 640*480, i also have a strange thing: when I point the mouse to certain place, the click seems to happen in another place. I couldnt find an fixed offset to play with.

I am using keyboard and mouse, but that not so easy as it sounds.
When I get to the resolution butten, it wont let me change the "auto" into any figure.

I am opened to any suggestion, including remote controling.

---

### Post by Tomatz on 2009-01-27
> **YigalB said:**
> 

I am using keyboard and mouse, but that not so easy as it sounds.
When I get to the resolution butten, it wont let me change the "auto" into any figure.



Read my last post properly ;)

If you click the advanced button (in nvidia-settings) you can enter the resolution you want manually.

---

### Post by YigalB on 2009-01-27
> **Tomatz said:**
> Read my last post properly ;)

If you click the advanced button (in nvidia-settings) you can enter the resolution you want manually.

Not exactly: in the advanced I can chose between 640, 320, auto or off.
Auto keeps the 640*480. 

Below there is a panning box in which I can enter manualy, but it is downgraded into 640x480, no matter what I type.

---

### Post by SnakeHips on 2009-01-28
> **SnakeHips said:**
> 

and does it give you any options? there should be one marked recommended ,if this is the case then accept that and install.


Did you accept the default recommended? and what driver did that give you? If it gave the 173 (nvidia-glx-new) then I think something has failed in the identification of your card ,if you chose this manually then this looks like the reason your subsequent attempts to configure dont work.

```
Nvidia-Settings 
```
Nvidia driver version

I've not had chance to study all you latest posts so if this is old news - apols. Goin back to M$ Windies is always an option -though dont you find this a great place of learning?

---

### Post by Tomatz on 2009-01-28
> **YigalB said:**
> Not exactly: in the advanced I can chose between 640, 320, auto or off.
Auto keeps the 640*480. 

Below there is a panning box in which I can enter manualy, but it is downgraded into 640x480, no matter what I type.

OK, no worries. Can you select 640x480 and the just write the changes to xorg.conf, Then post the contents of xorg.conf in... ```
code tags (#).
``` So i can manually edit it for you to use your preferred resolution (and fix the h+v refresh rates if needed).

Do not reboot or log out after you have made changes though ;)

---

### Post by YigalB on 2009-01-28
> **SnakeHips said:**
> Did you accept the default recommended? and what driver did that give you? If it gave the 173 (nvidia-glx-new) then I think something has failed in the identification of your card ,if you chose this manually then this looks like the reason your subsequent attempts to configure dont work.


I tried them all, and the results are the same. Note that I downgraded into 8.04, yet it's all the same. 
And yes - 173 is the default offered driver


> **SnakeHips said:**
> I've not had chance to study all you latest posts so if this is old news - apols. Goin back to M$ Windies is always an option -though dont you find this a great place of learning?
I am going back to M$ (I didn't do it yet because of work overload) just because I need this machine to work, and I can't play with it forever. This PC is serving my family, and they don't appreciate any learninmg curve ....

As for learning - I did learn a lot. I like that and I am not afraid of any trial or idea, it's just because I found myself circling and back to the same point. Sometimes it's better to accept a failure.

Another issue is a bit of disapointment (from the OS - not from the wonderful people in this forum).
To my view, it's unacceptable that OS wont support AGP card like FX5200. I am not saying that Ubuntu should support ISA cards with jumpers, but since the PnP message of PCI, there is no excuse not to automatically detect hardware and assign the approperiate driver. For me, this is a flag for the maturity and peopl oriented delivery.
I see it as a clear bug. Not feature, nor nice to have.
I am also surprized for the lake of easy to use GUI utilities that can interface between the user and the XORG file in this example. I had also a very similiar problem with static IP. It's a concept issue. E.g. - untill now I didnt find how to easily define my CRT as the display device. I love that CRT (has two inputs - I can share with two computers), and I am not going to change it just because Ubuntu is not allowing me to define the CRT.

So far, I installed many Ubuntu machines, and I can clearly say it's easier to install Ubuntu. Unlike W$, I never need the MB's CD, and the time from power up to a working, fully updated system, is the best with Ubuntu. 
Until this time.

---

### Post by Jacked36 on 2009-01-28
I am VERY new to Linux and have been following this thread with great interest as I too have been trying to get an FX5200 card to give me 1280x1024 resolution without success.   This morning I swapped the video card for a Radeon 7500 which straight away gives me a very useable 1152x864.   At last I can continue my adventure with Ubuntu.

---

### Post by YigalB on 2009-01-28
> **Tomatz said:**
> OK, no worries. Can you select 640x480 and the just write the changes to xorg.conf, Then post the contents of xorg.conf in... ```
code tags (#).
``` So i can manually edit it for you to use your preferred resolution (and fix the h+v refresh rates if needed).

Do not reboot or log out after you have made changes though ;)

I already posted several XORGs in this thread.
Can you take one of them and edit it for me? 
I tried it also, but failed.
Also, how do I specify the screen type in the XORG?

---

### Post by Tomatz on 2009-01-28
> **YigalB said:**
> I already posted several XORGs in this thread.
Can you take one of them and edit it for me? 
I tried it also, but failed.
Also, how do I specify the screen type in the XORG?

They were basic "stub" files (usually a full xorg.conf is not needed anymore). You need to generate a full xorg.conf with nvidia-settings.

You will see what i mean when you do it ;)

---

### Post by YigalB on 2009-01-28
> **Tomatz said:**
> OK, no worries. Can you select 640x480 and the just write the changes to xorg.conf, Then post the contents of xorg.conf in... ```
code tags (#).
``` So i can manually edit it for you to use your preferred resolution (and fix the h+v refresh rates if needed).

Do not reboot or log out after you have made changes though ;)

OK... here it comes:

```
nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Virtual	640	480
		Depth	24
		Modes		"640x480@60"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Screen"
	# 
	Identifier	"screen1"
	Device		"device1"
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Screen	0
EndSection

Section "Device"
	# 
	Identifier	"device1"
	Driver		"nvidia"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Screen	1
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"	"CoreKeyboard"
	Inputdevice	"Configured Mouse"	"CorePointer"
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
	Gamma	1
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
EndSection

Section "Monitor"
	# 
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
	Gamma	1
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

---

### Post by Tomatz on 2009-01-28
Firstly, the installation of the driver didn't work :( You are using the **visa** driver instead of the nvidia driver.

I have edited your xorg.conf so it _should_ use the nvidia driver and 1024x768 resolution _BUT_ i can give no promises that it will work as xorg is having a hard time (obviously) detecting your hardware.

Do this:

**Download** the xorg.conf.zip attached to this post extract it and **put the actual xorg.conf file on to the Desktop (this is important)**

Open a terminal

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back
```

Now

```
sudo cp ~/Desktop/xorg.conf /etc/X11/xorg.conf 
```


_Now Reboot or logout_


**Now if it borks, from the cli type *(write this down)*:**


```
sudo cp /etc/X11/xorg.conf.back /etc/X11/xorg.conf
```


Now ***ctrl alt bkspace***


If it didn't work and you had to restore the original xorg.conf, then as a last resort you can use the screens and graphics tool but its pretty flaky and it will only probably configure the visa driver.

Run the following in a terminal:

```
gksu displayconfig-gtk
```


Good luck ;)

---

### Post by YigalB on 2009-01-29
Oh yea - we have a progress!
Not a solution - but definitely a progress.

I have now 800*600. Not more though :(

I run ```
diff
``` and noticeed that somehow the file was modified, ao here is the current XORG file (btw - I couldnt attach it. I assume it need to be zipped - how do I do that? is there a command line for zip?)
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

PS - I have red update pending with NVIDIA envy update. Can I accept it?

---

### Post by Tomatz on 2009-01-29
> **YigalB said:**
> Oh yea - we have a progress!
Not a solution - but definitely a progress.

I have now 800*600. Not more though :(

I run ```
diff
``` and noticeed that somehow the file was modified, ao here is the current XORG file (btw - I couldnt attach it. I assume it need to be zipped - how do I do that? is there a command line for zip?)
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```


This is your xorg.conf after you copied the modified one i sent?

If so, the problem is now worse as you are using the vesa driver and xorg isn't even seeing that you have an nvidia card :(


Basically your system will (graphically) run very slow configured like this.

As a last resort you can run:

```
gksu displayconfig-gtk
```

To see if you can manually set xorg to work with your card.


Other than that, have you tried installing an older version of ubuntu? I  suggest you try 8.04 LTS.

---

### Post by YigalB on 2009-01-29
> **Tomatz said:**
> 
As a last resort you can run:

```
gksu displayconfig-gtk
```

To see if you can manually set xorg to work with your card.


Other than that, have you tried installing an older version of Ubuntu? I  suggest you try 8.04 LTS.

When I restarted I already got the ```
gksu displayconfig-gtk
```
I noticed that it did try testing higher resolutions and failed.
If I hadn't known that this screen and card are capable of higher resolutions, I might have suspected that the problem is not with Ubuntu, but this is not the case.

I already downgraded to 8.04 - I am not sure if it's LTS or not, nor what is the difference between regular 8.04 and LTS.

---

### Post by Tomatz on 2009-01-29
> **YigalB said:**
> When I restarted I already got the ```
gksu displayconfig-gtk
```
I noticed that it did try testing higher resolutions and failed.
If I hadn't known that this screen and card are capable of higher resolutions, I might have suspected that the problem is not with Ubuntu, but this is not the case.

I already downgraded to 8.04 - I am not sure if it's LTS or not, nor what is the difference between regular 8.04 and LTS.

8.04 is 8.04 LTS (long term support). The only things i can suggest is that you try envyng again (make sure you select the second driver down the list in envyng) or get a new graphics card.

I'd hate to see you go back to XP :(

---

### Post by YigalB on 2009-01-29
> **Tomatz said:**
> 8.04 is 8.04 LTS (long term support). The only things i can suggest is that you try envyng again (make sure you select the second driver down the list in envyng) or get a new graphics card.

I'd hate to see you go back to XP :(

Will try envyng soon, but I am getting off line for few hours.

Assuming it fails, before we really give up - is there any one from the guys that handle the under the hood that would like access to this pc in order to debug the problem? 
I am willing to allow remote access.

---

### Post by Tomatz on 2009-01-29
> **YigalB said:**
> Will try envyng soon, but I am getting off line for few hours.

Assuming it fails, before we really give up - is there any one from the guys that handle the under the hood that would like access to this pc in order to debug the problem? 
I am willing to allow remote access.

Nope but you can report a bug over at launchpad, a dev may assist you but you could be waiting a while.

---

### Post by YigalB on 2009-01-29
> **Tomatz said:**
> Nope but you can report a bug over at launchpad, a dev may assist you but you could be waiting a while.

Sorry - envy failed. 
I tried the 3 drivers there.

I reported a bug.

---

### Post by Tomatz on 2009-01-29
> **YigalB said:**
> Sorry - envy failed. 
I tried the 3 drivers there.

I reported a bug.

Bummer :(

You should give another distro a try for now. Maybe mandriva?

[http://www.mandriva.com/](http://www.mandriva.com/)

Its not as easy to use as ubuntu and IMO package management sucks but its quite a nice OS.

---

### Post by YigalB on 2009-01-29
> **Tomatz said:**
> Bummer :(

You should give another distro a try for now. Maybe mandriva?

[http://www.mandriva.com/](http://www.mandriva.com/)

Its not as easy to use as ubuntu and IMO package management sucks but its quite a nice OS.

Good question.
I am confused by the number of Linux distributions. Honestly - I think there should be only one, and all should unite forces.
So I decided in the past to focus on one only.
It's also because of the target of these PCs - I donate them to those who can't afford, and this means I must support them as well. I really don't see how can I support another line, even if this is just a GUI change (is it?).

But since you asked - I will give it a try. I will install Mandriva on a different hard drive, and play with it for a while.

---

### Post by Slim Odds on 2009-01-29
I don't know that this will help, but I use the FX5200 on two 8.04.2 systems here. It works fine.

Here's the config for one with dual monitors:```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL1917W"
    HorizSync       31.0 - 84.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "TwinViewXineramaInfoOrder" "CRT-0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "CRT-0: nvidia-auto-select +1440+0, CRT-1: nvidia-auto-select +0+0"
EndSection

```

---

### Post by YigalB on 2009-01-29
> **Tomatz said:**
> Bummer :(
You should give another distro a try for now. Maybe mandriva?
[

Guess what - Mandriva is using 1024x768 out of the box. With lifeCD and after installation. No question asked, no drivers/xorg investigations.

So it's ruling out the theory written here before that it's Nvidia problem, and prove it's Ubuntu's bug.

---

### Post by SnakeHips on 2009-01-29
> **YigalB said:**
> I tried them all, and the results are the same. Note that I downgraded into 8.04, yet it's all the same. 
And yes - 173 is the default offered driver



I am going back to M$ (I didn't do it yet because of work overload) just because I need this machine to work, and I can't play with it forever. This PC is serving my family, and they don't appreciate any learninmg curve ....

As for learning - I did learn a lot. I like that and I am not afraid of any trial or idea, it's just because I found myself circling and back to the same point. Sometimes it's better to accept a failure.

Another issue is a bit of disapointment (from the OS - not from the wonderful people in this forum).
To my view, it's unacceptable that OS wont support AGP card like FX5200. I am not saying that Ubuntu should support ISA cards with jumpers, but since the PnP message of PCI, there is no excuse not to automatically detect hardware and assign the approperiate driver. For me, this is a flag for the maturity and peopl oriented delivery.
I see it as a clear bug. Not feature, nor nice to have.
I am also surprized for the lake of easy to use GUI utilities that can interface between the user and the XORG file in this example. I had also a very similiar problem with static IP. It's a concept issue. E.g. - untill now I didnt find how to easily define my CRT as the display device. I love that CRT (has two inputs - I can share with two computers), and I am not going to change it just because Ubuntu is not allowing me to define the CRT.

So far, I installed many Ubuntu machines, and I can clearly say it's easier to install Ubuntu. Unlike W$, I never need the MB's CD, and the time from power up to a working, fully updated system, is the best with Ubuntu. 
Until this time.

I admire your persistence with trying to resolve this one and I agree with your findings that Ubuntu (or any linux flavour for that matter) to be faster to boot and more stable. I've 1% of the problems I used to get with M$ since changing - the days of the old 'blue screen of death' are long gone for me.

Anyhow ,I'm going to read through the latest posts in this thread and if I can offer any further help I will.

---

### Post by Tomatz on 2009-01-29
> **YigalB said:**
> Guess what - Mandriva is using 1024x768 out of the box. With lifeCD and after installation. No question asked, no drivers/xorg investigations.

So it's ruling out the theory written here before that it's Nvidia problem, and prove it's Ubuntu's bug.

I'd say ubuntu and nvidia BUT maybe I'm biased ;)

---

### Post by Tomatz on 2009-01-29
> **YigalB said:**
> Good question.
I am confused by the number of Linux distributions. Honestly - I think there should be only one, and all should unite forces.
So I decided in the past to focus on one only.
It's also because of the target of these PCs - I donate them to those who can't afford, and this means I must support them as well. I really don't see how can I support another line, even if this is just a GUI change (is it?).

But since you asked - I will give it a try. I will install Mandriva on a different hard drive, and play with it for a while.

Not a GUI change a kernel change. Its still linux but Mandriva is based on red hat where as ubuntu is based on Debian. I started out on mandrake (now Mandriva). Its nice but the rpm package management system is years behind the Debian package management system (apt). 

You will learn what dependency hell is soon enough ;)

What desktop environment are you using?

---

### Post by YigalB on 2009-01-30
> **Tomatz said:**
> I'd say ubuntu and nvidia BUT maybe I'm biased ;)

As I see it, if Ubuntu doesn't reach the level of relations with Nvidia as Mandriva, it's Ubuntu.....

BTW - can I "copy" the driver from Mandriva to Ubuntu?
Can I copy the XORG? Would that solve the problem?

---

### Post by Tomatz on 2009-01-30
> As I see it, if Ubuntu doesn't reach the level of relations with Nvidia as Mandriva, it's Ubuntu.....

Not really...

Just stick with it and you will learn. That's what linux is all about ;)

> BTW - can I "copy" the driver from Mandriva to Ubuntu?
Can I copy the XORG? Would that solve the problem?


Mandriva uses a completely different kernel and package management system (installer) so the drivers wouldn't be compatible.



Try ubuntu again when jaunty is released ;)

---

### Post by Tomatz on 2009-01-30
Have a look here:

[http://ubuntuforums.org/showthread.php?p=6643969#post6643969](http://ubuntuforums.org/showthread.php?p=6643969#post6643969)

Another user having problems with the 5200 ;)

---

### Post by YigalB on 2009-01-30
I think I have some more data to be considered. The issue is not over yet!
First, Mandriva was a nice try, but I am still staying with Ubuntu. Just for the record :)

Now, I have another PC involved. In order to keep aligned, I will call the PC discussed so far PC_A, and the other one PC_B.
PC_A was tested with FX5200, rarely it gave 800x600, mostly 640x480.
I installed PC_B with unknown VGA card (i searched the PCB and all I could locate is "model 6t6870". I tried googling - no results). PC_B was installed with 8.04, and gave me endless resolution options, all I could ask for, if I had magnifying glass instead of eyes.

Now I replaced cards between the PCs: 
PC_A got the unknown card, while PC_B got my famous FX5200.

PC_A couldn't boot beyond the BIOS.
PC_B gave me the same resolutions it had before.

Conclusion1: FX5200 is working well, so is Ubuntu drivers with that card inside that PC.

As I write these lines, I re-installed PC_A, with 8.10. After initial boot I got 800*600. Now it is updating the 245 updates since 8.10 was issued.

Now I am confused. Is it really Ubuntu bug, as I claimed before? 
How could it be PC depended? 
Perhaps the answer is within the BIOS. I will try looking at the BIOS setup and see if there is a relevant flag, but it doesn't make any sense since the BIOS is not aware of the transactions over the AGP bus. But I will try.
Another thing to do is to update the BIOS. Usually I avoid it, because of the risk, but in that case I think I will have to.

Any other idea or suggestions?

---

### Post by Tomatz on 2009-01-30
> **YigalB said:**
> I think I have some more data to be considered. The issue is not over yet!
First, Mandriva was a nice try, but I am still staying with Ubuntu. Just for the record :)

Now, I have another PC involved. In order to keep aligned, I will call the PC discussed so far PC_A, and the other one PC_B.
PC_A was tested with FX5200, rarely it gave 800x600, mostly 640x480.
I installed PC_B with unknown VGA card (i searched the PCB and all I could locate is "model 6t6870". I tried googling - no results). PC_B was installed with 8.04, and gave me endless resolution options, all I could ask for, if I had magnifying glass instead of eyes.

Now I replaced cards between the PCs: 
PC_A got the unknown card, while PC_B got my famous FX5200.

PC_A couldn't boot beyond the BIOS.
PC_B gave me the same resolutions it had before.

Conclusion1: FX5200 is working well, so is Ubuntu drivers with that card inside that PC.

As I write these lines, I re-installed PC_A, with 8.10. After initial boot I got 800*600. Now it is updating the 245 updates since 8.10 was issued.

Now I am confused. Is it really Ubuntu bug, as I claimed before? 
How could it be PC depended? 
Perhaps the answer is within the BIOS. I will try looking at the BIOS setup and see if there is a relevant flag, but it doesn't make any sense since the BIOS is not aware of the transactions over the AGP bus. But I will try.
Another thing to do is to update the BIOS. Usually I avoid it, because of the risk, but in that case I think I will have to.

Any other idea or suggestions?

All it could be in the bios is the default display adaptor may be set to "on board".

Check this out:

> Linux driver support

The GeForce FX series is no longer supported [20] by the binary NVidia drivers as of version 177.80. Owners of GeForce FX hardware now have to use the legacy drivers, which cannot be used at the same time as the regular drivers and will not be updated to work with newer Linux kernels or Xorg releases.

[http://en.wikipedia.org/wiki/GeForce_FX_Series](http://en.wikipedia.org/wiki/GeForce_FX_Series)


Basically fx support is on the way out but I'm glad you finally got it sorted! Maybe ubuntu just didn't like the combination of your mainboard and the 5200 (and the legacy drivers) for some messed up reason? IMO it is a bug.

:popcorn: for you!

BTW what did you think of mandriva?

---

### Post by YigalB on 2009-01-31
> **Tomatz said:**
> All it could be in the bios is the default display adaptor may be set to "on board".
Will be checked, but I don't think so as there is no on-board vga controller in this case. Yet there are other definitions - sometimes motherboard makers have their own private jokes

[/QUOTE] Basically fx support is on the way out[/QUOTE]
Please don't say that. There are many thousands of FX boards out there. One of Ubuntu messages MUST be to work on s old as possible hardware. this is certainly not too old! 
If someone decided it is - that a wrong perception of the Ubuntu spirit.

[/QUOTE] but I'm glad you finally got it sorted! Maybe ubuntu just didn't like the combination of your mainboard and the 5200 (and the legacy drivers) for some messed up reason? IMO it is a bug. [/QUOTE]
It is a bug - I agree, yet I need to bring the RnD guys with as much data to debug it, assuming they will.


[/QUOTE] BTW what did you think of mandriva?[/QUOTE]
Actually, I did like it. The GUI is nicer to my eyes. However, I am not going to switch there - it's either Ubuntu or M$. I am not going to start learning how to maintain another OS. Human brains limitations, I assume.
Another view is that once I switch - there may be no way back. So I may lose many cups of Ubuntu I collected - and I do like them roasted.

---

### Post by SnakeHips on 2009-01-31
[/QUOTE] BTW what did you think of mandriva?[/QUOTE]
Actually, I did like it. The GUI is nicer to my eyes. However, I am not going to switch there - it's either Ubuntu or M$. I am not going to start learning how to maintain another OS. Human brains limitations, I assume.
Another view is that once I switch - there may be no way back. So I may lose many cups of Ubuntu I collected - and I do like them roasted.[/QUOTE]

I'm asking myself "what would I do" in your situation and here's my thought's. You seem loyal to Ubuntu (as an M$ alternative) and looking forward the easiest solution to this problem would be a new card or soldier on and **force** the 169 (nvidia-glx) package.
There's also some legacy packages you might want to experiment with nvidia 96 or something like that. 

I'd be inclined to EBAY something like a '6' series upward Nvidia card.

Hope it helps

---

### Post by YigalB on 2009-01-31
> **Tomatz said:**
> 
I'm asking myself "what would I do" in your situation and here's my thought's. You seem loyal to Ubuntu (as an M$ alternative) and looking forward the easiest solution to this problem would be a new card or soldier on and **force** the 169 (nvidia-glx) package.
There's also some legacy packages you might want to experiment with nvidia 96 or something like that. 

I'd be inclined to EBAY something like a '6' series upward Nvidia card.

Hope it helps

I think it will not fly. If you recall, I tried another card that worked well in another PC, and it didn't work here. I will investigate the BIOS options, maybe update BIOS first.

---

### Post by SnakeHips on 2009-01-31
Yes I read about the other 'card' you tried.

what does this give you? if it complains 'not found' you'll need the package nvclock from synaptic.

```
nvclock -i
```

edit: and this one as well
```
cat /proc/driver/nvidia/agp/status
```

---

### Post by sargetech on 2009-08-23
Hi Folks, I just wanted to throw my 2 cents in and post my xorg.conf.I am using a GeForce FX5200 card with Hardy 8.04.3,using the 173.14.20 nvidia driver. I hope it helps somebody out please see below:
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by Dexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce FX5200"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic CRT Display"
	Modelname	"Monitor 1024x768"
	Horizsync	31.5-61.0
	Vertrefresh	50-75
 
  
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load            "v4l"
	
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"NVIDIA GeForce FX5200"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
	Vendorname	"NVIDIA"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

after using these settings I got my CRT monitor to work fine.I use 1024x768@60hz, it's a small old monitor, but it's still is very bright and the display is razor sharp!!
I hope I can help someone with this:)

---

