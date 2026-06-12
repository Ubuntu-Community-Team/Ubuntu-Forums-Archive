---
title: "Creating a Ramdisk"
date: 2005-11-12
forum: Desktop Environments
---

### Post by Elitist_Phoenix on 2005-11-12
I'm wondering is there any easy way to create a Ramdisk (of specified size) in ubuntu? If there isn't and you have a really easy way please add it.

---

### Post by magnusbb on 2005-11-12
It's a kernel module (enabled in Ubuntu) that you could use to mount a ram disk. As far as I know the size is static (16 MB), set by the kernel, but it should be possible to change it.

You could take a look over here,
[http://www.vanemery.com/Linux/Ramdisk/ramdisk.html](http://www.vanemery.com/Linux/Ramdisk/ramdisk.html)

(it's old, but I bet the process hasn't changed that much).

This article suggests that you should open **/etc/grub.conf**:
And in that file add "ramdisk_size=your-size-in-kilobytes" at the end of the line starting with **kernel.**

Read there for further instructions.

And after all, what's the point with a RAM disk nowdays?

---

### Post by Elitist_Phoenix on 2005-11-12
Yeah, I saw this when I did some googling just wondering if theres and script or command in the ubuntu.

I might give it ago, just I've never used grub before (always lilo). Do I have to do anything after editing the .conf? Like running the lilo, after editing lilo.conf.

The point of the ramdisk is the stick a hosts file in which is pretty big and which really slows the computer down when used (it might actually be a bug).

---

### Post by Huzudra on 2008-01-20
another nifty use for a ramdisk is to store the FF cache, cookies, and temp internet files for security reasons and for faster browsing.  on my windows box theres a definite difference between FF caching on disk and in ram.

---

### Post by rosegarden78 on 2008-01-20
Interesting ... in windows days I used a .sys program that was included as well as shareware from tucows.com before becoming an Ubuntu promoter. Would you feel comfortable using shareware from SourceForge if it wasn't in the repositories?

---

### Post by Huzudra on 2008-01-20
i'm pretty trusting of the linux community.  but since the current kernel has it built in and i'm a noob all i really want is an easy script and someone to tell me what to change in the script to make the disk the size i want.  

on my windows box i have a bit of ;'borrow ware' which allows me to create a ramdisk very early in boot and change it to any size i like, assign any letter, etc etc acts just like a real disk in almost every respect except at the lowest levels for some benchmarks.

the implementation in linux sounds alot nicer than the windows program i use  what with it all being in the kernel already.  as long as i can make a ramdisk thats about 80mb for FF's disk cache i'll be happy.  might not see as much of a boost under nix as i do in windows however.

---

### Post by rosegarden78 on 2008-01-21
I was fond of using ramdisks for swap file and temporary Internet files as a Windows user.  I'm using XFCE window manager I don't see that hard drive light blink.  You said it's built into the kernel.  Where did you see it?  Is it a command like mkdir?  Well I just checked Google and the repositories and find no evidence of ramdisk for users only for LiveCD installation.

---

### Post by rune0077 on 2008-01-21
> **Huzudra said:**
> i'm pretty trusting of the linux community.  but since the current kernel has it built in and i'm a noob all i really want is an easy script and someone to tell me what to change in the script to make the disk the size i want.  


To the best of my knowledge the size of the RAM-disk is build into the kernel. Compiling a new kernel let's you set the size yourself, but I'm not sure there's an easy way to do this once the kernel is compiled.

---

### Post by Rhubarb on 2008-01-21
If you read this guide, you'll have a RAM disk working easily:
[http://www.vanemery.com/Linux/Ramdisk/ramdisk.html](http://www.vanemery.com/Linux/Ramdisk/ramdisk.html)

Just remember some operations require administrative privileges, so put sudo infront of those operations that require it.

rune0077: you can make your ram disk larger / smaller by changing your /boot/grub/menu.lst and adding **ramdisk_size=80000** to the end of the kernel line for an 80MB RAM disk (look in the link I gave above).
If you don't specify anything in the /boot/grub/menu.lst, by default you get a 64MB RAM disk.

If anyone here wants better step by step instructions, let me know and I'll post it here for you (or I'll create a new howto thread for it)

---

### Post by Huzudra on 2008-01-23
> **Rhubarb said:**
> If you read this guide, you'll have a RAM disk working easily:
[http://www.vanemery.com/Linux/Ramdisk/ramdisk.html](http://www.vanemery.com/Linux/Ramdisk/ramdisk.html)

Just remember some operations require administrative privileges, so put sudo infront of those operations that require it.

rune0077: you can make your ram disk larger / smaller by changing your /boot/grub/menu.lst and adding **ramdisk_size=80000** to the end of the kernel line for an 80MB RAM disk (look in the link I gave above).
If you don't specify anything in the /boot/grub/menu.lst, by default you get a 64MB RAM disk.

If anyone here wants better step by step instructions, let me know and I'll post it here for you (or I'll create a new howto thread for it)
now, can you explain more about how to make the ramdisk appear at each boot formatted, clickable, and ready to use?  i'd like to use it for the FF diskcache for my GF's PC since she browses alot of picture intense sites.

---

### Post by rosegarden78 on 2008-01-26
If you want fast browsing and optimal memory management, try the Opera browser 9.5 Beta direct from [www.opera.com](www.opera.com) - no guarantee the ramdisk memory management is better than Opera but it's worth a shot!  You could always make an executable shell script for ramdisk, then add the script to Autostarted Programs to make it ready good luck!

---

### Post by Huzudra on 2008-01-26
> **rosegarden78 said:**
> If you want fast browsing and optimal memory management, try the Opera browser 9.5 Beta direct from [www.opera.com](www.opera.com) - no guarantee the ramdisk memory management is better than Opera but it's worth a shot!  You could always make an executable shell script for ramdisk, then add the script to Autostarted Programs to make it ready good luck!

that last part about the script, thats what i need...no clue how i do that though :lol:

---

### Post by RawMustard on 2008-02-04
I formatted /dev/ram0 on my feisty 64bt system and then mounted it to /media/ramdisk and all went fine.  I can browse the disk, but no way can I write to the root of the disk.  I can however write to the lots+found directory which was created.  chown myuser:root /media/ramdisk and then chmod 0750 /media/ramdisk doesn't do a thing.  The folder has the correct permissions, but still I can't write to the root of the disk.

Any tips from anyone how I might fix this problem?

Never mind, I performed sudo umount -v /media/ramdisk and then remounted it again and it worked :)

