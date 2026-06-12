---
title: "a lot of mistakes on kernel and nvidia"
date: 2005-06-03
forum: Desktop Environments
---

### Post by vanaedium on 2005-06-03
Hi
I've actually THE problem with nvidia driver. After upgraded the kernel 2.6.10-5-k7 i found the new driver for nvidia 7664 and i've tried to install manually  ](*,)  but the result was a disaster as always no X!!
I've setted from "nvidia" to "nv" in xorg.conf to restore and when I've been inside kde the kicker always crash. So I've thinked there was a conflict between the new kernel with kicker so i've upgraded to kde 3.4.1. But nothing change.....i realized that was styleclock (gl requiered) the problem: so I uninstalled the cool clock and kicker magically appeared!!! ](*,) 
I've downgraded to the old kernel and I've tried to reinstall nvidia-glx but X doesn't work. The problem is , I think with the kernel module.............what have I to do to reset to the old situation? Or is there someone that would tell me how to install manually the new driver? I've tried a guide from fedora (becouse that distro use udev too) but the nvidia devices  aren't in the same place and I can't find them!!!
hmmmmmm...... the nv driver is faster than nvidia  :roll: 
Help please

Ps Sorry for my terrible english

---

### Post by codejunkie on 2005-06-03
you should just have to reinstall the nvidia packages nvidia-glx, nvidia-settings, and the linux-restricted-modules for your kernel.

---

### Post by vanaedium on 2005-06-03
not enough sob...
It requires nvidia kernel modules that it can't find

---

### Post by codejunkie on 2005-06-03
what the nvidia driver form ubuntu or the one from nvidia?

---

### Post by vanaedium on 2005-06-03
the nvidia driver 7174, the nv-ubuntu works

---

### Post by codejunkie on 2005-06-03
are you trying to install the official driver from [www.nvidia.com](www.nvidia.com) or the one that shows up in synaptic/kynaptic the one from ubuntu provides all the needed kernel modules with the package linux-restricted-modules you have to builde your own when you install the official one from [www.nvidia.com?](www.nvidia.com?)

---

### Post by vanaedium on 2005-06-03
i was trying to install from nvidia.com but with incomplete instructions for debian......but now I'm searching to restore my old situation with synaptic with reinstallation but it can't find nvidia kernel modules.

---

### Post by codejunkie on 2005-06-03
oh! ok what kernel are you using

---

### Post by vanaedium on 2005-06-03
2.6.10-5-k7 version 2.6.10-34.1 the last one

---

### Post by codejunkie on 2005-06-03
ok do sudo apt-get install nvidia-glx nvidia-settings linux-restricted-modules-k7 
and then change the nv back to nvidia in /etc/X11/xorg.conf

---

### Post by vanaedium on 2005-06-03
no as always i've already tried before

---

### Post by codejunkie on 2005-06-03
also if that dosen't work make sure you have uninstalled the nvidia driver from [www.nvidia.com](www.nvidia.com) with sh NVIDIA-Linux-x86-1.0-7664-pkg1.run --unistall
completely uninstall these packages through synaptic nvidia-glx nvidia-settings linux-restricted-modules-k7 and reinstall them. the nvidia driver might have corrupted one or more when you tried to install it.

---

### Post by vanaedium on 2005-06-03
wow now works!!!!! Thanx man!! :) 
Do you know how to install with the script nvidia(etc).run?
I think this package build the kernel module for nvidia but is there a guide to install it by shell and not from repository? With special care to udev permissions?
I'm searching that because kde3.4 and renderaccel=true crash (gnome works). Maybe in this release (7664) this bug is solved, who knows?!
Thanx again

---

### Post by codejunkie on 2005-06-03
glad to be of some help. and to your other question i installed the official nvidia driver once but it involved downloading alot of development packages and i can't rember which ones and the linux-kernel-headers,linux-headers-k7,and the build-essential packages and the nvidia installer did it on it's own but i reformated because my 10gig drive was almost full.

---

### Post by codejunkie on 2005-06-03
i thought that i would let you know i just installed the new nvidia driver from [www.nvidia.com](www.nvidia.com) successfully it seems pretty stable and i gained 60 fps.

