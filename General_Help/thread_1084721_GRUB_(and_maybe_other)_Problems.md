---
title: "GRUB (and maybe other) Problems"
date: 2009-03-02
forum: General Help
---

### Post by lockettowl on 2009-03-02
Sorry if this is redundant. I tried to follow instructions in other threads, but I'm not tech-savvy enough to be sure they apply to my particular situation.

I have Ubuntu 8.10 and I've been having some challenges. It started with my not being able to use the Synaptic package manager or do any upgrades. Then, I started having problems booting my system. It started with a long list of error messages. Then, one time I turned on my computer and got only something the effect of:

Loading GRUB 1.5...
Error 25

and then no progress past that point. I decided that I probably needed to reinstall Ubuntu (is this right?), but I really needed to find a way to do this without loosing my files. I'm not too overly concerned about settings, mainly just some class notes, pictures, and other files of that nature.

I read that one way to do this would be to create a new partition and move my /home folder to it. However, GParter wouldn't let me create a new partition. I also thought about uploading files to an online storage system. But, I ran into problems with Java and a multiple file uploader (I'm doing all of this using an 8.04 live CD because I have only the one computer). Eventually, I couldn't even mount the drive that has all my files

So, all of brought me back to trying to boot my current installation so that I can at least move my files to a safe place and then do a clean install. But, it appears that in order to do this, I have to figure out the GRUB thing. I tried to include all the steps of my experience so that there wouldn't be any missing key information.

Does anyone have suggestions? Please make them simple to follow, I'm still somewhat of a novice with this stuff.

---

### Post by TeoBigusGeekus on 2009-03-02
A small clarification please.
Do you mean that you can't use gparted whenever you boot up with the live cd?

---

### Post by hexanol on 2009-03-02
GRUB reports a "error 25" when there is a disk read error when trying to probe or read data from a particular disk (at least, that's what the documentation says).

So, that doesn't look like really good news. Especially that there would be no reason for GRUB to suddenly fail, except if you somehow messed your MBR, VBR or /boot/grub directory, which would in normal case never happens. But then, you wouldn't get an error 25...

Can't help you much right now.

---

### Post by lockettowl on 2009-03-02
Yes, everything I'm doing now, including GParted, is with the Live CD. I can start it and get all the way to applying the changes, by it refuses to actually create the partition once I click "apply"

---

### Post by TeoBigusGeekus on 2009-03-02
Quite odd...
The first thing that comes to my mind is to install Ubuntu again on some **free** space in your hard drive. 
Then boot from there, do your backup and finally blow the damn thing up with a nice clean reinstall.

---

### Post by lockettowl on 2009-03-02
Hey, that makes sense. I should have enough room to do that.

Can I install in free space without loosing files even though I haven't been able to make a new partition?

---

### Post by TeoBigusGeekus on 2009-03-02
Try to make a new partition with the installer.
I am not sure about what will happen to your files if you install on free space.

Another thing: have you been able to access the drive with the live cd - i.e. read a document, play an mp3, etc?

---

### Post by hexanol on 2009-03-02
If gparted doesn't work, how he will be able to re-partition his drive to make a fresh install ? I'm not sure about it, but I guess the install wizard is using parted, so if gparted isn't capable of applying changes, I doubt the install wizard will.

---

### Post by TeoBigusGeekus on 2009-03-02
> **hexanol said:**
> If gparted doesn't work, how he will be able to re-partition his drive to make a fresh install ? I'm not sure about it, but I guess the install wizard is using parted, so if gparted isn't capable of applying changes, I doubt the install wizard will.

Touche, but it's worth a try.

---

### Post by hexanol on 2009-03-02
Yes, but I suspect he might have a failing drive (says he have problem with gparted, problems mounting the partition, error 25 from grub) so I guess he should first check his drive health (I'm not sure how, don't have any experience) before.

Alright, I'm out for lunch.

---

### Post by lockettowl on 2009-03-02
Yes, I can get to the drive.

---

### Post by TeoBigusGeekus on 2009-03-02
So you can access your drive but you can't create a new partition on it.
Try to reinstall Ubuntu as mentioned before...
If you could find an external hd for backup would be perfect as well.

---

### Post by cyberpirate on 2009-03-02
you could also try knoppix

[http://www.knoppix.net/](http://www.knoppix.net/)

its like ubuntu live cd but has more utilities to work with

---

### Post by lockettowl on 2009-03-02
It turns out I can't partition through installation, either. I'm now getting GRUB error 15. I read that I can reinstall GRUB using a CD, which, of course I can't use or create because I have to have my Ubuntu Live CD in. Any ideas?

---

### Post by hexanol on 2009-03-02
Well, error 15 means

> 15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK. 

If you want more info on GRUB, there's an [online manual]("http://www.gnu.org/software/grub/manual/grub.html").

Reinstalling grub is just about copying some files in the /boot/grub directory (you could also reinstall the stage1 in the MBR but it looks like this part is ok, else you wouldn't be able to reach stage1.5/2 [i.e. you would get another kind of error message]). You can find those file on the live cd, in the "/usr/lib/grub/x86_64-pc" or "/usr/lib/grub/i386-pc" directory depending if you have a 32 or 64 bit live cd. But then, if you can't mount your "root" partition, you won't be able to copy those files to their destination. You could also install grub in a separate partition (or make a grub boot floppy, which can be handy) but this won't make you more capable of booting your operating system.

You should check your drive health. I don't know which tools is best, but I know there was some interesting one on the "[Parted Magic]("http://partedmagic.com/")" live CD. Basically, try to get the [S.M.A.R.T]("http://en.wikipedia.org/wiki/Self-Monitoring,_Analysis,_and_Reporting_Technology") data your hard drive is reporting. Until then, I'm not giving you more info.

Good luck!

---

### Post by lockettowl on 2009-03-02
OK, so I'm in /usr/lib/grub/i386-pc
Where do I go from there?

---

### Post by hexanol on 2009-03-03
Well, if you are from a live CD, you first mount your "root" filesystem (i.e. the partition where you installed Ubuntu the last time) somewhere, like in /mnt/temp/, and you copy the files from /usr/lib/grub/i386-pc/ to /mnt/temp/boot/grub/. This will "reinstall" the stage2 of grub. If you want to reinstall the stage1 and 1.5, you need to open a "grub prompt" (with the command grub) then you enter something like "root (hdX,Y)", "setup (hdX)" and voila.

So, to reinstall stage2 of grub from a live CD, you must know which partition holds your "root" filesystem . Let's suppose this partition is /dev/sda1
```
$ mkdir /mnt/temp
$ sudo mount **/dev/sda1** /mnt/temp/
$ *(sudo?)* cp /usr/lib/grub/i386-pc/* /mnt/temp/boot/grub/
```

To reinstall stage1 and stage1.5
```
$ grub
grub> root (**hd0,0**)
grub> setup (**hd0**)
grub> quit
```

Things in bold may vary depending on your system. In both case (stage1, stage1.5 and stage2 reinstall), if you can't access your root filesystem, these commands will fail.

But like I said in the previous post, you should check your drive health. I don't suspect grub to be in cause, except if you have done weird things to your system.

---

