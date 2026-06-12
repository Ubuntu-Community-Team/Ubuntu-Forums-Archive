---
title: "Dell Studio 1558 I5"
date: 2010-04-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Simon_WM on 2010-04-28
Hey Guys,

I'm thinking of changing from Windows 7 to Linux Ubunut 9.10 ---> 10.4
Although i would like to now if Linux Ubuntu can run on a 64x I5 processor and will run with out any glitches like, 

No Sound,
No Wifi,
No Ethernet connection
No SD Card.

Any reviews / ideas?

Atm am running linux as a vm but wish to go full on and format my laptop 500gb hdd.

or should i try and duel boot?

---

### Post by quiksilver on 2010-04-29
I will be installing 10.04 on my 1558 very soon. (Within the next day or 2)

I already reformatted my HDD and gave Win7 100GB (250GB total HDD size here). All the junk Dell had installed was too irritating.

Keep in mind that most Dells will be different. (Especially with their recent refurb sale).

I have the i5 430m with the Intel Centrino Advanced-N 620 wireless card rather than the Broadcom. (Broadcoms have given me issues in the past) I also have the 512MB ATI Mobility Radeon HD 4530 over the Intel HD Graphics.

Either way, I'll let you know if I run into any issues in a day or so.

---

### Post by Si2100 on 2010-04-30
Hi, Thanks for reply.

i can asure you i have the same processor and graphics card. - but when you were useing windows 7 what audio driver did you use? i used IDT Audio...

But Ubuntu 10.4 is running great apart from no sound :confused:

---

### Post by Si2100 on 2010-04-30
Heyy, Quickslik

updated to 10.4 and souns is now working =]

---

### Post by quiksilver on 2010-04-30
Well, after installing the OS (which is insanely fast compared to win7), things worked out pretty good.

Few issues.

1. Insanely slow repository access. I'm sure it is because 10.04 just came out, and everybody is hammering it. But waiting 3 hours to download the ATI drivers was pretty annoying. VLC and other apps also were really slow. I'm sure things will be normal in a week. So I'm going to keep trying every couple days to see when things free up and are tolerable.

2. No sound. The downloads needed to fix this issue were taking way too long, so I still haven't fixed it yet, but this post looked very promising. (If you have the realtek ID 665 sound chip - alsamixer can tell you)

[http://ohioloco.ubuntuforums.org/showthread.php?t=1278146&page=2](http://ohioloco.ubuntuforums.org/showthread.php?t=1278146&page=2) (Post #18 )

3. VERY light touchpad. You hardly have to graze the thing and the mouse goes flying. It is still workable though. (and re-validates my love of the thinkpad nub) Also, since the 1558 has multi-touch, but multi-touch is not activated by default, the mouse freaks out a bit when it senses more than one finger.

Other than that, things are running great. Wireless worked without a hitch for me (non-broadcom). Ethernet is fine. Don't really use SD cards or Bluetooth though, so won't be testing them.

One really nice feature is that I can mount my windows partition without having to give my password anymore. I always thought that was useless. So moving things over is even easier.

Hope that helps.

---

### Post by Si2100 on 2010-04-30
> **quiksilver said:**
> Well, after installing the OS (which is insanely fast compared to win7), things worked out pretty good.

Few issues.

1. Insanely slow repository access. I'm sure it is because 10.04 just came out, and everybody is hammering it. But waiting 3 hours to download the ATI drivers was pretty annoying. VLC and other apps also were really slow. I'm sure things will be normal in a week. So I'm going to keep trying every couple days to see when things free up and are tolerable.

2. No sound. The downloads needed to fix this issue were taking way too long, so I still haven't fixed it yet, but this post looked very promising. (If you have the realtek ID 665 sound chip - alsamixer can tell you)

[http://ohioloco.ubuntuforums.org/showthread.php?t=1278146&page=2](http://ohioloco.ubuntuforums.org/showthread.php?t=1278146&page=2) (Post #18 )

3. VERY light touchpad. You hardly have to graze the thing and the mouse goes flying. It is still workable though. (and re-validates my love of the thinkpad nub) Also, since the 1558 has multi-touch, but multi-touch is not activated by default, the mouse freaks out a bit when it senses more than one finger.

Other than that, things are running great. Wireless worked without a hitch for me (non-broadcom). Ethernet is fine. Don't really use SD cards or Bluetooth though, so won't be testing them.

One really nice feature is that I can mount my windows partition without having to give my password anymore. I always thought that was useless. So moving things over is even easier.

Hope that helps.

QuickSilver, you can turn the the speed of the mouse pad, as there is an app for it in the Software Centre, its called "Touch Pad" it can turn down the speeds and touch sensitivity.

---

### Post by quiksilver on 2010-04-30
> **Si2100 said:**
> QuickSilver, you can turn the the speed of the mouse pad, as there is an app for it in the Software Centre, its called "Touch Pad" it can turn down the speeds and touch sensitivity.

Great application. Thanks for the tip.

Got the sound working without any issues by updating alsa using the link above.

So regarding the original post, I'd recommend you go for it. No big issues I see.

---

### Post by Glenn Louttit on 2010-05-02
Hi. I have a Dell Studio 1558 I5 520m processor with a ATI Mobility Radeon HD 4570 512MB Video Card running Lucid Lynx (10.04). I am running both ubuntu and kubuntu.
I have some issues.
Each time I try to change the visual effects in the change desktop background, I lose my control bar on the windows and my mouse changes the pointer from a pointer to a cross.
I know that there is a driver that I have enabled in the past but currently have disabled because it did not work properly before - the kubuntu start up screen was distorted

Also Sound works fine, in fact nearly everything works well, even the sound buttons on key board which did not initially work (they froze the key board in the past) now do.

BUT 

The audio output sockets on the side of the computer do not emit sound to external speakers.
Any suggestions re video card drivers and how to get the sound to external speakers?

Thanks

---

### Post by venkidwaraka on 2010-05-03
I am using Ubuntu 10.04.I have the same system, but I am not able to turn on my wireless or it is not getting detected. So I am not able to connect to the internet using wiFi.
I guess some of the drivers are broken in this.
Can anyone suggest any help so that I can enable by wireless networking possible in ubuntu.

The result of [COLOR="Red"]lshw -C network[/COLOR] is as follows:

[B]*-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: b8:ac:6f:5a:81:e8
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=172.22.0.45 latency=0 link=yes multicast=yes port=MII speed=100MB/s[/B]

Thanks in Advance...

---

### Post by angryalf on 2010-09-20
Hi!

I have Dell 1558 too and have only 1 problem with start WIFI (result same as prev reply).
Can any recommend how to solve this?

Thanks.

---