These are the steps in detail i took just in case you wan't to try it hope it helps.
opened up terminal sudo gedit /etc/X11/xorg.conf  changed nvidia to vesa
saved and restarted x with ctrl+atl+backspace logged in and opened synaptic
clicked on search typed nvidia under Look in:choose Description and Name and search i selected all that were listed by clicking on the first item holding the shift key 
then selecting the last item right clicked and choose Mark for Complete Removal if this does'nt work 
you can just select each one and remove.
i downloaded the new driver from [www.nvidia.com](www.nvidia.com) and placed it my home directory then 
i did sudo apt-get install build-essential linux-headers-k7 linux-kernel-headers
after that finished i pressed ctrl+alt+F1 logged in as root with sudo su then i ran telinit 3
then i ran killall gdm to stop the xserver cd /home/myusername/ then ls because it's hard for an old man to remember that long name nvidia uses for its driver. and finally 

sh NVIDIA-Linux-x86-1.0-7664-pkg1.run the installer asked me to accept the license agreement i said yes it said no precompiled kernels found would you like the installer to download a kernel for you again i answered yes it again said no precompiled kernel modules found this is normal for the nvidia installer because it does'nt have any newer precompiled kernels for my kernel. then the installer will now build one for you the installer built the kernel module like it should told me it was finished successfully and i exited the nvidia setup and ran nano /etc/X11/xorg.conf replaced vesa with nvidia saved my /etc/X11/xorg.conf rebooted and it worked like a charm.

i hope this helps you, i know these instructions are a little long and drawn out but again as i said i getting old and this way if or when i forget how in installed it i'll know where i can find how to do it again.

---

### Post by simonkitch on 2005-06-03
[QUOTE=codejunkie]ok do sudo apt-get install nvidia-glx nvidia-settings linux-restricted-modules-k7 
and then change the nv back to nvidia in /etc/X11/xorg.conf[/QUOTE]
 Thanks for that codejunkie, I'v just switched to Ubuntu from fedora. The first thing I wanted to do was get My NVIDIA 6600gt running optimally. Nearlly went to the NVIDIA hompage an download the driver and did an sh NVIDIA... Thought I better check out the forums first and happened on this post. Spot on worked out of the box!

---

