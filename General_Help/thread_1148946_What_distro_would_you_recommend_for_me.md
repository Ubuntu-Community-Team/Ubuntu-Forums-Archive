---
title: "What distro would you recommend for me?"
date: 2009-05-04
forum: General Help
---

### Post by Virtualboxbuntu on 2009-05-04
Hello,

I currently have Linux Mint 6 KDE on my desktop. I think that superficially, it's fantastic. Unfortunately, it inherits most of Kubuntu's packages and repositories. In my experience, its packages are all jumbled up, and I can't install certain packages without breaking others.

I've tried PC BSD in VirtualBox and it's great, but it doesn't work on my desktop's motherboard.

My desktop is a few years old, but it can run pretty much any operating system fast. It came with Windows Vista Premium 32 bit (although it has an AMD 64x2 processor), which I have long since removed.

Here is my criteria for a distro:

-NOT based on *buntu

-64 bit available (not required but would like it)

-Easy installation of programs (maybe like PC BSD's PBIs, I suppose CNR would do). It's not necessary, I consider apt-get or zypper or whatever to be okay.

-MUST have the latest major release of KDE; at least 4.2.0

-Not have messed-up packages like Kubuntu

-Should be regularly updated

Some special hardware of mine that MUST work:

-DLink wireless G adapter. It works out of the box in Linux Mint and PC BSD, and strangely not at all in Windows Vista. I'm not sure about other distros.

-NVidia card. It uses the 173 driver. I don't care how, but I have to be able to get that driver.


Thank you very much in advance for helping me, I can't stand Kubuntu's broken packages. I think I will try OpenSuSE right now, but in case it doesn't work, I'd like your suggestions.

---

### Post by garythegoth on 2009-05-04
> **Virtualboxbuntu said:**
> Hello,

I currently have Linux Mint 6 KDE on my desktop. I think that superficially, it's fantastic. Unfortunately, it inherits most of Kubuntu's packages and repositories. In my experience, its packages are all jumbled up, and I can't install certain packages without breaking others.

I've tried PC BSD in VirtualBox and it's great, but it doesn't work on my desktop's motherboard.

My desktop is a few years old, but it can run pretty much any operating system fast. It came with Windows Vista Premium 32 bit (although it has an AMD 64x2 processor), which I have long since removed.

Here is my criteria for a distro:


-NOT based on *buntu

-64 bit available (not required but would like it)

-Easy installation of programs (maybe like PC BSD's PBIs, I suppose CNR would do). It's not necessary, I consider apt-get or zypper or whatever to be okay.

-MUST have the latest KDE

-Not have messed-up packages like Kubuntu

-Should be regularly updated

Some special hardware of mine that MUST work:

-DLink wireless G adapter. It works out of the box in Linux Mint and PC BSD, and strangely not at all in Windows Vista. I'm not sure about other distros.

-NVidia card. It uses the 173 driver. I don't care how, but I have to be able to get that driver.


Thank you very much in advance for helping me, I can't stand Kubuntu's broken packages. I think I will try OpenSuSE right now, but in case it doesn't work, I'd like your suggestions.

openSUSE 64bit is pretty sweet, but it uses KDE 4.2.1. It has way better hardware detection than Ubuntu from my experience. It **SHOULD** be able to install a driver for your nVidia card, but its been slightly dodgy when I tried it. The 32bit GNOME version screwed up whenever I tried to install the graphics driver, whereas the 64bit KDE version worked fine. So trial and error may be your friend :)

---

### Post by 67GTA on 2009-05-04
Based on your criteria, I was going to suggest Opensuse. It is my second choice next to the buntu's. The only con is figuring out the multimedia mess.

---

### Post by snowpine on 2009-05-04
Sidux KDE might be a good option... very cool and up-to-date distro... you might have to do a little research whether it will meet your hardware needs though.

---

### Post by Virtualboxbuntu on 2009-05-04
> **67GTA said:**
> Based on your criteria, I was going to suggest Opensuse. It is my second choice next to the buntu's. The only con is figuring out the multimedia mess.

I almost forgot that most distros don't come with multimedia codecs! I've gotten so used to Linux Mint.

I will begin downloading OpenSuse. What I meant by latest KDE is that it must be at least the latest **major** release; i.e. 4.2.0. Sorry I didn't make that clear enough.

---

### Post by Stupendoussteve on 2009-05-04
Arch Linux would work, but I think you probably wanted easy to install as well.

OpenSUSE is the main one I can think of, though you might like Vector Linux, Zenwalk or Sabayon.

---

### Post by Virtualboxbuntu on 2009-05-04
> **Stupendoussteve said:**
> Arch Linux would work, but I think you probably wanted easy to install as well.

OpenSUSE is the main one I can think of, though you might like Vector Linux, Zenwalk or Sabayon.

Yes, I tried Sabayon in VirtualBox once, it looked great, but I didn't mess around with it a lot. I believe it's based on Gentoo, which is a source distro, right? In that case, I might not be prepared for that.

---

### Post by SuperSonic4 on 2009-05-04
> **Stupendoussteve said:**
> Arch Linux would work, but I think you probably wanted easy to install as well.

OpenSUSE is the main one I can think of, though you might like Vector Linux, Zenwalk or Sabayon.

There is always the chakra live cd but you'll have to try and find the 64bit version.

You could always get the Mandriva dvd (64 bit) or cd (32 bit), I believe the CD has the nvidia drivers and (some) codecs installed.

---

### Post by Virtualboxbuntu on 2009-05-04
OpenSuSE 11.1 has downloaded, it seems to have KDE 4.1. But I'm sure there's some way to change that.

In the meantime, I'll install it and see if it works on my desktop.

---

### Post by Virtualboxbuntu on 2009-05-05
OpenSuSE does not work on my hardware.

Sabayon would be next on my list, but there's no official CNR client, and I believe it's based on Gentoo, so I'm not quite ready for that.

Fedora KDE is next to be downloaded then, because I've already had some experience with it in VirtualBox. If that doesn't work, then Mandriva is up next, followed perhaps by Sidux.

---

### Post by abhilashm86 on 2009-05-05
how about building arch linux, its suits for your criteria.........

---

### Post by Virtualboxbuntu on 2009-05-05
I suppose I may try that if I have to, but I don't have a lot of experience, or any at all really, with anything like that. I've already downloaded Fedora KDE, so I'll try that first. If I were to build Arch Linux I'd need some sort of guide, like "Building Arch Linux for Complete Dummies."

---

### Post by Sarai the Geek on 2009-05-05
I was going to recommend Mandriva if you didn't like Suse. I haven't tried it but the package management seems to be, superficially, similar to synaptic/apt-get. Hopefully it will work better, though! ;)

