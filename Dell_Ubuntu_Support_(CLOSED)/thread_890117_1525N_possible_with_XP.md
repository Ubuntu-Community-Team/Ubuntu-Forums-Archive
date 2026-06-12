---
title: "1525N possible with XP?"
date: 2008-08-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Gaudentius on 2008-08-14
I have one of the newer 1525N's with pre-installed Hardy.

If I wanted to dual-boot with Windoze, could I use an XP disk or am I stuck having to use Vista?  I understand that whatever I choose, I'll initially lose Ubuntu and have to re-install it.

I ask because I have a XP-sp2 disk laying around that was for a now-scavenged Dell tower running Ubuntu.  There are a few applications that would be nice using on my laptop with XP that just do quite run with Ubuntu (ie. Quickbooks).

Set aside that there may be other options, is it possible with the following specs:

Inspiron 1525
Intel Core 2 Duo T7250, 2GHz, 800MHz FSB, 2MB L2 Cache
fancy, dancy, black shell
4GB, DDR2, 667MHz, 2 Dimm
15.4" Widescreen WXGA LCDTrueLife
Intel Graphics Media Accelerator X3100
120GB 7200 RPM SATA with Free Fall Sensor (better to have it and not need it, than need it and not have it)
Ubuntu 8.04 with DVD Playback
Integrated 10/100 NIC
8X DVD+/-RW Dual Layer
Integrated High Def Audio (2.0)
Intel 3945 WLAN (802.11 a/g) Mini-card

You probably didn't need all that info, but I just copied and pasted another post.

GD

---

### Post by linux_tech on 2008-08-14
You can set up a dual boot with XP.  Install XP first,
then Ubuntu.  [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by modena on 2008-08-18
Gaudentius 
Just make sure before you start that your xpsp2 cd will install onto a SATA system (most xp cds won't).  
If not you will have to use a program like n-Lite to remaster the xp disk with SATA drivers.
After that the xp installation should be painless.

---

### Post by superm1 on 2008-08-19
> **Gaudentius said:**
> I have one of the newer 1525N's with pre-installed Hardy.

If I wanted to dual-boot with Windoze, could I use an XP disk or am I stuck having to use Vista?  I understand that whatever I choose, I'll initially lose Ubuntu and have to re-install it.

I ask because I have a XP-sp2 disk laying around that was for a now-scavenged Dell tower running Ubuntu.  There are a few applications that would be nice using on my laptop with XP that just do quite run with Ubuntu (ie. Quickbooks).

Set aside that there may be other options, is it possible with the following specs:

Inspiron 1525
Intel Core 2 Duo T7250, 2GHz, 800MHz FSB, 2MB L2 Cache
fancy, dancy, black shell
4GB, DDR2, 667MHz, 2 Dimm
15.4" Widescreen WXGA LCDTrueLife
Intel Graphics Media Accelerator X3100
120GB 7200 RPM SATA with Free Fall Sensor (better to have it and not need it, than need it and not have it)
Ubuntu 8.04 with DVD Playback
Integrated 10/100 NIC
8X DVD+/-RW Dual Layer
Integrated High Def Audio (2.0)
Intel 3945 WLAN (802.11 a/g) Mini-card

You probably didn't need all that info, but I just copied and pasted another post.

GD
Why not just set up KVM and use virtualization instead?

---

### Post by Gaudentius on 2008-08-20
> **superm1 said:**
> Why not just set up KVM and use virtualization instead?

KVM?  Qu'est-ce que ça?

Total n00b here.  How does it work?  Is there a tutorial available?

I'll search around some, but if you could post a tutorial I could check out, that'd be great!

GD

---

### Post by superm1 on 2008-08-20
There is a big howto on KVM here: [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

You can also consider VirtualBox (It supports VT-x too and has a GUI).

Personally i think VirtualBox is a little easier to use, but you'll see.

---

### Post by Tsarj on 2008-08-21
Agreed. VirtualBox is amazing.

---

