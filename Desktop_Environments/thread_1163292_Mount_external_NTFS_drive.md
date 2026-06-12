---
title: "Mount external NTFS drive"
date: 2009-05-18
forum: Desktop Environments
---

### Post by Burillo on 2009-05-18
This darn thing still doesn't work properly. According to NTFS-3G website, i have to do the following:

Unprivileged block device mounts work only if all the below requirements are met:

   1. ntfs-3g is compiled with integrated FUSE support
   2. the ntfs-3g binary is at least version 1.2506
   3. the ntfs-3g binary is set to setuid-root
   4. the user has access right to the volume
   5. the user has access right to the mount point 

Now this is kinda funny.

1. How the **** am i supposed to know how to compile ntfs-3g with FUSE support?! I googled this for hours and still couldn't find it (and YES, i've read the README, INSTALL or whatever files were in the source dir). Maybe i'm just blind, or dumb, i don't know. If i have to do that - why don't the Ubuntu maintainers do that for me?

2. I believe this requirement is met, so no comments on that one.

3. Been there, done that. No success so far.

4. What is that supposed to mean? I have a external HDD with 3 partitions on it (two NTFS and one ext3) - and given the successful mount of ext3 partition i assume that i have access-rights to the other partitions as well.

5. This is really weird. Every time i connect my Ipod to my Ubuntu it creates a new directory, and then removes it after i unmount the device. So this raises a question - how can i have access rights to a directory that doesn't exist? I mean in theory this NTFS drive should be mounted the same way as my iPod - a new directory is created, removed when unmounted - so i don't need to have a directory at all - it should be automagically created!

I've been trying to make this work since freakin' Dapper, each time hoping that a new version will finally fix the problem. Not only each major update systematically breaks my X and a bunch of other stuff, it doesn't even solve the old problems!
[SIZE="1"]I also can't compile my webcam driver anymore since the update but that should really be in another topic :-)[/SIZE]

EDIT:

just so to speak - my fixed drives work fine with fstab. However, I don't want to edit fstab and create a folder for every external NTFS drive i come across, nor i do want to use terminal to mount the freakin' drives every time.

---

### Post by aysiu on 2009-05-18
You shouldn't have to recompile NTFS-3G. If you have NTFS-3G installed through the repositories, it should work just fine.

---

### Post by coffeecat on 2009-05-18
> **aysiu said:**
> If you have NTFS-3G installed through the repositories, it should work just fine.

Isn't ntfs-3g installed by default anyway? Automounting of external NTFS drives read/write has worked out of the box for me since at least Hardy, so I don't understand why it doesn't for the OP.

---

### Post by sherl0k on 2009-05-18
Indeed, it's installed with Jaunty by default.

I believe what the problem is, is that it's not mounting because it wasn't safely unmounted the last time you unplugged it from your Windows computer. ntfs-3g doesn't like to mount Windows drives that aren't cleanly unmounted.

The easiest fix is to plug it back into a Windows PC, then choose "safely remove hardware." When you plug it back into Ubuntu it will recognize and load.

---

### Post by Burillo on 2009-05-18
Well it's not like i don't know what i'm doing. I always cleanly unmount my drives and indeed tried to mount them by hand, unmount and then mount with gnome automount. You see, even if the drive was unmounted abruptly - the ntfs driver will warn you even in terminal and will force you to use the -f key in order to mount it. And, as i already said, this was not the case. I know that the driver is installed by default, what's more - i tried mounting drives on a fresh install - no configuration, no messing - and it didn't work.

PS i tried purging ntfs-3g and reinstalling it, compiling it from sources - everything you can imagine.

---

### Post by sherl0k on 2009-05-18
Very true, it was just a possible solution.

I have actually seen this problem with a firewire drive of mine, and to make it work I had to use the USB port instead. I'm going to go out on a limb and guess that there's only one port to connect with.

Does it work with Windows? Have you tried another USB cable?

---

### Post by coffeecat on 2009-05-19
I've noticed the occasional thread from someone for whom automounting of ntfs drives is not working. Not often though, and it's always puzzled me. It's clearly an issue, but not a common one otherwise these boards would be flooded with threads about this. I'm just speculating here, but I wonder if there is an obscure bug somewhere in the interaction of the ntfs-3g driver, the kernel USB driver and the particular chipset for the motherboard USB controller. Most likely in the chipset if this is the cause.

My machines have either Intel or nvidia motherboard chipsets and I don't have this problem. **Burillo**, try running lspci and see which is your USB controller. It won't help you solve the problem but it might shed some light on this.

---

### Post by Burillo on 2009-05-19
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV530LE [Radeon X1600]
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
04:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

This is what lspci gives me. Didn't clean it since anything could be the cause...

And i already use USB for the drive, and it works perfectly fine with windows. Also it works perfectly with Linux, i just always have to mount it by hand. I didn't try other drives since the update, i think i'm gonna try one if i get my hands on it - just to see if the problem is specific to my hard drive or is it a general problem with my NTFS...

