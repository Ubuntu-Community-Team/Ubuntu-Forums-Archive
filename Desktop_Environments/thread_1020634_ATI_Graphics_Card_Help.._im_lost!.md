---
title: "ATI Graphics Card Help.. im lost!"
date: 2008-12-24
forum: Desktop Environments
---

### Post by stormeagle on 2008-12-24
Hey everyone,

Firstly my O.S. Is ubuntu Intrepid 8.10

I'm having a lot of trouble with my Graphics card.
When i start up i get this message
"You must run Ubuntu in Low graphics mode"
When i try to configure it or set to defaults it sets my Xorg.conf to blank
Aticonfig is a blank document

Command Prompt1
(Attempt to fix my problem

----------------
cody@cody-desktop:~$ glxgears
363 frames in 5.0 seconds = 72.473 FPS
XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
after 943 requests (938 known processed) with 0 events remaining.
cody@cody-desktop:~$ fgrlxconfig
bash: fgrlxconfig: command not found
cody@cody-desktop:~$ fgrlxconfig
bash: fgrlxconfig: command not found
cody@cody-desktop:~$ glxgears
750 frames in 5.0 seconds = 149.989 FPS
735 frames in 5.0 seconds = 146.872 FPS
XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
after 3295 requests (33 known processed) with 0 events remaining.
cody@cody-desktop:~$ glxinfo |grep render
direct rendering: Yes
OpenGL renderer string: Software Rasterizer
cody@cody-desktop:~$ fgrlxconfig
bash: fgrlxconfig: command not found
cody@cody-desktop:~$ fglrxinfo
The program 'fglrxinfo' is currently not installed. You can install it by typing:
sudo apt-get install xorg-driver-fglrx
bash: fglrxinfo: command not found
cody@cody-desktop:~$ aticonfig --initiate
The program 'aticonfig' is currently not installed. You can install it by typing:
sudo apt-get install xorg-driver-fglrx
bash: aticonfig: command not found
cody@cody-desktop:~$ sudo apt-get install xorg-driver-fglrx
[sudo] password for cody:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
fglrx-amdcccle fglrx-kernel-source
Suggested packages:
libamdxvba1
The following NEW packages will be installed:
fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx
0 upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/20.2MB of archives.
After this operation, 55.8MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously deselected package fglrx-kernel-source.
(Reading database ... 419286 files and directories currently installed.)
Unpacking fglrx-kernel-source (from .../fglrx-kernel-source_2%3a8.552-0ubuntu0.1_i386.deb) ...
Selecting previously deselected package xorg-driver-fglrx.
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_2%3a8.552-0ubuntu0.1_i386.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.552-0ubuntu0.1_i386.deb) ...
Processing triggers for man-db ...
Setting up fglrx-kernel-source (2:8.552-0ubuntu0.1) ...
Adding Module to DKMS build system
Doing initial module build
Installing initial module
Done.

Setting up xorg-driver-fglrx (2:8.552-0ubuntu0.1) ...

Setting up fglrx-amdcccle (2:8.552-0ubuntu0.1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
cody@cody-desktop:~$ aticonfig --inituate
aticonfig: unrecognized option '--inituate'
aticonfig: parsing the command-line failed.
cody@cody-desktop:~$ aticonfig --initiate
aticonfig: unrecognized option '--initiate'
aticonfig: parsing the command-line failed.
cody@cody-desktop:~$ aticonfig --initiate
aticonfig: unrecognized option '--initiate'
aticonfig: parsing the command-line failed.
cody@cody-desktop:~$ aticonfig -initiate
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11
cody@cody-desktop:~$ Hey everyone,
bash: Hey: command not found
cody@cody-desktop:~$

Graphics Card: ATI PCI Express X1650 Radeon

If you can help or just point me in the right place it would be very appreciated!

---

### Post by gettinoriginal on 2008-12-24
Try this in terminal:

sudo dpkg-reconfigure xserver-xorg

---

### Post by stormeagle on 2008-12-25
Did what you suggested, than followed this guide [Linkie]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide").

The last thing it tells is typing fglrxinfo in console to see if everything worked well, this is what i get:

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12


Here is a copy of my Xorg (After the install of the guide)

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Help. =)
Thankyou for your input

---

### Post by gettinoriginal on 2008-12-25
Ok, did some research and found this, worth a try: :P

