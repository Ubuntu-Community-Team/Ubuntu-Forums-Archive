---
title: "Lirc configuration"
date: 2006-08-19
forum: Desktop Environments
---

### Post by christooss on 2006-08-19
I installed lirc with simple

apt-get install lirc

How can I setup lirc now?

---

### Post by noof on 2006-08-19
I'm actually struggling to do that right now. The thing is that you'll need a kernel module as well. Since I wanted the newset version (0.8.0) instead of the one in the ubuntu-repos, I'm trying to use the one from debian unstable. So far I've done this (you should do a 'apt-get remove lirc' first):
> 
sudo apt-get install dialog module-assistant
sudo m-a prepare
wget http://ftp.se.debian.org/debian/pool/main/l/lirc/lirc_0.8.0-5_i386.deb
wget http://ftp.se.debian.org/debian/pool/main/l/lirc/lirc-modules-source_0.8.0-5_all.deb
sudo dpkg -i lirc-modules-source_0.8.0-5_all.deb
sudo dpkg --force-depends -i lirc_0.8.0-5_i386.deb

then you need to edit /etc/lirc/lirc-modules-source.conf to something like:
> #   lirc-modules-source config file used by Debian GNU/Linux

# Space separated list of lirc kernel drivers to build
LIRC_MODULES="serial"

# It87 module configuration
LIRC_IT87_CFLAGS="UNCONFIGURED"

# Parallel module configuration
LIRC_PARALLEL_PORT="UNCONFIGURED"
LIRC_PARALLEL_IRQ="UNCONFIGURED"
LIRC_PARALLEL_TIMER="UNCONFIGURED"

# Serial module configuration
LIRC_SERIAL_PORT="0x3f8"
LIRC_SERIAL_IRQ="4"
LIRC_SERIAL_CFLAGS=" -DLIRC_SERIAL_SOFTCARRIER"

# Sir module configuration
LIRC_SIR_PORT="UNCONFIGURED"
LIRC_SIR_IRQ="UNCONFIGURED"
LIRC_SIR_CFLAGS="UNCONFIGURED"

and then do
> sudo m-a build lirc
and you'll end up with a .deb for the module. I never had time to try it out though, but it compiled and installed cleanly.

---

### Post by jon_benge on 2006-08-20
Look [here]("http://ubuntuforums.org/showthread.php?t=183545&highlight=lirc")

---

### Post by christooss on 2006-08-21
This is my cat /proc/bus/input/devices

> 
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0005 Version=0051
N: Name="ImPS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event2 ts0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

---

### Post by Randy_84dger on 2006-08-21
I've had a struggle to get lirc working, followed [this]("http://www.ubuntuforums.org/showthread.php?t=39125") post (using newest lirc sources), worked fine. Still having to start lirc manually at every boot, by following the guide from setserial onwards. Also, the /dev/lirc that sould be available is actually /dev/lirc0 but can be fixed (by either starting lircd with the --device option, or symlinking lirc0 to lic).

Hope it helps,
Al.

---

### Post by dantx24 on 2006-08-26
I have an Audigy 2 ZS Platinum sound card (built-in IR receiver), the stock RM-1500 remote, and Kubuntu 6.06/Dapper with 2.6.15-26-k7 kernel.

Is there a coherent, up-to-date guide to get these things working?

I've tried to follow this guide, everything compiles, but when I try to use checkinstall to make a package for the module file, and one for the actual lirc, and it tries to install, and conflicts with what's already there, and what's already there won't go away without taking kde-desktop and 24 other programs with it. 

I force the install, and Adept tells me I have a broken package and won't let me do anything else till i let it remove it.... 

Its giving me more gray hair... :-({|= Pardon the exasperated tone.

Thanks for your help

---

### Post by Randy_84dger on 2006-08-26
> Is there a coherent, up-to-date guide to get these things working?

Unfortunately not. Some posts have talked about HOWTOs in writing, but I couldn't find a solid recentish guide (other than [this year old post]("http://www.ubuntuforums.org/showthread.php?t=39125")).

Al.

---

### Post by brundles on 2006-08-29
The How-To referenced by Randy_84adger above is the best I've found, despite it's age.

That said I found with Dapper Drake the install actually turned out to be simpler (for an SM-1000 anyway).

Assuming the original Ubuntu LIRC package isn't installed it was just a case of downloading 0.8.0 from lirc.org then a configure, make and make install.

After that's done, just symlink lirc as necessary and away you go.

What packages are you trying to remove? I found originally that using Synaptic to remove lirc and lirc-modules-source was sufficient to make way for the above. 

Overall it's not as clean as a package in Synaptic and it's possible that a future update might break it, but I'll worry about that then

---

### Post by Xappe on 2006-09-08
> **dantx24 said:**
> I have an Audigy 2 ZS Platinum sound card (built-in IR receiver), the stock RM-1500 remote, and Kubuntu 6.06/Dapper with 2.6.15-26-k7 kernel.

Is there a coherent, up-to-date guide to get these things working?

I've tried to follow this guide, everything compiles, but when I try to use checkinstall to make a package for the module file, and one for the actual lirc, and it tries to install, and conflicts with what's already there, and what's already there won't go away without taking kde-desktop and 24 other programs with it. 

I force the install, and Adept tells me I have a broken package and won't let me do anything else till i let it remove it.... 

Its giving me more gray hair... :-({|= Pardon the exasperated tone.

Thanks for your help

I've installed lirc and got it running for both my ir devices this week. 

1. install linux-headers package for your running kernel and relink or creat /usr/src/linux so that it points at the headers (sudo ln -s /usr/src/linux-headers-'uname -r' /usr/src/linux)
2. run ./setup.sh in the lirc-0.8.0 dir and choose the driver you want
3. if your device needs a kernel module, then modprobe the right one and put  a line for it in /etc/modules
4. run lircd and test your remote with irw, if you get input, you're fine

My Audigy Platinum eX uses the livedrive_midi (I think it's the same that the Audigy 2 uses, but i'm not really sure) userspace module for wich no kernel modules are needed.
You need the alsa snd-emu10k1 module to be loaded (it should be already) and you need to enable the ir port by adding

option snd-emu10k1 enable_ir=1

to /etc/modprobe.d/alsa-base

then run lircd with:

# lircd --driver=livedrive_midi --device=/dev/snd/midiC0D1 

(midiC0D1 is the one for card 0, if your card is numbered 1 for example, it should be midiC1D1 I think)

---

### Post by tlue on 2006-09-16
deleted

---

### Post by tlue on 2006-09-16
> **Randy_84dger said:**
> Unfortunately not. Some posts have talked about HOWTOs in writing, but I couldn't find a solid recentish guide (other than [this year old post]("http://www.ubuntuforums.org/showthread.php?t=39125")).

Al.

I don't really know.
But this thread helped me: [http://www.ubuntuforums.org/showthread.php?t=188381](http://www.ubuntuforums.org/showthread.php?t=188381)
so this guide seems to be quite good:
[http://www2.truman.edu/~dat725/htpc_single.html#htpc6](http://www2.truman.edu/~dat725/htpc_single.html#htpc6)

---

