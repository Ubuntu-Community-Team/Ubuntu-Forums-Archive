---
title: "Installing Intrepid (Ubuntu 8.10) got error"
date: 2008-12-24
forum: General Help
---

### Post by l3modz on 2008-12-24
Hi all, after I can't use my [offline repos]("http://ubuntuforums.org/showthread.php?t=952461"), I decises tu use Intrepid now... but I've got error when install it

First install it sucsess, when it proses require reboot and moved the Installation CDROM, then it rebooted....
All of booting was fine, until I enter my user and password on Gnome... but it freeze, I've wait for a looooooooooong time :confused: but I can use my Desktop, then I install it again but I got this error:

```

[  0.445777] ACPI:Aborted because broken padding
[ 2.10.1667] Crc error
[  2.190332] Kernel panic - not Syncing:VFS:Unable to mount root fs on unknown-block (8.10)

```


BTW I've check md5 for my ISO, it OK. And I've installed linux for ten time on this hardisk by using it CDROM??? like Knoppix, Mandriva, Redhat 9, Fedora, even Windows???

Any idea about this ??? :confused: :confused:

---

### Post by l3modz on 2008-12-24
How I can resolve it???

Ive search for all thread, I've just [got this]("http://ubuntuforums.org/showthread.php?t=966436") but I still have problem with login to my Gnome desktop

---

### Post by l3modz on 2008-12-24
I've try change my harddisk ! well I tried again and now I got this error, not same from above !!!


```
[  0.446548] ACPI:Aborted because no cpio magic
[ 2.10.1350] Crc error
[  2.190172] Kernel panic - not Syncing:VFS:Unable to mount root fs on unknown-block (8.10)
```

I give up... ](*,)

:guitar:

---

### Post by bujang on 2008-12-26
> **l3modz said:**
> I've try change my harddisk ! well I tried again and now I got this error, not same from above !!!

I give up... ](*,)

:guitar:

Hi I'm newbie to Ubuntu to... When I want to install it, I got this error to ???
```
[  0.447517] ACPI:Aborted because broken padding
[ 2.101870] Crc error
[  2.190512] Kernel panic - not Syncing:VFS:Unable to mount root fs on unknown-block (8.10)
```

I've try to boot this PC with KNOPPIX, this my hardware::
```

.........................
.........................
Autocofigurating device .... ....... ..... Done
Mouse is ImPS/2 Logithech Wheel Mouse at /dev/input/mice
Soundcard : Intel Corporation 82880 1DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller driver=snd-intel8x0
AGP bridge detected
 Video is Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device, using Xorg(i810) Server
 Monitor is SAM0116, H:30-55kHz, V:50-120Hz
 Using Modes "800x600" "640x480"
...........
...........

```
all detected by KNOPPIX and well, like my HDD, graphics even my sound, then I check my HDD0
```

root@Knoppix:~ fdisk -l /dev/hda
Disk /dev/hda:20.0GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Unit=cylinders of 16065 * 512 = 822528 bytes

   Device      Boot      Start      End         Block     Id       System
/dev/hda1                  1        2434     19551073+    83       Linux

```


But when I booting installer Ubuntu 8.10 from CDROM, I get this error ???
Is that my HDD have bad sectors? or my CDROM can read the Ubuntu CD??? it an old CDROM :lolflag:

Do you have any idea if I want to install Ubuntu to my PC??

Thanks in advance, sorry my english bad :D

---

### Post by bujang on 2008-12-27
well after I change CDROM with new one, I success install Intrepid

but when I'm login to Gnome after enter my user and password desktop it hang...


I can use gnome desktop....???? :confused:
Help

Thanks in advance

---

### Post by bujang on 2008-12-27
what is this???
did I must change my PC too ??? huh... :confused:

---

### Post by Trab on 2009-01-28
hello all, hopefully this may help some of you.

I just had this problem today. For me, it was related to an issue with my RAM (I believe either the slot is bad, or one of my sticks is bad).

In my case, I couldn't even get Vista (which is on a seperate partition) to boot. I ended up moving one of my RAM sticks to a different slot, and that fixed it.

I believe CRC error has something to do with RAM, but Google will be much more helpful.

cheers,
Trab

---

### Post by itsjustarumour on 2009-02-07
[QUOTE=l

```

[  0.445777] ACPI:Aborted because broken padding
[ 2.10.1667] Crc error
[  2.190332] Kernel panic - not Syncing:VFS:Unable to mount root fs on unknown-block (8.10)

```
[/QUOTE]

I've just had the same thing when trying to install the latest Kubuntu Jaunty 9.04 Alpha 4 from a CDR Image I had downloaded and burnt with K3b.

I tried burning it a second time, with the "verify data" box checked.  After it had burnt the image, it checked it and came up with an error.  Looked like my download had got corrupted somehow.  I downloaded and burnt the image again, and *voila*, all OK.

Hope this might help someone  :-)

---

### Post by dstein on 2009-07-16
My computer froze this morning while I was using Firefox. Ctrl-Alt-Backspace and Ctrl-Alt-F* did not do anything. When I restarted, I got the same error messages as reported in this post. None of the kernels that are listed in GRUB work - I always get errors. Any ideas how to fix this or why this happened? Thanks.

---

### Post by Sofa_King_Cool79 on 2009-08-03
I am also getting very similar errors to this. The only thing I can point it to is Bad RAM. I have a new harddrive and new cd/dvd rom and the CD is not all scratched up or anything. I cannot use any of the kernels in the GRUB or run ubuntu off of the CD. I get no cpio magic and other kernel panic errors. When I collect enough beer cans to get some new RAM I will reply back with my results. 
-Regards

---

### Post by dstein on 2009-08-08
It was in fact bad RAM. I ran memtest86+ on the GRUB menu, and it consistently detected errors at the same address. I removed one of my sticks and no longer got the error. Should I be worried that my personal files are corrupt. For the most part, things worked fine with the bad memory.

---

