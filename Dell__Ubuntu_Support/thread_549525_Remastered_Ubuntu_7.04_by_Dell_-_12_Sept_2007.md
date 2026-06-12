---
title: "Remastered Ubuntu 7.04 by Dell - 12 Sept 2007"
date: 2007-09-12
forum: Dell  Ubuntu Support
---

### Post by chrome307 on 2007-09-12
**Last Updated:  	September 12th, 2007 18:46**

Source:

[http://news.softpedia.com/news/Remastered-Ubuntu-7-04-by-Dell-65323.shtml](http://news.softpedia.com/news/Remastered-Ubuntu-7-04-by-Dell-65323.shtml)


Last evening, Dell announced the immediate availability of a remastered Ubuntu 7.04 (Feisty Fawn) that will help you with the installation process of Ubuntu OS on **[COLOR="Red"]Inspiron E1505N, 1420N and 530N[/COLOR]** Dell computers. The remastered ISOs include all the necessary drivers and patches that will get Ubuntu up and running with the hardware included in the previously mentioned systems. "For example, this media takes care of all of the steps identified here to get the OS installed on the Inspiron 1420. Please try this out, and let us know how it works." - stated John Hull, Manager of Linux OS Engineering at Dell.

**The Dell Linux team removed OpenOffice.org packages that you find in a regular Ubuntu 7.04 CD, to make room for the necessary drivers and patches.** Moreover, be aware that the remastered CDs from Dell are not officially supported by Dell in any way, therefore do NOT call Dell technical support with questions about these images, or the included software and be sure to update the OS after the installation.

**Available to download here:**

[http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Dell-Remastered-Ubuntu-30344.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Dell-Remastered-Ubuntu-30344.shtml)

**Ubuntu 7.04 Feisty Fawn**

[http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ubuntu-Feisty-Fawn-20757.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ubuntu-Feisty-Fawn-20757.shtml)

**Kubuntu 7.04 Feisty Fawn**

[http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Kubuntu-Feisty-Fawn-20764.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Kubuntu-Feisty-Fawn-20764.shtml)

**Xubuntu 7.04 Feisty Fawn**

[http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Xubuntu-Feisty-Fawn-22250.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Xubuntu-Feisty-Fawn-22250.shtml)

**Edubuntu 7.04 Feisty Fawn**

[http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Edubuntu-Feisty-Fawn-20766.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Edubuntu-Feisty-Fawn-20766.shtml)

**Alpha version of Ubuntu 7.10 (for testing purposes only)**

[http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ubuntu-Gutsy-Gibbon-27851.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ubuntu-Gutsy-Gibbon-27851.shtml)

---

### Post by sciurus on 2007-09-12
The links above seems to be to Canonical's releases, not the remastered one from Dell. Here are the dell press release and download links.

Dell Linux Engineering team has a remastered copy of the Ubuntu 7.04 Live CD available for download. It includes native system hardware support and many of the fixes listed below. The media will help you get the system installed and running with the necessary drivers.

The media has been created specifically to resolve issues on the following system:

    * Inspiron E1505N
    * Inspiron 1420N
    * Inspiron 530N 

NOTE:This media contains GPL-licensed drivers only, and does not contain Conexant modem driver for the Inspiron 1420n, E1505n, and 6400n (which can be downloaded separately from [http://support.dell.com](http://support.dell.com)). All drivers on this media are already available in the Ubuntu 7.04 apt repositories.

Download Dell Ubuntu Image

DISCLAIMER: These images are both unofficial Dell recovery media. They are not officially Dell-supported. Do not call Dell Technical support with questions about this image, or software installed by this image, as they will not be able to help you. To get help, please send an email to the Dell linux-desktops mailing list. 

[http://linux.dell.com/dru/images/ubuntu-7.04-desktop-i386-dell-cd-0.2-2.iso](http://linux.dell.com/dru/images/ubuntu-7.04-desktop-i386-dell-cd-0.2-2.iso)

[http://linux.dell.com/dru/images/ubuntu-7.04-desktop-i386-dell-dvd-0.3-3.iso](http://linux.dell.com/dru/images/ubuntu-7.04-desktop-i386-dell-dvd-0.3-3.iso)

NOTE: After installation, be sure to update to the latest system software.

NOTE: The CD image has been modified to remove components such as OpenOffice to make room for additional Dell specific drivers and fixes.

---

### Post by ubermenschx on 2007-09-13
Will the 7.10 release for this be out Oct 18 with the other standard versions?

---

### Post by notwen on 2007-09-13
> **ubermenschx said:**
> Will the 7.10 release for this be out Oct 18 with the other standard versions?

Possibly sometime later, I'm sure Gutsy will bring in even more packages that may or may not cause more issues.

---

### Post by EL-Sato on 2007-09-15
mmm interesting, ill try it on my 1720, just to see :)

---

### Post by WAB on 2007-09-17
I'm trying to install this remastered version on my 1420. In my country it is not possible get a n-series machine, so I had to buy a vista based one. However I need to preserve the vista system, and when I install with the ubuntu live CD I can't  get a dual boot system. 
I used the vista disk manager for shrinking a big partition obtaining the necessary space for the installation. 

For the ubuntu installation process I created a boot partition (/boot), a swap partition a root partition (/) and a home one (/home).

Later on, the "migation assistant" does not produce anything, and in the last step (where the installation starts) this item is empty. In this same step the advanced option ask for a device for boot instalation, in my case the boot partition corresponds to /dev/sda6, but using value this did not work.

Finally, after the 7 step I rebooted my machine, starting a classical windows error interface, after a few seconds started vista, and ubuntu became a ghost.

I've seen past threads about this, but the information is too old and not very useful. How can I modify some boot configuration (in grub for example) if I can't get acces to my ubuntu system (I don't know rescue disks or something...)? or better, how can I solve this problem, without affect my MBR or finally have to install vista again?

---

### Post by yther on 2007-09-19
Regarding dual-booting Vista and Linux, I found [this article](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx) very useful when putting Kubuntu on my Inspiron.

Basically you use Vista's boot menu to load either Vista itself or GRUB, which can then boot anything else you'd like it to.  I use a similar setup on an XP box; the benefit is that Windows never knows it's not the only thing installed, so it doesn't try to "fix" anything.  :D

Good luck!

---

### Post by WAB on 2007-09-19
Hi guys, I solved the dual boot problem using an additional piece of software called EASYBCD.exe. Using this I finally could boot Vista and Ubuntu without overwrite my MBR with GRUB neither change the original partitions. 

It has an ugly effect because firstly you see the vista boot loader, and when you select Ubuntu, then you are "redirected" to GRUB for making a second time selection.

However it is acceptable and the problem was fixed. Media direct is still working.:)

---

### Post by captevo on 2007-10-05
Hello all,
I used Dell Remastered version, and got everything working on my Vostro 1400.
Questions:
When 7.10 releases, should I fo distribution upgrade?  would it break my current installation? 
Or should I wait for Dell Remastered Gutsy?
Thanks...

---

