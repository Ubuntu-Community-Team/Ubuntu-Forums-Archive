---
title: "Removing Ubuntu from Windows dual boot"
date: 2006-10-06
forum: Desktop Environments
---

### Post by djensen47 on 2006-10-06
I enjoyed the time I spent setting up Ubuntu. Of all the Linux distros I think it's the best. The next time I need to setup a linux server, I will definitely use ubuntu. I also like this community. This is probably the only forums where I could actually post this and not get flamed (I hope).

With that having been said, I'm "lazy" but I want full performance and linux desktops are not for the lazy. I'm sure I could fix this performance or that performance issue with time but since Windows already figured that out for me, I'm going with that for my desktop. Plus I got tired of switching back and forth for 1 or 2 apps on Windows. And again, time to setup ruled over getting Wine running.

Now I want to remove my Ubuntu linux partition and grub.

In a windows command prompt do I just need to ...
fdisk /mbr

and then reformat my linux partitions for NTFS? Is it really that simple?

---

### Post by boban on 2006-10-06
Yes :)

You could try fixmbr [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true) only in windows rescue mode...

---

### Post by Pjotr123 on 2006-10-06
Don't be afraid of flames! It's very good that you gave Linux a serious try. If only more people would do that....

I myself gave up on the former version of Ubuntu, for much the same reasons as you. It was only with the current Ubuntu that I decided, after some trying, to take the ultimate plunge. 

This was a result of a few factors coming together: growing security concerns about Windows, Windows Genuine Advantage (???) troubles and an unexpected amount of spare time.

Perhaps we will see you again after Ubuntu has become even better and easier than it is now!

Greeting, Pjotr.

---

### Post by djensen47 on 2006-10-09
Oh, I'll be back but it will be in reference to Ubuntu Server. :) 

Thanks for the confirmation on the uninstall.

---

### Post by elninio on 2008-03-05
Is it possible to uninstall on a computer without a cd-row drive, like booting in safe mode perhaps? I have a ubuntu server, ubuntu desktop, and windows xp running. Im trying to sell the computer to a friend who only wants windows (so i can use the money to buy a laptop). How can I go about doing this?

Thanks in advance.

---

### Post by inozemtsev on 2008-03-05
You can install the recovery console on your hard drive, and boot into it from the bootloader menu: [http://support.microsoft.com/kb/216417](http://support.microsoft.com/kb/216417) (if you don't have the Windows CD, try running %windir%\i386\winnt32.exe /cmdcons)

---

### Post by elninio on 2008-03-05
i dont have this file anywhere on my hardrive, what should I do?

---

### Post by inozemtsev on 2008-03-05
Download the install floppies here: [http://support.microsoft.com/default.aspx?scid=kb;en-us;q310994](http://support.microsoft.com/default.aspx?scid=kb;en-us;q310994)

Then boot off them and get into Recovery Console that way.

---

### Post by elninio on 2008-03-06
my computer does not have floppy or cd rom drive, am i doomed?

---

### Post by inozemtsev on 2008-03-06
You could copy the i386 folder off a Windows CD through the network from a computer that does have a CD-ROM drive. I think that's the last idea I have :) Also, if your PC came from a manufacturer and was not custom-built, there may be an i386 folder elsewhere (like the C: drive)

---

