---
title: "How to Make Money with Ubuntu."
date: 2009-05-15
forum: General Help
---

### Post by HunterThomson on 2009-05-15
[SIZE=3][COLOR=SeaGreen]Boy this it the title if you want people to read you post :P
1,100 hits in one week :) Sorry guys for the little social engineering hack[/COLOR][/SIZE]

I will put money in your paypall acount if you sucessfully help me get my...

ATI FireGL 5700 (realy HD 3650)

To work with the Catalyst driver. 

$20 + $10hr... OBO

[SIZE=4][COLOR=Blue]HOWLY COW !!! IT WORKS !!!

sudo aticonfig --acpi-services=off !!!

SuperTuxKart at 1680x1050 200FPS !!![/COLOR][/SIZE]


[SIZE=4][COLOR=Red]
NOPE I will NEVER buy ATI ever agin](*,)
I can't get the ATI card to work in Archlinux. I now "HOPE" to sell this laptop 1 week latter for $250 less then what I paid. I am now going to buy a laptop with and INTEL 4500MDH.[/COLOR][/SIZE]

[SIZE=3][COLOR=Blue]Arg, Well I guess I'll keep it... The only other laptop I would want is a Dell Latitude E6500 but that laptop seems to have far more problmes then this one. 

I guess it's just an Ubuntu box. Could be worse. [/COLOR][/SIZE]

---

### Post by Kareeser on 2009-05-15
Without a contract, it's pretty much bogus, but I'll try and help you pro bono, how's that.

What have you tried so far?

---

### Post by HunterThomson on 2009-05-16
> **Kareeser said:**
> Without a contract, it's pretty much bogus, but I'll try and help you pro bono, how's that.

What have you tried so far?

I'll do it you'll see.
Thank you for replying.

I have tried the gnome driver install thing.
the qt-sabayn installer
And donloading it from the ATI web page and installing it.

All leve me with a black screen and unable to reboot.

edit i meen the envyng-qt

---

### Post by FIONEX on 2009-05-16
What have you tried so far?  I know that this wiki works for me almost every time.  **Just read EVERY WORD!**

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

Start reading at "**Installing the drivers manually**"
Make sure to do this at the end:

sudo aticonfig --initial -f 
sudo aticonfig --input=/etc/X11/xorg.conf

I started out with the same problem as you but I finally got it working.

---

### Post by HunterThomson on 2009-05-16
> **FIONEX said:**
> What have you tried so far?  I know that this wiki works for me almost every time.  **Just read EVERY WORD!**

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

Start reading at "**Installing the drivers manually**"

Ok i'll try the wiki thank you for the link.

---

### Post by Arup on 2009-05-16
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

If everything fails add the repo posted there and you will get latest ATI driver via your system. No need to install anything, just enable via system>hardware drivers

---

### Post by HunterThomson on 2009-05-16
Ok. it looks good I will be sure to do that at the end like you said.

Get your paypall account ready :P
It has a lot of steps I have never seen or done before.

---

### Post by FIONEX on 2009-05-16
yeah the wiki is awesome.  If you just follow it word for word, it never fails.  It even predicts any problems you might run into.  At the end, it even gives you a link to tune the driver.  I can help you get Xv running after you get your video card up.

Don't worry about the money - I don't need it.  Just let me know if it works or not so I can help you debug it.  Ubuntu 9.04 has been hell, but atleast it boots in 15 seconds...

---

