---
title: "Linux Kernel 2.6.38"
date: 2011-03-21
forum: Desktop Environments
---

### Post by GRIngram on 2011-03-21
Im a Ubuntu 10.10 (32bit) user and was considering upgrading the kernel from the existing 2.6.35-28-generic to the new 2.6.38

Ive downloaded the source and have got half way through the process and am now trying to sort out the config. Should I use the "make oldconfig" as it is? and if I do what should I change for 2.6.38... or should I configure the new one from scratch... either way I dont know what setting to keep the same and which to change... HELP

My cpuinfo (sudo /proc/cpuinfo)is

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
stepping	: 7
cpu MHz		: 2000.000
cache size	: 2048 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm dts
bogomips	: 4666.49
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
stepping	: 7
cpu MHz		: 2000.000
cache size	: 2048 KB
physical id	: 0
siblings	: 4
core id		: 3
cpu cores	: 4
apicid		: 3
initial apicid	: 3
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm dts
bogomips	: 4666.10
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
stepping	: 7
cpu MHz		: 2000.000
cache size	: 2048 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 4
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm dts
bogomips	: 4666.09
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
stepping	: 7
cpu MHz		: 2000.000
cache size	: 2048 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 4
apicid		: 2
initial apicid	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm dts
bogomips	: 4666.09
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:


and my hardwareinfo (sudo lspci)is


00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600GT] (rev a1)
03:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
05:00.0 Communication controller: Conexant Systems, Inc. Device 2702 (rev 01)
05:01.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)

and last of all Im using gconfig

Thanks in advance 
GRingram

---

### Post by jcolyn on 2011-03-21
Here is an easier method of installing the 2.6.38 kernel. Go here [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") and scroll down to the latest 2.6.38-natty and open. If you are running 32 bit download in this order the linux-header ending in .all.deb then the linux-header ending in i386.deb then the linux-image ending in i386.

AMD64 linux-headers.all.deb, linux-headers.amd64.deb, and linux-image.amd64.deb

To install go to the folder where you downloaded the files to and first double-click the linux-header file ending in .all.deb. Once installed double-click the linux-header file ending in i386.deb or amd64.deb if your system is 64 bit. Last double-click the linux-image ending in i386.deb or amd64.deb as above. During the install of the linux-image grub is automatically updated.

Be sure to install in the order given then reboot. Your computer will now reboot into the new kernel. For more info on this method check this thread. [http://forums.linuxmint.com/viewtopic.php?f=42&t=40185&hilit=kernel](http://forums.linuxmint.com/viewtopic.php?f=42&t=40185&hilit=kernel)

You may have to re-install your nvidea driver...

---

### Post by GRIngram on 2011-03-21
Colyn,
You are a legend.!!!
Ive installed the new kernel and my PC is now even faster than it was.
Youve gotta feel sorry for those poor "windaz" users, that with each release they need faster and faster hardware.... while the linux world updates their OS so it goes faster and faster with the same hardware.
Thanks again
GRingram

PS - nvidia is just fine.... Im luvin my "new" pc

---

### Post by Bucky Ball on 2011-03-21
Please mark thread as solved from Thread Tools to help others.

Incidentally, this is posted in the wrong forum. You probably wanted Installation and Upgrades. A DE is Gnome, Xfce, KDE, or any other of the large array of available desktop environments. ;)

---

### Post by KegHead on 2011-03-29
Hi!

I know this is closed!

Thanks for your help!

It worked perfectly!

KegHead

---

