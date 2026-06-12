---
title: "unable to start XP from GRUB"
date: 2009-05-16
forum: General Help
---

### Post by droople on 2009-05-16
Hi All

I installed 9.04 on my external hard driver and connect to my laptop.

I can start ubuntu after I change the grub from "(hd1,0)" to "(hd0,0)". Grub always think the disk which it's installed is the first hard disk, right?

But when I tried to start windows XP, it shows "starting up...." then nothing happened...

Here is the grub
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
chainloader	+1

Any idea?

Thank you in advance.

Cheers

---

### Post by Legace on 2009-05-16
Open terminal, type in **sudo fdisk -l** and post the output here.

---

### Post by 73ckn797 on 2009-05-16
With the external drive connected what is the output of terminal command:

```
blkid
```

That will show drive order as seen by the system.

---

### Post by droople on 2009-05-16
Hi Legace and 73ckn797

Thank you for your help.

Currently I've got another problem: unable to entre graphic longin screen, so unable to try your terminal command :(

[http://ubuntuforums.org/showthread.php?p=7293247#post7293247](http://ubuntuforums.org/showthread.php?p=7293247#post7293247)

---

### Post by droople on 2009-05-17
Ok, finally, i can go into the graphic.

blkid:
```
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="ACD40AEBD40AB79A" TYPE="ntfs" 
/dev/sda5: UUID="36E00432E003F741" TYPE="ntfs" 
/dev/sda6: UUID="12BC02A4BC028309" LABEL="Music" TYPE="ntfs" 
/dev/sda7: UUID="3C50E0EB50E0AD38" LABEL="Roms" TYPE="ntfs" 
/dev/sda8: UUID="407C672C7C671BC2" LABEL="My Documents" TYPE="ntfs" 
/dev/sda9: UUID="3A28B49828B4549B" LABEL="Pagefile" TYPE="ntfs" 
/dev/sdb1: UUID="1f0bcc45-9adf-44a9-909e-eeb26a144d6f" TYPE="ext3" 
/dev/sdb5: UUID="5ba1e0b5-16e3-460b-ad95-26fd84afe418" TYPE="swap" 
/dev/sdb6: UUID="987090EC7090D27C" TYPE="ntfs" 
/dev/sdb7: UUID="CEF0EAA8F0EA964D" TYPE="ntfs" 
/dev/sdb8: UUID="FE746DD8746D9465" TYPE="ntfs" 

```

fdisk -l:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94512f6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10444    83891398+   7  HPFS/NTFS
/dev/sda2           10445       60801   404492602+   5  Extended
/dev/sda5           10445       21541    89136621    7  HPFS/NTFS
/dev/sda6           21542       34596   104864256    7  HPFS/NTFS
/dev/sda7           34597       52872   146801938+   7  HPFS/NTFS
/dev/sda8           52873       59922    56629093+   7  HPFS/NTFS
/dev/sda9           59923       60801     7060536    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2543    20426616   83  Linux
/dev/sdb2            2544        9729    57721545    f  W95 Ext'd (LBA)
/dev/sdb5            2544        2741     1590403+  82  Linux swap / Solaris
/dev/sdb6            2742        5483    22025083+   7  HPFS/NTFS
/dev/sdb7            5484        8225    22025083+   7  HPFS/NTFS
/dev/sdb8            8226        9729    12080848+   7  HPFS/NTFS

```

Any suggestion?

---

### Post by droople on 2009-05-17
bump

---

### Post by Legace on 2009-05-17
Try this:
```
title		Microsoft Windows XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by 73ckn797 on 2009-05-17
> **droople said:**
> Ok, finally, i can go into the graphic.

blkid:
```
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="ACD40AEBD40AB79A" TYPE="ntfs" 
/dev/sda5: UUID="36E00432E003F741" TYPE="ntfs" 
/dev/sda6: UUID="12BC02A4BC028309" LABEL="Music" TYPE="ntfs" 
/dev/sda7: UUID="3C50E0EB50E0AD38" LABEL="Roms" TYPE="ntfs" 
/dev/sda8: UUID="407C672C7C671BC2" LABEL="My Documents" TYPE="ntfs" 
/dev/sda9: UUID="3A28B49828B4549B" LABEL="Pagefile" TYPE="ntfs" 
/dev/sdb1: UUID="1f0bcc45-9adf-44a9-909e-eeb26a144d6f" TYPE="ext3" 
/dev/sdb5: UUID="5ba1e0b5-16e3-460b-ad95-26fd84afe418" TYPE="swap" 
/dev/sdb6: UUID="987090EC7090D27C" TYPE="ntfs" 
/dev/sdb7: UUID="CEF0EAA8F0EA964D" TYPE="ntfs" 
/dev/sdb8: UUID="FE746DD8746D9465" TYPE="ntfs" 

```fdisk -l:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94512f6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10444    83891398+   7  HPFS/NTFS
/dev/sda2           10445       60801   404492602+   5  Extended
/dev/sda5           10445       21541    89136621    7  HPFS/NTFS
/dev/sda6           21542       34596   104864256    7  HPFS/NTFS
/dev/sda7           34597       52872   146801938+   7  HPFS/NTFS
/dev/sda8           52873       59922    56629093+   7  HPFS/NTFS
/dev/sda9           59923       60801     7060536    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2543    20426616   83  Linux
/dev/sdb2            2544        9729    57721545    f  W95 Ext'd (LBA)
/dev/sdb5            2544        2741     1590403+  82  Linux swap / Solaris
/dev/sdb6            2742        5483    22025083+   7  HPFS/NTFS
/dev/sdb7            5484        8225    22025083+   7  HPFS/NTFS
/dev/sdb8            8226        9729    12080848+   7  HPFS/NTFS

```Any suggestion?

You sure have a lot of partitions! The suggestion posted by Legace ought to help.

---

### Post by droople on 2009-05-17
> **73ckn797 said:**
> You sure have a lot of partitions! The suggestion posted by Legace ought to help.

Because I have two disks.

No, if it's hd(0,0) it shows error 13, Invalid or Unsupported executiable format, as hd(0,0) is where GRUB installed, sdb, Windos XP is on sda.

If it's hd(1,0), then still "starting up...." then nothing happened...:(

---

### Post by bacardiandwatermelon on 2009-05-17
If you unplug the external drive and change grub to root		(hd0,0).. Does it boot to XP?

---

### Post by reevine on 2009-05-17
> **bacardiandwatermelon said:**
> If you unplug the external drive and change grub to root		(hd0,0).. Does it boot to XP?
there is a problem though. if he takes out his external drive. he will either get Error 15 or Error 21, because the files for grub to run off of are on the external drive inside the boot folder on the Ubuntu installation.

try what Legace said to do but dont change the root. leave it as (hd1,0)

so it should look like this:

```

title		Microsoft Windows XP
rootnoverify	(hd1,0)
savedefault
makeactive
chainloader	+1

```

so just add "makeactive" (without quotations) to your Windows listing.

some versions of windows wont boot without (XP in most cases) that because they have to be an "active" in order to boot. Vista doesn't need that because it has a slightly smarter bootloader. (Vista still sucks ;) )

---

### Post by droople on 2009-05-18
> **bacardiandwatermelon said:**
> If you unplug the external drive and change grub to root		(hd0,0).. Does it boot to XP?

My Grub is on the MBR of external disk, not internal disk.

---

### Post by droople on 2009-05-18
> **reevine said:**
> there is a problem though. if he takes out his external drive. he will either get Error 15 or Error 21, because the files for grub to run off of are on the external drive inside the boot folder on the Ubuntu installation.

try what Legace said to do but dont change the root. leave it as (hd1,0)

so it should look like this:

```

title		Microsoft Windows XP
rootnoverify	(hd1,0)
savedefault
makeactive
chainloader	+1

```

so just add "makeactive" (without quotations) to your Windows listing.

some versions of windows wont boot without (XP in most cases) that because they have to be an "active" in order to boot. Vista doesn't need that because it has a slightly smarter bootloader. (Vista still sucks ;) )

If (hd1,0), then freezing at "starting up"...

My GRUB is on external disk, not internal disk.

---

### Post by bacardiandwatermelon on 2009-05-18
> **droople said:**
> My Grub is on the MBR of external disk, not internal disk.

Oh yeah, whoops :-P

---

### Post by reevine on 2009-05-18
> **droople said:**
> If (hd1,0), then freezing at "starting up"...

My GRUB is on external disk, not internal disk.
yes the GRUB files will be on your external drive like i said but GRUB itself will be installed on your internal drive. to make it so grub is installed on your external drive do the following:

1. go into ubuntu and go to terminal.
2. type these commands (each line is a new entry):

```

sudo grub

```

```

find /boot/grub/stage1

```
you should get just (hd1,0)

let me know if you get something else

if you got (hd1,0) continue with this code:

```

root (hd1,0)

```
```

setup (hd1)

```

then exit and and shutdown. after that boot into your XP install disk and go to the recovery option. then enter:

```

fixmbr

```

reboot without the disc and you should be able to boot into windows.

dont forget to add "makeactive" in the menu.lst file. this will might make it so you can boot into windows from GRUB

hope this helps. if you dont understand how to do something just let me know

---

### Post by helofromseattle on 2009-05-18
check your boot.ini in xp, I think it might be corrupted, boot into the xp install disc and select the recovery console select your install (usally one), type your password or hit enter if you didn't set one. Now, type "fixmbr" and hit "y". Try "fixboot" if that doesn't work.;)

---

### Post by droople on 2009-05-18
> **helofromseattle said:**
> check your boot.ini in xp, I think it might be corrupted, boot into the xp install disc and select the recovery console select your install (usally one), type your password or hit enter if you didn't set one. Now, type "fixmbr" and hit "y". Try "fixboot" if that doesn't work.;)

I can boot into XP without any problem if I remove that external disk, so I think no problem in boot.ini.

---

### Post by reevine on 2009-05-18
you might want to try repairing it anyways. Ubuntu will boot into it unless there is something wrong. if you dont have any important info in your ubuntu installation then just reinstall ubuntu.

---

### Post by kulturloseramerikaner on 2009-05-19
Does your external drive use an eSATA cable?  Did you add an eSATA card to your system to allow you to connect it?  If so, try opening your box, pulling the drive from the external enclosure, and attaching it directly to the mobo w/ standard SATA cable.
I had I similar issue on my system in which I triple-boot Wintendo, Ubuntu Hardy, and PC-BSD 7.1.  I use GRUB to boot, but PC-BSD did not like the external drive and errored out when I tried to start it.  What I did was to move the drive containing BSD to the SATA port on the mobo that I had a storage drive on and move the storage drive to the external enclosure and card using the eSATA.  I then reconfigured the GRUB menu.lst so that Wintendo was on (hd0,0) and attached to the SATA port marked as 0 on the mobo, Ubuntu was on (hd1,0) and attached to the SATA port marked as 1 on the mobo, and BSD was on (hd2,0) and attached to the SATA port marked as 2 on the mobo. The storage drive now sits in the enclosure and I have no trouble booting to any OS.

---

### Post by droople on 2009-05-19
> **kulturloseramerikaner said:**
> Does your external drive use an eSATA cable?  Did you add an eSATA card to your system to allow you to connect it?  If so, try opening your box, pulling the drive from the external enclosure, and attaching it directly to the mobo w/ standard SATA cable.
I had I similar issue on my system in which I triple-boot Wintendo, Ubuntu Hardy, and PC-BSD 7.1.  I use GRUB to boot, but PC-BSD did not like the external drive and errored out when I tried to start it.  What I did was to move the drive containing BSD to the SATA port on the mobo that I had a storage drive on and move the storage drive to the external enclosure and card using the eSATA.  I then reconfigured the GRUB menu.lst so that Wintendo was on (hd0,0) and attached to the SATA port marked as 0 on the mobo, Ubuntu was on (hd1,0) and attached to the SATA port marked as 1 on the mobo, and BSD was on (hd2,0) and attached to the SATA port marked as 2 on the mobo. The storage drive now sits in the enclosure and I have no trouble booting to any OS.


It's an 2.5' IDE External Disk, connect to my laptop by USB 2.0 cable.

---

### Post by droople on 2009-05-19
> **reevine said:**
> you might want to try repairing it anyways. Ubuntu will boot into it unless there is something wrong. if you dont have any important info in your ubuntu installation then just reinstall ubuntu.

I connected my external disk to other computer, also cannot boot their XP. So, is all XP boot.ini or MBR broken?

find /boot/grub/stage1
return (hd1,0)

I'm not going to run setup (hd1) as this will change my Windows disk MBR.

I will try reinstall Ubuntu, thank you anyway.

---

### Post by reevine on 2009-05-19
ok thank you for letting me know that it wont boot into another persons windows. well i hope when you reinstall it works. good luck

---

### Post by droople on 2009-05-24
> **reevine said:**
> ok thank you for letting me know that it wont boot into another persons windows. well i hope when you reinstall it works. good luck

An update, I installed Debian, Ubuntu, OpenSuse, Slackware, Mandriva on my external disk.

Only Mandriva can automatically put linux root as hd0, and windows root as hd1.....

And only Mandriva made GRUB can boot my XP.

Here is the entry

```
title windows
root (hd1,0)
map (0x81) (0x80)
map (0x80) (0x81)
makeactive
chainloader +1
```

So the difference is the two map lines.

Can anyone explain to me?

Cheers
Jason

---

### Post by reevine on 2009-05-24
> **droople said:**
> An update, I installed Debian, Ubuntu, OpenSuse, Slackware, Mandriva on my external disk.

Only Mandriva can automatically put linux root as hd0, and windows root as hd1.....

And only Mandriva made GRUB can boot my XP.

Here is the entry

```
title windows
root (hd1,0)
map (0x81) (0x80)
map (0x80) (0x81)
makeactive
chainloader +1
```

So the difference is the two map lines.

Can anyone explain to me?

Cheers
Jason
ok when you map a drive you make it so that one drive is then moved to a "different" location. like a common map command is:

```

map (hd0) (hd1)
map (hd1) (hd0)

```

so its making hd0 become hd1. its to help grub boot the drive correctly

---

### Post by droople on 2009-05-30
> **reevine said:**
> ok when you map a drive you make it so that one drive is then moved to a "different" location. like a common map command is:

```

map (hd0) (hd1)
map (hd1) (hd0)

```

so its making hd0 become hd1. its to help grub boot the drive correctly

Hi Reevine

Could you tell me what does (0x80) mean? (hd0)?

Cheers
Jason

---

### Post by reevine on 2009-05-30
im guessing its has something to do mandriva's version of windows entry

---

### Post by VMC on 2009-05-30
> **droople said:**
> Hi Reevine

Could you tell me what does (0x80) mean? (hd0)?

Cheers
Jason

 0x80 boots the first hard drive on the system

---

### Post by droople on 2009-05-30
> **reevine said:**
> im guessing its has something to do mandriva's version of windows entry

thanks a lot.

You mean different distibution using different GRUB entry, and GRUB still can recognise it?

huh....

Cheers

---

### Post by reevine on 2009-06-02
well there are a couple of different ways to do one thing in terminal and other stuff so it may apply to Grub too

---

### Post by droople on 2009-06-03
thanks a lot Reevine

---

### Post by reevine on 2009-06-03
no problem glad to help

---

