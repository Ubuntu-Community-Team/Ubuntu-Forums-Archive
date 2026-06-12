---
title: "Help with grub"
date: 2009-04-21
forum: General Help
---

### Post by Epidemic_HardyBoy on 2009-04-21
Ok, I am running an EEEPC 900ha.
MY brother thought it would be a nice thing to do to format my ubuntu drive.. I dont have a external disk drive so I cant pop in the CD to re-install...

IS THERE A WAY TO DISABLE GRUB from BIOS?
Please help me.

---

### Post by jsowoc on 2009-04-21
When your EEE PC starts, it shows the splash screen for a few seconds, then it tries to boot from the first valid device that is defined in the BIOS.

If grub is installed on the internal hard drive of the computer, it will be called up. If you don't want grub to start up, go into the BIOS (it's F2 on the EEE 701, look at the splash screen if it's different), and then look for boot order. Pick that you want to boot from external USB before the internal drive.

Now you should be able to put in your USB key with a live image of Ubuntu and do whatever recovery steps you need from there.

---

### Post by Epidemic_HardyBoy on 2009-04-21
Yea, I am going to use a ubcd :D
It is a uber fix cd image

thanks :D

---

### Post by Epidemic_HardyBoy on 2009-04-21
Oh god, someone help me?!

I am on an eeepc and cannot boot windows. I want my windows back.
Grub is giving and error and i cannot boot into windows
this happened after my brother reformated my partition for ubutnu.

---

### Post by jsowoc on 2009-04-21
Can you describe your "uber fix CD" in more detail and what you did with it?

In addition, what is the error you get when you cannot boot into Windows?

---

### Post by bodhi.zazen on 2009-04-21
Note : I changed your title to something more appropriate.

We need to know your partitions (do you still have a windows partition ? )

Does ubuntu boot ?

You probably need to repair your windows installation, although if windows was reformatted with Ubuntu you will need to re-install windows.

---

### Post by Epidemic_HardyBoy on 2009-04-21
Well, it is the XOSL Boot System Loader. (It wont work)

And the error is blank, it tries to load grub then dissapears and tries again..

it happens in like 3 second intervols and dissapear in a quickness.

---

### Post by Epidemic_HardyBoy on 2009-04-21
And I have the NFTS windows partition still..(The ubuntu one is gone)
and I try to get the wingows to boot though XOSL and I get this...

NTLDR is missing_

---

### Post by miegiel on 2009-04-21
> **Epidemic_HardyBoy said:**
> And I have the NFTS windows partition still..(The ubuntu one is gone)
and I try to get the wingows to boot though XOSL and I get this...

NTLDR is missing_

NTLDR is the "grub" for windows, check the UBCD for a tool to fix it, else you can try repairing windows with the windows install CD.

---

### Post by Epidemic_HardyBoy on 2009-04-21
I am in XOSL and this is my choices to boot.

HD1  mbr  Master Boot Record 0mb
HD1  primary  HPFS or NTFS  80g
HD1  primary  ext2  60g
HD1  primary  Microsoft FAT32 LBA 8008mb
HD1  primary  unknown  39mb

---

### Post by Epidemic_HardyBoy on 2009-04-21
> windows install CD
I do not have a cd/dvd drive on the EEEPC NETBOOK.

---

### Post by Epidemic_HardyBoy on 2009-04-21
Please help!
I would love to use my laptop again.

---

### Post by Epidemic_HardyBoy on 2009-04-21
I fixxed the partitions.
I now only have my windows partition.
But now I am getting error 17. Help?

---

### Post by miegiel on 2009-04-21
> **Epidemic_HardyBoy said:**
> I fixxed the partitions.
I now only have my windows partition.
But now I am getting error 17. Help?

[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

---

### Post by Epidemic_HardyBoy on 2009-04-21
I read this, I do not have the same version of BIOS that he does I am guessing.

I cannot change any settings.
Thanks for the help guys, please keep it coming

---

### Post by Epidemic_HardyBoy on 2009-04-21
Do think If I just run a Gentoo live and then re-install gentoo it would fix the grub?

---

### Post by bodhi.zazen on 2009-04-21
You need to restore the windows boot loader or re-install Linux (any version should do).

To restore windows you need a windows disk. Contact whoever made your computer ;)

To install Linux, use a light weight distro and make a separate /boot partition. The /boot partition will store grub and all the files you need to boot. You can delete the linux root partition and the linux kernels so long as you keep grub and the grub files.

---

### Post by Epidemic_HardyBoy on 2009-04-21
Like a little stored version I get it, but Gentoo would work? Im Unetbootin a gentoo live to a usb as we speak

---

