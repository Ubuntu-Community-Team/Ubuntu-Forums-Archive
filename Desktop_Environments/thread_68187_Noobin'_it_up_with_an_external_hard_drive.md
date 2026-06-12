---
title: "Noobin' it up with an external hard drive"
date: 2005-09-22
forum: Desktop Environments
---

### Post by twoseids on 2005-09-22
Hey all,

Been on Linux for a couple months now (Ubuntu Hoary is my first and only distro so far) and just switched to KDE the other day - and I like it!

Anyway, I just got a Western Digital USB hard drive, but I can't for the life of me get my computer to see it.  Is there a simple command I can do to mount it?  I tried mount -a but that didn't work.  I totally don't know what I'm doing, can you tell?   \\:D/ 

Or do I need a little more configuration before I can use it?  Oh, by the way, it's formatted for NTFS, so do I need to reformat it for FAT first?  Help!

---

### Post by aysiu on 2005-09-22
If it's FAT, as least you'll be able to write to it. NTFS has to be read-only, for the most part.

---

### Post by twoseids on 2005-09-22
[QUOTE=aysiu]If it's FAT, as least you'll be able to write to it. NTFS has to be read-only, for the most part.[/QUOTE]
 Crap!  How do I re-format it for FAT?  Is it easier to do in Windows?  Or can I do it in Ubuntu?

---

### Post by mlomker on 2005-09-22
If there isn't anything on it and you'll be using it just under your linux box then I'd reformat it.  

If you want an icon for it on your desktop then go into Control Center, Desktop, Behavior, Device Icons and make sure the right boxes are checked (maybe just check all of them).

**sudo fdisk -l** will give you a list of partitions that are visible and **sudo mkfs.ext3 /dev/partition** will format it for ext3.

You can look at my [mini how-to](http://ubuntuforums.org/showpost.php?p=355988&postcount=8) on fstab once you've formated your partition.  You can leave it NTFS but it's read-only  with Ubuntu's kernel and that's probably not useful.

---

### Post by mlomker on 2005-09-22
[QUOTE=twoseids]Crap!  How do I re-format it for FAT? [/QUOTE]

You could do it in Windows, otherwise **mkfs.vfat /dev/partition**.

---

### Post by twoseids on 2005-09-22
[QUOTE=mlomker]You could do it in Windows, otherwise **mkfs.vfat /dev/partition**.[/QUOTE]
 Thanks, that looks really helpful.  One more question, if I may:

What's the difference between ext3 and FAT?  Pros and cons for doing it one way over the other?

By the way, this drive would probably be used by me (Linux) and my wife (Windows), if possible.  If not possible, then I'll just use it on my machine and let my wife figure something else out for hers.  (We're mainly using it to store pics and vids)

Thanks!

---

### Post by GeneralZod on 2005-09-22
[QUOTE=twoseids]Thanks, that looks really helpful.  One more question, if I may:

What's the difference between ext3 and FAT?  Pros and cons for doing it one way over the other?

By the way, this drive would probably be used by me (Linux) and my wife (Windows), if possible.  If not possible, then I'll just use it on my machine and let my wife figure something else out for hers.  (We're mainly using it to store pics and vids)

Thanks![/QUOTE]

FAT is a rather simple, dated and inferior filesystem whose sole advantage stems from the fact that it is readable and writable by pretty much every OS in existence ;)  Apparently there is now a free ext2 reader/ writer for Windows, though, but I can't  remember what it's called, I'm afraid :(

---

### Post by twoseids on 2005-09-22
[QUOTE=GeneralZod]FAT is a rather simple, dated and inferior filesystem whose sole advantage stems from the fact that it is readable and writable by pretty much every OS in existence ;)  Apparently there is now a free ext2 reader/ writer for Windows, though, but I can't  remember what it's called, I'm afraid :([/QUOTE]
 Sounds like I need to do FAT then.  Unless anyone knows of any good reasons why I shouldn't?  (finger hovering over the ENTER button)

---

### Post by twoseids on 2005-09-22
Okay, I told you I'm a noob.  I just tried typing **mkfs.vfat /dev/partition** and it didn't work.  Duhhh...I guess I was supposed to substitute the word "partition" with the actual partition, huh?   :? 

So here's what I got when I typed **sudo fdisk -l**:

```
Device Boot      Start         End         Blocks   Id  System
/dev/hda1           1         4         32098+       de  Dell Utility
/dev/hda2   *      5           1794    14378175    7  HPFS/NTFS
/dev/hda3        1795        2432      5124735     f   W95 Ext'd (LBA)
/dev/hda5   *   1795        1807      104391        83  Linux
/dev/hda6        1808        2367     4498168+      83  Linux
/dev/hda7        2368        2432        522081     82  Linux swap / Solaris
```

