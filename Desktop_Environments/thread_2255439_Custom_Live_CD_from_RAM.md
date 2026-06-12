---
title: "Custom Live CD from RAM"
date: 2014-12-05
forum: Desktop Environments
---

### Post by buntuluxx on 2014-12-05
I am attempting to create a custom Ubuntu Live CD with UCK and have it boot to RAM entirely.

This guide provides instructions on how to enable the boot to RAM option.
[https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM)

I let UCK do the squash stuff, extract the iso and create the directories

It created /home/ubuntu/tmp/remaster-root (with all following direcories)
              /home/ubuntu/tmp/remaster-iso (with /casper , /boot etc.)

I am using the UCK console option to enter commands.

I was able to edit the boot script at /usr/share/initramfs-tools/scripts/casper

However now I am stuck at this stage of the guide:
**Regenerate initrd.gz** (in my case it is called initrd.lz which is located at  /home/ubuntu/tmp/remaster-iso/casper/initrd.lz

 Since we edited bootup scripts, we need to regenerate the file we know as /casper/initrd.gz to incorporate these changes: 
```
sudo cp -L /etc/resolv.conf /casper/chroot/etc/
sudo mount -t proc none /casper/chroot/proc
sudo mount -o bind /dev /casper/chroot/dev
sudo chroot /casper/chroot /bin/bash
```

The /casper/chroot/etc/ directory shown in the guide should be the   equivalent to my /home/ubuntu/tmp/reamster-root/etc , which was created   by UCK.
But it won't work and return the following:

```
root@ubuntu:/# sudo cp -L /etc/resolv.conf /home/ubuntu/tmp/remaster-root/etc/
sudo: unable to resolve host ubuntu
cp: target '/home/ubuntu/tmp/remaster-root/etc/' is not a directory

```

I also tried to start with /remaster-root, but it failed as well.

```
root@ubuntu:/# sudo cp -L /etc/resolv.conf /remaster-root/etc/
sudo: unable to resolve host ubuntu
cp: target '/home/ubuntu/tmp/remaster-root/etc/' is not a directory

```


Can somebody help me out?

---

### Post by sudodus on 2014-12-05
You can make a custom iso file according to this link (based on Debian, but can be tweaked to be based on Ubuntu).

[http://willhaley.com/blog/create-a-custom-debian-live-environment/](http://willhaley.com/blog/create-a-custom-debian-live-environment/)[URL="http://willhaley.com/blog/create-a-custom-debian-live-environment/"]
[/URL]
It will create a standard ISO file which can boot from a CD disk. If you treat the iso file with isohybrid, a cloned copy will also be easily bootable from USB (and it will have the read-only file system ISO9660, so there is no risk that anything will be written to it).

I have used this method successfully. You can set up a shell-script file based on the blog post (like I did), and include the program packages and tweaks that you wish to use, and go.[URL="http://willhaley.com/blog/create-a-custom-debian-live-environment/"]
[/URL]

---

### Post by buntuluxx on 2014-12-05
Thank you for the reply!
I have heard about a specific LiveCD Creation tool within Ubuntu 14.04 itself. 

Would that be an option?
I have looked into it a little, but couldn't figure out how to sideload third party programs, drivers etc.

Any experiences?

---

### Post by sudodus on 2014-12-06
Please tell me the name of the  LiveCD Creation tool within Ubuntu 14.04 itself! Or describe it, because I can only guess which tool you are thinking of.

The easiest way to make a persistent live USB pendrive is to use ***Startup Disk Creator*** alias usb-creator-gtk. Then you can add/remove whichever programs you want and tweak the interface. Things will not be wiped at reboot, which is good except in your case, and I think it is complicated to make a reliable system, that removes 'history' except programs and tweaks.

So you need something else. The basic case is to use a live system without persistence, for example from an Ubuntu desktop iso file. But then you cannot save what you add/remove  and tweak. That is why I suggested using Will Haley's blog. I don't think it is easy to do what you want, but it is possible, and there are several ways to do it. Let us hope you will get tips from people who have used other methods, for example ***Remastersys*** (which I have *not* tried) or similar tools.

---

### Post by buntuluxx on 2014-12-06
[Ubuntu Builder ]("http://linux.softpedia.com/get/System/Software-Distribution/Ubuntu-Builder-85246.shtml") is what I meant.  

I only need the livecd to carry mdadm for my raid, vlc, codecs, a file manager and java runtime. 
With Ubuntu Builder you can apparently add packages, but removing existing ones from the iso seems difficult.

---

### Post by sudodus on 2014-12-06
I have heard about Ubuntu Builder but haven't used it. I guess it works similar to Remastersys. It is a good idea to browse the information about various methods and tools, and then select one of them.

---

### Post by matt_symes on 2014-12-06
Wasn't Ubuntu Builder the fork of Remastersys after the developer of Remastersys stopped developing it ?

---

### Post by buntuluxx on 2014-12-06
Nevermind, Ubuntu Builder development has been discontinued as well.
[https://launchpad.net/ubuntu-builder/+announcement/12508](https://launchpad.net/ubuntu-builder/+announcement/12508)
It is incompatible with trusty.

Remastersys seems like a viable alternative.
I will look into it and report back.

Edit

I have just found out about relinux, the predecessor which is supposed to be superior to both Ubuntu Builder and remastersys, in terms of functionality and features.
[https://launchpad.net/relinux](https://launchpad.net/relinux)

Installing and testing atm.

---

### Post by buntuluxx on 2014-12-06
Nope, that was also a reach.
As usual, everything is broken and development has been seized.

Frustrating.

I need an application capable of creating a livecd distro, that carries mdadm, vlc codecs, maybe truecrypt,  java runtime and boot to ram entirely.

---

### Post by sudodus on 2014-12-07
Did you try according to Will Haley's blog? It works for me, that is what I used for 9w (and OBI-9w), and what is used (and developed a lot) for ToriOS.

Did you try Remastersys? There are threads here at the Ubuntu Forums, that report success with Remastersys and Ubuntu 14.04 LTS.

---

### Post by buntuluxx on 2014-12-07
I am currently trying this:  [https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM)
I let UCK implement the iso and directories.
/home/ubuntu/tmp/remaster-root has been created by the uck tool
From there I can access all OS files and directories

I am stuck at this portion: 
[h=4]Regenerate initrd.gz[/h] Since we edited bootup scripts, we need to regenerate the file we know as /casper/initrd.gz to incorporate these changes: 

sudo cp -L /etc/resolv.conf /casper/chroot/etc/
sudo mount -t proc none /casper/chroot/proc
sudo mount -o bind /dev /casper/chroot/dev
sudo chroot /casper/chroot /bin/bash

his /caspter/chroot/etc is the equivalent to my /home/ubuntu/tmp/reamster-root/etc (created by uck)

but it doesn't work

---

### Post by yancek on 2014-12-07
> Did you try Remastersys? There are threads here at the Ubuntu Forums, that report success with Remastersys and Ubuntu 14.04 LTS. 		

That would be the first thing I would try.  I used it on Ubuntu 12.04 and other Ubuntu derivatives and have also seen posts here at the forum indicating it was used successfully on 14.04.   You could also try 'grub-mkrescue' from another system.  Instructions below, you might need to modify your grub.cfg file.

[https://www.gnu.org/software/grub/manual/html_node/Invoking-grub_002dmkrescue.html](https://www.gnu.org/software/grub/manual/html_node/Invoking-grub_002dmkrescue.html)

---

### Post by buntuluxx on 2014-12-07
.

This guide provides instructions on how to enable the boot to RAM option.
[https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM)

I let UCK do the squash stuff, extract the iso and create the directories

It created /home/ubuntu/tmp/remaster-root (with all following direcories)
              /home/ubuntu/tmp/remaster-iso (with /casper , /boot etc.)

I am using the UCK console option to enter commands.

I was able to edit the boot script at /usr/share/initramfs-tools/scripts/casper

However now I am stuck at this stage of the guide:
**Regenerate initrd.gz** (in my case it is called initrd.lz which is located at  /home/ubuntu/tmp/remaster-iso/casper/initrd.lz

 Since we edited bootup scripts, we need to regenerate the file we know as /casper/initrd.gz to incorporate these changes: 
```
sudo cp -L /etc/resolv.conf /casper/chroot/etc/
sudo mount -t proc none /casper/chroot/proc
sudo mount -o bind /dev /casper/chroot/dev
sudo chroot /casper/chroot /bin/bash
```

The /casper/chroot/etc/ directory shown in the guide should be the  equivalent to my /home/ubuntu/tmp/reamster-root/etc , which was created  by UCK.
But it won't work and return the following:

```
root@ubuntu:/# sudo cp -L /etc/resolv.conf /home/ubuntu/tmp/remaster-root/etc/
sudo: unable to resolve host ubuntu
cp: target '/home/ubuntu/tmp/remaster-root/etc/' is not a directory

```

I also tried to start with /remaster-root, but it failed as well.

```
root@ubuntu:/# sudo cp -L /etc/resolv.conf /remaster-root/etc/
sudo: unable to resolve host ubuntu
cp: target '/home/ubuntu/tmp/remaster-root/etc/' is not a directory

```


Can somebody help me out?

---

