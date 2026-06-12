---
title: "Lubuntu on old (pre 2007) machine without SSE2"
date: 2014-11-25
forum: Gaming &amp; Leisure
---

### Post by bob116 on 2014-11-25
My father (73)  would like to watch videos on youtube, and also play some games. I have had no luck installing java, and I am wondering if there is a better choice of OS. The hardware is old, so Ubuntu 14.10 won't run smoothly. Any advice is appreciated. It's been quite a few years since I have dealt with linux.

---

### Post by sudodus on 2014-11-25
Lubuntu has the lightest foot-print of the Ubuntu family flavours. But there might be several obstacles (not only CPU horsepower and RAM size). So please describe the computer with as many details as possible, at least

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

See this link for more details [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

There are also alternatives to flash video, for example this one:

[Activate Alternative Html5 Youtube Video Player And Play ...]("http://www.youtube.com/watch?v=NwXglEC4loI")

---

### Post by bob116 on 2014-11-25
john@john-KM400-8235:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:06.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
00:06.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
00:06.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

john@john-KM400-8235:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 6
model        : 8
model name    : AMD Athlon(tm)
stepping    : 1
cpu MHz        : 1833.048
cache size    : 256 KB
physical id    : 0
siblings    : 1
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca  cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow
bogomips    : 3666.09
clflush size    : 32
cache_alignment    : 32
address sizes    : 34 bits physical, 32 bits virtual
power management: ts

---

### Post by sudodus on 2014-11-25
[Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640") tells us

> Let's begin with a simple test to see if the hardware in question is a)  fairly old but straightforward to deal with or b) very old and needs  some tricks. 

Using any Linux distro, installed or from a live boot, please copy the  command into the terminal and run. It takes some seconds to complete.
 
    ```
 sudo lshw -C cpu | grep -i sse2 
```
If you get a line full of abbreviations everything is good. Chances are that the install is simply next, next, next, finish.

If the command doesn't yield an output your computer is at least ten  years old. It will be running open source programs fine but closed  source like Flash player and Skype might give problems. Besides, we are  dealing with a slow processor so consider if it's worth the effort,  especially if you are new. Please see post #2 in the thread.

(Details: The command above checks if the processor has the SSE2  instructions set, which is required by a number of closed-source  programs. In the [Intel]("http://en.wikipedia.org/wiki/Comparison_of_Intel_processors") family the oldest member with SSE2 is a Pentium 4 and for [AMD]("http://en.wikipedia.org/wiki/Comparison_of_AMD_processors")  the oldest is a K8. Though SSE2 is not necessary for an open source  Lubuntu install it still serves as a baseline for reasonable  performance.)

It looks like your dad's computer has a K7 processor that lacks sse2, which makes it impossible to run Flash.

[http://www.cpu-world.com/CPUs/K7/AMD-Athlon%20XP%202500+%20-%20AXDA2500DKV4D.html](http://www.cpu-world.com/CPUs/K7/AMD-Athlon%20XP%202500+%20-%20AXDA2500DKV4D.html)

Maybe it can run the alternative HTML5 for Youtube, but it might be a good idea to look for a computer, that is some years newer to get better video playing. In many countries it is possible to get a used computer for a very good price.

---

### Post by sudodus on 2014-11-25
I think VIA graphics will work with the 12.04 version of Ubuntu, for example implemented as [Precise Gnome Classic Tweaks]("https://help.ubuntu.com/community/PreciseGnomeClassicTweaks"), but there are problems with newer versions.

Anyway, it is possible to use the computer at least for email, simple internet browsing, writing documents, etc, but I think it will be too weak/old for watching Youtube videos.

-o-

Playing games is a different issue. It depends very much on what kind of games. Many games are made for Windows, and only some of them work with linux. Some games need a new computer, some need on old Windows version ...

If you specify the games, someone else can tell you what computer and or operating system he needs for them. (I know very little about games.)

---

### Post by bob116 on 2014-11-25
The thought had crossed my mind. We were trying to avoid buying a new system. I would rather build one, There is no point in paying for a new operating system. I will try HTML5, hopefully that will work.

---

### Post by mörgæs on 2014-11-26
The processor is not only pre 2007, it's likely from around 2002. 

Anyway, before giving up on Flash did you read post #2 in the Old Hardware thread?

---