[http://ubuntuforums.org/archive/index.php/t-774574.html](http://ubuntuforums.org/archive/index.php/t-774574.html)

---

### Post by stormeagle on 2008-12-26
Well...

I did all of that tutorial,

cody@cody-desktop:~$ sudo fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14
cody@cody-desktop:~$

here is my xorg.conf

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "ServerFlags"
	Option         "AIGLX" "1"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Option	    "XAANoOffscreenPixmaps" "1"
	Option      "TexturedVideo" "1"
	Option      "TexturedVideoSync" "1"
	Option      "BackingStore" "1"
	Option      "Textured2D" "1"
	Option      "TexturedXRender" "1"
	Option      "BackingStore" "1"
	Option      "AccelMethod" "EXA"
	Option      "DRI" "1"
	Option      "DynamicClocks" "1"
	Option      "ForceGenericGPU" "0"
	Option      "VideoOverlay" "0"
	Option      "OpenGLOverlay" "0"
EndSection

Section "Extensions"
## For Textured2d and Textured XRender
	Option      "RENDER" "1"
	Option      "XVideo" "1"
	Option      "Composite" "1"
	Option      "Damage" "1"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode      "0666"
EndSection


hmm this is intersting:

cody@cody-desktop:~$ glxgears
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14
cody@cody-desktop:~$

What to do?

---

### Post by stormeagle on 2008-12-26
After i used to first Tutorial (Linkie in my first reply) my computer at Restart would not say "Ubunutu needs to run in Low Graphics Mode) anymore.

After following the suggested guide (Basically the same thing with additions, It said "Ubunutu needs to run in Low Graphics Mode" again

---

### Post by pietjanjaap on 2008-12-26
Install envy. It is in ubuntu.
Read on the envy website how it works in textmode if you need it there.

Then start envy(with gui), then remove everything.
reboot
start envy, install driver
reboot.
if you have not enough screen sizes to choose off then start, gksu displayconfig-gtk, change only the monitor, see wat your optimize screen is off your monitor.
then reboot

---

### Post by stormeagle on 2008-12-26
Removed all with Envy (success)
Note: The "Ubuntu must run in Low Graphics mode was gone, sweet)
Install ATI driver (Failed)

Note:
"There was an error during the Installation process. Below is the log file.

python pulse.py ati 
root@cody-desktop:/usr/share/envy# python pulse.py ati
Envy - Version 0.9.10
ENVY ERROR: Your Operating System does not seem to be supported by Envy

Fix?

---

### Post by stormeagle on 2008-12-26
Now, im running the Mesa Driver

cody@cody-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 1.4 (2.1 Mesa 7.2)

cody@cody-desktop:~$

I want to run the ATI driver (fglrx?)

Ati Catalyst Controller and Envy are not functioning

---

### Post by stormeagle on 2008-12-28
Bump
Help???
Plx

---

### Post by stormeagle on 2008-12-29
final bump before dump to XP again..

H 
E
L
P 

Please

---

### Post by stormeagle on 2008-12-29
Final Bump before dump to XP..

S
O
S

Please.

---

### Post by Rohan Kapoor on 2008-12-30
This is my 2cents. Envy doesn't work with Ubuntu 8.10 it destroyed my system, try this, go to system-administration-hardware drivers and see if anything for ATI/AMD shows up. That fixed up mine very nicely. Good luck!

---

### Post by zika on 2008-12-30
just a shot in a dark. did You try graphic driver from ati.amd.com site (as I can see there is one with catalyst ver. 8.12, 10-dec-2008. )? I have ATI HD 3650 and I'm using driver from that site.

---

### Post by Navarre on 2008-12-30
I've been dinking with my Ubuntu vs ATI setup for a few days now, I think I have the driver re-install down to a few commands

go ahead and boot into ubuntu using low graphics
go to the amd.com site and download the ati graphics driver, that should give you a ati-driver-installer-8-12-x86.x86_64.run file.  

$ chmod +x ati-driver-installer-8-12-x86.x86_64.run 
$ sudo ati-driver-installer-8-12-x86.x86_64.run

I think you can then run this command to set up an initial xorg.conf If it does not work here then do it after the reboot after activating the drivers below.

$ sudo aticonfig -initial 

Next navigate the menus 
System -> Administration -> Hardware Drivers

Ati should be listed in that window, press the activate button, after that is finished reboot.

Ati Catalyst control center should now be on your Applications Menu.  You can use that to configure your displays.  It seems I always have to use System -> Preferences -> Screen Resolution to get my screen set correctly.  

Now to be honest I am running dual monitors, so my aticonfig line is different, aticonfig --help is mostly useful for figuring out particular options.  That should get you going, have fun.

--Nav

---

### Post by Rohan Kapoor on 2008-12-30
> **Navarre said:**
> I've been dinking with my Ubuntu vs ATI setup for a few days now, I think I have the driver re-install down to a few commands

go ahead and boot into ubuntu using low graphics
go to the amd.com site and download the ati graphics driver, that should give you a ati-driver-installer-8-12-x86.x86_64.run file.  

$ chmod +x ati-driver-installer-8-12-x86.x86_64.run 
$ sudo ati-driver-installer-8-12-x86.x86_64.run

I think you can then run this command to set up an initial xorg.conf If it does not work here then do it after the reboot after activating the drivers below.

$ sudo aticonfig -initial 

Next navigate the menus 
System -> Administration -> Hardware Drivers

Ati should be listed in that window, press the activate button, after that is finished reboot.

Ati Catalyst control center should now be on your Applications Menu.  You can use that to configure your displays.  It seems I always have to use System -> Preferences -> Screen Resolution to get my screen set correctly.  

Now to be honest I am running dual monitors, so my aticonfig line is different, aticonfig --help is mostly useful for figuring out particular options.  That should get you going, have fun.

--Nav

You're running dual-monitors!!! Like Me!

---

### Post by Navarre on 2008-12-30
yeah I had to choose between dual monitor as a single big display or compiz fancy-shmancy 3d affects.  More real estate is better than toys, at least for now. 

The older ati (mine's a 9800) have a hard texture limit of 2048x2048, my screen(s) is 3360x1050, compiz makes a single texture out of your desktop so it can lay it on the spinny cube.  Mine just plain don't fit.  So my options are to see if I can get compiz to split the textures so they do fit (tbh I don't even know if compiz is open source)  OR buy a new video card.  But if I'm shopping for a new video card then I obviously need a new mobo which means a new computer.  So the short of it is... big screen and no compiz effects.

---

### Post by Rohan Kapoor on 2008-12-30
> **Navarre said:**
> yeah I had to choose between dual monitor as a single big display or compiz fancy-shmancy 3d affects.  More real estate is better than toys, at least for now. 

The older ati (mine's a 9800) have a hard texture limit of 2048x2048, my screen(s) is 3360x1050, compiz makes a single texture out of your desktop so it can lay it on the spinny cube.  Mine just plain don't fit.  So my options are to see if I can get compiz to split the textures so they do fit (tbh I don't even know if compiz is open source)  OR buy a new video card.  But if I'm shopping for a new video card then I obviously need a new mobo which means a new computer.  So the short of it is... big screen and no compiz effects.
I'm running it on a laptop so... I'm in the same boat, two screens and no compiz which sucks but yeah, you take what you get and you fight back!

---

### Post by stderr on 2008-12-30
I had similar issues with EnvyNG under 8.10. I would advise:

Remove all previous fglrx module builds:

```
sudo rm -r /var/lib/dkms/fglrx/*
```

Remove fglrx and everything associated:

```
sudo apt-get remove fglrx*
```

Download the latest ATi installer from their site. Chmod it so it's executable, and run as root. e.g.

```
sudo ./ati_.......(whatever it's called)
```

Following that, reboot, and hope.

edit: Oh, and downgrading back to XP may solve this one minor issue, but I would argue that it's a crazy move to make! I honestly wouldn't revert to any Winblows OS if I were paid a living wage just for doing so...

---

### Post by Rohan Kapoor on 2008-12-30
> **stderr said:**
> I had similar issues with EnvyNG under 8.10. I would advise:

Remove all previous fglrx module builds:

```
sudo rm -r /var/lib/dkms/fglrx/*
```

Remove fglrx and everything associated:

```
sudo apt-get remove fglrx*
```

Download the latest ATi installer from their site. Chmod it so it's executable, and run as root. e.g.

```
sudo ./ati_.......(whatever it's called)
```

Following that, reboot, and hope.

edit: Oh, and downgrading back to XP may solve this one minor issue, but I would argue that it's a crazy move to make! I honestly wouldn't revert to any Winblows OS if I were paid a living wage just for doing so...
Well if they paid me enough... I might have to consider it.

---

### Post by stderr on 2008-12-30
> **darth-vader said:**
> Well if they paid me enough... I might have to consider it.

I think it's one of those things... I might agree to it, but secretly I'd be quad booting distros and hacking up my browser identification to read "Microsoft Internet Exploder" :)

---

### Post by Rohan Kapoor on 2008-12-30
Not a bad idea!

---

