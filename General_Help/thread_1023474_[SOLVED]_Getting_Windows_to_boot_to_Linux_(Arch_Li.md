---
title: "[SOLVED] Getting Windows to boot to Linux (Arch Linux, but problem is not Arch-specif"
date: 2008-12-27
forum: General Help
---

### Post by Nicholas Escalona on 2008-12-27
I was happily configuring my base Arch install (dual booting with WinXP MCE SP3) when I got the bright idea to set Windows to autoboot, through GRUB. I did this because the rest of my family isn't Linux-compatible, so I figured whenever I wanted to run Linux, I might as well just hit whatever button at boot-time to arrest autobooting Windows, watch GRUB pop up, and select Linux.

It didn't work that way though, probably because NTLDR is the bootloader on the MBR, rather than GRUB. I want to keep it that way, because GRUB can't boot Windows. The problem is, when the system boots, it never even glances at my Linux partitions or at GRUB, the system loads up NTLDR which boots Windows right away.

So basically, I need to work with boot.ini so I get a menu with Windows and Linux before either boots. I've already set this menu up, all that remains is to make the Linux selection actually do something. What follows is my partition setup on the computer, as written to disk when I installed Arch (i.e., Arch is recognizing its own partitions as unbootable)

```

Partition  File system  Contents          Appx. size  Bootable?  Type
sda1       NTFS         Windows XP SP2    100 GiB     flagged    Primary
sda2       -            Arch Linux swap   1 GiB       unflagged  Primary
sda3       ext3         Arch Linux /      16 GiB      unflagged  Primary
sda4       ext3         Arch Linux /home  33 GiB      unflagged  Primary

```

What follows is the contents of my boot.ini. It is perfectly unchanged from original XP install, except for the addition of the last line (and I lowered timeout from 30 to 10).

```

[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(3)="Arch Linux"

```

The "Arch Linux" selection, as I mentioned, does not work. It just ends up rebooting the system and looping back to the NTLDR menu. This is probably because the root partition isn't flagged bootable. (I would have flagged it, except the Arch installation wiki never said to)

I've been Googling for solutions, but all the HOWTOs on Linux/Windows dual-booting I've found (e.g. [this]("http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html")) do all the bootloader configuration from inside Linux. Of course, that's my very problem; I've got a chest with its key locked inside.

Ideally, I want to be able to reboot the system and have a bootloader menu pop up with both Windows and Linux options. The Windows option will automatically be chosen after 10 seconds.

---

### Post by Skripka on 2008-12-27
Slow down...what do you mean GRUB can't boot windows?  

I just booted my WinXP drive via GRUB this afternoon. :confused:

---

### Post by Nicholas Escalona on 2008-12-28
GRUB only boots Windows by telling NTLDR to, IIRC. And NTLDR can't boot Windows unless its in the MBR. Probably.

This is why GRUB normally has an unusual entry for Windows in its menu config file. There is no kernel or initial RAM disk (initrd) specified for Grub to boot. I think the chainloader +1 bit is the part that calls NTLDR.

```

title Windows XP
rootnoverify (hd0,0)
chainloader +1

```

Edit: right, I edited before seeing post below

---

### Post by Sealbhach on 2008-12-28
Grub boots Windows using a Chainloader, something like this in the /boot/grub/menu.lst
```

# (8) Windows
title Win98
root  (hd0,0)
makeactive
chainloader +1

```

---

### Post by logos34 on 2008-12-28
> **Nicholas Escalona said:**
> 
Ideally, I want to be able to reboot the system and have a bootloader menu pop up with both Windows and Linux options. The Windows option will automatically be chosen after 10 seconds.

Assuming Sealbach's entry works:

you can make windows boot first by looking around for a 'default' OS line (I believe) in Arch menu.lst and adjusting it accordingly.

---

### Post by Nicholas Escalona on 2008-12-28
> **logos34 said:**
> Assuming Sealbach's entry works:

you can make windows boot first by looking around for a 'default' OS line (I believe) in Arch menu.lst and adjusting it accordingly.

That's the opposite of what I'm trying to do. In fact, I did exactly that, and it caused all of my current problems. I'd love to edit the menu.list file (and remove Windows from the default spot), but it's in a separate partition, ext3 formatted, so Windows can't touch it.

---

### Post by logos34 on 2008-12-28
> **Nicholas Escalona said:**
> That's the opposite of what I'm trying to do. In fact, I did exactly that, and it caused all of my current problems. I'd love to edit the menu.list file (and remove Windows from the default spot), but it's in a separate partition, ext3 formatted, so Windows can't touch it.

You can access your linux partition with [fs-driver.]("http://www.fs-driver.org/")  Very popular.

If you want to use windows to boot linux, I think all you need to do is correct one mistake:
> 
multi(0)disk(0)rdisk(0)partition(3)="Arch Linux"

should be

> c:\linux.bin="Linux"

But first you need to boot from a live cd, write grub to the Arch / partition, run the dd command, and copy the 'linux.bin' file or whatever you name it to the windows c:

---

### Post by Nicholas Escalona on 2008-12-28
> **logos34 said:**
> But first you need to boot from a live cd, write grub to the Arch / partition, run the dd command, and copy the 'linux.bin' file or whatever you name it to the windows c:

I'm a Linux noob, could you explain how I can run GRUB from the LiveCD?

Edit: Oh hang on, I don't think that'll work. Arch works on a rolling release system. Wouldn't I have to update the linux.bin every time I see an update?

Perhaps instead I'll use GRUB to choose between Windows and Linux.

---

### Post by logos34 on 2008-12-28
> **Nicholas Escalona said:**
> I'm a Linux noob, could you explain how I can run GRUB from the LiveCD?

Edit: Oh hang on, I don't think that'll work. Arch works on a rolling release system. Wouldn't I have to update the linux.bin every time I see an update?

Perhaps instead I'll use GRUB to choose between Windows and Linux.

no, you won't need to update it.  You're simply writing grub's stage1 to the bootsector/first 512 bytes of Arch / (sda3). 

From a terminal on the live cd:

> sudo grub

grub> root (hd0,2)
grub> setup (hd0,2)
grub> quit

Then, run the dd command as described in the link you referenced. Either copy it directly to windows C: (if you can mount windows partition with write access), or put it on a usb flash or floppy, and transfer it.  Edit boot.ini with the entry.

---

### Post by Nicholas Escalona on 2008-12-28
Thanks! But how would I mount a flash drive, and where would its directory appear?

---

### Post by billgoldberg on 2008-12-28
Wouldn't it be easier to just reinstall the grub and make Windows the default boot option?

ps:

rootnoverify (hd0,1)

didn't work for me.

I had to just use

root (hd0,1)

--

My grub entry for Windows (Windows 7) is:

# (2) Windows
title Windows 7
root (hd0,1)
makeactive
chainloader +1

---

### Post by billgoldberg on 2008-12-28
> **Nicholas Escalona said:**
> Thanks! But how would I mount a flash drive, and where would its directory appear?

well,

make a new folder in /media and call it flashdrive (or something)

```
sudo mkdir /media/flashdrive
```

Then use the command 

```
sudo fdisk -l
```

to find on what partition your flash drive has.

Let's say it has /dev/sdb2

You can then mount /dev/sdb2 using

```
sudo mount /dev/sdb2 /media/flashdrive
```

---

### Post by bodhi.zazen on 2008-12-28
Moved to general help.

The Cafe is not for support threads.

---

### Post by Nicholas Escalona on 2008-12-28
billgoldberg's suggestion worked perfectly. Just one issue remains. Since my system is partitioned so [FONT="Courier New"]/boot[/FONT] is in the same partition with [FONT="Courier New"]/[/FONT], need I use dd on the entire root partition? For example, will this line work?```
dd if=/dev/sda3/boot of=/mnt/usbflash/linux.bin bs=512 count=1
```I've checked that both the root partition and the USB flash drive partition are mounted correctly.

---

### Post by logos34 on 2008-12-28
> **Nicholas Escalona said:**
> ```
dd if=/dev/sda3/boot of=/mnt/usbflash/linux.bin bs=512 count=1
```

no, just

> dd if=/dev/sda3 of=/mnt/usbflash/linux.bin bs=512 count=1

---

### Post by Nicholas Escalona on 2008-12-28
Oh of course, it just copies the boot sector, first 512 B. Next time I should read.

Problem resolved, system works great. Thanks all.

---

