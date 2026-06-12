---
title: "GRUB | 2x drives | CentOS_7 and Win 1O Pro"
date: 2017-03-02
forum: Fedora/RedHat and derivatives
---

### Post by gandahar1988 on 2017-03-02
Hey, I'd like to start adventure with Linux :KS but I have a little problem. My notebook does not allow me to select the drive in the BIOS. I can only select "boot from hard drive" without being able to choose a particular disk (1 of 3). The BIOS has disabled the options: secure boot and UEFI boot, I know that they are unnecessary. Two of my drives are media m2 (256GB with Linux Centos7x64 + 512GB Windows 10 Prox64) and the third disk is SSD/SATA (512GB data). At the moment when I change/swap drives in m2 sockets I can run Linux or Windows. Please let me know how do I must configure GRUB or another b-loader to boot Linux by default (with the media 256GB/M2 as primary) and Windows 10 Pro (as seconadry on M2/512GB in "slave" slot).

[ATTACH=CONFIG]273954[/ATTACH]

Thank you for your help and interest [IMG]https://ubuntuforums.org/images/icons/icon7.png[/IMG]

---

### Post by howefield on 2017-03-02
Thread moved to the "*Fedora/RedHat and derivatives*" forum.

---

### Post by gandahar1988 on 2017-03-02
I'm sorry but I can not find it on the forum, if I could ask a direct link?

---

### Post by oldfred on 2017-03-02
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

But most CentOS installs are LVM which I do not know much about.

If Windows fast start up is off then grub can find Windows install if both installs are UEFI (or both BIOS/CSM)
UEFI & BIOS are not compatible and you cannot switch once you start to boot. Or grub can only boot systems installed in same boot mode.

And grub can only find installs that are not hibernated.

       
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by coffeecat on 2017-03-02
> **gandahar1988 said:**
> Hey, I'd like to start adventure with Linux

Welcome to the forum and welcome to the Linux world.

I'm not really in a position to answer your question as I have no recent experience with CentOS, but just a few general comments to someone who appears to have landed up in the wrong place. You are not unwelcome - far from it - but this is not the best place to get help for CentOS. Our focus is on the Ubuntu family of distributions - the hint is in the title "ubuntuforums" :wink: - whereas CentOS comes from the Red Hat family. If you are uncertain about the meaning of the words distro (distribution), this wikipedia article will get you started:

[https://en.wikipedia.org/wiki/Linux_distribution](https://en.wikipedia.org/wiki/Linux_distribution)

We provide areas of the forum, such as this, for distros other than Ubuntu and its official variants for the convenience of forum members who are mostly using Ubuntu or an official variant. We never intended it to be a primary source of support for the non-Ubuntu distributions. For CentOS, you are probably better off in their own forum here:

[https://www.centos.org/forums/](https://www.centos.org/forums/)

Also - as a newcomer to the Linux world, are you sure that CentOS is the best choice for you? It is an excellent distro, but has a focus on the enterprise environment. Depending on your needs, you might find another distro more suitable.  

> **gandahar1988 said:**
> I'm sorry but I can not find it on the forum, if I could ask a direct link?

What can't you find?

---

### Post by gandahar1988 on 2017-03-04
thank's for info.

---