---

### Post by RawMustard on 2008-02-05
Does anyone know how to tell gnome what icon to use for the ramdisk in nautilus?
When mount the ramdisk, I get a broken icon in nautilus :(

Hmm broken icon theme Mist, fixed it by adding the folder devices with the gnome-dev-memory.png icon in each folder.

---

### Post by Jouke74 on 2008-02-06
You might also want to check out tmpfs... there you can also specify the ramdisk size. The basic commando is:

"mount -t tmpfs -o size=1G,nr_inodes=10k,mode=0700 tmpfs /space" 

which will allow up to 1 GiB in RAM/swap with 10240 inodes and only accessible by the owner of the directory /space.

---

### Post by silver on 2008-07-10
According to stinger30au :

"Ubuntu and Debian auto-mount a ramdisk using tmpfs. This gets mounted to /dev/shm and is usable by anyone (just cd to /dev/shm and start plonking files in there).

the ram disk is dynamic, not static (resizes automatically and will use up to half your available ram)"

[http://ubuntuforums.org/showthread.php?t=182764](http://ubuntuforums.org/showthread.php?t=182764)

---

### Post by stinger30au on 2008-07-10
> **Elitist_Phoenix said:**
> I'm wondering is there any easy way to create a Ramdisk (of specified size) in ubuntu? If there isn't and you have a really easy way please add it.


ubuntu comes with a ram disk built in

it lives in

/dev/shm


it is an auto sizing ram disk too, very smart

---

