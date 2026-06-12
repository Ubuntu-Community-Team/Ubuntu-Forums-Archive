---
title: "[Elementary OS] No GUI on Bootup"
date: 2014-05-23
forum: Debian
---

### Post by lloyd094 on 2014-05-23
I have an HP Envy Touchsmart 15 Quad Edition (and this is according to dxdiag in Windows 8.1):


System Manufacturer: Hewlett-Packard
System Model: HP ENVY TS 15 Notebook PC
BIOS: F.56
Processor: Intel(R) Core(TM) i7-4700MQ CPU @ 2.40GHz (8 CPUs), ~2.4GHz
Memory: 8192MB RAM


Card name: Intel(R) HD Graphics 4600
Manufacturer: Intel Corporation
Chip type: Intel(R) HD Graphics Family
DAC type: Internal
Device Type: Full Device
Device Key: Enum\PCI\VEN_8086&DEV_0416&SUBSYS_1962103C&REV_06
Display Memory: 1792 MB
Dedicated Memory: 0 MB
Shared Memory: 1792 MB
Current Mode: 1920 x 1080 (32 bit) (60Hz)
Monitor Name: Generic PnP Monitor
Monitor Model: unknown
Monitor Id: CMN15BB
Native Mode: 1920 x 1080(p) (60.049Hz)


I received this computer for this past Christmas, and I decided since it was summer to dual boot eOS. I have worked with linux before, so I know my way around fairly well, however because this is a UEFI computer, I also followed along with this guide a bit: [http://forums.opensuse.org/showthread.php/487837-How-to-Dual-boot-(preinstalled)-Windows-8-and-Linux-UEFI-etc](http://forums.opensuse.org/showthread.php/487837-How-to-Dual-boot-(preinstalled)-Windows-8-and-Linux-UEFI-etc)


Now I'm lost. I have my computer set up for Dual Boot with eOS installed, but I don't get the GUI. Every time I log in I get terminal, and from some researching, it seems that linux also doesn't detect my monitor. I went with multiple guides on how to fix this issue, but none of them seemed to work for me. Maybe I can get help here?


Thanks ahead of time for all the effort/work put into help!

---

### Post by oldfred on 2014-05-23
Are you booting Elementary in UEFI mode?

Often video parameters needed. Not sure what version Elementary is using but Ubuntu often needed parameters, and with Intel video nomodeset would not work but some of the others may.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

      
 Some other Intel boot options Each line is one that may work
acpi_osi=Linux  acpi_backlight=vendor
 i915.i915_enable_rc6=1


 (13.10) Intel graphics driver fails to manage HD 4600 on HP Split x2
[http://ubuntuforums.org/showthread.php?t=2191109](http://ubuntuforums.org/showthread.php?t=2191109)
Needed all the settings??


 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)

---

### Post by prmurthy on 2014-05-23
Hi, you might want to look through my post on installing Luna on a 840 G1 in this same forum.

---

### Post by Stinger on 2014-05-24
Hi lloyd094
Welcome to the Ubuntu forums.
I think I know what your problem is, your hardware is to new for the 3.2 kernel and X-server that comes with elementary luna, but hopefully it can be fixed ;)
Check your kernel with this command in terminal:
```
uname -r 
```
Mine says 3.2.0-61-generic, and if you get something similar, it's to old for your hardware.

To fix it you need too use the LTS Enablement stack from Precise.

To install the Saucy hardware enablement packages in eOS Luna or Precise , please run the following command:

```
sudo apt-get install --install-recommends linux-generic-lts-saucy xserver-xorg-lts-saucy libgl1-mesa-glx-lts-saucy
```
Remember to reboot to activate the new kernel and x-server.
```
sudo reboot
```
[LTS Enablement Stack page]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")


I wrote about it earlier on this thread:
[ [elementaryOS] 5 Myths About elementary]("http://ubuntuforums.org/showthread.php?t=2214635") 
( Bottom half )

---

