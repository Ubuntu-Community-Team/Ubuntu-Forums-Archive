---
title: "Error 24"
date: 2009-04-22
forum: General Help
---

### Post by anachronon on 2009-04-22
Can anyone help?  My hard drive decided to choke.  So now, when I try to boot, the GRUB loader gives me "Error 24".  I have researched this error, and have discovered that it is likely a corrupted file system.  Yet, I can find NO info on how to fix this problem.  Has anyone had any success with this?  I really don't want to go through the weeks of battling with a reinstall.

---

### Post by codeseer on 2009-04-22
Run 'blkid' in the terminal and post the output here please.

---

### Post by JK3mp on 2009-04-22
> **codeseer said:**
> Run 'blkid' in the terminal and post the output here please.

second this... and what did you do prior to this? Can't see it just...choking. update? new install?

---

### Post by anachronon on 2009-04-22
OK, I booted the computer from an older, Live CD that I had (v7.04), and I attempted to run "blkid".  It accepted the command, but gave no output.

I next attempted to mount the hard drive.  The response was:

> Cannot mount volume.
mount: wrong fs type, bad option,bad superblock on /dev/sdb1    missing codepage or other error    In some cases useful info is found in syslog-try    dmesg|tail or so

This HDD is a SATA drive, and it has had a nasty habit of locking up at the worst times, always requiring a hard reboot (power off-on).  I suspect that I am having an IRQ conflict.  But, I have been unable to track it down.  Anyway, this time, Linux was installing a system update when the HDD decided to lock.  The result, upon attempted reboot, was "Error 24".

---

### Post by anachronon on 2009-04-23
No further replies?  Does that mean that it's toast?

---

### Post by codeseer on 2009-04-23
Sorry, for some reason I didn't get the email about your last post.

You will probably have to run 'blkid' as 'sudo blkid'.

---

### Post by anachronon on 2009-04-23
OK, runnig "blkid" under "sudo" worked; it is a root command.  Here is the output:

```
/dev/sda1: UUID="5c8a8649-187a-415e-97f8-43ffdb617ff9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="3bbbbe4e-6b0c-4e29-baa2-9968a72a089d" TYPE="swap" 
```

Hope this is of use.

---

### Post by codeseer on 2009-04-23
Alright, let's get you to run a recovery on Grub.

