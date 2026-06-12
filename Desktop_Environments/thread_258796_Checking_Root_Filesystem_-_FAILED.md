---
title: "Checking Root Filesystem - FAILED"
date: 2006-09-16
forum: Desktop Environments
---

### Post by Miki01 on 2006-09-16
Okay, well, I haven't booted from Ubuntu for about a week or so, but now when the bootscreen says 'checking root filesystem', it fails and brings be to a command promt saying something about fsck. So I tried booting from recoverymode and type fsck. I get a bunch of errors saying how many things are '8, when supposed to be 0'. And a bunch of other things have errors.

How do I go about fixing this? I cannot format it and reinsall Ubuntu, because I have many valuable and needed files in there.

Please help me out, thank you all in advance, your help is greatly appreciated.

---

### Post by Miki01 on 2006-09-16
Anyone? Please?

---

### Post by jimbob on 2006-09-16
If you have a system rescue CD like Knoppix, etc I would boot it  and try to mount your volume manually to at least see if you can get to any of your files.  

If you can you could try to rescue them by copying them off and then go ahead and run fsck yourself to see if you can get around the error.

Sorry I can't be of more help.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Miki01 on 2006-09-16
Rescue CD? I have the LiveCD of Ubuntu 6.06. How would I go about mounting it manually?

---

### Post by jimbob on 2006-09-16
The live CD might work if it has not mounted your root volume.

Open a root terminal and enter:

   #mount /dev/hdaX /mnt    ;(where X is the number of your root partition)
   #cd /mnt/home/(your directory name)
   #ls 

If your files appear to be there you could try to save them to another partition or hard drive if you have one.  After that unmount the volume and try to run a fsck to see exactly what it reports is wrong.  Check the man pages for fsck to interpret the error codes.

