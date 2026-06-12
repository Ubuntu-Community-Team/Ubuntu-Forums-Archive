---
title: "windows xp and ubuntu dual boot, find the xp"
date: 2005-12-16
forum: Desktop Environments
---

### Post by tipi on 2005-12-16
Hi guys,

Yesterday i sold my notebook that had only ubuntu on it,
so now (since i can't miss it anymore) I tried to install ubuntu on my desktop pc 
trying to get a dualboot with windows xp,
however something went wrong and now there's no option at startup
asking "xp or ubuntu"

heres a
sudo fdisk -l

Schijf /dev/hda: 81.9 GB, 81964302336 bytes
255 koppen, 63 sectoren/spoor, 9964 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hda1   *           1        6508    52275478+  83  Linux
/dev/hda2            6509        9964    27760320    f  W95 Ext'd (LBA)
/dev/hda5            6780        9964    25575448+   7  HPFS/NTFS
/dev/hda6            6509        6779     2176744+  82  Linux swap / Solaris

Partitietabel ingangen zijn niet in schijfvolgorde

Schijf /dev/hdb: 163.9 GB, 163928604672 bytes
255 koppen, 63 sectoren/spoor, 19929 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hdb1               1       19928   160071628+   7  HPFS/NTFS
thijs@ubuntutut:~$

windows is still on there somewhere
also this is another disk in the pc containing all my music, movies etc
Schijf /dev/hdb: 163.9 GB, 163928604672 bytes
also unable to acces it from ubuntu

how can i fix this
anyone?
greetz from .be

---

### Post by Sutekh on 2005-12-16
```

/dev/hda5 6780 9964 25575448+ 7 HPFS/NTFS

```
That looks like the WinXP partition.

Did you install GRUB (the bootloader) when you isntalled Ubuntu?  Do you remember where you installed it?  

What happens when you're PC boots, does it load Windows, Ubuntu or do nothing?

---

### Post by tipi on 2005-12-17
ubuntu boots like it always does , first thing i see at startup
is grub loading press esc. to ... 
guess that's the standard message .

---

### Post by Sutekh on 2005-12-17
When you say 

" first thing i see at startup
is grub loading press esc. to ... "

What happens when you press escape? Anything

Does GRUB load up with any options at all?

---

### Post by Luuraja on 2005-12-17
[QUOTE=tipi]Hi guys,

Yesterday i sold my notebook that had only ubuntu on it,
so now (since i can't miss it anymore) I tried to install ubuntu on my desktop pc 
trying to get a dualboot with windows xp,
however something went wrong and now there's no option at startup
asking "xp or ubuntu"
...........
how can i fix this
anyone?
greetz from .be[/QUOTE]

Take a look on GAG Bootloader. It can be found at [http://gag.sourceforge.net/]("http://gag.sourceforge.net/")
Very simple to configure, understands lot of different opsys-es.

---

### Post by schdefan on 2005-12-17
if you see grub at boot time and afterwards ubuntu is booting you need to configure /boot/grub/menu.lst.
You have to add an entry for windows.
In your case it should look like the following if you installed WinXP on /dev/hda5
```
title           Ubuntu kernel 2.6.12-9-386 
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda5 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda5
title           Microsoft Windows XP Professional
root            (hd0,4)
savedefault
makeactive
chainloader     +1
```

And also you have to increase the timeout higher than 0 to see the grub menu.

schdefan

---

### Post by bonzodog on 2005-12-17
[QUOTE=Luuraja]Take a look on GAG Bootloader. It can be found at [http://gag.sourceforge.net/]("http://gag.sourceforge.net/")
Very simple to configure, understands lot of different opsys-es.[/QUOTE]

um...this bootloader project doesn't recognise ext3 or reiserfs partitions AFAIK, and is outdated. I have a friend who has been using this on some other systems, but we went to see if would work in ubuntu, and it wouldn't as it cannot see ext3.

---

### Post by Luuraja on 2005-12-17
Very valuable info. Thanks, schdefan!

GAG Bootloader I love since I dealed with BSD (PC-BSD), which install with default bootloader messed up all my partitions. After this experience (installed XP again) I found GAG and after that I have no problems.
Gag recognizes Win NTFS or BSD or Linux partitions without any trouble. You must only have to find them using Setup and make them bootable.

---

### Post by tipi on 2005-12-17
okay home from work , 
so now i'm gonna try all this and see what it does,
thx for your fast replies

---

### Post by tipi on 2005-12-17
i started allover again 
after using the gag app. system was totaly screwed up
so did a total clean install of winxp leaving 40gig of the 80 gig drive unpartioned
than booted from the ubuntu cd and used the option "use remaining space
to install ubuntu" after this it asked if i wanted to dual boot with winxp....
thats all good now ,love it
also, now i can see the windowspart in ubuntu and read it.
Only one other question.... how can I see my backup hd,

this one:  
"Schijf /dev/hdb: 163.9 GB, 163928604672 bytes"

this is what "sudo fdisk -l" says

Schijf /dev/hda: 81.9 GB, 81964302336 bytes
255 koppen, 63 sectoren/spoor, 9964 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hda1               1        5099    40957686    7  HPFS/NTFS
/dev/hda2   *        5100        9762    37455547+  83  Linux
/dev/hda3            9763        9964     1622565    5  Uitgebreid
/dev/hda5            9763        9964     1622533+  82  Linux swap / Solaris

[COLOR="Red"]Schijf /dev/hdb: 163.9 GB, 163928604672 bytes
255 koppen, 63 sectoren/spoor, 19929 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes[/COLOR]

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hdb1               1       19928   160071628+   7  HPFS/NTFS

---

### Post by Toxicity on 2005-12-17
wait wait wait, with dual boot if you have grub installed, and have access to your ubuntu partition you shouldn't have to format your windows partition or anything drastic... if you knew the identifiers. But with grub you generally do get that message standard in some cases. basically pressing esc shows the real menu where as doing nothing loads the default with no prompt. If you edit the grub file to not hide the menu and wait say 10 seconds it probably would have showed up fine... if not you would simply add a block for loading your windows partition.

Hah... but the foreigness in there kind of throws me, so excuse my ignorance.

---

### Post by daibak on 2005-12-27
[QUOTE=tipi]i started allover again 
after using the gag app. system was totaly screwed up
so did a total clean install of winxp leaving 40gig of the 80 gig drive unpartioned
...
thats all good now ,love it
also, now i can see the windowspart in ubuntu and read it.
Only one other question.... how can I see my backup hd,

this one:  
"Schijf /dev/hdb: 163.9 GB, 163928604672 bytes"

this is what "sudo fdisk -l" says
[/QUOTE]

Not clear what you've done and what you're asking.
Do I understand you have an internal (IDE) 80GB hard drive plus an external  USB or FireWire hard drive, and that you can see all your internal partitions but none of the external disk ones?

If so, my three-year-old HP Pavilion notebook with 30GB IDE disk and 160GB external FireWire disk drives never let me see the external drive at boot... and that's not a Ubuntu problem. That's any OS, Linux or Windows, unless you have a newer BIOS with a USB boot option. There are many Linux gurus who recompile their own start-up initrd (temporary RAM disk in memory) with pre-loaded SCSI modules and claim to circumvent this ckicken & egg BIOS Catch-22 but that's way over the head of folks like me starting out in Linux.

I dual-boot from a GAG 4.5d floppy whenever notebook is docked so I know a GAG floppy set-up/boot diskette will quickly reveal this is the case if you cycle 1-9 through all disk options to Add OS. GAG only sees Windows FAT16, FAT32 and NTFS partitions as well as all flavors of Linux on the internal hard drive in such a case.

Your formatted Windows FAT32 (read/write) and NTFS (normally read-only in Linux for data safety) partitions should show on both internal and external drives once Ubuntu 5.10 loads. Type in Breezy terminal if using GNOME

```
sudo gedit /etc/fstab
```

to see exactly what devices are available, and then make any additional mount partition additions to /etc/fstab to take effect next time you boot up.

---

### Post by icarius on 2005-12-27
I recently installed Ubuntu on my laptop in addition to XP. I used Partition magic within windows to create an unallocated partition. I then rebooted with an iso image of ubuntu on a DVD in my drive and installed it on the unallocated partition, which it partitioned itself into a swap and a ext3 partition, at the end it asked me if I wanted to install grub, and you have to say yes. I hope this helps, it worked like a charm.

---