### Post by HunterThomson on 2009-05-16
> **Arup said:**
> [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

If everything fails add the repo posted there and you will get latest ATI driver via your system. No need to install anything, just enable via system>hardware drivers

at this point that system>hardware drivers things scares me. 
But your up next if this wiki fails.

---

### Post by HunterThomson on 2009-05-16
Nope no good black screen agin....

---

### Post by HunterThomson on 2009-05-16
OK so I am in the recovory mode
at the shell I put back the xorg.conf but all is still scrwed up.

---

### Post by FIONEX on 2009-05-16
ok..do yourself a favour and check the xorg logs by going into safe mode, then choose ROOT from the menu.

Then do:

less /var/log/Xorg.0.log.old

Whenever you see "(EE)", then that's your problem.  Post what the "(EE)" says.

---

### Post by HunterThomson on 2009-05-16
shoot. I formated it alredy... If I do it agin would you know how to fix the errors? I think I try that updating the repos method this time.

Good thing I have a SSD makes all of this go real fast :P

---

### Post by HunterThomson on 2009-05-16
Ok installed agin.
I think I am doing the updating the repo then using the "hardware driver" gnome thing. I'll post the (EE)'s

---

### Post by FIONEX on 2009-05-16
always look at logs first "/var/log/Xorg.0.log" or "/var/log/Xorg.0.log.old".  Then act accordingly.  The ati driver has problems with 9.04, there's no doubt about it.  But it does work because it's working for me.

---

### Post by HunterThomson on 2009-05-16
Ok, and on second though I'll folow the wiki agin. 

I forgot to do the two things you said.... Do I no edit the xorg.conf and just do thoughs two steps or add the one line to the xorg.conf and do your two steps at the end.

---

### Post by FIONEX on 2009-05-16
You edit xorg and add the Driver "fglrx".  Then you do "sudo aticonfig --initial -f".  Then you do "sudo aticonfig --input=/etc/X11/xorg.conf"

Post your xorg.conf after you do all that.

---

### Post by HunterThomson on 2009-05-16
OK will do. I'll post it before I reboot.

---

### Post by FIONEX on 2009-05-16
If you reboot and it doesn't work, then you dont have to reinstall to get linux working.  Just go into Recovery Mode --> Root.


sudo apt-get remove fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx


Then restore xorg.conf by removing the Driver "fglrx" line.

---

### Post by HunterThomson on 2009-05-16
Ok here is the xorg.conf I have now. Pre-reboot.

What do you think. I'll wate to reboot utill you reply.

---

### Post by FIONEX on 2009-05-16
It's weird that you're not getting something like this at the end of the device section:
	BusID       "PCI:1:0:0".

It would be different for you than PCI:1:0:0

---

### Post by HunterThomson on 2009-05-16
HOE, I forgot the two steps agin I'll post the new xorg.conf...

owe it tels me no supported adapters detected when I run the fist step

---

### Post by FIONEX on 2009-05-16
Ok that makes sense then because "aticonfig --initial -f" should add that line in.

---

### Post by HunterThomson on 2009-05-16
> **FIONEX said:**
> Ok that makes sense then because "aticonfig --initial -f" should add that line in.

well a guy that works for ATI told me my card was suported no dout. Why can't it find the supported device?

shoud I try that auto config sents your two commands cant find my device?

(I edited the post above after I tried to run your first command.)

---

### Post by FIONEX on 2009-05-16
Replace your xorg.conf with the content of the file I attached and then do the sudo aticonfig --initial -f

---

### Post by FIONEX on 2009-05-16
Also post the result of this command:

lspci | grep HD

---

### Post by HunterThomson on 2009-05-16
here is the output of the command lspci | grep HD


00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]

---

### Post by FIONEX on 2009-05-16
ok, add this to the Device section in xorg.conf as well:

	BusID       "PCI:1:0:0"


Then post your xorg.conf.  Don't attach it, just paste it.

---

### Post by HunterThomson on 2009-05-16
Nope still not deteced with your xorg.conf

---

### Post by HunterThomson on 2009-05-16
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Option	    "AIGLX" "on"
EndSection

Section "Module"
	Load  "glx"
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
	Option	    "TexturedVideo" "on"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "UseFastTLS" "1"
	BusID		"PCI:1:0:0"
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
	Group        "Video"
	Mode         0666
EndSection
```

---

### Post by Yellow Pasque on 2009-05-16
Post an Xorg log from a failed attempt to start with the fglrx driver (/var/log/Xorg.0.log)

---

### Post by HunterThomson on 2009-05-16
Is that wrong and the busID is realy 

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
**_01:00.0_** VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series] 
```

I don't know what I am talking about though... that was just a guess.... sorry.

---

### Post by HunterThomson on 2009-05-16
> **Temüjin said:**
> Post an Xorg log from a failed attempt to start with the fglrx driver (/var/log/Xorg.0.log)

sorry I messed up and reinstalled before I could but I am sure I'll get anuther chance....

---

### Post by FIONEX on 2009-05-16
Ok...Im kinda confused because your card isn't even listed on the website.  I'm assuming you downloaded the driver Linux x86_64 driver - Catalyst 9.4.  Assuming that's correct, then try this command then:

sudo aticonfig --initial -f --input=/etc/X11/xorg.conf

