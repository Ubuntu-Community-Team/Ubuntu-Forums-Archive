---
title: "Resolving Kernel Panics"
date: 2008-12-24
forum: General Help
---

### Post by XanTrax on 2008-12-24
Hello,

I have recently installed Ibex on my laptop and just installed minimal things like compiz-git, screenlets, and songbird.  I believe it was after installing screenlets and activating some of them that I saw the kernel panics begin more...although, it was happening before when I was listening to Pandora and/or using Songbird.

Regardless, I can not seem, for the life of me, to be able to resolve these kernel panics.  It is mostly when my computer is sitting idle for awhile though it has happened to me at random times while using it.  There is no pattern as to when it happens, it always seems to be completely random.  As to try to fix the problem I disabled screenlets and the startup daemon, disabled bluetooth. I generally only use pidgin, firefox, and songbird at the same time, nothing else really special.  I have checked all the logs in /var for some form of information, one of the only things I could think of is something with my wireless network card (the dreaded Atheros card) because my daemon.log is flooded with this:

```

daemon.log:Dec 19 23:15:26 kozler-laptop NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 7 
daemon.log:Dec 19 23:17:30 kozler-laptop NetworkManager: <info>  (ath0): supplicant connection state change: 7 -> 0 
daemon.log:Dec 19 23:17:30 kozler-laptop NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 4 
daemon.log:Dec 19 23:17:30 kozler-laptop NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 7 

```

Though I doubt it is related to the kernel panic.  

kern.log yields this:

```

Dec 24 13:58:16 kozler-laptop kernel: [62424.980054] Uhhuh. NMI received for unknown reason a1 on CPU 0.
Dec 24 13:58:16 kozler-laptop kernel: [62424.980054] You have some hardware problem, likely on the PCI bus.
Dec 24 13:58:16 kozler-laptop kernel: [62424.980054] Dazed and confused, but trying to continue
Dec 24 15:40:17 kozler-laptop kernel: [68546.755483] rix 15934 (0) bad ratekbps 0 mode 1
Dec 24 15:46:25 kozler-laptop kernel: [68914.488209] rix 15934 (0) bad ratekbps 0 mode 1
Dec 24 15:46:25 kozler-laptop kernel: [68914.488221] rix 15934 (0) bad ratekbps 0 mode 1
Dec 24 15:46:25 kozler-laptop kernel: [68914.488226] rix 15934 (0) bad ratekbps 0 mode 1
Dec 24 17:44:59 kozler-laptop kernel: Inspecting /boot/System.map-2.6.27-9-generic
Dec 24 17:44:59 kozler-laptop kernel: Cannot find map file.
Dec 24 17:44:59 kozler-laptop kernel: Loaded 59075 symbols from 101 modules.

```

I am assuming @ 15:46 (3:46 PM) is when the kernel panic was thrown as you can see, 2 hours later when I got home, @ 17:44 (5:44 PM) is when I booted the system back up.  I know this is a kernel panic because the caps lock light blinks and nothing on the computer is usable except the power button to shut it off.  

Anyone have any ideas?  I have never resolved a kernel panic before so some help would be awesome :).

Thanks!

EDIT: Here is some hardware information for anyone that may think it is relative

```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc M56GL [Mobility FireGL V5250]
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

```

I can also post the more verbose ones if you would like (-v, -vv, and -vvv, please specify)

EDIT 2:  I have also tried checking the drive for errors (booting into recovery console -> check disk utility) and nothing is found or fixed, so I want to see if it is relative to the kernel or my hardware is faulty.



EDIT 3:  After reading:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116752](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116752)

It is making me think it could be an overheating problem?  This laptop does get extremely hot when I am doing more things (graphics stuff usually) but I dont think its relative because it happens more when it just sits idle and a very cool room.

---

### Post by spiderbatdad on 2008-12-25
>  Dec 24 13:58:16 kozler-laptop kernel: [62424.980054] You have some hardware problem, likely on the PCI bus. 

