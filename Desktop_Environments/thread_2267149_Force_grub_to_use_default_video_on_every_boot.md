---
title: "Force grub to use default video on every boot"
date: 2015-02-27
forum: Desktop Environments
---

### Post by iansan on 2015-02-27
In a [previous question]("http://ubuntuforums.org/showthread.php?t=2261946&page=2") I explained a grub issue I'm having where booting from the menu works every other time for Ubuntu 14.04 64-bit. User oldfred said that this could be related to video and/or shutdown. I marked that post as solved since I planned to use a partition to test as he suggested, but can't take that approach right now and so I'd like to resolve this with grub settings if possible.

How do I force grub to use default video settings on boot? It sounds to me that when grub uses the default video settings those are the boots that work correctly, and when it uses non-defaults I get the blank screen boot. My graphics card is a MSI GeForce GTX 970. I'm not using the Nvidia drivers because of past issues with kernel updates.

---

### Post by oldfred on 2015-02-27
Grub does use default X by Y settings from install if possible. 

Did I post these before? I think then Nouveau does not work and you have to have a very new nVidia installed from a ppa.

 The GTX 970/980 Maxwell GPUs Light Up With Nouveau On Linux 3.19
[http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg](http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg)
NVIDIA GeForce GTX 970/980: Windows vs. Ubuntu Linux Performance 2015 note versions ppas used to update
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1)
Install with Asrock Z97 & nVidia 970
[http://ubuntuforums.org/showthread.php?t=2257406](http://ubuntuforums.org/showthread.php?t=2257406)
[http://ubuntuforums.org/showthread.php?t=2259210](http://ubuntuforums.org/showthread.php?t=2259210)


 Details on settings in /etc/default/grub
 info -f grub -n 'Simple configuration'
> `GRUB_GFXMODE'
     Set the resolution used on the `gfxterm' graphical terminal.  Note
     that you can only use modes which your graphics card supports via
     VESA BIOS Extensions (VBE), so for example native LCD panel
     resolutions may not be available.  The default is `auto', which
     tries to select a preferred resolution.  *Note gfxmode::.


   From a grub command line to see available settings pressing <c> & escape to get back to menu
vbeinfo

---

### Post by iansan on 2015-03-05
I set GRUB_GFXMODE=640x480, ran sudo update-grub, and restarted but this didn't change the bad boots on every other cycle. The grub menu continued to work as it does on every boot, this time at the lower 640x480 resolution.

It looks like nouveau isn't working:
```
dmesg | grep nouveau
[    0.628163] nouveau E[  DEVICE][0000:01:00.0] unknown chipset, 0x124020a1
[    0.628165] nouveau E[     DRM] failed to create 0x80000080, -22
[    0.628821] nouveau: probe of 0000:01:00.0 failed with error -22
```

Ubuntu 15.04 is coming out next month and looks to include kernel 3.19 with some basic Maxwell GPU support. I'll do a fresh install of it and report back on whether it solves this issue or not.

---

### Post by iansan on 2015-06-17
So I'm still using 14.04 and I did get this resolved. [Blacklisting the nouveau driver]("http://askubuntu.com/questions/451221/ubuntu-14-04-install-nvidia-driver") fixed the blank screen I was getting after grub. Hope this helps someone.

---