[Steps 1-5 here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

Edit:

I'm going to step away for about 45 minutes. If the Grub recovery doesn't fix your issue, please post the Results.txt that is generated from [running this]("http://sourceforge.net/projects/bootinfoscript/").

```
sudo ./boot_info*.sh
```

---

### Post by anachronon on 2009-04-24
> **codeseer said:**
> Alright, let's get you to run a recovery on Grub.

[Steps 1-5 here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

Edit:

I'm going to step away for about 45 minutes. If the Grub recovery doesn't fix your issue, please post the Results.txt that is generated from [running this]("http://sourceforge.net/projects/bootinfoscript/").

```
sudo ./boot_info*.sh
```
No luck.  I tried doing the rescue routine.  But, when it came time to read the partition, it said that it could not mount the drive.  So, I next tried to get a read-out using the command above.  The response was "command not found".

---

### Post by codeseer on 2009-04-24
> **anachronon said:**
> No luck.  I tried doing the rescue routine.  But, when it came time to read the partition, it said that it could not mount the drive.  So, I next tried to get a read-out using the command above.  The response was "command not found".

So, Grub gave you 'cannot mount drive'; humm...

For the readout, you have to use the 'cd' command to change directory to where you saved the shell script that you downloaded, then run it.

So this:

```
find /boot/grub/stage1
```

..gave you something like this:

```
find /boot/grub/stage1
 (hd0,0)
```

..then when you did this:

```

root (hd0,0)
setup (hd0)

```

..it said that it couldn't mount the drive?

---

### Post by anachronon on 2009-04-24
Actually, the command:

```
find /boot/grub/stage1
```

yields: "no such file or directory".

It was when I tried the "Alternate/Install CD" procedure described in Section 6 of the recovery instructions, that I got "unable to mount drive".

---

### Post by anachronon on 2009-04-24
P.S.  Yet, the BIOS always recognizes the HDD, without a problem.

---

### Post by codeseer on 2009-04-24
> **anachronon said:**
> Actually, the command:

```
find /boot/grub/stage1
```

yields: "no such file or directory".

It was when I tried the "Alternate/Install CD" procedure described in Section 6 of the recovery instructions, that I got "unable to mount drive".

Did this return 'no such file or directory'?

```
find /grub/stage1
```

---

### Post by anachronon on 2009-04-25
> **codeseer said:**
> Did this return 'no such file or directory'?

```
find /grub/stage1
```
Yes, same as other command.

---

### Post by codeseer on 2009-04-25
Well obviously it's there. It couldn't be anywhere else, seeing as you only have one hard drive.

When you put in the Live CD and boot up, your drive isn't in the Places menu, correct?

---

### Post by anachronon on 2009-04-25
> **codeseer said:**
> Well obviously it's there. It couldn't be anywhere else, seeing as you only have one hard drive.

When you put in the Live CD and boot up, your drive isn't in the Places menu, correct?
When using the live CD, the drive IS listed in the "Places" menu.  But, when I click on it, I get an error saying that Linux cannot mount the drive.  Yet, even then, it still remains listed in "Places".

---

### Post by codeseer on 2009-04-25
Well, it does seem like a file system issue or perhaps something worse.

Have you got any way of backing the entire drive up; in other words imaging it to another media? Do you have another drive or something?

Edit:

Go ahead and run a check, without changes, on the file system. The command should be:

```
sudo fsck -t ext3 -n /dev/sda1
```

---

### Post by anachronon on 2009-04-25
OK, runing "fsck" produced:

```
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: No such file or directory while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

I am using Ubuntu Studio, rather than standard Ubuntu.  However, it should still be using the ext3 file system.  Is there a disk repair utility that I could try?

On backup, there isn't much on the HDD yet.  It would likely all fit onto a DVD.  Really, the most important stuff is backed-up.  Mostly, the issue is plug-ins, settings, a hard-to-install video driver, and a few hand-made icons.  Is there a way that I can copy/image this HDD, when I don't have a funxtioning operating system (and the live CD can't read the drive)?

---

### Post by codeseer on 2009-04-25
Well, you could try partimage. You should be able to grab partimage from Synaptic in the Live CD and see if it will image /dev/sda1. If it will, then you can burn that image using Brasero or something.

If you had another drive that you could save the image to, it'd be the easiest though.

You may alternatively give this guide a try: [http://www.sysresccd.org/Sysresccd-manual-en_Burning_a_DVD_RW_from_SystemRescueCd_by_mounting_it]("http://www.sysresccd.org/Sysresccd-manual-en_Burning_a_DVD_RW_from_SystemRescueCd_by_mounting_it")

..you will need to do the second option on step five. It may or may not work, but it's worth a shot.

---

### Post by anachronon on 2009-04-25
Well, the version on the live CD is rather old (7.04), and it did not have "partimage" in its Synaptic database.  I tried updating the database.  But, I got an error saying that the version was too old, and no longer supported.

For copying, I also have a 2 gig, USB thumb drive.  That might fit the little that I have on the HDD.  I also have a 60G external, USB HDD.  But, I hesitate to use that one, as that is where I keep all of my critical stuff from both of my computers, backed-up.

Is there some sort of "Disk Doctor" utility that I can use?  There is really nothing critical on that HDD, that isn't already backed-up.  I am mostly concerned about not having to spend months getting another installation just right.

---

### Post by codeseer on 2009-04-25
fsck was the 'disk doctor'.

Try this:

```
sudo mke2fs -n /dev/sda1
```

Post the output.

---

### Post by anachronon on 2009-04-26
> **codeseer said:**
> fsck was the 'disk doctor'.

Try this:

```
sudo mke2fs -n /dev/sda1
```

Post the output.
No luck.  The result was:

```
mke2fs 1.40-WIP (14-Nov-2006)
Could not stat /dev/sda1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?

```

---

### Post by codeseer on 2009-04-26
I think you may be dealing with a dead drive.

If you have another system, you could slave it in, perhaps you could try reading it from there. If you have a Windows install somewhere, you could perhaps install the ext3 drivers and try reading it.

If you know the brand of the drive, you can usually get a drive diagnostics utility that can be burned to a CD and booted that will tell you more information about the state of the drive.

You could also try the SystemRescueCD, more specifically, the TestDisk and PhotoRec utilities; if you had no luck with Clonezilla or PartImage.

If none of that works, then your only options are to take it to a data recovery place and have them throw it around on their hardware based tools (which is very expensive) or just try to wipe the drive with the vendor specific tools or Secure Erase/HDDErase, which will make low level calls to the drive's chip to basically restore it to 'blank' condition; that is similar to the way it was when it was new, which means it will destroy all data.

Edit:

Let me know if you need any information about any of those options.

---

### Post by anachronon on 2009-04-26
Hey, thanks for all your time and effort.  But really, it looks like the drive is dead.  No sense going through a lot of trouble to recover a few trivial things.  Anything of importance has been backed-up, long ago.

I have spent the day doing numerous other checks on the computer, to make sure that the HDD is the problem, and not a more serious mobo issue.  I even ran "memtest86" for over two hours, just to eliminate the possibility of an intermitant memory problem.

From what I have been reading, this particular (older) mobo seems to have problems with the newer SATA drives.  Both Asus (mobo) and Seagate (HDD) have claimed that there are no compatibility issues.  But, this HDD has had intermitant problems since day-one.  Finally, it was damaged beyond repair.  Guess, I'll just go back to an IDE.  The newer ones seem pretty fast.  I do graphics work, but nothing that requires lightning speed, like gaming.  Just photo editing and 3D modeling.

Anyway, thanks again.

---

### Post by anachronon on 2009-04-26
Just one other thing.  I read that, on this mobo, a newer SATA drive (with NCQ) can sometimes conflict with the nVidia GeForce video card.  That may also have been the problem.  I could solve that by installing a Promise card.  But, that would cost just as much as a new HDD.  Plus, the HDD is likely damaged no, so I'd still have to replace it, as well.

---

### Post by codeseer on 2009-04-26
Alrighty. Glad to help.

---