### Post by Vurdak829 on 2005-06-05
Uhm, i've tryed like suggested in this topic, but my nvidia 6600gt doesn't work yet.. only a black screen...:(

my log is here [http://iqd.altervista.org/Xorg.0.log.old](http://iqd.altervista.org/Xorg.0.log.old)

---

### Post by Paulus on 2005-06-05
**Thankyou** so much codejunkie!   Thanks to you my upgrade went as smooth as a babies bottom!  After following the coolbits guide @ Linux-gamers.net  I can finally overclock my Geforce FX!!!!!!   In my case underclock since i flashed my card to a fx5950u.   No more artifacts! 

thanks again, this should be a how-to

---

### Post by codejunkie on 2005-06-06
[QUOTE=Vurdak829]Uhm, i've tryed like suggested in this topic, but my nvidia 6600gt doesn't work yet.. only a black screen...:(

my log is here [http://iqd.altervista.org/Xorg.0.log.old](http://iqd.altervista.org/Xorg.0.log.old)[/QUOTE]

no logs there good man post it here and include your /etc/X11/xorg.conf file 
also post these specs.

version of ubuntu/kubuntu: warty,hoary,breezy
kernel version 
processor type 
amount of ram
computer manufacture/model number 
and i'll try and help you out.

---

### Post by Vurdak829 on 2005-06-06
[QUOTE=codejunkie]no logs there good man post it here and include your /etc/X11/xorg.conf file 
also post these specs.

version of ubuntu/kubuntu: warty,hoary,breezy
kernel version 
processor type 
amount of ram
computer manufacture/model number 
and i'll try and help you out.[/QUOTE]

Ok, sorry  :oops: 
My xorg log [http://phpfi.com/64715](http://phpfi.com/64715)
My xorg.conf [http://phpfi.com/64716](http://phpfi.com/64716) (i've commented many modules for testing but, once i've uncommented all of them, the result is the same)
I have ubuntu hoary x86
2.6.10.5-386
Amd64 3400+ (i still use a 386 system because there are too many thing that i can't hold up in a amd64 system :D)
1Gb of ram ddr
mother board: asus k8vse delux
video card ( :P ): asus geforce 6600gt
uhm..i hope someone can help me :(

---

### Post by codejunkie on 2005-06-06
[QUOTE=Vurdak829]Ok, sorry  :oops: 
My xorg log [http://phpfi.com/64715](http://phpfi.com/64715)
My xorg.conf [http://phpfi.com/64716](http://phpfi.com/64716) (i've commented many modules for testing but, once i've uncommented all of them, the result is the same)
I have ubuntu hoary x86
2.6.10.5-386
Amd64 3400+ (i still use a 386 system because there are too many thing that i can't hold up in a amd64 system :D)
1Gb of ram ddr
mother board: asus k8vse delux
video card ( :P ): asus geforce 6600gt
uhm..i hope someone can help me :([/QUOTE]

ok you used the Intel x86 install CD disk insted of AMD64 install CD disk right 
and your using the i386 kernel image you should be using the k7 kernel with the AMD64 because it's optimised for AMD cpu's and the i386 kernel doesn't support the 1gig of Ram it only see's around 700-900mb of it.first i would upgrade the kernel to the k7 kernel with 
sudo apt-get update and then
sudo apt-get install linux-image-k7 linux-k7 nvidia-glx nvidia-settings this will install the nvidia driver from ubuntu this should work but if your wanting the newest nvidia driver from [www.nvidia.com](www.nvidia.com) repeat the steps to install the nvidia driver that should work. as for the xorg.conf file the only thing you should have commented out is Load "dri" and Load "GLCore" so your xorg.conf file should look like this. 
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
#	Option          "NoLogo"
EndSection

Section "Monitor"
	Identifier	"FLATRON 775F"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"FLATRON 775F"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

hope this helps if your still having trouble just post your results and any other questions and i'll try and help the best i can.

---

### Post by Vurdak829 on 2005-06-06
Ok, i've tryed with the kernel optimized for k7, i've reinstalled nvidia drivers, but the result's are the same (i' ve used your xorg.conf too). The xorg log is the same. I think that is probably a xorg problem or a hardware problem..

---

### Post by codejunkie on 2005-06-06
did it work before you tried the steps to install nvidia driver or no x from the first time you installed at all?

---

### Post by codejunkie on 2005-06-06
also if you did a server install there is no gui installed by default you have to do 
sudo apt-get install ubuntu-desktop reboot the computer if you did a standard install you could also try sudo dpkg-reconfigure xserver-xorg on the first section choose either vesa or nv and reboot try them both if one doesn't work and just press enter on the other questions it sets things up the way they should be by default so there should be no reason to change them but it gives you the option to if you want.

---

### Post by Vurdak829 on 2005-06-06
[QUOTE=codejunkie]did it work before you tried the steps to install nvidia driver or no x from the first time you installed at all?[/QUOTE]

yeah, it worked. I've tryed reconfiguring xorg, but nothing..
I've tryed also with kernel 2.6.11, but the results are the same..

---

### Post by codejunkie on 2005-06-06
did you try the steps that i give you about changing the driver to vesa or nv

---

### Post by Vurdak829 on 2005-06-06
[QUOTE=codejunkie]did you try the steps that i give you about changing the driver to vesa or nv[/QUOTE]

i've tryed. Vesa doesn't work (xorg doesn't start) and i'm writing this (with nv) after a reboot.

---

### Post by codejunkie on 2005-06-06
if nv works then open synaptic and install the nvidia-glx nvidia-settings and the linux restricted modules then run nvidia-glx-config restart and you should be back working again. although it might not work with the 2.6.11 kernel package i've never tested it.

---

### Post by Vurdak829 on 2005-06-06
[QUOTE=codejunkie]if nv works then open synaptic and install the nvidia-glx nvidia-settings and the linux restricted modules then run nvidia-glx-config restart and you should be back working again. although it might not work with the 2.6.11 kernel package i've never tested it.[/QUOTE]

Nothing yet. Always the black screen :(
I'm thinking to try with another distro. Windows xp doesn't work on my pc, and fedora doesn't recognize the video card (it works only with vesa). I'm thinking about gentoo, but i will wait my exams..

---

### Post by codejunkie on 2005-06-06
if the nvidia drivers from  [www.nvidia.com](www.nvidia.com) installed completly and x would'nt start they might be conflicting with the ones installed through synaptic you could try one more thing open synaptic and click search type nvidia and under Look In: choose Description and Name and click search right click on everything there even if it's not checked if something is left behind mark for complete removal will come up choose it for everything that shows up listed then click apply this will completly remove everything now hit ctrl+alt+F1 and remove the nvidia drivers from [www.nvidia.com](www.nvidia.com) with sudo nvidia-installer --uninstall now reinstall nvidia-glx nvidia-settings and the linux-restricted-modules for your kernel through synaptic and  run sudo nvidia-glx-config enable other than that im out of ideas.

---

### Post by Vurdak829 on 2005-06-06
[QUOTE=codejunkie]if the nvidia drivers from  [www.nvidia.com](www.nvidia.com) installed completly and x would'nt start they might be conflicting with the ones installed through synaptic you could try one more thing open synaptic and click search type nvidia and under Look In: choose Description and Name and click search right click on everything there even if it's not checked if something is left behind mark for complete removal will come up choose it for everything that shows up listed then click apply this will completly remove everything now hit ctrl+alt+F1 and remove the nvidia drivers from [www.nvidia.com](www.nvidia.com) with sudo nvidia-installer --uninstall now reinstall nvidia-glx nvidia-settings and the linux-restricted-modules for your kernel through synaptic and  run sudo nvidia-glx-config enable other than that im out of ideas.[/QUOTE]

I've followed step by step what you've said, but still nothing..i'm sure that is an hardware problem..

---

### Post by codejunkie on 2005-06-06
just an afterthought if your still using the 2.6.11 kernel if so this is probaly what is causing all the headaches because there are no linux-restricted-modules package provide in synaptic for that kernel and this package provides the kernel module required for the nvidia driver to work  try using a standard kernel image like linux-image-2.6.10-5-k7.

---

### Post by Vurdak829 on 2005-06-06
[QUOTE=codejunkie]sorry i could'nt help but i tried.[/QUOTE]

However, 1000 thanks :)

---

### Post by Vurdak829 on 2005-06-06
[QUOTE=codejunkie]just an afterthought if your still using the 2.6.11 kernel if so this is probaly what is causing all the headaches because there are no linux-restricted-modules package provide in synaptic for that kernel and this package provides the kernel module required for the nvidia driver to work  try using a standard kernel image like linux-image-2.6.10-5-k7.[/QUOTE]

All the tests were doing with 2.6.10.5-k7. I've removed 2.6.11 after the first try.

---

### Post by codejunkie on 2005-06-06
well again sorry i haven't been much help here but i searched that card of yours in the forum and some people said they get better frame rates and stability using the nv driver insted of nvidia could be the reason.

---

### Post by Vurdak829 on 2005-06-06
[QUOTE=codejunkie]well again sorry i haven't been much help here but i searched that card of yours in the forum and some people said they get better frame rates and stability using the nv driver insted of nvidia could be the reason.[/QUOTE]

Ok, but with nv i can't use hw acceleration. If i try to use hw acceleration with xorg and nv, the problems are the same..

---

### Post by Vurdak829 on 2005-06-07
Now i'm using fedora core 4, and nvidia drivers work properly..
It may be a kernel problem on ubuntu..

---

### Post by suoko on 2005-06-07
Hi,
I have some problems with offcial nvidia drivers too.
Ubuntu deb drivers works correctly with my geforce 256 but the official ones don't.

I have installed :
linux-headers-2.6.10-5
linux-headers-2.6.10-5-k7
linux-image2.6.10-5-k7
linux-patch-ubuntu-2.6.10
linux-source-2.6.10
linux-tree-2.6.10

and uninstalled nvidia related packages.

Trying to install official nvidia drivers running the script as it is, it DOES create the module nvidia.ko but then it fails saying: 
"ERROR: Unable to load the kernel module 'nvidia.ko'.  This is most likely
       because the kernel module was built using the wrong kernel source files.
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option."

So I tried to specify the kernel source path after I decompressed the kernel source /usr/src/linux-source-2.6.10.tar.bz2.
I ran the script this way:
 ./NVIDIA-Linux-x86-1.0-7664-pkg1.run --kernel-source-parh=/usr/src/linux-source-2.6.10

This time the script didn't even create the module and failed saying:
"ERROR: If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.
       
       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the equivalent nvidia-installer command line option.
       
       Depending on where and how the kernel sources (or the
       kernel headers) were installed, you may need to specify
       their location with the SYSSRC environment variable or
       the equivalent nvidia-installer command line option."

---

### Post by codejunkie on 2005-06-07
[QUOTE=suoko]Hi,
I have some problems with offcial nvidia drivers too.
Ubuntu deb drivers works correctly with my geforce 256 but the official ones don't.

I have installed :
linux-headers-2.6.10-5
linux-headers-2.6.10-5-k7
linux-image2.6.10-5-k7
linux-patch-ubuntu-2.6.10
linux-source-2.6.10
linux-tree-2.6.10

and uninstalled nvidia related packages.

Trying to install official nvidia drivers running the script as it is, it DOES create the module nvidia.ko but then it fails saying: 
"ERROR: Unable to load the kernel module 'nvidia.ko'.  This is most likely
       because the kernel module was built using the wrong kernel source files.
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option."

So I tried to specify the kernel source path after I decompressed the kernel source /usr/src/linux-source-2.6.10.tar.bz2.
I ran the script this way:
 ./NVIDIA-Linux-x86-1.0-7664-pkg1.run --kernel-source-parh=/usr/src/linux-source-2.6.10

This time the script didn't even create the module and failed saying:
"ERROR: If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.
       
       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the equivalent nvidia-installer command line option.
       
       Depending on where and how the kernel sources (or the
       kernel headers) were installed, you may need to specify
       their location with the SYSSRC environment variable or
       the equivalent nvidia-installer command line option."[/QUOTE]

these errors usually mean you don't  have the correct linux-headers package for the kernel your using but you said you've installed them have you also installed the build-essential package this might help.

---

### Post by suoko on 2005-06-08
[QUOTE=codejunkie]these errors usually mean you don't  have the correct linux-headers package for the kernel your using but you said you've installed them have you also installed the build-essential package this might help.[/QUOTE]


Was it a question?
If so, yes: I ran "sudo apt-get install build-essential" too

---

### Post by wylfing on 2005-06-08
This error appears whenever the nvidia installer can't load the nvidia module. There are two reasons why this could happen, and the error message only describes one of them. Reason #1: wrong kernel source (this is what the error message says). Reason #2: the nvidia module is already loaded.

To check the 2nd one, type ```
sudo lsmod | grep nvidia
``` If you see nvidia, nvidia-agp, nvagp, or agpgart you should remove them before running the nvidia installer. You will have to use ```
sudo rmmod -f [module]
``` for some of them because they will not go quietly. You MUST stop X first (e.g., 'sudo killall gdm') or you will get a hard lock up.

After you've unloaded all those modules, try running the official nvidia installer again.

---

### Post by DFreeze on 2005-06-10
Hi all,

Sorry to bump into the conversation like this, but I have a similar setup and some questions, so here goes:

I installed Ubuntu, did some tweaks, installed some apps, got Nvidia working. But now I have upgraded to the k7 kernel. Should I reinstall the Nvidia drivers after the kernel upgrade, or does that have nothing to do with it? Reason I ask is because X seems to freeze more often than before the upgrade.

offtopic: are any of the apps kernel specific? I installed quite a few, before upgrading . Do I have to reinstall any of them?

---

### Post by wylfing on 2005-06-10
If there is a conflict between the nvidia driver and the kernel, the kernel won't allow the driver to be loaded and X won't even start.

[edit]
No, you don't have to reinstall your applications.

---

