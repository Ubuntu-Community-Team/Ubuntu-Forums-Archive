---
title: "Keyboard freeze: very puzzling problem"
date: 2006-07-30
forum: Desktop Environments
---

### Post by kikinovak on 2006-07-30
Hi,

A friend of mine just brought along her PC to install. It's a no-name "multimedia tower" full with "Designed for Microcrap" stickers on it.

About two years ago, I had installed Slackware 10.1 on this machine (I've been a Slackware user for years), and for a long time, it ran without problems. Then, it began to produce annoying keyboard freezes now and then. 

About a week ago, I put CentOS 4.3 (RHEL 4 clone) on that machine, and everything went perfectly. Rebooted the PC at least 20 times or so, never an error. 

Now I tried to install a distro I recently discovered and which I sort of like: Xubuntu. (Used Slack with XFCE mainly, but missed Gnome libs, d-bus and all these things...). Took a Ubuntu CD, chose "server install" to install the minimum and then eventually go on with apt-get install xubuntu-desktop... there we go again: keyboard freeze upon reboot. Tried to change the keyboard, to no avail. Same problem with another keyboard.

BUT: installed CentOS again on this machine, and it works flawlessly. Which leaves me clueless. The keyboard attached to it is a classic pc-105 keyboard. Plus there's an optical USB mouse attached to USB. 

Here's some info about hardware (I'm writing this message from within CentOS):

[nat@bebette ~]$ /sbin/lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV31 [GeForce FX 5600] (rev a1)
02:02.0 Communication controller: Intel Corporation 536EP Data Fax Modem
02:09.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 8b)
02:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)

[nat@bebette ~]$ /sbin/lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 002: ID 0db0:6982 Micro Star International Medion Flash XL V2.7A Card Reader
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

[nat@bebette ~]$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping        : 9
cpu MHz         : 2793.979
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5591.53

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping        : 9
cpu MHz         : 2793.979
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5585.25

Now I'm really clueless. Except what's new for me is the dual processor... since my hardware requirements are rather modest usually, I'm used to working on old Pentium II or III or at the most first-generation PIV.

Any suggestions?

Niki

---

