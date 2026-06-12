---
title: "multiboot"
date: 2009-05-23
forum: General Help
---

### Post by mehrotra.akash on 2009-05-23
i have a P4 3GHz 2GB ram with ATI Xpress 200 onboard card
2 HDD's
1- 80GB
other 250GB
currently win XP is installed, but want to try out linux, so i am planning to install quite a few distos , use them for a month and then see which one i like and clean format the comp and install that one

the versions i am looking to install simultanneously are
ubuntu
kubuntu
fedora
mint
XP
Vista
Win 7 RC

1 - is it possible to have so many OS's on a comp? - HDD space is not a problem
2- any tips on doing it - whether installations will be like a typical dual boot or some other steps required>
3- is it better for me to go for the 32 bit versions or 64 ??(my P4 supports EM64T)
4- are there any major problems i could face with my graphics card?


just found this page  [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)
says that my card is restricted to 9.3 driver, so does it mean that i cannot run ubuntu/kubuntu 9.04??g

---

### Post by logos34 on 2009-05-23
> **mehrotra.akash said:**
> 
the versions i am looking to install simultanneously are
ubuntu
kubuntu
fedora
mint
XP
Vista
Win 7 RC

1 - is it possible to have so many OS's on a comp? - HDD space is not a problem

Sure, no prob.  The limit is 4 primary partitions per disk, but you can make a big extended partition and put all the linux OSs inside on logical partitions (limit 63)...As long as one windows installation is on a primary, it can serve as boot partition for other windows installations on logicals.  Or use primary partitions for all three windows...

You might also consider running them all inside VirtualBox or VMWare server

> 2- any tips on doing it - whether installations will be like a typical dual boot or some other steps required>
3- is it better for me to go for the 32 bit versions or 64 ??(my P4 supports EM64T)

There's some guides over at [apcmag.com]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm")...They're all about dualbooting, but might be helpful

One thing I would do is install kubuntu inside ubuntu to save a partition, so basically when you want kubuntu you just logout of ubuntu and into the kubuntu desktop.

All you need to do is:

sudo apt-get install kubuntu-desktop

You can use Grub or EasyBCD to chainload all the OSs.
Personally, I would try to use grub.  Grub is the default on all of the distros you mentioned...Whichever one you install last will detect all the other OSs and add boot entries to grub menu.  If you should later decide to uninstall that distro, just make sure to reinstall grub pointing to one of the remaining partitions, otherwise you'll be unable to boot.

For pros and cons of x64 vs 32-bit read [this sticky]("http://ubuntuforums.org/showthread.php?t=765428").

> 4- are there any major problems i could face with my graphics card?

anyone?

---

### Post by mehrotra.akash on 2009-05-24
1- for the partitioning could  you provide some guide as to how to install linux on extended partitions

2- my ATI Xpress card is in legacy now, so will i not be able to run ubuntu 9.04 at all? or will i only not get the advanced graphics?

---

### Post by TheNosh on 2009-05-24
since primary/extended/logical partitioning has already been mentioned, i couldn't do a decent job of explaining it to you, i'd just like to ask a question... why on earth do you want to do this?

why 3 versions of windows?
also mint is so similar to ubuntu/kubuntu

i'm not trying to criticize, quite the opposite, i'm just expecting an interesting answer;)

---

### Post by logos34 on 2009-05-24
the nosh has a point about mint...I almost mentioned it...underneath it's basically identical to ubuntu, just that it includes restricted codecs/drivers out-of-the-box and has different look/themes

search the ubuntu community docs (link below) for info on xpress200, should be something mentioned there

---

### Post by mehrotra.akash on 2009-05-24
> **TheNosh said:**
> since primary/extended/logical partitioning has already been mentioned, i couldn't do a decent job of explaining it to you, i'd just like to ask a question... why on earth do you want to do this?

why 3 versions of windows?
also mint is so similar to ubuntu/kubuntu

i'm not trying to criticize, quite the opposite, i'm just expecting an interesting answer;)


as i was told above i will be installing kubuntu on ubuntu to save a partition
using mint as, while based on ubuntu it has a different GUI and seems more user frendly

the 3 versions of windows are as the comp is also going to be used by the family during this period and they want to try out vista, but use XP if they dont like it

i myself want to try out win 7 RC and see if there are any compatibility problems with my hardware

could you tell me where i can find a guide on installing the OS's on extended partitions?

---

### Post by bm40 on 2009-05-24
A good guide is how to install and boot 145 operating systems.

[www.justlinux.com/forum/showthread.php?t=147959]("http://www.justlinux.com/forum/showthread.php?t=147959")

I have 1 hard drive that has 3 primary partitions that have win xp and win 7 rc and
a small fat 16 partition to hold grub.

Second hard drive with 2 primary partitions and 1 extended partition with 6 logical partitions.
I have 1 partition as a linux-swap that all linux use. 1 partition ntfs for all files, so all os's can read. Logical partitions have Ubuntu 9.04 and some other Linux distro's.

My main OS is Ubuntu. I do a lot of computer work for other people so I have to keep up with windows.

---

### Post by 3rdalbum on 2009-05-24
The Xpress 200 does not have 3D support in the proprietary driver. DO NOT INSTALL THE ATI/AMD PROPRIETARY DRIVER. It might have basic 3D support in the open-source driver, so you could run Compiz (visual effects) rather slowly. Failing that, it definitely has 2D acceleration support and can run Ubuntu 9.04.

Any graphics card works with Ubuntu, it's just a matter of acceleration.

You can install KDE on top of regular Ubuntu, and switch between KDE and Gnome at the login screen. So, no need to install Kubuntu. Linux Mint is basically Ubuntu with some extra bits added, and while it's a good distribution there's really no point running both it AND Ubuntu. It's not "more user friendly", it's the same level of friendliness, it just looks a little different. You can achieve the same look and feel by customising Ubuntu.

---

### Post by Legace on 2009-05-24
Umm.. What I suggest you do is that you install XP, Vista, 7, and a Linux. After you've tried out that distro, install another distro on top of it (on the same partition). This way, you won't need to create many partitions (only 4).

---

### Post by mehrotra.akash on 2009-05-24
thx

what I will do is install the 3 versions of windows, try to install fedora and ubuntu using the guide given by bm40 above

if i am able to do that then ok otherwise, will install ubuntu and KDE, use it uninstall it try fedora and see which one i like and install that one alongwith the windows i like in dual boot

---

### Post by bodhi.zazen on 2009-05-24
You can also look at something like virtualbox to take these OS for a test drive ;)

See if these links help :

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817") 

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018")

---