---

### Post by FIONEX on 2009-05-16
> **HunterThomson said:**
> Is that wrong and the busID is realy 

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
**_01:00.0_** VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series] 
```

no that's not wrong.  I have the same bus id, and aticonfig put those numbers in my xorg.conf

I suggest that you just reboot with the xorg.conf I gave you.
If you reboot and it doesn't work, then you dont have to reinstall to get linux working. Just go into Recovery Mode --> Root.


sudo apt-get remove fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx


Then restore xorg.conf by removing the Driver "fglrx" line.

---

### Post by HunterThomson on 2009-05-16
> **FIONEX said:**
> Ok...Im kinda confused because your card isn't even listed on the website.  I'm assuming you downloaded the driver Linux x86_64 driver - Catalyst 9.4.  Assuming that's correct, then try this command then:

sudo aticonfig --initial -f --input=/etc/X11/xorg.conf

Ya that is the driver I installed the x86_64. Ya ti is a "Mobility FireGL 5700" they do have "Mobility FireGL 5000" if you go though there thing to get a driver.

But I folowed the link form the wiki to get the driver.

Or were you sayign the HD 3650 is not listed.

=====

the output form that command is...

```
cruzer@GNU-Box:~$ sudo aticonfig --initial -f --input=/etc/X11/xorg.conf
[sudo] password for cruzer: 
Unable to open /etc/ati/control, please reinstall the driver.
aticonfig: No supported adapters detected
cruzer@GNU-Box:~$


