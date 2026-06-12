---
title: "Nvidia Graphic card not working with DELL XPS 1530"
date: 2008-04-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by papuaq on 2008-04-30
hello all,
I am experiencing a problem in installing Nvidia graphic card driver in my Dell xps 1530. I am trying to install hardy.
Its is working fine with my feisty.no
In hardy, its not showing by default any restricted driver. By manually enabling the restricted driver, after rebooting, the display is gone.
I have Nvidia Geforce 8600, 256 mb graphic card.
I have also tried to install the driver for linux from Nvidia site. While manually installing that, its show some conflict with /usr/lib/xorg/modules/libwfb.so 
After enabling the restricted driver, the display is gone. After that I uninstalled nvidia-glx-new, but after that the the machine is not able to identify the drivers, and the max res. becames 800 by 600. For that i have to again reconfigure xserver-xorg. 
Please help me out.

---

### Post by z0mbie on 2008-04-30
When you install it manually, make sure you have these packages installed:
```

sudo aptitude install linux-headers-`uname -r` xserver-xorg-dev build-essential gcc gcc-4.2
```

Then press **Ctrl+Alt+F4** to get a black & white command prompt, login.

Stop the GUI with this command:
```
sudo /etc/init.d/gdm stop
```

Then install the latest driver from Nvidia with:
```
sudo sh NVIDIA-Linux-x86-169.12-pkg1.run
```

Accept everything and allow it to edit your Xorg. 

Then start the GUI when it's done with:
```
sudo /etc/init.d/gdm start
```

To go back to GUI press **Ctrl+Alt+F7**

Now you should have your drivers working and receive better resolutions.

---

### Post by papuaq on 2008-05-01
Thanks for the reply, but i have already tried it. Both the ways, either installing the restricted driver from the System-> Administration -> hardware driver and by manually installing, as detailed by you, gives white screen.

---

