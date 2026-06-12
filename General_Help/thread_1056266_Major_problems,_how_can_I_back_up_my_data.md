---
title: "Major problems, how can I back up my data?"
date: 2009-01-31
forum: General Help
---

### Post by bakaeigo on 2009-01-31
Okay, here's a little background first.

On January 29, I installed updates including a kernel update. When I rebooted, ubuntu would go through the boot sequence, then when the login window was supposed to appear, the screen went blank and into sleep mode. If I pressed Ctrl+Alt+F1, I was able to log in via the terminal and execute commands, but "startx" always failed.

So I rebooted, this time using an earlier kernel. GNOME loaded and my system was functional, but compiz didn't work as the kernel was not accepting the nvidia drivers. I read a guide online that said to un-install and reinstall the drivers, so I did that. After I rebooted into the latest kernel, every system message, even in GRUB, has mis-spelled words (For example "Wbuntw" instead of "Ubuntu" and "ggnerck" instead of "generic"). 

Now whenever I boot with any kernel version, the same thing happens: Words are mis-spelled in GRUB and in Ubuntu's boot sequence and the screen is sometimes randomly filled with what look like apostraphes, but the GNOME login window loads. I can log in, but it always freezes when loading my desktop, with no icons on the desktop and about half of the panel loaded. I can't get into the terminal with Ctrl+Alt+F1, the only way to get out of this is to turn the computer off.

I put in my Intrepid LiveCD so that I could back up my files before trying something else, but this doesn't work either. Everything seems to work okay until the desktop starts to load, at which point it acts almost exactly like my HD installation. The icons load and the panel mostly loads (save one or two icons) but it doesn't respond to any mouse clicks or keyboard commands.

I tried the Hardy LiveCD and even a Fedora 10 LiveCD I had, but they both did the same thing, freezing after loading the desktop.

 First and foremost I need to save my data, but I can't with none of the liveCDs working. After I have my data backed up I guess I'll have to reformat and start fresh.

How can I get my data onto my external HDD?

Thanks for any help.

---

### Post by wolfen69 on 2009-01-31
i would try a couple other live cd's like puppy and knoppix first.

---

### Post by bakaeigo on 2009-01-31
> **wolfen69 said:**
> i would try a couple other live cd's like puppy and knoppix first.

Thanks, I'll try that and post the results here.

---

### Post by ajgreeny on 2009-01-31
Or you can do the backup with the command line after booting the live CD.  Just use Ctrl+Alt+F1 to get the console, login with your username and password, (p'word will not show on screen, but don't worry) then use the copy command, **cp**, to copy the files you want to your external drive.  You could also use **rsync** which will do it as well.

---

### Post by bakaeigo on 2009-01-31
> **ajgreeny said:**
> Or you can do the backup with the command line after booting the live CD.  Just use Ctrl+Alt+F1 to get the console, login with your username and password, (p'word will not show on screen, but don't worry) then use the copy command, **cp**, to copy the files you want to your external drive.  You could also use **rsync** which will do it as well.

I don't quite understand -- If I am booting with the livecd, won't I not have to enter my username and password?

I can enter the console with the liveCD, but nothing at all shows up in the /mnt or /media folders, so I'm not sure how I'd transfer any files.

I can also enter the console with my regular installation, but my USB hard drive doesn't show up under /mnt or /media either. What should I do in order for it to recognize my HD?

---

### Post by ajgreeny on 2009-01-31
Yes, as I said login with your username and password.  You will then probably need to make a folder to use as backup mount point sudo mkdir /media/backup and then, if it doesn't automount, mount the external disk with ```
sudo mount /dev/sdx /media/backup/ -t vfat -o iocharset=utf8,umask=000
``` changing the dev name to whatever your system names the external disk, find that with ```
sudo fdisk -l
```
I am surprised, however, that your system does not mount the external disk automatically.  I thought ubuntu always did that.

---

### Post by Gizenshya on 2009-01-31
are you sure its not a hardware failure?

If it was a kernel update problem (or any update problem), it wouldn't change the ROM LiveCD's.

Sounds liek RAM to me.

---

### Post by Rhyader on 2009-01-31
I don't have any idea what's wrong with your Ubuntu, or how to fix it.

After reading what the last guy said, yeah, you should boot a diagnostic CD first and see if you have a hardware error that may prevent you from copying anything correctly. Could be bad memory.

But assuming that your hardware is working correctly, I DO know how to back up your current files to an external drive.

If you're desperate and willing to forgo all things GUI, and work completely in command line mode, you might try this. On another computer, download and burn "System Rescue CD" from 
[http://www.sysresccd.org](http://www.sysresccd.org)
Which I very highly recommend.

Boot from the system rescue CD. When you get the command prompt, you are root. Forget this "sudo" stuff. You do not have to "log in". My difficulty was getting the device names. My lame way of doing it was - and be careful here - using the partition editor "parted". If you start it and type "print all" you will be able to see a list of all devices that the system thinks are there, which should include your external hard drive. Do NOT type anything else in "parted"; it's a partition editor. If the geeks here know any other way to probe your computer, preferably a safer way, then by all means do that instead. Maybe "fdisk -l". But this is what I had to do. However you do it, get your device names and write them down. Quit "parted" (or fdisk). Then let's say your external drive is /dev/sdc and it's partition is /dev/sdc1 (these are examples: yours will be "/dev/{*something*}") Make sure you know what type of partition it is. You have to know all this technical stuff ... 

Type ............ fdisk type .... filesystem type
linux ........... 83 ............ ext3 or ext2
windows fat 32 .. A, B, C ....... vfat
windows ntfs .... ? ............. ntfs or ntfs-3g

You didn't say - but if we assume that your Ubuntu partition is /dev/sda1, type 83 and its filesystem is ext3 ... and that your external hard drive is ntfs (because the stores sell them formatted that way) ... if this is not the case then the parameters of the commands will be different.

first check what is mounted:
> df

assuming you are going to mount your disks:
> cd /mnt
> mkdir source
> mkdir backup
> mount -rv -t ext3 /dev/sda1 /mnt/source
> mount -rwv -t ntfs-3g /dev/sdc1 /mnt/backup

( Here you change the parameters if your system is different. Your external drive might be ext2 or ext3 or vfat. You might have different /dev/{*names*}. Note that the system recovery disk comes with ntfs-3g installed. Do NOT write to a ntfs partition without ntfs-3g, or you will screw up the filesystem. )

Now you have mounted the Ubuntu partition read only and the external partition read write. Copy the files by whichever text mode you like best...

1. Use Midnight commander. Type "mc". Navigate and copy. OR 
2. Use "cp" with the recursive option. (see "man cp") OR
3. Use "tar" to make archive files on the external drive. (see "man tar")

Hopefully this wasn't all gibberish and might be of some interest.

---

