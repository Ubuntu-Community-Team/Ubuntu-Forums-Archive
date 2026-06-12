---
title: "Issues with ATI drivers"
date: 2011-01-22
forum: Desktop Environments
---

### Post by Hellburn on 2011-01-22
Hello everyone :)

Recently I had to format my hard drive (and change my second OS - win xp 32bit to win 7 64bit). Then I installed both systems: Firstly win 7 and then ubuntu 10.04 32bit.

The problem is I can't turn on the visual effects on my ubuntu. Also I get something like [-=this=-]("http://img98.imageshack.us/img98/870/img2941z.jpg") when ubuntu starts and shutdowns (instead of [-=this=-]("http://pl.wikibooks.org/wiki/Plik:Ubuntu_instal0.png")). Here's a [-=quick video=-]("http://www.mediafire.com/?nasbmar8hi840m4") how this looks.

I tried to install ATI drivers. If I install the older ones I can't set the high resolutions (1024x768 and higher).
If I install the newest ATI drivers (it doesn't matter how i do it - manually or automaticaly) ubuntu freezes in [-=loading screen=-]("http://pl.wikibooks.org/wiki/Plik:Ubuntu_instal0.png") when all of the dots are red.

It's weird because before the format everything worked just fine with ATI drivers (same ubuntu 10.04 32 bit).

My computer:
AMD Athlon 3200+
4 gb ram DDR2
HIS Radeon HD 4670 512 DDR3
Samsung SyncMaster 2233 21,5'

Win 7 ultimate 64bit
Ubuntu 10.04 32bit (polish version from ubuntu.pl) EDIT: Currently 10.10

Looking forward for any solutions.
~hell

---

### Post by Krytarik on 2011-01-23
Great support by media!;)

What do you mean with "old" drivers?
How do you install the current one?

I would always try first to install the proprietary driver via "System -> Administration -> Hardware Drivers".

Check this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

Greetings.

---

### Post by Hellburn on 2011-01-23
1. Old drivers
The latest version is 10.11. My ubuntu freezes at startup after installing 10.4 or newer versions.
After installing 10.3 or older, can't set the high resolutions.

2. Installation:
I've tried to install it manually (download from ATI driver site, unpack, install). Also tried to install with [these instructions]("http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide").
Tried via "System -> Administration -> Hardware Drivers".
Result is the same.