cruzer@GNU-Box:/etc/ati$ ls
amdpcsdb.default.dpkg-new   control.dpkg-new                signature.dpkg-new
atiogl.xml.dpkg-new         logo_mask.xbm.example.dpkg-new
authatieventsd.sh.dpkg-new  logo.xbm.example.dpkg-new
cruzer@GNU-Box:/etc/ati$
```

---

### Post by FIONEX on 2009-05-16
I just figured out why...

you should be using this driver instead:

[http://support.amd.com/us/gpudownload/fire/Pages/fire_linux.aspx?type=2.4.3&product=2.4.3.3.2.3.10&lang=English](http://support.amd.com/us/gpudownload/fire/Pages/fire_linux.aspx?type=2.4.3&product=2.4.3.3.2.3.10&lang=English)

---

### Post by HunterThomson on 2009-05-16
Ok done all we can do at this point... rebooting and Ill post the (EE)

Edit: not rebooting..... se next post.

---

### Post by HunterThomson on 2009-05-16
> **FIONEX said:**
> I just figured out why...

you should be using this driver instead:

[http://support.amd.com/us/gpudownload/fire/Pages/fire_linux.aspx?type=2.4.3&product=2.4.3.3.2.3.10&lang=English](http://support.amd.com/us/gpudownload/fire/Pages/fire_linux.aspx?type=2.4.3&product=2.4.3.3.2.3.10&lang=English)

OK. I'll try that. how do I get the stuff I already install out?

---

### Post by FIONEX on 2009-05-16
If you reboot and it doesn't work, then you dont have to reinstall to get linux working. Just go into Recovery Mode --> Root.


sudo apt-get remove fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx


Then restore xorg.conf by removing the Driver "fglrx" line.

---

### Post by HunterThomson on 2009-05-16
> **FIONEX said:**
> If you reboot and it doesn't work, then you dont have to reinstall to get linux working. Just go into Recovery Mode --> Root.


sudo apt-get remove fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx


Then restore xorg.conf by removing the Driver "fglrx" line.

you sure you don't want me to try that driver instead?

---

### Post by FIONEX on 2009-05-16
Hey man, I'm heading out so I'm gonna leave you with some advice.

Remove the driver (if it doesn't work) by using
sudo apt-get remove fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx
then clean out you xorg.conf by deleting "driver  "fglrx"".

Then go to ATI's driver page and choose the different drivers and follow the wiki.  There's a FireGL  Mobility V5000.  There's also the FireGL V5600...They're both a bit different.  I'm thinking the FireGL mobility V5000 would probably be the one for you.

What I would try first through is to go to System -> Administration -> Hardware drivers and try that, because it's EASY!

---

### Post by HunterThomson on 2009-05-16
I think I am going to. 
I'll just do all that uninstalling suff as if it didn't work. Then do the the same thing in the wiki exept I'll use the new driver you found insead.

---

### Post by HunterThomson on 2009-05-16
> **FIONEX said:**
> Hey man, I'm heading out so I'm gonna leave you with some advice.

Remove the driver (if it doesn't work) by using
sudo apt-get remove fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx
then clean out you xorg.conf by deleting "driver  "fglrx"".

Then go to ATI's driver page and choose the different drivers and follow the wiki.  There's a FireGL  Mobility V5000.  There's also the FireGL V5600...They're both a bit different.  I'm thinking the FireGL mobility V5000 would probably be the one for you.

What I would try first through is to go to System -> Administration -> Hardware drivers and try that, because it's EASY!

OK cool I think you put me on the right path.

---

### Post by FIONEX on 2009-05-16
It turns out the drivers I showed you don't work with Ubuntu 9.04's Xorg server.  Ubuntu 9.04 uses Xorg 1.6 (version 7.4).  As you can see, the drivers I suggested can support upto version 7.3.  You can still try them out and see.. but I think it'll be a waste.  So just try the System -> Admin -> Hardware  thing first...Otherwise, you might have to downgrade to xorg 1.5 and use the catalyst 9.3 driver instead of the catalyst 9.4 driver.

---

### Post by HunterThomson on 2009-05-16
> **FIONEX said:**
> It turns out the drivers I showed you don't work with Ubuntu 9.04's Xorg server.  Ubuntu 9.04 uses Xorg 1.6 (version 7.4).  As you can see, the drivers I suggested can support upto version 7.3.  You can still try them out and see.. but I think it'll be a waste.  So just try the System -> Admin -> Hardware  thing first...Otherwise, you might have to downgrade to xorg 1.5 and use the catalyst 9.3 driver instead of the catalyst 9.4 driver.

ok

---

### Post by Yellow Pasque on 2009-05-16
Nvm

---

### Post by HunterThomson on 2009-05-16
hum. no (EE) in the log. just it warrnings (WW) the...

fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found

seems to be the worst one. I'll post the full one when i get all that off.

---

### Post by HunterThomson on 2009-05-16
```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux GNU-Box 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri May 15 20:28:07 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "aticonfig Layout"
(**) |-->Screen "aticonfig-Screen[0]-0" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]-0"
(**) |   |-->Device "aticonfig-Device[0]-0"
(**) Option "AIGLX" "on"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) ATI Technologies Inc Mobility Radeon HD 3650 rev 0, Mem @ 0xc0000000/268435456, 0xd8300000/65536, I/O @ 0x00007000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
(II) Loading extension XFree86-DRI
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.60.3
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.60.3
	Module class: X.Org Video Driver
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for fglrx
(II) ATI Proprietary Linux Driver Version Identifier:8.60.3
(II) ATI Proprietary Linux Driver Release Identifier: 8.602                                
(II) ATI Proprietary Linux Driver Build Date: Apr  1 2009 15:01:03
(II) Loading PCS database from /etc/ati/amdpcsdb
(WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0
(WW) Video driver ABI version of the X server is 5.0
(--) Chipset Supported AMD Graphics Processor (0x9591) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) fglrx(0): pEnt->device->identifier=0x1ee5a30
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "UseFastTLS" "1"
(**) fglrx(0): Option "TexturedVideo" "on"
(**) fglrx(0): Option "DPMS" "true"
(II) fglrx(0): 10BitPixelFormat disabled by default
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(--) fglrx(0): Chipset: "ATI Mobility Radeon HD 3650" (Chipset = 0x9591)
(--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x3604)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xd8300000
(--) fglrx(0): I/O port at 0x00007000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.88
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: FGL M86
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(II) fglrx(0): Using adapter: 1:0.0.
(--) fglrx(0): Video RAM: 262144 kByte, Type: DDR3
(II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x10000000)
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): RandR 1.2 support is enabled!
(II) fglrx(0): RandR 1.2 rotation support is enabled!
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in

Backtrace:
0: /usr/X11R6/bin/X(xorg_backtrace+0x26) [0x4f1b66]
1: /usr/X11R6/bin/X(xf86SigHandler+0x41) [0x485a61]
2: /lib/libc.so.6 [0x7fe8fc738040]
Saw signal 11.  Server aborting.
(WW) xf86CloseConsole: VT_WAITACTIVE failed: Interrupted system call
 ddxSigGiveUp: Closing log