So what do I type in place of "partition" in the command above?

---

### Post by mlomker on 2005-09-22
> 
```
Device Boot      Start         End         Blocks   Id  System
/dev/hda2   *      5           1794    14378175    7  HPFS/NTFS

```

So what do I type in place of "partition" in the command above?

Do you only have one NTFS drive?  If so, then that's it.  You can type **df -h** to take a look at the size and see if that sounds right.  Needless to say, you need to be right on this.   ;-)

---

### Post by GeneralZod on 2005-09-22
[QUOTE=mlomker]Do you only have one NTFS drive?  If so, then that's it.  You can type **df -h** to take a look at the size and see if that sounds right.  Needless to say, you need to be right on this.   ;-)[/QUOTE]

Woah, wait - would a USB drive be presented as a /dev/hdx?

---

### Post by twoseids on 2005-09-22
[QUOTE=mlomker]Do you only have one NTFS drive?  If so, then that's it.  You can type **df -h** to take a look at the size and see if that sounds right.  Needless to say, you need to be right on this.   ;-)[/QUOTE]
 No, that's my Windows partition.  Maybe my external drive isn't showing up at all?  (The external drive is 40GB by the way)

---

### Post by mlomker on 2005-09-22
[QUOTE=GeneralZod]Woah, wait - would a USB drive be presented as a /dev/hdx?[/QUOTE]

You're right.  It should be /dev/sd?

---

### Post by mlomker on 2005-09-22
> Maybe my external drive isn't showing up at all?  (The external drive is 40GB by the way)

Sounds like it.  Here's some diagnostic commands:

```

lsusb
dmesg | tail #right after plugging it in
cat /proc/scsi/scsi

```

In case you're wondering...lots of things look like 'scsi' devices to linux.

---

### Post by twoseids on 2005-09-22
```
eric@eric:~$ lsusb
Bus 001 Device 003: ID 046d:c016 Logitech, Inc. Optical Mouse
Bus 001 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 001 Device 001: ID 0000:0000
eric@eric:~$ dmesg | tail #right after plugging it in
ACPI: Battery Slot [BAT1] (battery absent)
ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
eth0: no IPv6 routers present
cs: IO port probe 0x0100-0x04ff: clean.
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
atkbd.c: Keyboard on isa0060/serio0 reports too many keys pressed.
eric@eric:~$ cat /proc/scsi/scsi
cat: /proc/scsi/scsi: No such file or directory
```

---

### Post by mlomker on 2005-09-22
It isn't being seen by your machine at all!  If it cannot be seen with **lsusb** then it might as well be unplugged.  I assume it's turned on and all that?  You said that it worked with Windows?

---

### Post by twoseids on 2005-09-22
[QUOTE=mlomker]It isn't being seen by your machine at all!  If it cannot be seen with **lsusb** then it might as well be unplugged.  I assume it's turned on and all that?  You said that it worked with Windows?[/QUOTE]
 Nope, haven't turned it on with Windows yet. The box says it's Linux-compatible, so I didn't even bother.  Tell ya what - lemme go over to Windows and check it out - and then I'll come back.

I have both USB things plugged in too, just to be sure there is enough power...

---

### Post by twoseids on 2005-09-22
[QUOTE=twoseids]Nope, haven't turned it on with Windows yet. The box says it's Linux-compatible, so I didn't even bother.  Tell ya what - lemme go over to Windows and check it out - and then I'll come back.

I have both USB things plugged in too, just to be sure there is enough power...[/QUOTE]
 It's not being recognized over on Windows either. Looks like a lot of time wasted as this appears to be a bum drive. I'll be taking this back to the shop tomorrow.  Thanks for all your comments, though - I think it will get me started when I have a drive that WORKS!

---

### Post by twoseids on 2005-09-23
Well, my problem's solved.  For the sake of those whose Linux level is at or below mine, I'm putting my solution here:

1.  The hard drive wasn't getting enough power from the USB port, and I was hooking up the second power supply incorrectly.
2.  Once it was hooked up correctly, I could see the drive in Windows - it was NTFS format.
3.  Went to Linux, and it was there too - as /dev/sda
4.  Followed mlomker's directions and typed:  **mkfs.vfat /dev/sda5**
5.  When I did **sudo fdisk -l**, it still looked like it was NTFS, but when I tried writing to the drive, it worked!
6.  When I went to Windows later and checked out the properties, it was indeed FAT

So thanks to all for your help!

---