I tried to change cable, tried another ports (i got three of them) - and also when the problem started to appear i had a different external hard drive with exact same problems (i think it was Dapper back then). And by "problem started to appear" i mean i started trying Linux, not that it was OK before Dapper.

---

### Post by coffeecat on 2009-05-19
OK, next time I'm on my Intel machine I'll compare lspci output, but I don't think my theory of the USB controller stands up. Intel is too common for this to be an issue.

Next idea - I've also seen threads where Seagate USB drives wouldn't automount in Ubuntu. Enough to suspect that there might be something odd about the Seagate USB firmware - not the actual Seagate HD. Is your drive a Seagate? I know you say you were getting problems with a different drive, but that was with Dapper. That was three years ago - NTFS support wasn't as good then.

---

### Post by Burillo on 2009-05-19
> **coffeecat said:**
> OK, next time I'm on my Intel machine I'll compare lspci output, but I don't think my theory of the USB controller stands up. Intel is too common for this to be an issue.

Next idea - I've also seen threads where Seagate USB drives wouldn't automount in Ubuntu. Enough to suspect that there might be something odd about the Seagate USB firmware - not the actual Seagate HD. Is your drive a Seagate? I know you say you were getting problems with a different drive, but that was with Dapper. That was three years ago - NTFS support wasn't as good then.

My drive is indeed a SeaGate one, but it has noname HDD enclosure. I too heard about some problems with seagate drives, but that's defintely not the case. I can't seem to see ANY reasons the drive wouldn't automount AND would manually mount perfectly... If it can't mount - it can't mount, it's that simple. I don't think gnome automount does something significantly different in the mounting process.

---

### Post by coffeecat on 2009-05-20
> **Burillo said:**
> My drive is indeed a SeaGate one, but it has noname HDD enclosure. I too heard about some problems with seagate drives, but that's defintely not the case. I can't seem to see ANY reasons the drive wouldn't automount AND would manually mount perfectly... If it can't mount - it can't mount, it's that simple. I don't think gnome automount does something significantly different in the mounting process.

I agree. A noname enclosure shouldn't be a problem. I think the Seagate issue is down to their enclosure.

Sorry - I'm completely out of ideas.

---

### Post by Burillo on 2009-05-20
So am i - otherwise i wouldn't have posted here :-) normally i try every possible and impossible solution before asking for help, but, as i said - i don't know what's wrong...

[offtopic] by the way, the word "mocha" in your pesonal rank sounds similar to one russian word meaning "urine" :-) [/offtopic]

---

### Post by Burillo on 2009-05-20
I've been fiddling around with ntfs-3g and found out that ubuntu repos seem to have an old version of ntfs-3g. so i purged it and compiled a fresh one from the website (and also reinstalled fuse packages and anything relevant to filesystem handling). compilation went ok, tried mounting - still doesn't work. i did as the website suggested - created a group called ntfsuser, added myself there and executed these under root:
```
chown root.ntfsuser $(which ntfs-3g)
chmod 4750 $(which ntfs-3g)

```
and tried mounting again. I don't know whether the NTFS-3G folks have changed the error message or was it something i did, but now the error displayed is different from the one i used to have. I attached a screenshot of the error.

Is there any place other than dmesg i can look for some clues? like system logs or something... I am really pissed off by now and won't stop until ntfs-3g will work perfectly...

---

### Post by Burillo on 2009-05-26
This is my fstab entries relating to these drives (should they even be there???):

> # Entry for /dev/sdb1 :
UUID=54420864704AD1B2 /media/HDD ntfs-3g rw,users,exec,noauto,locale=ru_RU.cp1251,iocharset=ru_RU.cp1251 0 0
# Entry for /dev/sdb2 :
UUID=3920C19A3AD2294B /media/STORAGE ntfs-3g rw,users,exec,noauto,locale=ru_RU.cp1251,iocharset=ru_RU.cp1251 0 0
# Entry for /dev/sdb3 :
UUID=f44f29bc-f824-4dfb-a786-f3225d496b74 /media/Linux ext2 rw,users,noauto,exec,relatime 0 0

---

### Post by Burillo on 2009-05-26
If i remove those entries from fstab the following error occurs while mounting:

Cannot get volume.fstype.alternative

Does this mean something?

EDIT:

Seems like the problem is gone.

So, in case of anyone has this - here are the steps i took:

1) clean fstab from entries relating to those drives
2) (re)install ntfs-config and enable all the options

---

### Post by robgora on 2009-05-27
> **Burillo said:**
> If i remove those entries from fstab the following error occurs while mounting:

Cannot get volume.fstype.alternative

Does this mean something?

EDIT:

Seems like the problem is gone.

So, in case of anyone has this - here are the steps i took:

1) clean fstab from entries relating to those drives
2) (re)install ntfs-config and enable all the options

I am also experiencing this exact issue and I have re-installed ntfs-config but it still won't automount. The funny thing is that it automounted fine when I was running the 64 bit version of Ubuntu 8.04. Any other suggestions? Mine will just show up as a USB drive but I can manually mount it. And yes I have a Seagate hard drive.

---