```

---

### Post by HunterThomson on 2009-05-16
I am downloading ubuntu intrepid 8.10 and see if that works.

I think that was the one when it still mite work.
Heck be better if I can use the good driver and I'll still get security updates till 04/2010.

---

### Post by HunterThomson on 2009-05-16
So funny:lolflag:

5 votes yes
4 votes no

:lolflag:

just what I was thinking

---

### Post by lisati on 2009-05-16
> **HunterThomson said:**
> So funny:lolflag:

5 votes yes
4 votes no

:lolflag:

just what I was thinking

Almost: it's now 6 votes "yes".

Thought: Where there's a will, there's a queue of relations who pop out of the woodwork..

---

### Post by HunterThomson on 2009-05-16
boy o boy 810 will not even give me a desktop out of the box like 9.04. All i get is garble and crash.

I am so glad i didn't get this laptop in 8.10 days.

---

### Post by HunterThomson on 2009-05-16
I am going to try to install the dirvers in 8.10 form the shell and if that dosn't work. I give up.

In archlinux I could not even wach videos but in Ubuntu 9.04 videos seemed to work just fine. So, I'll just live with it. In all honisty I never play video games. Sure I install them and play them once. All I realy do is wach torrented moves, make a fool of myself on forums and learn to write python. And my python is vary far form OpenGL.

So, I'll just wait a few months and hope it will all get sorted out.

It's Linux time right ;) Give it 6 months.
My warranty lasts for 3 more years.

Well do you think the 32bit Ubuntu has a better chance?

---

### Post by t0p on 2009-05-16
> **HunterThomson said:**
> I am downloading ubuntu intrepid 8.10 and see if that works.

I think that was the one when it still mite work.
Heck be better if I can use the good driver and I'll still get security updates till 04/2010.

If you install hardy you'll get updates for even longer - April 2011 I think.

BTW, your poll needs another option.  I have no idea at all if you'll get that card working.

---

### Post by HunterThomson on 2009-05-16
Well I found a guy that has the exact same laptop and the exact same Mobility FireGL 5700. 

He geve me his xorg.conf and gave me a link to teh exact same driver download he got from the ATI web site. And all the stuff he did. He even is on x86_64.

The thing that mite work is he said I had to run this command.

sudo aticonfig --acpi-services=off (this will avoid the panic.)


So, I'll try it and if not I realy will be running a GNU-box.

I'll also post the insturctions here and maybe make a How-To for this exact laptop... IF it works.

---

### Post by HunterThomson on 2009-05-16
[SIZE="4"][COLOR="RoyalBlue"]HOWLY COW !!! IT WORKS !!!

ATICONFIG ACPI=OFF !!!

SuperTuxKart at 1680x1050 200FPS !!!\\:D/[/COLOR][/SIZE]

---

### Post by FIONEX on 2009-05-18
Stay true to your promise and write that how-to for your laptop model!
You're almost an expert on that video card by now!

---

### Post by HunterThomson on 2009-05-19
> **FIONEX said:**
> Stay true to your promise and write that how-to for your laptop model!
You're almost an expert on that video card by now!

I will when I get it working right. I'll write a good one. I am now building ubuntu form a CLI install.

---

### Post by HunterThomson on 2009-05-19
WOW I hate ubuntu. I am in a CLI install and I said (apt-get install xorg) and Ubuntu wants to install every driver posable and even "hal" 

WTF !!!

Why even have a CLI vertion of ubuntu ?

Even xserever-xorg-video-vmware ! Ubuntu is crazy. It like just assumes your an idiot.

---

### Post by lisati on 2009-05-19
> **HunterThomson said:**
> WOW I hate ubuntu. I am in a CLI install and I said (apt-get install xorg) and Ubuntu wants to install every driver posable and even "hal" 

WTF !!!

Why even have a CLI vertion of ubuntu ?

Even xserever-xorg-video-vmware ! Ubuntu is crazy. It like just assumes your an idiot.

It must be time for a well-earned break! Good luck!

---

### Post by skymera on 2009-05-19
> **HunterThomson said:**
>  It like just assumes your an idiot.

I think you mean: "**You're** and idiot"

---

### Post by HunterThomson on 2009-05-19
> **lisati said:**
> It must be time for a well-earned break! Good luck!

ya your right... I'll stop posting....

---