---

### Post by oldos2er on 2009-05-05
> **Virtualboxbuntu said:**
> If I were to build Arch Linux I'd need some sort of guide, like "Building Arch Linux for Complete Dummies."

 Arch has an excellent installation guide: [http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide)

---

### Post by JK3mp on 2009-05-05
If you don't wanna build arch ground up. You could try Chakra, is a base of Arch linux but with graphical installer and all. Only downer possibility is KDE4. Aside from that, fedora does great as far as hardware detection, i've never had an issue with em and as others said OpenSuse is very easy and usable.

---

### Post by Virtualboxbuntu on 2009-05-06
Well, PC-BSD failed and OpenSuSE failed, but Fedora does work with my hardware. Yum seems equivalent to apt-get, which is fine for me.

Thanks for all your help!

---

### Post by Virtualboxbuntu on 2009-05-16
On second thought, it is not fine. I have yet to find a distro where CMake works properly, and I really want to be able to 1-click-install stuff, so Mint and MintInstall are on my computer to stay.

---

### Post by lessgov2007 on 2009-05-16
Ever thought about simply using Debian? By default the debian I think installs Gnome, however you can have it install KDE for you, or even just install the base system and use another method if you choose.

It is not possible to interactively select a different desktop during the installation. However, it is possible to get debian-installer to install a KDE desktop environment instead of GNOME by using preseeding (see Section B.4.11, &#8220;Package selection&#8221;) or by adding the parameter desktop=kde at the boot prompt when starting the installer. Alternatively the more lightweight Xfce and LXDE desktop environments can be selected by using desktop=xfce or desktop=lxde. 
 Some CD images (businesscard, netinst and DVD) also allow selection of the desired desktop environment from the graphical boot menu. Select the &#8220;Advanced options&#8221; option in the main menu and look for &#8220;Alternative desktop environments&#8221;.

Why not just use Kubuntu? I dunno...

---