Check this link on how to create a system rescue CD:

    [http://www.sysresccd.org/Download.en.php](http://www.sysresccd.org/Download.en.php)

---

### Post by Miki01 on 2006-09-16
Thanks for your help :D I was able to boot!

But, on with the casualties...

Here's what I got after entering my name and password:

> GDM could not write to your authorization file.
This could mean that you are out of disk space or that
your home directory could not be opened for writing. 
In any case, it is not possible to log in.
Please contact your system administrator.

I was not able to log in. I don't think Its a disk space problem, since I still have 10GB left in my hda1 partition. Do you know how to get around this? How to fix it?

**_EDIT_**: I went back to try logging in again, but this time, it didn't even boot... Here's what it gave me: 

> Decompressing Linux...done.
Booting the kernel.
mount: Mouting /dev/hda1 on /root failed: Invalid argument
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem does not have sbin/init

I'm starting to get desperate, because Dapper has some valuable files and memories of mine... Even worse is that GRUB has errors now. GRUB now shows:

> GRUB Loading stage1.5.

GRUB loading, please wait...
Error 2
_

I've read from a Google search that Error 2 means I have a corrupt linux partition. Can it be fixed? I hope for the best...

Windows has some memorable files I have too. Plus, I was not the one who purchased the WinXP installation CD-Key, so I don't wan't to make the $180 purchase go to waste... Please help, Monday is coming soon too, and I have computer sciences class w/ programming in Windows.

Thanks you in advance.

---

### Post by jimbob on 2006-09-17
You mention that you have XP also.  Is it on the same disk?  Can you boot it up OK?

Unfortunatly it sounds to me like you have a corrupt root file system.

I would concentrate on saving whatever files I could and worry about booting Ubuntu from /dev/hda1 later.  Did you try to mount it manually from the live CD?  

If you can get it mounted you could copy your files to a separate HD or to a spare partition on hda as I suggested above.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Miki01 on 2006-09-17
I have XP as well, but I cannot boot it because GRUB has errors and I cannot press esc to choose XP to boot...

How do I save my files? I only have one HDD. I don't know what to do...

I was able to boot Ubuntu once after copying the files to hda1, but after that it gave me the error saying that I cannot log in. Either something is write-protected or that I have no more hard drive space. But I don't see 10GB left in my linux partition being too little space...

---

### Post by jimbob on 2006-09-17
Tell me exactly what is on each partition of your only HDD.

Most folks have XP on the first partition but it sounds like you have your Ubuntu there.

I booted my Ubuntu live/install CD and chose the "boot into safe graphics mode" and it did not try to mount any HDD partitions.

Can you get that far?

Let's hope someone with more knowledge than me picks up this thread while we're trying things.

What are you running on to be able to access this forum?  Is it a Linux box of some sort?

---

### Post by Miki01 on 2006-09-17
Well, currently I'm on my dad' laptop running Windows 2000.

I have Ubuntu on my first partition and XP on the second. My HDD is 80GB; 74.5 of which is actually useable. About 37GB are used for each of the two partitions.

I will try using my liveCD to try to boot into safe graphics mode. I'll see how it goes.

I don't really understand this liveCD thing anyway. I remember ordering free Ubuntu CDs, and I got 5.10 with two CDs, one install, the other Live. I remember then ordering 6.06 and it only came with one CD, but it didn't install because the CD may have went through a strong electrostatic or magnetic field. I had to download and burn a copy of Ubuntu 6.06 LTS to install it instead... 

When I enter the 'Rescue a broken system' menue from the CD, I cannot even complete it, because it can't mount. I select hda1 and press enter and I get a red error screen asking me to check the 'syslog'. How do I do that? I can't even get into Ubuntu... (see attachment).

---

### Post by jimbob on 2006-09-18
Electrostatic and/or magnetic fields don't affect CD's.

With 5.10 yes, there were separate live and install CD's.  With 6.01 there is a single CD with both available which is what you have.  When you boot the CD you should see "boot into safe graphics mode"; select this and boot.  Do not click on the install icon, but instead open a terminal window and follow the instructions in my second post.

Syslog is located at /var/log/syslog.  You can look at it after you get the terminal window open.

---

### Post by Miki01 on 2006-09-18
Is the boot from safe graphics mode a hidden menu on 6.06? All I can see from booting the CD is

Install in text mode
Install in OEM mode
Install a server
Check CD for Defects
Rescue a Broken System (doesn't work, cannot mount hda1)
Memory Test
Boot from first hard drive

---

### Post by jimbob on 2006-09-18
Looks like you have the install CD, not the Live/Install version that I have.  My options are:

  Start or install Ubuntu
  Start Ubuntu in safe graphics mode   (which I wanted you to try)
  Check CD for defects
  Memory Test
  Boot from first Hard disk

OK, since you don't have my option #2 above, the thing I would do is use someone else's computer and download and burn the system rescue CD I mentioned above.

That will give you a text-based system from which you can try to at least recover some of the data from your HDD.

---

### Post by Miki01 on 2006-09-18
Ah, yes, I tried to download the system rescue CD from the link you gave on the first page.

I tried clicking that sometime yesterday night, and all I got was timeouts. I tried again today and got the same thing:

> An error occurred while loading [http://www.sysresccd.org/Download.en.php:](http://www.sysresccd.org/Download.en.php:)
Timeout on server
 Connection was to [www.sysresccd.org](www.sysresccd.org) at port 80

Could it be somewhere in the URL? I will try again tomorrow. Ah, please excuse me, I forgot to mention before, thank you so very much for helping me throughout.

---

### Post by fokuslee on 2006-09-22
hey to just boot in windows use window cd for recovery and type fixmbr 
however u will looes grub 
so reinstall linux

and why would strong magnetic field destroy a cd?

---

### Post by exit3219 on 2006-09-22
Like others have said, the simplest way to do it is to copy files to another disk / partition. But as you have 1 disk only, your only option is to use the Windows partition. Is it FAT32 or NTFS? You can also write the things you need to keep to a CD/DVD, if you have a burner.

If your corrupted partition is on hda1, have you tried a fsck /dev/hda1 from the live cd? Make sure hda1 is not mounted when you try this. If you get a warning like ```
WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)?
```
do NOT proceed! (say no or press ctrl+c)

You said fsck returns errors. But at the end what does it say? It should stop eventually and either say it has fixed your partition or that it's so messed-up it can't fix it. When fsck has finished type 'echo $?' in the console and tell us the result (that number).

---

