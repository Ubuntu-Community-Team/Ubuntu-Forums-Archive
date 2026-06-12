---
title: "[SOLVED] Ibex: screen resolution problem only to 640x480"
date: 2008-12-05
forum: General Help
---

### Post by abcuser on 2008-12-05
Hi,
using Ubuntu Ibex I can only use 640x480 screen resolution from System | Preferences | Screen Resolution.

I have a dual boot with Windows XP sp3 where I can have screen resolution 800x600, 1024x768, 1152x864, 1280x600, 1280x720, 1280x768, 1280x960 or 1280x1024 without any problem. So my monitor and graphic card is not a problem.

lscpi outputs:
```

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)

```

xrandr outputs:
```

Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480         0.0* 

```

What should I do to fix screen resolution? By the way on hardy I had no screen resolution problem with this PC.

Thanks

---

### Post by dexter on 2008-12-05
What driver are you using for you graphic card?

---

### Post by abcuser on 2008-12-06
Hi,
I never had any problem with drivers on Ubuntu, so I just don't know how to check which graphic driver is installed. Can you please help me out how to check which graphic driver I have?

One more important think, during install Ubuntu 8.10 has frozen, black screen. It looks like there was some graphic driver that my PC didn't like. So I repeated installation but this time I pressed <F4> key at first install window and selected "safe graphic mode" from drop down menu. If I understand correctly now some default vesa graphic card is selected. Here is my /etc/X11/xorg.conf file if this helps:
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```
Thanks a lot,
Abcuser

---

### Post by abcuser on 2008-12-06
Hi,
I have started Windows XP (I have dual boot with Ubuntu) and there is the following intel graphic card driver installed:
[img]http://www.shrani.si/f/2b/vE/1QxaPMGq/intel.png[/img]

I searched for Linux driver and got web page: [http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=865&DwnldID=8203&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=865&DwnldID=8203&lang=eng)
I downloaded tar file. I untared it and execute "sudo ./install". I entered info 1 for "install driver" and pressed Enter.

I got the following error on screen:
```

The script will now compile the agpgart module and DRM kernel modules
for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

```
And in dri.log file there are the following messages:
```

make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/abcuser/g/dripkg/agpgart-2.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/abcuser/g/dripkg/agpgart-2.0/backend.o
/home/abcuser/g/dripkg/agpgart-2.0/backend.c:68: error: conflicting types for &#8216;agp_backend_acquire&#8217;
include/linux/agp_backend.h:105: error: previous declaration of &#8216;agp_backend_acquire&#8217; was here
/home/abcuser/g/dripkg/agpgart-2.0/backend.c:77: error: conflicting types for &#8216;agp_backend_acquire&#8217;
include/linux/agp_backend.h:105: error: previous declaration of &#8216;agp_backend_acquire&#8217; was here
/home/abcuser/g/dripkg/agpgart-2.0/backend.c:88: error: conflicting types for &#8216;agp_backend_release&#8217;
include/linux/agp_backend.h:106: error: previous declaration of &#8216;agp_backend_release&#8217; was here
/home/abcuser/g/dripkg/agpgart-2.0/backend.c:93: error: conflicting types for &#8216;agp_backend_release&#8217;
include/linux/agp_backend.h:106: error: previous declaration of &#8216;agp_backend_release&#8217; was here
/home/abcuser/g/dripkg/agpgart-2.0/backend.c:220: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;drm_agp&#8217;
/home/abcuser/g/dripkg/agpgart-2.0/backend.c: In function &#8216;agp_add_bridge&#8217;:
/home/abcuser/g/dripkg/agpgart-2.0/backend.c:281: error: implicit declaration of function &#8216;inter_module_register&#8217;
/home/abcuser/g/dripkg/agpgart-2.0/backend.c:281: error: &#8216;drm_agp&#8217; undeclared (first use in this function)
/home/abcuser/g/dripkg/agpgart-2.0/backend.c:281: error: (Each undeclared identifier is reported only once
/home/abcuser/g/dripkg/agpgart-2.0/backend.c:281: error: for each function it appears in.)
/home/abcuser/g/dripkg/agpgart-2.0/backend.c: In function &#8216;agp_remove_bridge&#8217;:
/home/abcuser/g/dripkg/agpgart-2.0/backend.c:301: error: implicit declaration of function &#8216;inter_module_unregister&#8217;
make[2]: *** [/home/abcuser/g/dripkg/agpgart-2.0/backend.o] Error 1
make[1]: *** [_module_/home/abcuser/g/dripkg/agpgart-2.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [default] Error 2
make -f Makefile.linux DRM_MODULES=gdg.ko modules
make[1]: Entering directory `/home/abcuser/g/dripkg/drm'
make -C /lib/modules/2.6.27-9-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
rm: cannot remove `/home/abcuser/g/dripkg/drm/.tmp_versions/CVS': Is a directory
make[2]: *** [crmodverdir] Error 1
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/abcuser/g/dripkg/drm'
make: *** [gdg.ko] Error 2

```

I have look into install.sh script and see there is awk command used by script, so I aslo installed awk support: sudo apt-get install gawk

But all this errors are just to geeky for me. But it looks like I need some kind of software before installing graphic driver, is it? What should I do?

Regards

---

### Post by abcuser on 2008-12-06
Hi,
I have found out solution! Settings must be set in BIOS for video driver to use 8 MB of shared memory instead of just 1 MB as set as default.

In my BIOS is the following settings: Devices | Video setup | Shared system memory is set to 1024K. Help info for this settings is: "Select how much system memory to use for video when the built-in video device is in use." From drop down menu I changed settings from 1014K to 8192K, saved settings in BIOS and started Ubuntu.

Ubuntu: System | Preferences | Screen Resolution | Resolution drop down menu now has the following options: 640x480, 800x600, 1024x768, 1280x1024. I have selected 1024x768 and my screen resolution problem is solved.

Regards,
Abcuser

---