### Post by z0mbie on 2008-05-01
Here's another method you can try:
[http://www.funnestra.org/ubuntu/hardy/#nvidia-driver](http://www.funnestra.org/ubuntu/hardy/#nvidia-driver)

& Last but not least, try the automated graphics driver installer [Envy]("http://www.albertomilone.com/nvidia_scripts1.html").?

---

### Post by papuaq on 2008-05-01
I think envy package is missing, has been obsoleted, or
is only available from another source. 
I am installing  envyng-qt envyng-gtk envyng-core. lets see.

---

### Post by papuaq on 2008-05-01
first i tried through the system->administration->Restricted drivers
failed.
then i downloaded NVIDIA-Linux-x86-169.12-pkg1.run this from there site.
failed.
then i tried the steps described in the following link
[http://www.funnestra.org/ubuntu/hardy/#nvidia-driver](http://www.funnestra.org/ubuntu/hardy/#nvidia-driver)
failed
then i installed EnvyNG.
installed 169.12
then 96.43.05
then 71.86.04 Nvidia drivers. but failed.
The final out come after complition of each step is white screen.
I also replaced the xorg.conf file of my ubuntu 7.10(In which the Nvidia driver is working fine) to the the hardy xorg.conf file.

---

### Post by shae on 2008-05-01
Try disabling compiz after you install the drivers.  The white screen thing sounds like a compiz problem (which is automatically enabled after you install a compiz-capable driver).

---

### Post by papuaq on 2008-05-02
thanks for the reply, Plese assist me, how to disaple compiz.

---

### Post by rossmoore on 2008-05-02
Do you have access to your gnome desktop now, or do you have to use a command line?

If you've got your desktop up then you go System->Appearances, choose visual effects tab and choose none.

If you need to use the command line, try
sudo apt-get --remove compiz

You can also do this I believe (from memory):
mkdir ~/.config/compiz
touch ~/.config/compiz/disable

You'll have to restart the X server to pick up.

---

### Post by papuaq on 2008-05-02
I have uninstalled compiz, then enabled the nvidia restricted driver. after reboot, got the same white screen. 
To make it to normal, i generally go to command prompt, from there i shutdown the xserver, then reconfigure the xserver. again restarting the xserver make's the desktop visible. but still graphic card is disabled.

---

### Post by atariluc on 2008-05-03
same problem with me. tried everithing. look this:

nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.
 any ideas???
thanks

---

### Post by papuaq on 2008-05-07
hello every one. The same problem I am facing with the Knoppix 5.3 live CD. Its also not detecting the graphic card. Is this the problem with the kernel version 2.6.24.
Since graphic card driver is not installing properly, I am not able to play 3D games in my ubuntu hardy.

---

### Post by papuaq on 2008-05-07
hello every one. The same problem I am facing with the Knoppix 5.3 live CD. Its also not detecting the graphic card. Is this the problem with the kernel version 2.6.24.
Since graphic card driver is not installing properly, I am not able to play 3D games in my ubuntu hardy.

---

### Post by OffHand on 2008-05-08
> **atariluc said:**
> same problem with me. tried everithing. look this:

nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.
 any ideas???
thanks

Post the output of: cat /etc/X11/xorg.conf

---

### Post by papuaq on 2008-05-09
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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by OffHand on 2008-05-09
Your xorg.conf is not configured properly. I will post mine (I got a XPS M1530 with Nvidia graphics and Intel wireless) when I get back from work in about 8/9 hrs. You can probably just copy my xorg.conf file if you have an Intel/Nvidia 1530.

---

### Post by xtracool_protik on 2008-05-12
Well buddy papuaq I've the same problem I tried with all the ways available here on net but in vain I get a white screen and black strip in the middle
 Way to fix this w/out modifying the xorg.conf is start ubuntu in recovery mode and do xfix it will automatically be as previous However NVIDIA drivers are missing and surely all the play is missing as can't get compiz working.
 Well please anybody help me with this problem
 Thank you very much in advance
 I've Dell XPS1530 1280x800 screen and NVIDIA8400 GS 128MB

---

### Post by OffHand on 2008-05-12
I have attached my xorg.conf Hopefully it will work for you. Maybe you only need to use a part of it.

---

### Post by VMC on 2008-05-12
> **OffHand said:**
> I have attached my xorg.conf Hopefully it will work for you. Maybe you only need to use a part of it.

What do you  mean "attached". I don't see the attachment anywhere. Is there somewhere else I need to go?

edit: okay, now I see it. I guess you were attaching and I was posting.

---

### Post by OffHand on 2008-05-12
> **VMC said:**
> What do you  mean "attached". I don't see the attachment anywhere. Is there somewhere else I need to go?

Something went wrong. Refresh the page and it should be there

---

### Post by reggie123 on 2008-05-12
> **papuaq said:**
> hello every one. The same problem I am facing with the Knoppix 5.3 live CD. Its also not detecting the graphic card. Is this the problem with the kernel version 2.6.24.
Since graphic card driver is not installing properly, I am not able to play 3D games in my ubuntu hardy.

Hello all!

Has anybody tried to install the nvidia beta drivers 173.08?
([http://us.download.nvidia.com/XFree86/Linux-x86/173.08/NVIDIA-Linux-x86-173.08-pkg1.run]("http://us.download.nvidia.com/XFree86/Linux-x86/173.08/NVIDIA-Linux-x86-173.08-pkg1.run"))

Cheers,
Reggie

---

### Post by OffHand on 2008-05-13
> **reggie123 said:**
> Hello all!

Has anybody tried to install the nvidia beta drivers 173.08?
([http://us.download.nvidia.com/XFree86/Linux-x86/173.08/NVIDIA-Linux-x86-173.08-pkg1.run]("http://us.download.nvidia.com/XFree86/Linux-x86/173.08/NVIDIA-Linux-x86-173.08-pkg1.run"))

Cheers,
Reggie
Yes, I am using them. They work fine on my machine.

---

### Post by papuaq on 2008-05-13
I have changed the entries of the xorg.conf file, both given by OffHand and the one in ubuntu 7.10 of my machine(In which the driver is working fine). i also downloaded the beta driver 173.08 as well as 171.05. But no success.  
One doubt in that. While installing the drivers(173.08 or any other nvidia driver) it ask for downloading something through ftp. The connection i am using, ftp is blocked. 
Also i have checked that the mention linux os give in that run file are Reh hat, fedora, mendrake and Suse. All are RPM based. Is the problem due to that. And also in the mentioned version, the kernel 2.6.24 is not there.

---

### Post by OffHand on 2008-05-13
> **papuaq said:**
> I have changed the entries of the xorg.conf file, both given by OffHand and the one in ubuntu 7.10 of my machine(In which the driver is working fine). i also downloaded the beta driver 173.08 as well as 171.05. But no success.  
One doubt in that. While installing the drivers(173.08 or any other nvidia driver) it ask for downloading something through ftp. The connection i am using, ftp is blocked. 
Also i have checked that the mention linux os give in that run file are Reh hat, fedora, mendrake and Suse. All are RPM based. Is the problem due to that. And also in the mentioned version, the kernel 2.6.24 is not there.

Do you have build-essential and the linux headers installed? You need them in order to install the Nvidia drivers. You do not need an internet connection if you have them.

---

### Post by papuaq on 2008-05-13
yeap, i have already installed it.
Even this time i completly removed nvidia-glx-new, nvidia-glx-new-dev, nvidia-kernel-common and then installed the 173.08, still the same problem.

---

### Post by OffHand on 2008-05-13
> **papuaq said:**
> yeap, i have already installed it.
Even this time i completly removed nvidia-glx-new, nvidia-glx-new-dev, nvidia-kernel-common and then installed the 173.08, still the same problem.

what's the output of: glxinfo

---

### Post by papuaq on 2008-05-13
Before, ubuntu was atleast detecting the restricted Nvidia driver. 
After i uninstall the nvidia-glx-new, nvidia-glx-new-dev, nvidia-kernel-common, the Hardware Driver link is not even showing it. 
I just tried this- uninstall the above packages, then installed the 173.08 manually.
After reboot i again got the white screen. 
Then as always i simply reconfigured the X by the command dpkg-reconfigure xserver-xorg

the output of glxinfo is:
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x49 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

---

### Post by OffHand on 2008-05-13
Try: sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by papuaq on 2008-05-13
nothing happened.
Its even not detecting the existing Graphic card.

---

### Post by OffHand on 2008-05-13
> **papuaq said:**
> nothing happened.
Its even not detecting the existing Graphic card.

What is the output of: lspci

---

### Post by jsc1959 on 2008-05-13
If it were me I think I would just try a re-install from scratch. I have a 1530 and it works just fine. Nvidia video card is detected no problem. Sorry if this is kinda moot or if a re-install is out of the question.

---

### Post by papuaq on 2008-05-14
hi jsc 1959, which version of ubuntu you are using. My graphic card is working fine in 7.10, but not in hardy. I have have downloaded the iso, and installed the system with that. 


The output of lspci is:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by OffHand on 2008-05-14
Your system sees the card - curious. I would try a clean install at this point. If you have /home on a separate partition this isn't too painful.

---

### Post by papuaq on 2008-05-14
Thanks. My fresh installation is complete. now update is going on. After that again i am thinking to install the driver through restricted driver only. Any kind of advice at this time??

---

### Post by OffHand on 2008-05-14
> **papuaq said:**
> Thanks. My fresh installation is complete. now update is going on. After that again i am thinking to install the driver through restricted driver only. Any kind of advice at this time??

If you are comfortable with manually installing the Nvidia driver, you could give the beta driver I am using a try.

[http://www.nvidia.com/object/linux_display_ia32_173.08.html](http://www.nvidia.com/object/linux_display_ia32_173.08.html)

p.s. you need the linux headers and build-essential in order to install the driver manually.

---

### Post by papuaq on 2008-05-14
I am having GeForce 8600 GT and the mentioned driver is having support for the following new GPUs:

    * Quadro FX 3600M
    * GeForce 9800 GX2
    * GeForce 9800 GTX
    * GeForce 9600 GT
    * GeForce 9500M GS
    * GeForce 8400
    * GeForce 8400 GS

Will it work fine for me??

---

### Post by papuaq on 2008-05-14
Still same problem. I have installed linux-headers build-essential, then manually installed the 173.05 driver. After restart, the screen tucked up showing the last line of boot something like /etc/rc.local. Then it asked for runing the OS in low graphics mode. Then as usual, i reconfigured the X, restarted it. Resolution is fine, but graphic card driver is not working fine.

---

### Post by VayHow on 2008-05-14
I've just finished installing 8.04 on my XPS M1530, with MD & Vista on the same HD. But I didn't experience your problem. I saw it's shown as "not in use" but a tick beside in restricted hardware drivers the 1st time I log on. This is the only thing confused me. After I updated system from source, it turned normal there. I just check the Nv driver (169.12? not so sure. should be) and click OK. Then enabled "Extra" and more advanced effect in CCSM. Everything works fine now. This is all fresh install on physical partition, including MD & Vista. Hope it helps.

---

### Post by cyclouno on 2008-05-14
same problem here... tried it all but no matter what is done hardy dumps nvidia 8600m gt DELL... so back to gutsy... prob with kernel or driver dunno?? will wait for next version of ubuntu......

---

### Post by OffHand on 2008-05-14
> **papuaq said:**
> Still same problem. I have installed linux-headers build-essential, then manually installed the 173.05 driver. After restart, the screen tucked up showing the last line of boot something like /etc/rc.local. Then it asked for runing the OS in low graphics mode. Then as usual, i reconfigured the X, restarted it. Resolution is fine, but graphic card driver is not working fine.

Did you change the driver to nvidia instead of nv in your xorg.conf? And what does the nvidia xserver tool tell you?

---

### Post by papuaq on 2008-05-14
I do not found any nv entry in my xorg file. 
One more important doubt. I am having T8100 intel processor. On the net its showing that its a 64 bit processor. totally confused now. If this is the problem, then how its working fine on 32 bit guesty cd. Still I have installed fresh hardy with 64 bit CD. Still the problem exist as it is.

---

### Post by OffHand on 2008-05-14
> **papuaq said:**
> I do not found any nv entry in my xorg file. 
One more important doubt. I am having T8100 intel processor. On the net its showing that its a 64 bit processor. totally confused now. If this is the problem, then how its working fine on 32 bit guesty cd. Still I have installed fresh hardy with 64 bit CD. Still the problem exist as it is.

It would be in section "`device"

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8600M GT]"
    Driver         "nvidia" <============  check if this says nv or nvidia
    Option	   "RenderAccel" "True"
    Option 	   "AllowGLXWithComposite" "True"
    Option         "AddARGBGLXVisuals" "True"
EndSection

There is absolutely no problem with running a 32bit OS on a 64bit CPU.

---

### Post by papuaq on 2008-05-16
I have changed (hit and try) all the possibilities that i can do in my knowledge. But still no success. May be its a problem with ubuntu 8.04 or the Nvidia driver support for it.

---

### Post by xtracool_protik on 2008-05-16
Hey buddy as reggie said try beta drivers they worked for me - 8400GS XPS1530

([http://us.download.nvidia.com/XFree8...73.08-pkg1.run](http://us.download.nvidia.com/XFree8...73.08-pkg1.run))

---

### Post by reggie123 on 2008-05-16
Hi,

I had the same problems and try almost anything/config/dpkg-reconfigures... (like you did too), but I manage to SOLVE it today :-)

Mine problem started after dist-upgrade from 7.10 to 8.04. 
There are a lots of issues with dist-upgrade scripts, and here is nvidia workaround:

Stop GDM (```
sudo /etc/init.d/gdm stop
```) and go in terminal line.

Backup your xorg.conf (if this does not work for you!)

Remove all nvidias:
```
sudo apt-get remove --purge nvidia-glx nvidia-glx-new
```

Remove all nvidia drivers:
```
sudo nvidia-installer --uninstall
```


In:
```
sudo gedit /etc/apt/sources.list
```

edit more sources for beta/beta repositories:
look for this line:

*deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted*


after this line add:
[I]# add hardy-proposed
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-proposed main restricted universe [/I]

...and save file.

Do:
```
sudo apt-get update
sudo apt-get upgrade
```

You should now have a lot of beta/beta fixtures, install them and reboot

Install new nvidia beta drivers:
```
sudo sh NVIDIA-Linux-x86-173.08-pkg1.run
```

Reboot again... :-)

You now have a working Dell & Ubuntu 8.04 :-)

**Hopefully this will work for you and hopefully I did not missed a step. This is a workaround since you are installing packages that are not officially guaranteed to work, and not yet put in regular updates!!!**

The alternatives is to wait a few weak for general &#8220;main&#8221; update.


Cheers,
Reggie

---

### Post by xtracool_protik on 2008-05-17
One more thing guys yesterday I installed beta drivers for NVIDIA now my Hardy is working fine then I upgraded it with Ubuntu Studio - wow that looks really cool :KS 
Anyway the problem is my generic kernel is working fine however one that is created by studio - rt not working gives error as wrong x configuration or something However I didn't play with it at all due to fear of going through all for generic kernel also :confused:
 Can anybody help me
And Thanks Reggie u were a great help:lolflag:

---

### Post by papuaq on 2008-05-23
thanks reggie123, I have given it a try, now its working fine. Thanks a lot.

---

### Post by rosarioarun on 2008-06-22
I almost tried everything you all said... But still the problem exists....
Still hardy for me is in Low Graphics Mode

---

### Post by veedub on 2008-06-22
There is a new envy driver.  Use synaptic to install the nvidia-glx-new-envy driver from the repositories.  Make sure sure you select the 173.14.05 driver(right click on nvidia-glx-new-envy, then select versions, then select 173.14.05 Hardy Proposed, then click close, and select the driver for install).  The 169 driver does not work on the xps 1530.  Make sure you uninstall ALL other nvidia drivers before installing the new 173.14.05.  New driver works perfectly on my xps1530. :)

---

### Post by rosarioarun on 2008-06-22
My synaptic shows that
nvidia-glx-new-envy (169.12+2.6.24.500-500.29)
is this the version you mentioned... Can i install this.
If not i couldnt find 173.14.05 anywhere

---

### Post by veedub on 2008-06-22
You have to select the driver version by clicking on the package, then hitting ctrl E.

Also, make sure you have enabled the hardy-proposed updates.  See my screenshots.....

---

### Post by rosarioarun on 2008-06-23
Thanks a lot.... 
But still i couldnt enable my visual effects. Its asks me to enable the restricted nvidia driver. If i give yes it starts downloading the nvidia-glx-new.... should i install that...

---

### Post by rosarioarun on 2008-06-23
Some how managed and solved the problem...
All my visual effects are now enabled....
Thanks a lot for all your support...
Special thanks to veedub...

---

### Post by srirajdutt on 2008-07-30
I found the version 173.14.09 which is the one I could find....now gow do I activate my nvidia drive. In Ssystem->Administration->Hardware Drivers , it still shows not in use...if I click enable there, it starts downloading the other version 169.....
after installing this package and changing the settings in the software sources, what am I supposed to do.
Thanks in advance
Please help me out...I have been trying to nvidia work for the past 15 days

---

### Post by srirajdutt on 2008-07-30
I reloaded the packages list and installed all the new updates it had given but in system-administration-hardware drivers it is showing graphics card not in use...
if I try to enable, it is download the 169... version...
help me out soon
thanks in advance

---

### Post by OffHand on 2008-07-31
> **srirajdutt said:**
> I reloaded the packages list and installed all the new updates it had given but in system-administration-hardware drivers it is showing graphics card not in use...
if I try to enable, it is download the 169... version...
help me out soon
thanks in advance

Did you go through the whole thread? I do not really feel like going over this all over again because the solution to your problem is probably already posted.

If you have tried all please come back and let us know.

---

### Post by BRRFOC on 2008-08-01
Greetings, I'm using the Nvidia Quadro NVS 135 on Dell D630 and have experienced problems getting driver to load and set up reliable xorg.conf, tried unsuccessfully to configure using nvidia-xconfig, and I've tried different glx drivers from Ubuntu Gutsy repository.

Has anyone installed Nvidia vendor 173.08 driver and had success using suspend/resume or hibernate?

---

### Post by santhosh.raju on 2008-10-29
If at all your problem is resolved .PLEASE WRITE THAT IT IS RESOLVED.
If not the solution is go to shell prompt and then kill x-server after killing x-server install nvidia driver downloaded from site and modify /etc/X11/xorg.conf from generic to nvidia.This should work and if it did not remove existing driver by going to hardware drivers and then remove it.

---

### Post by 080729jk on 2008-10-30
&#25968;&#25454;&#22823;&#38598;&#20013;&#30340;[**IT&#36816;&#32500;**](http://www.mochabsm.com/buy/index.htm)&#31649;&#29702;&#23454;&#36341; url]&#20197;&#19994;&#21153;&#36816;&#34892;&#21644;&#26381;&#21153;&#23458;&#25143;&#20026;&#20013;&#24515;&#65292;&#21046;&#35746;&#26631;&#20934;&#21270;&#30340;&#31649;&#29702;&#27969;&#31243;&#12289;&#35268;&#33539;&#21270;&#30340;&#31649;&#29702;&#21046;&#24230;&#12289;&#20998;&#24037;&#26126;&#30830;&#30340;&#23703;&#20301;&#36131;&#20219;&#21046;&#21644;&#37327;&#21270;&#34913;&#37327;&#30340;&#32489;&#25928;&#32771;&#26680;&#26159;&#23665;&#35199;&#24314;&#34892;&#22823;&#38598;&#20013;&#31995;&#32479;&#36816;&#34892;&#32500;&#25252;&#30340;&#37325;&#35201;&#20445;&#38556;&#12290;&#12288;&#12288; &#24314;&#35774;&#38134;&#34892;&#23665;&#35199;&#20998;&#34892;&#65288;&#31616;&#31216;&#8220;&#23665;&#35199;&#24314;&#34892;&#8221;&#65289;&#20449;&#24687;&#25216;&#26415;&#31649;&#29702;&#37096;&#26159;&#23665;&#35199;&#24314;&#34892;&#20869;&#37096;&#36827;&#34892;&#21508;&#31867;[**&#32593;&#31649;&#36719;&#20214;**](http://www.mochabsm.com/)&#30340;&#24320;&#21457;&#12289;&#36816;&#32500;&#30340;&#26381;&#21153;&#37096;&#38376;&#12290;&#20449;&#24687;&#25216;&#26415;&#31649;&#29702;&#37096;&#20869;&#37096;&#30340;&#26426;&#26500;&#35774;&#32622;&#20197;&#36866;&#24212;&#37329;&#34701;&#19994;&#21153;&#21457;&#23637;&#20026;&#31532;&#19968;&#35201;&#32032;&#65292;&#24418;&#25104;&#20102;&#20197;&#26085;&#24120;&#32500;&#25252;&#20026;&#20027;&#35201;&#26680;&#24515;&#12289;&#20197;&#24320;&#21457;&#26032;&#22411;&#37329;&#34701;&#20135;&#21697;&#36866;&#24212;&#26085;&#30410;&#25193;&#20805;&#30340;&#37329;&#34701;&#19994;&#21153;&#20026;&#20027;&#32447;&#30340;&#22810;&#37325;&#32452;&#32455;&#24418;&#24335;&#12290;&#12288;&#12288; IT&#36816;&#32500;&#31649;&#29702;&#25968;&#25454;&#22823;&#38598;&#20013;&#31995;&#32479;&#24314;&#35774;&#21518;&#65292;[**&#32593;&#31649;**](http://www.mochabsm.com/)&#23665;&#35199;&#24314;&#34892;&#38598;&#20013;&#24335;&#25968;&#25454;&#20013;&#24515;&#26356;&#38656;&#35201;&#31995;&#32479;&#12289;&#31185;&#23398;&#12289;&#39640;&#25928;&#30340;&#31649;&#29702;&#20307;&#31995;&#12290;&#12288;&#12288; &#20026;&#20102;&#26356;&#22909;&#22320;&#25552;&#39640;&#20449;&#24687;&#25216;&#26415;&#31649;&#29702;&#37096;&#30340;[**IT&#36816;&#32500;&#31649;&#29702;**](http://www.mochabsm.com/buy/index.htm)&#27700;&#24179;&#21644;IT&#36816;&#33829;&#25928;&#29575;&#65292;&#24182;&#20026;&#23665;&#35199;&#24314;&#34892;&#19994;&#21153;&#31995;&#32479;&#25552;&#20379;&#26356;&#39640;&#36136;&#37327;&#30340;&#36816;&#32500;&#20445;&#38556;&#65292;&#23665;&#35199;&#24314;&#34892;&#20449;&#24687;&#25216;&#26415;&#31649;&#29702;&#37096;&#30340;&#31649;&#29702;&#23618;&#35748;&#35782;&#21040;&#26412;&#36523;&#22312;IT&#26381;&#21153;&#31649;&#29702;&#26041;&#38754;&#65292;[**&#32593;&#32476;&#25299;&#25169;**](http://www.mochabsm.com/wztp.htm)&#29305;&#21035;&#26159;&#27969;&#31243;&#31649;&#29702;&#26041;&#38754;&#38656;&#35201;&#36827;&#19968;&#27493;&#25552;&#39640;&#65307;&#24182;&#23545;&#23665;&#35199;&#24314;&#34892;&#19994;&#21153;&#24212;&#29992;&#31995;&#32479;&#30340;&#36816;&#32500;&#25903;&#25345;&#25552;&#20986;&#20102;&#26631;&#20934;&#21270;&#12289;&#27969;&#31243;&#21270;&#12289;&#21046;&#24230;&#21270;&#21644;&#21487;&#34913;&#37327;&#21270;&#30340;&#26356;&#39640;&#35201;&#27714;&#65292;&#21516;&#26102;&#24076;&#26395;&#20943;&#23567;&#20154;&#21592;&#27969;&#22833;&#23545;&#36816;&#32500;&#24037;&#20316;&#30340;&#36127;&#38754;&#24433;&#21709;&#12290;&#12288;&#12288;

---

### Post by c.okugami on 2009-03-05
Here is more recent update of installing 8.10 kubuntu on Dell m1520 laptop. There are so many version of installing NVIDIA driver and 8.10 OS. 

This instruction show you simplest installation with using current latest driver (NVIDIA 180.29) (6.march.2009) With using this, I had no need to re-compile kernel or installing older g++ etc. 
  

Dell : m1530 laptop computer 
My OS: kubuntu 8.10 (32 bits) 
  

1) Install kubuntu 8.10. 
   then back up your current xorg.conf

   sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bk 

2) Download Nvidia-Linux-180.29-pkg1.run 
3) Ctl-F1, login as your admin account 
4) sudo /etc/init.d/kdm stop  
   This will kill current xserver 
5) sudo bash Nvidia-Linux-180.29-pkg1.run 
   When driver as you to download kernel
   Select "NO", DON"T DOWNLOAD IT. 
   
   Then ask you automatically update your xconfig, 
    answer "YES" 

6) sudo /etc/init.d/kdm start 
   You will see NVIDIA screen in flash then see your KDE.


In some reason, through package manager, I couldn't get it working. Hopely, it will get fixed soon. 

In addition, 
if you are keen for GPU CUDA programming, do following  

1) Download Cuda Tookkit and Cuda SDK 
   for ubuntu 8.04 (32 bits) 
 
   NOTE: DON"T DOWNLOAD CUDA DRIVER FROM THIS SITE!!! 

2) To compile Cuda, you will need additional package: 

sudo apt-get install mesa-common-dev 
sudo apt-get install freeglut3-dev glutg3-dev libglut3 
sudo apt-get install libxmu-dev


3) sudo install tool kit and sdk. 

4) make 


Nvida 180 driver works beautifully on my dell now.

---

