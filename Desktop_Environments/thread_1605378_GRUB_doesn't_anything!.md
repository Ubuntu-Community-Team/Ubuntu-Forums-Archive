---
title: "GRUB doesn't anything!"
date: 2010-10-25
forum: Desktop Environments
---

### Post by mr32 on 2010-10-25
Heey,

I'm in big trouble. I've got a double boot system (Windows XP Pro and Ubuntu Maverick). Since I updated Grub2, Grub doesn't work anymore!

I'd tried[ this]("http://ubuntuforums.org/showthread.php?t=1580752") (because I **HAD** that error). But since than, I'd a black screen (harddisk didn't anything, and Grub too...) And now, after using a couple of[ these commands]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html") via the Ubuntu Lucid Lynx Live CD I get a mini bash in Grub, but no entry's to one of the two systems!

What's wrong, and what do I have to do? (and what did I wrong???)

I hope that anyone wants to help me fast!!!

mr32 :cool:

---

### Post by 3Miro on 2010-10-25
It is hard to tell what went wrong on the first try, without looking at the specific command that you typed. On the second try, if you get grub without a menu, then you can try:
```
grub -mkconfig
```
to generate a new grub.cfg file.

---

### Post by mr32 on 2010-10-25
In the mini-bash?

I tried it in the terminal of the Live CD, but I got this error:

[I]"/usr/sbin/grub-probew: error: cannot find a device for / (is /dev mounted?)." 

[/I]Before I ran that script, I filled in this: "*sudo mount /dev/sdb1 /mnt"  *(sbd1 is my windows partition, where the MBR is installed)

---

### Post by 3Miro on 2010-10-25
MBR is not on /dev/sdb1, MBR is on /dev/sdb (without a number).

If you can access grub on boot time, then it is installed somewhere. You have to check the Grub root to see where the config files are (grub is installed on the MBR, however, the config files on /dev/sd(something with a number)). You have to figure out where and fix the grub.conf file. Normally you would do that with a "update-grub" command, however, I am not sure how to do it form the live cd.

Have you tried the official Ubuntu wiki:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
```
 Restore GRUB2 - Recovering from a Windows XP / Vista / 7 Reinstallation
Fire up a terminal from the Live CD for Ubuntu 10.04.
$ sudo fdisk -l (Note the partition number on which Linux resides)
$ sudo mount /dev/sdaX /mnt (Replace X with the partition number housing Linux)
$ sudo grub-install --root-directory=/mnt/ /dev/sda
$ sudo update-grub
$ sudo reboot

Credits to
http://mundogeek.net/archivos/2009/12/08/recuperar-grub-2/ for the enlightening post & 
http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html for the awesome translation. 
```

---

### Post by mr32 on 2010-10-26
I did what you wrote. But when I ran this line: 
```
sudo update-grub
```
I got this as message: 
```
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
```

What do I have to do?

---

### Post by GreatKeyHunter on 2010-10-26
do you have different hard drives or are both OS on the same hard drive?

---

### Post by drs305 on 2010-10-26
> **mr32 said:**
> I did what you wrote. But when I ran this line: 
```
sudo update-grub
```
I got this as message: 
```
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
```

What do I have to do?

That message is often generated when you try to update-grub from the LiveCD or aren't on your Ubuntu partition.

Boot the LiveCD and run the boot info script from the following link. Post the contents of RESULTS.txt, which is the file the script generates.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by mr32 on 2010-10-27
It isn't necessary anymore. I took to much time... I'd re-installed Ubuntu, much faster. And if you replace the original config files of Ubuntu, everything is what is was, so...

Thanx for al your help!!!

mr32 :cool:

---

