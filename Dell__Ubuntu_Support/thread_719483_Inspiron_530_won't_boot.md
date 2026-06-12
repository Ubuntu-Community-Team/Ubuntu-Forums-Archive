---
title: "Inspiron 530 won't boot"
date: 2008-03-09
forum: Dell  Ubuntu Support
---

### Post by Jalfro on 2008-03-09
I have a new Dell Inspiron 530 with Ubuntu 7.10 pre-installed.  It will only occasionally boot to the login screen, even when booting from a CD.  It regularly goes to something called Busybox with the following prompt: (initramfs)

I have no idea what this means.  Please help.:confused:

---

### Post by gbrainin on 2008-03-09
It means that something is wrong.  Busybox is a very small system that gives basic unix-like functionality; initramfs is a RAM-based file system.  These are used as sort of a "rescue" system when something goes wrong with the main OS.

The question, then, is why does your system sometimes think it needs to boot into rescue mode?  That requires some more experimenting.  Since it happens with the live CD as well as the main system, my first guess is hardware.

Therefore, I would suggest that you boot into the Dell hardware utility partition and run the hardware tests.  I think this is one of the selections in the GRUB menu; if not, you need to hit F12 at the initial splash screen.

If you do find a hardware problem, DO NOT call the regular Dell support line.  They will not know what to do with you, even if the problem has nothing to do with Windows.  Call the Dell Linux support line at 1-866-622-1947.  Actually, come to think of it, it wouldn't hurt to try them even if you don't get any results from the hardware tests (but I would still run them first).

Good luck!

---

### Post by al_mckin on 2008-03-10
Ever see anything like this?

[http://ubuntuforums.org/showthread.php?t=720879](http://ubuntuforums.org/showthread.php?t=720879)

---

### Post by Aearenda on 2008-03-10
I have seen this on my 530 - see if this helps: [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/USB-SATA_race_condition_causes_hang](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/USB-SATA_race_condition_causes_hang)

This applies to Feisty, but also works on Gutsy, although I still get the busybox prompt occasionally.

---

### Post by freddybob on 2008-03-11
Out of interest (because it worked for me) does changing the USB ports your keyboard and/or mouse are plugged into make a difference?

I had this problem when booting with the keyboard and mouse plugged into the upper two USB ports on the back of the machine.  The problem went away when I used the lower two ports instead.

---

### Post by Aearenda on 2008-03-13
My keyboard and mouse are in the lower sockets anyway, and a scanner is plugged in to an upper socket; I get the busybox problem occasionally. I'll rearrange them and see what happens!

---

### Post by xandraius on 2008-03-14
Correct almost 98%. The support people can TS the hardware. Just do not mention the OS at all. Tell them you are having a a no post issue but can access the Utility parition.  They will most likely want you to run the diags and the DST (Drive Short Test). Anything except Error 7 is the HDD. Error 7 is OS/ Partition.

---

### Post by gbrainin on 2008-03-14
Or you could call the Dell Linux support line (866-622-1947), get them to address the hardware issues, and not have to fib.

---

### Post by mrbean71 on 2008-04-09
Please try to change sata mode from IDE to RAID in your BIOS.
This could solve your problem, it seems a kernel problem:

[BUG #153702]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702")

Bye.

---

### Post by Aearenda on 2008-04-09
3 Weeks ago on post #6 I said I would rearrange the USB sockets - well that didn't make any significant difference to the rate of busybox occurence. 

One week ago I installed Hardy beta on my 530, and had to switch to RAID mode to get it to boot as mrbean71 explained in post #9. I have not seen the busybox problem recur since then. The only downside is an outrageously ugly BIOS setup screen for RAID mode that occurs on every boot, before entry to GRUB.

---

### Post by prinknash on 2008-04-19
Like a number of people, I seem to have solved the problem of my Inspiron 530 not booting with 8.04 by changing the BIOS setting from IDE to RAID. (Interestingly, I didn't have this problem with either 7.04 or 7.10.) But I'm wondering if there's any problem with having the BIOS set to RAID when IDE would normally be the appropriate setting. Does anybody know what changing the setting actually does and whether it can do any damage?

p

---

### Post by imagine2 on 2008-04-26
Hello,

I also had the same trouble on the inspiron 530 (whereas it was great with my Dell laptop!). First I updated to hardy and it did not boot anymore. I tried to use Dell rescue tools (after hitting F12 at the initial splash screen) and finally decided to format the whole hard disk... I used then feisty to reinstall everything because my hardy version would also refuse to launch and went the the "Busybox" unixlike functionality. Then feisty proposed me to upgrade at the end of its installation. Everything was great. At one moment Hardy told me I had to restart  and everything was ok... It just began to refuse booting. This time, at the initial splash, I did F2 and changed the initial boot that is proposed: it is written "stroke Enter" to change it. Instead of this, I put the hard disk as the booting system. Now it seems to work... If I add no further message in the 10 coming minutes, everything is ok...

---

### Post by imagine2 on 2008-04-26
Well, my  option I indicated in the last post only works from time to time. At the initial splash, I did as Mrbean71 advised in post #9:

" Re: Inspiron 530 won't boot
Please try to change sata mode from IDE to RAID in your BIOS.
This could solve your problem, it seems a kernel problem:

BUG #153702 "

Is it possible that it the access to the hard disk is slower? When the session begins in gnome, it seems to need more time to load the menu bars.

Kind regards.

---

### Post by Aearenda on 2008-04-26
prinknash: I think the BIOS setting change causes the kernel to access the drives using different BIOS calls, so avoiding the bug.

imagine2: I have tried both the RAID workaround and the all_generic_ide workaround mentioned in bug #153702; it seems to me that the RAID mode is faster. But anything is possible!

---

