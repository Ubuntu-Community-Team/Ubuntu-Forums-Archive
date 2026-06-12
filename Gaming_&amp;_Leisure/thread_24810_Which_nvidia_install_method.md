---
title: "Which nvidia install method?"
date: 2005-04-08
forum: Gaming &amp; Leisure
---

### Post by titus on 2005-04-08
Hi, i've installed the nvidia drivers in the past by downloading the binary .run package from nvidia, dropping to runlevel 3 (fedora core 3) and running this package, and then altering xorg.conf

I notice that in the unoffical guide it mentions apt installing nvidia-glx and nvidia-settings, then running nvidia-settings to configure.

What are the differences between the two methods?

Which is preferred for ubuntu?

Is there anything else I should think about?

Thanks,

titus.

---

### Post by Leif on 2005-04-08
The apt method is preferred, as this will get you officially supported ubuntu packages. It's also a fair bit easier, and will get upgraded automatically as nvidia updates their drivers.

---

### Post by jdodson on 2005-04-08
i agree with leif, use the apt method.  the upgrades are easier and maintaing the packages is easier.  plus it is way simpler to setup with three apt commands.

are you using fedora for this?

---

### Post by titus on 2005-04-08
i'm on ubuntu now (5.04)

I've now installed via this method and get a nice 12k from glxgears.

:)

seems to be working well.

thanks guys,

titus.

---

### Post by dermotti on 2005-04-08
What card you getting 12k on ?

---

### Post by titus on 2005-04-09
6800gt, it's up to 14k after i dropped to i386 to use cedega reliably.

:)

---

### Post by SquireSCA on 2005-04-09
What are those 3 commands?  I tried several methods of installing the drivers and I could never get them to work.  I also have a 6800GT that should get great performance, if only I could install the drivers.  The only distros I was ever able to successfully install ATI or NVidia drivers for was Mandrake and Suse.  Ubuntu threw me a curve and had me stumped.

I went and put WinXP back on my system but left 40GB free on the boot drive in order to play around with ubuntu, but leaving me Windows to fall back on if(when) I screw it up...  hehe

I had three main problems with ubuntu:

1) Installing NVidia drivers.
2) Getting my second SATA drive to mount under Gnome(KDE does it automatically).
3) Enabling DMA on my DVD drives.

The first problem was just my not doing it right, Iam sure.  The second is a Gnome issue, as KDE automatically mounts all hard drives for you. SOmeone just didn't think to do it by default, that's all.  

The third item, is just plain stupid.  It's 2005, and 99.9% of people have decent PC's and would need DMA enabled by default.  It's not 1997 where the average PC might be a Pentium 90Mhz with a 2X CDROM and DMA would be questionable...

---

### Post by titus on 2005-04-09
I followed this :

[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

good luck.

titus

---

### Post by Omnios on 2005-04-12
Im a New Linux total Newb. I have a xserver error "black screen of death" so I downloaded the nvidea drivers but cant seem to use sudo nvidia-glx-config enable to install it I looked in xserver reconfig to see if it was in there but couldnt seem to find it there either. ALso is there a key short cut for dos mode?

---

### Post by MaX on 2005-04-12
[QUOTE=Omnios]Im a New Linux total Newb. I have a xserver error "black screen of death" so I downloaded the nvidea drivers but cant seem to use sudo nvidia-glx-config enable to install it I looked in xserver reconfig to see if it was in there but couldnt seem to find it there either. ALso is there a key short cut for dos mode?[/QUOTE]
 DOS mode?? You're on linux now, its called a terminal input. and the fast way there is Ctrl+Alt+F1-F6.

---