I think the log you want to look at is dmesg. After a fresh boot, run ```
dmesg > ~/Desktop/dmsg.txt
``` You may need to incorporate some "boot options" or "boot parameters" into the kernel by editing the kernel line in /boot/grub/menu.lst. Possibilities might include: acpi=off pci=routeirq. Dmesg will tell you more.

---

### Post by XanTrax on 2008-12-25
> **spiderbatdad said:**
> I think the log you want to look at is dmesg. After a fresh boot, run ```
dmesg > ~/Desktop/dmsg.txt
``` You may need to incorporate some "boot options" or "boot parameters" into the kernel by editing the kernel line in /boot/grub/menu.lst. Possibilities might include: acpi=off pci=routeirq. Dmesg will tell you more.

I have run dmesg and read the previous dmesg logs and nothing is found of any use or relativity.  The only thing that has yielded any useful or relative information is kern.log.

Any other ideas?

Thanks for your time.

---

### Post by spiderbatdad on 2008-12-25
> **XanTrax said:**
> I have run dmesg and read the previous dmesg logs and nothing is found of any use or relativity.  The only thing that has yielded any useful or relative information is kern.log.

Any other ideas?

Thanks for your time.

It is unlikely that there is nothing useful or relative in your dmesg log.
If you would like help perhaps you could upload the log here as an archive. The file will be too large to upload as text, so right click and create an archive. Upload the archive here with the manage attachment tool below.

---

### Post by XanTrax on 2008-12-25
> **spiderbatdad said:**
> It is unlikely that there is nothing useful or relative in your dmesg log.
If you would like help perhaps you could upload the log here as an archive. The file will be too large to upload as text, so right click and create an archive. Upload the archive here with the manage attachment tool below.

Of course, I am probably missing something.  I am usually pretty good about reading the logs but I could be missing something in dmesg.  Wouldnt kern.log yield more information than dmesg?.  

In fact, another kernel panic just happened again so I will include the current dmesg log and the one from the previous boot.

dmesg = dmesg log from todays boot after it paniced (approx 15 minutes ago @ 3:00 PM EST)

dmesg.0 = dmesg log from yesterday after yesterdays kernel panic


Thanks again for your help.  I especially want to get this resolved now because I am sharing my internet connection to my home server that I have in my room (no wireless card in it atm and im too lazy to run a cat5 through my house :p).


EDIT: Also, if you find anything in dmesg, can you let me know what it is exactly that you found so that I may know for future reference?  Thank you :).


EDIT 2: I saw that in the kern.log about "you may have some hardware problem, most likely on the PCI bus".  How would I maybe go about identifying problems with the PCI bus?  Only real diagnostic check I have done is a check disk on the drive, which didnt find any problems.

---

### Post by spiderbatdad on 2008-12-25
This could be a significant problem:```
ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
```
Which may be related to the message:```
ACPI Warning (tbfadt-0442): Optional field "Gpe1Block" has zero address or length: 000000000000102C/0 [20080609]
```

I am looking for a solution. So far I have only found to turn acpi off. So might as well try that and get a new dmesg. Now there are a number of "warnings" in dmesg that are normal and no cause for alarm. The above is not an example of one of those warnings.

To temporarily boot with the acpi=off parameter. Enter the grub menu at start up and select your linux kernel (probably already selected) press e then use the arrow key to move to the line that starts with the word 'kernel', press e again. Now go to the en of that line and delete 'quiet splash --' type instead 'acpi=off' Hit enter and then press b.

Get a new dmesg archive after boot. To make the parameter permanent, you will need to edit the file /boot/grub/menu.lst under the debian kernel section and edit the end of the kernel line there.

I believe the above problem is causing overheating in your system. Not sure.

---

### Post by XanTrax on 2008-12-25
> **spiderbatdad said:**
> This could be a significant problem:```
ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
```
Which may be related to the message:```
ACPI Warning (tbfadt-0442): Optional field "Gpe1Block" has zero address or length: 000000000000102C/0 [20080609]
```

I am looking for a solution. So far I have only found to turn acpi off. So might as well try that and get a new dmesg. Now there are a number of "warnings" in dmesg that are normal and no cause for alarm. The above is not an example of one of those warnings.