There must be a solution :(. Please help me :(.

---

### Post by Krytarik on 2011-01-23
No panic, we will manage it.;)

First check how your system works with the default open source driver, by  removing/renaming the file /etc/X11/xorg.conf, if there is such, and leave it this way temporarily.

Then remove the driver installed via "Hardware Drivers".

Then try to remove any remnants of the manual install, look into the install instructions therefore, it may be not really possible to remove those drivers a clean way.

Then try to install the driver via "Hardware Drivers" again.

Did you try the PPA of Ubuntu-X-Swat?
If so, then disable it before in "System -> Administration -> Software Sources".

---

### Post by Hellburn on 2011-01-24
Currently I reinstalled Ubuntu and did not install any ATI graphic drivers.
Visual effects don't work and, for example, I have problems when watching youtube videos on 1080p (video freezes, but I can hear sounds). Similar problems with Cheese (the webcam problem), and Skype.

---

### Post by Claus7 on 2011-01-24
Hello,

> **Hellburn said:**
> Currently I reinstalled Ubuntu and did not install any ATI graphic drivers.
Visual effects don't work and, for example, I have problems when watching youtube videos on 1080p (video freezes, but I can hear sounds). Similar problems with Cheese (the webcam problem), and Skype.

I do not think that you will be able to use any visual effects unless you install the drivers either from synaptic or from ati's website. Just to point out that this might not help you either if you do not configure a xorg.conf file that will be descent enough.

I will provide you mine and the process I took in order to install all the necessary packages. Have in mind that you have a different card, so you have to make the necessary changes. Also this has to do with the screen resolution.

[http://ubuntuforums.org/showthread.php?t=1419962&page=2](http://ubuntuforums.org/showthread.php?t=1419962&page=2)

Regards!

PS: I do not think that you will manage to see videos on 1080p via flash, especially on full screen, yet if things go well, you should be able to download them and see them in such resolution with another program (e.g. mplayer).

---

### Post by Krytarik on 2011-01-24
Then try to install the proprietary driver via "Hardware Drivers", or "Additional Drivers", if you installed 10.10 now.

Claus7 may be right regarding general performance issue of fullscreen-flash, it's not as good as under Windows. You may try this guide after you got the proprietary driver working:
[http://ubuntuforums.org/showthread.php?t=1645908](http://ubuntuforums.org/showthread.php?t=1645908)

---

### Post by Hellburn on 2011-01-25
I've updated my ubuntu to 10.10 and then tried to install ATI drivers via "Additional Drivers".

I got this message: "Couldn't install driver. See var/log/jockey.log for more informations."

Here's a log:
```
2011-01-25 18:52:32,881 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-25 18:52:32,972 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-25 18:52:33,038 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-25 18:52:34,999 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-25 18:52:39,870 DEBUG: Installing package: linux-headers-2.6.32-27-generic-pae
2011-01-25 18:52:40,266 DEBUG: Package linux-headers-2.6.32-27-generic-pae does not exist, aborting
2011-01-25 18:52:40,704 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-01-25 18:52:40,704 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2011-01-25 18:52:40,705 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-01-25 18:53:11,407 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-25 18:53:11,435 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-25 18:53:17,488 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-25 18:53:17,503 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-25 18:53:17,544 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-25 18:53:17,559 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-25 18:53:17,622 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-25 18:53:17,636 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
```

Now I can see loading screen (ubuntu and those 5 dots) but still can't turn on visual effects. :(

---

### Post by Krytarik on 2011-01-25
Check in Synaptic if the "fglrx" driver is already installed. If so, "completely remove" it, and install it again. If not, simply install it.

---

### Post by Claus7 on 2011-01-26
Hello,

> **Hellburn said:**
> I've updated my ubuntu to 10.10 and then tried to install ATI drivers via "Additional Drivers".

I got this message: "Couldn't install driver. See var/log/jockey.log for more informations."

Here's a log:
```
2011-01-25 18:52:32,881 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-25 18:52:32,972 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-25 18:52:33,038 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-25 18:52:34,999 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-25 18:52:39,870 DEBUG: Installing package: linux-headers-2.6.32-27-generic-pae
2011-01-25 18:52:40,266 DEBUG: Package linux-headers-2.6.32-27-generic-**pae** does not exist, aborting
2011-01-25 18:52:40,704 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-01-25 18:52:40,704 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2011-01-25 18:52:40,705 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-01-25 18:53:11,407 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-25 18:53:11,435 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-25 18:53:17,488 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-25 18:53:17,503 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-25 18:53:17,544 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-25 18:53:17,559 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-25 18:53:17,622 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-25 18:53:17,636 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
```

Now I can see loading screen (ubuntu and those 5 dots) but still can't turn on visual effects. :(

...pae... why did you install this kernel in the first place? Also I hope that you did not just copy paste my xorg.conf since we do not have the same graphics drivers...

could you type:
uname -a 
just to see which kernel you've got? Unfortunately I do not have experience with pae kernels... Also do as *Krytarik* proposed, after you have ensured that you have the right kernel... 

Since things, even like that, are getting better, soon you'll find a solution.

Regards!

---

### Post by realzippy on 2011-01-26
*pae... why did you install this kernel in the first place?*

..afaik pae kernel nowadays is installed automatically on Ubuntu 32 bit when more than 3.5 Gb RAM
available...

---

### Post by Claus7 on 2011-01-26
Hello,

> **realzippy said:**
> *pae... why did you install this kernel in the first place?*

..afaik pae kernel nowadays is installed automatically when more than 3.5 Gb RAM
available...

I have more than 3.5 GB of ram and 64 bit 10.10. What I get from uname -r is:
2.6.35-24-generic

I just point out this, cause using the forums I saw that is used under special cases and causes some different handling concerning drivers e.t.c.. Yet, as I said before, I'm not an expert on pae kernels.

Regards!

---

### Post by Hellburn on 2011-01-26
Claus7:
Ubuntu installed pae automatically, I think. And I didn't copy your xorg.conf.
```
uname -a
Linux starclite-desktop 2.6.32-27-generic-pae #49-Ubuntu SMP Thu Dec 2 00:07:52 UTC 2010 i686 GNU/Linux

```

Krytarik:
I followed your instructions, but still can't install those ATI drivers... :(
Here's a jockey.log:
```
2011-01-26 13:28:51,864 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c>
2011-01-26 13:28:51,866 DEBUG: reading modalias file /lib/modules/2.6.32-27-generic-pae/modules.alias
2011-01-26 13:28:52,144 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-01-26 13:28:52,154 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2011-01-26 13:28:52,162 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-01-26 13:28:52,220 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2011-01-26 13:28:52,227 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2011-01-26 13:28:52,251 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2011-01-26 13:28:52,254 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2011-01-26 13:28:52,262 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-01-26 13:28:52,681 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-01-26 13:28:52,746 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-01-26 13:28:52,747 DEBUG: Firmware for DVB cards not available
2011-01-26 13:28:52,747 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-01-26 13:28:52,761 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-01-26 13:28:52,806 DEBUG: Software modem not available
2011-01-26 13:28:52,806 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2011-01-26 13:28:52,839 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2011-01-26 13:28:52,839 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2011-01-26 13:28:52,871 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2011-01-26 13:28:52,872 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2011-01-26 13:28:52,872 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-01-26 13:28:52,878 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-01-26 13:28:52,878 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-01-26 13:28:52,879 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-01-26 13:28:52,879 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-01-26 13:28:52,904 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-01-26 13:28:52,904 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-01-26 13:28:52,920 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-01-26 13:28:52,924 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-01-26 13:28:52,925 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-01-26 13:28:52,939 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-01-26 13:28:52,939 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-01-26 13:28:52,962 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-01-26 13:28:52,963 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-01-26 13:28:52,976 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-01-26 13:28:52,977 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-01-26 13:28:52,983 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-01-26 13:28:52,996 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-01-26 13:28:52,997 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-01-26 13:28:52,997 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-01-26 13:28:53,003 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-01-26 13:28:53,004 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-01-26 13:28:53,018 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-01-26 13:28:53,019 DEBUG: all custom handlers loaded
2011-01-26 13:28:53,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001787sd0000AA38bc04sc03i00')
2011-01-26 13:28:53,635 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-01-26 13:28:53,635 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-01-26 13:28:53,635 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2011-01-26 13:28:53,657 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2011-01-26 13:28:53,658 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-01-26 13:28:53,658 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-01-26 13:28:53,658 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'pci:v00001002d00004380sv00001458sd0000B002bc01sc06i01')
2011-01-26 13:28:53,664 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-01-26 13:28:53,664 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-01-26 13:28:53,664 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'platform:pcspkr')
2011-01-26 13:28:53,665 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-01-26 13:28:53,665 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-01-26 13:28:53,665 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-01-26 13:28:53,696 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2011-01-26 13:28:53,697 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k8temp', 'jockey_handler': 'KernelModuleHandler'}
2011-01-26 13:28:53,697 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-01-26 13:28:53,701 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-26 13:28:53,701 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-01-26 13:28:53,701 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'platform:eisa')
2011-01-26 13:28:53,702 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001458sd0000A002bc04sc03i00')
2011-01-26 13:28:53,707 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-01-26 13:28:53,707 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-01-26 13:28:53,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-01-26 13:28:53,708 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2011-01-26 13:28:53,708 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'pci:v00001002d00007910sv00001458sd00005000bc06sc00i00')
2011-01-26 13:28:53,714 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ati_agp', 'jockey_handler': 'KernelModuleHandler'}
2011-01-26 13:28:53,714 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-01-26 13:28:53,714 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-01-26 13:28:53,714 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'pci:v00001002d00009490sv00001787sd00002003bc03sc00i00')
2011-01-26 13:28:53,720 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-01-26 13:28:53,724 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-01-26 13:28:53,739 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-26 13:28:53,724 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-01-26 13:28:53,739 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2011-01-26 13:28:53,739 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'acpi:device:')
2011-01-26 13:28:53,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-01-26 13:28:53,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'acpi:PNP0501:')
2011-01-26 13:28:53,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'acpi:PNP0400:')
2011-01-26 13:28:53,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-01-26 13:28:53,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'pci:v000010ECd00008167sv00001458sd0000E000bc02sc00i00')
2011-01-26 13:28:53,750 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-01-26 13:28:53,750 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'input:b0001v10ECp0888e0001-e0,12,kramls1,2,fw')
2011-01-26 13:28:53,750 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-26 13:28:53,750 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-01-26 13:28:53,750 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-26 13:28:53,751 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-01-26 13:28:53,751 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF5:bd07/27/2007:svn:pn:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnGA-MA69VM-S2:rvrx.x:cvn:ct3:cvr:')
2011-01-26 13:28:53,767 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-01-26 13:28:53,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'usb:v041Ep4052d0100dc00dsc00dp00icFFisc00ip00')
2011-01-26 13:28:53,794 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'gspca_ov519', 'jockey_handler': 'KernelModuleHandler'}
2011-01-26 13:28:53,795 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-01-26 13:28:53,795 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-01-26 13:28:53,795 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-01-26 13:28:53,795 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'pci:v00001102d00000007sv00001102sd0000100Abc04sc01i00')
2011-01-26 13:28:53,803 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_ca0106', 'jockey_handler': 'KernelModuleHandler'}
2011-01-26 13:28:53,803 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'pci:v00001002d00004386sv00001458sd00005004bc0Csc03i20')
2011-01-26 13:28:53,809 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-01-26 13:28:53,814 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'pci:v00001002d00004385sv00001458sd00004385bc0Csc05i00')
2011-01-26 13:28:53,819 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2011-01-26 13:28:53,820 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-01-26 13:28:53,820 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-26 13:28:53,820 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-01-26 13:28:53,820 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'pci:v00001002d0000438Csv00001458sd00005002bc01sc01i8a')
2011-01-26 13:28:53,825 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2011-01-26 13:28:53,826 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-01-26 13:28:53,841 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-01-26 13:28:53,841 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-01-26 13:28:53,841 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'pci:v00001002d0000438Dsv00001458sd00005001bc06sc01i00')
2011-01-26 13:28:53,846 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'input:b0011v0002p0006e0000-e0,1,2,k110,111,112,113,114,r0,1,6,8,amlsfw')
2011-01-26 13:28:53,847 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-26 13:28:53,847 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95e102c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-01-26 13:28:53,847 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001787sd0000AA38bc04sc03i00')
2011-01-26 13:28:53,847 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2011-01-26 13:28:53,847 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2011-01-26 13:28:53,847 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-01-26 13:28:53,847 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-01-26 13:28:53,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'pci:v00001002d00004380sv00001458sd0000B002bc01sc06i01')
2011-01-26 13:28:53,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'platform:pcspkr')
2011-01-26 13:28:53,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-01-26 13:28:53,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2011-01-26 13:28:53,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-01-26 13:28:53,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-01-26 13:28:53,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'platform:eisa')
2011-01-26 13:28:53,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001458sd0000A002bc04sc03i00')
2011-01-26 13:28:53,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-01-26 13:28:53,849 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2011-01-26 13:28:53,849 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'pci:v00001002d00007910sv00001458sd00005000bc06sc00i00')
2011-01-26 13:28:53,849 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-01-26 13:28:53,849 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-01-26 13:28:53,849 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'pci:v00001002d00009490sv00001787sd00002003bc03sc00i00')
2011-01-26 13:28:53,849 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'acpi:device:')
2011-01-26 13:28:53,849 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-01-26 13:28:53,849 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'acpi:PNP0501:')
2011-01-26 13:28:53,850 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'acpi:PNP0400:')
2011-01-26 13:28:53,850 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-01-26 13:28:53,850 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'pci:v000010ECd00008167sv00001458sd0000E000bc02sc00i00')
2011-01-26 13:28:53,850 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'input:b0001v10ECp0888e0001-e0,12,kramls1,2,fw')
2011-01-26 13:28:53,850 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-01-26 13:28:53,850 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-01-26 13:28:53,850 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF5:bd07/27/2007:svn:pn:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnGA-MA69VM-S2:rvrx.x:cvn:ct3:cvr:')
2011-01-26 13:28:53,850 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-01-26 13:28:53,850 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'usb:v041Ep4052d0100dc00dsc00dp00icFFisc00ip00')
2011-01-26 13:28:53,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-01-26 13:28:53,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-01-26 13:28:53,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-01-26 13:28:53,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'pci:v00001102d00000007sv00001102sd0000100Abc04sc01i00')
2011-01-26 13:28:53,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'pci:v00001002d00004386sv00001458sd00005004bc0Csc03i20')
2011-01-26 13:28:53,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-01-26 13:28:53,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'pci:v00001002d00004385sv00001458sd00004385bc0Csc05i00')
2011-01-26 13:28:53,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-01-26 13:28:53,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-01-26 13:28:53,852 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'pci:v00001002d0000438Csv00001458sd00005002bc01sc01i8a')
2011-01-26 13:28:53,852 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-01-26 13:28:53,852 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'pci:v00001002d0000438Dsv00001458sd00005001bc06sc01i00')
2011-01-26 13:28:53,852 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'input:b0011v0002p0006e0000-e0,1,2,k110,111,112,113,114,r0,1,6,8,amlsfw')
2011-01-26 13:28:53,852 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9833f2c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-01-26 13:28:53,945 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-26 13:28:54,071 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-26 13:28:54,138 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-26 13:28:56,011 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-26 13:29:00,496 DEBUG: Installing package: linux-headers-2.6.32-27-generic-pae
2011-01-26 13:29:00,947 DEBUG: Package linux-headers-2.6.32-27-generic-pae does not exist, aborting
2011-01-26 13:29:01,383 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-01-26 13:29:01,383 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2011-01-26 13:29:01,383 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-01-26 13:29:18,405 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-26 13:29:18,421 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-26 13:29:42,282 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-26 13:29:42,298 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-26 13:29:42,342 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-26 13:29:42,358 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-26 13:29:42,423 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-26 13:29:42,438 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-01-26 13:29:44,644 DEBUG: Shutting down
```

---

### Post by realzippy on 2011-01-26
..from jockey:

2011-01-26 13:29:00,496 DEBUG: Installing package: linux-headers-2.6.32-27-generic-pae
2011-01-26 13:29:00,947 DEBUG: [COLOR="Red"]Package linux-headers-2.6.32-27-generic-pae does not exist[/COLOR], aborting
2011-01-26 13:29:01,383 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx



...strange.if you had 64bit ubuntu you would not have a pae kernel (as your uname -r claims..)
Anyway,try to install it manually:

[http://packages.ubuntu.com/lucid/i386/linux-headers-2.6.32-27-generic-pae/download](http://packages.ubuntu.com/lucid/i386/linux-headers-2.6.32-27-generic-pae/download)

If you really have 64 bit,it will say "wrong architecture"..

---

### Post by Krytarik on 2011-01-26
> **realzippy said:**
> *pae... why did you install this kernel in the first place?*

..afaik pae kernel nowadays is installed automatically **on Ubuntu 32 bit** when more than 3.5 Gb RAM
available...
@Claus7: Why did you just remove the most important part of realzippy's answer?

And I don't anywhere that Hellburn ;-) has the 64bit version of Ubuntu running. Search for the package in Synaptic, if it's not installed, do it. It believe, it's not installed by default, but should get installed by the driver jockey automatically, since I hadn't to install it manually.

After that try to install the driver again.

---

### Post by realzippy on 2011-01-26
OFFTOPIC:

@krytarik

Claus7 quoted me before I edited my post....

---

### Post by Krytarik on 2011-01-26
> **realzippy said:**
> OFFTOPIC:

@krytarik

Claus7 quoted me before I edited my post....
Oh, that makes sense then. That's obviously the downside of editing a post subsequently, either the other participants don't notice the edit or it's just not traceable.;)

---

### Post by Hellburn on 2011-01-27
Okay.
Firstly, after updating my 10.04 32bit to 10.10 ??bit I see 2 positions of ubuntu kernels on my grub:

2.6.35-24-generic-pae - ATI drivers are INSTALLED but I can't set 16:9 and 16:10 resolutions. Also I can't enter Catalyst Control Center because it was installed incorrectly or something like that.

2.6.35-27-generic-pae - ATI drivers are NOT INSTALLED and I can't set resolutions and CAN'T install ATI drivers.

[http://packages.ubuntu.com/lucid/i386/linux-headers-2.6.32-27-generic-pae/download](http://packages.ubuntu.com/lucid/i386/linux-headers-2.6.32-27-generic-pae/download)

I tried to install this: [http://packages.ubuntu.com/lucid/i386/linux-headers-2.6.32-27-generic-pae/download](http://packages.ubuntu.com/lucid/i386/linux-headers-2.6.32-27-generic-pae/download)
but I just can't click "install" button. This is crazy if you ask me :P.

I don't even know if my ubuntu was updated from 32bit to 64bit (is it possible?).

---

### Post by Krytarik on 2011-01-27
> **Hellburn said:**
> 
I don't even know if my ubuntu was updated from 32bit to 64bit (is it possible?).
I don't believe that it's possible. Neither do I believe that you have a 64-bit Ubuntu running, since the missing package isn't even available as 64bit-version, and it also wouldn't make sense:
[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

And you've already checked it by running "uname -a":
```
Linux starclite-desktop **2.6.32-27-generic-pae** #49-Ubuntu SMP Thu Dec 2 00:07:52 UTC 2010 i686 GNU/Linux
```
Otherwise it would say "2.6.32-27-amd64", I believe.

So, to install the header package, as I said earlier, search for it in Synaptic and install it from there. Then try again to install the "fglrx" driver, either also with Synaptic, or via "Additional Drivers"

---

### Post by Hellburn on 2011-01-28
1. Theres no linux-headers-2.6.32-27-generic-pae package in synaptic.
2. I can't install this package manually.
3. On -24 headers package -24 was already installed, but still couldn't install ATI drivers. I installed -25 (and removed -24), THEN installed ATI drivers.
Result? Ubuntu freezes at startup (loading screen)
4. Ubuntu -27 still works. I CAN enter CCC but CAN'T turn on visual effects.

5. Which one (-24 or -27) should I use?

This is going weirder and werider...

---

### Post by Krytarik on 2011-01-28
I believe I got now, what's really going on at your machine.

- You have the kernel "2.6.32-27-generic-pae" installed, those is a remnant of Ubuntu 10.04, thus you don't get the respective header package. Leave those kernel alone, but don't remove it as long as you don't get Ubuntu working with a kernel provided for Ubuntu 10.10.

- You have the kernel "2.6.35-24-generic-pae" installed, those is indeed a kernel provided for Ubuntu 10.10.

Upgrade to the latest kernel provided for Ubuntu 10.10:
```
sudo apt-get update
sudo apt-get upgrade
```Then try again to install the video driver via "System -> Administration -> Additional Drivers".

If that again results in a freezing boot screen, try upgrading to the driver packages provided by Ubuntu-X-Swat:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```To get to the console when the boot fails, choose "recovery mode" at the boot menu, then either choose "normal boot" or even "root shell prompt".

---

### Post by Claus7 on 2011-01-28
Hello,

recapitulation:

1) you had a 32 bit ubu box with lucid on, which you wanted to upgrade to maverick. There is no way that you upgraded to a 64 bit machine, since your original was a 32, unless you made some tweaking, which is not the case.

2) the pae kernel you see is because you have more than 3.5 GB memory and, as it is already pointed out, in order to harness its full capacity, ubu makes it as the default kernel installed for 32 bit processor architectures.

3) since you wan to enable visual effects you have to ensure the following:
you have a clean install of drivers on your ubu box, which do not conflict **by any means** with previous installations and faulty attempts. It would be better if your system was up to date, so the commands provided by *Krytarik* is all you need to do. If there are errors during the update you will be able to notice them from there.

(Also  *Krytarik* pointed out correctly the type of kernels you got. So, you are focusing on the 10.10 kernel, since this is what you want to do)

5) After you have made a full update of your system and you have removed duplicate kernels from synaptic (stick with one now and install those recommended from there, which is the normal procedure) then

6) remove everything that has to do with nvidia or ati drivers on your system and reboot.

7) while rebooting, if you want full harnessing of your card now, you have to install the proprietary drivers. It might be, that your card is working nicely with just the open source ones, yet since you want visual effects and the like, the proprietary ones are recommended.

Now for this you have the option of amd web site and synaptic. I would go for the latter, as every time there is a kernel update, you are not required to reinstall the drivers of your card.

So, consult the link I have provided you and install those necessary packages for your system.

7) Reboot. Then check as *Krytarik* proposes, if the driver is enabled and if not, enable it. Reboot again (don't worry, if done correctly once, you should not worry about it any more).

8) If things are ok, then you should be able to use CCC and whatever you like. If it's not and you are getting low screen resolution and the like, then you have to edit your xorg.conf file, find under /etc/X11...

Here is the tricky part. The tweaking has to be done via command line mode (mostly) by trial and error. The one I provide is a nice starting point.

Normally, if you follow these steps, your system will work ok, yet you have to do them all one by one. I do not have a personal experience on your card, so it might be that is not working fully with maverick, just give you my steps on a similar card in 10.10.

Regards!

---

### Post by Hellburn on 2011-01-28
I got really pissed of and done these things:
1. Reinstalled Ubuntu (format /, /boot, /home).
2. Updated Ubuntu 10.04 to 10.10 immediately after instalation.
3. Wrote in concole:
```
sudo apt-get update
sudo apt-get upgrade
```
4. Installed ATI drivers. - loading screen freezes.
5. Gone to the recovery mode and wrote:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```
No errors. Reboot.
6. Loading screen still is freezing.

What to do now?

---

### Post by Claus7 on 2011-01-28
Hello,

first of try to be patient as being out of temper does not help.

Now, why do you reinstall in order to upgrade. Why don't you burn a fresh new iso of ubu 10.10? This would be much much better and will save you from probable headaches.

So, if you try a fresh new installation do it directly from a maverick cd.

Can you see any error logs while you are trying to boot? Can you access your Desktop via recovery mode?

Also, where you able to have visual effects from your lucid installation?

Where exactly does your system freeze? While you are giving your password? Before? 

Can you drop to a command line and find out which driver you are using? How did you install the drivers? When you did so, were you able to boot normally?

...

Regards!

---

### Post by Hellburn on 2011-01-29
At the moment I don't have and empty cd to burn :P.
> Can you see any error logs while you are trying to boot? Can you access your Desktop via recovery mode?
After installation of ATI drivers? No errors. Just freezes.
From recovery mode I can only get to the dos-like thingy. Terminal, concole. You know what I mean.
> Also, where you able to have visual effects from your lucid installation?
No. I need ATI drivers installed to turn them on, I think.
> Where exactly does your system freeze? While you are giving your password? Before?
Just before opening sound. I get [this loading screen]("http://jantechblog.files.wordpress.com/2010/03/ubuntu1004branding-large_004.jpg"). After all dots turn red (from right to left) hdd stops working. Nothing happens - I need to reset.
> Can you drop to a command line and find out which driver you are using? How did you install the drivers? When you did so, were you able to boot normally?
Currently? ATI (installation was complete, no errors), but I can access ubuntu only from recovery mode. I installed them from "Additional Drivers".
...and no. My ubuntu freezes. That's not normal ;P.

---

### Post by Krytarik on 2011-01-29
I really recommend to grab a CD and do a clean, fresh install! I did never upgrade any OS to the next version. And doing so right after installing an old one, really doesn't make sense. Why don't you stick with 10.04 instead?

---

### Post by Claus7 on 2011-01-29
Hello,

> **Hellburn said:**
> 
Currently? ATI (installation was complete, no errors), but I can access ubuntu only from recovery mode. I installed them from "Additional Drivers".
...and no. My ubuntu freezes. That's not normal ;P.

since you get to that screen, my humble experience says that you have a drivers problem (ok you already knew that, right? ), so why don't you use the aticonfig commands in order to create a xorg.conf file, that might do your life easier? I had installed the drivers and if I did not have a descent xorg.conf file, my system was not booting normally no matter what...

And it would be nice before else to do a freshy fresh installation, cause that way you are more certain that nothing went wrong during the upgrade.

Regards!

---