To temporarily boot with the acpi=off parameter. Enter the grub menu at start up and select your linux kernel (probably already selected) press e then use the arrow key to move to the line that starts with the word 'kernel', press e again. Now go to the en of that line and delete 'quiet splash --' type instead 'acpi=off' Hit enter and then press b.

Get a new dmesg archive after boot. To make the parameter permanent, you will need to edit the file /boot/grub/menu.lst under the debian kernel section and edit the end of the kernel line there.

I believe the above problem is causing overheating in your system. Not sure.

Awesome, thank you very much for your time.  The overheating could very well be the problem because this laptop is notorious for overheating.  This laptop was given to me from my college included in my tuition and I have countless friends that have had their computers just fry from overheating or if you just put your hand next to the fan exhaust, its blowing extremely hot hair.

I can not try it right now but I will in the next 24 hours.  In fact, as of now 6:36 PM EST, I had just received another kernel panic while the machine was idle.  Only things running were pidgin and songbird.  If it wasnt in the kernel layer, I would start to think that songbird was the culprit...but I doubted from the start that software such as songbird could throw kernel panics.

Would disabling ACPI cause any problems with the hardware I have installed on this laptop?  The hardware I have is above and I can provide more detailed information on it if you need it.

Thank you very much for all your help, I would have never came across those messages and relate them back to the kernel panics.

Cheers, and merry christmas :)

---

### Post by spiderbatdad on 2008-12-25
disabling the acpi will not cause any damage to installed hardware, but we do want to look at the kernel diagnostic message again after you have disabled acpi. I too have a thinkpad, but only a T30. I boot with these parameters, shown in bold below.

```
## ## End Default Options ##

title	Ubuntu 8.10, kernel 2.6.27-9-generic
root	(hd0,0)
kernel	/boot/vmlinuz-2.6.27-9-generic root=XXXXX ro** lapic hpet=force pci=routeirq **
initrd	/boot/initrd.img-2.6.27-9-generic
```

---

### Post by XanTrax on 2008-12-26
> **spiderbatdad said:**
> disabling the acpi will not cause any damage to installed hardware, but we do want to look at the kernel diagnostic message again after you have disabled acpi. I too have a thinkpad, but only a T30. I boot with these parameters, shown in bold below.

```
## ## End Default Options ##

title	Ubuntu 8.10, kernel 2.6.27-9-generic
root	(hd0,0)
kernel	/boot/vmlinuz-2.6.27-9-generic root=XXXXX ro** lapic hpet=force pci=routeirq **
initrd	/boot/initrd.img-2.6.27-9-generic
```

Im going to try this way because when I did acpi=off it broke a lot of stuff.  Mouse didnt seem to work, wireless card wasnt recgonized, and the computer at boot had posted a lot of failed messages about things.  Could be an isolated incident or maybe I messed it up (dont believe I did tho), so, I am going to try your boot parameters.

---

### Post by XanTrax on 2009-01-01
Sorry this took so long.  I tried with your boot parameters and attached you can see dmesg logs.

dmesg = after boot with your parameters
dmesg.0 = original boot parameters where I had gotten another kernel panic

---

### Post by XanTrax on 2009-01-05
Alright, this seems to have done the trick (using your boot parameters).  Although, I wound up reinstalling Ubuntu because I try to reformat and reinstall any OS I am using every 4-6 months to keep everything neat and tidy.

Thank you for all your help.  I am confident your assistance resolved this because for about 3 days or so my computer stayed on and ideled and/or used and never kernel paniced again.  I am back to using the standard boot parameters after my reinstall.

---

### Post by XanTrax on 2009-01-18
Ok, I was mistaken...this did not fix the problem.  What did actually fix the problem (or so it seems) was upgrading my kernel to 2.6.27-10 as I was previously running 2.6.27-9.  I dont see the "dazed and confused" error anymore...I read on some bug reports that someone had the same problem and they upgraded to -10 and even tho dmesg still reported the error, it was managed now rather then throwing a kernel panic.

Thank you again for all your help.

---

