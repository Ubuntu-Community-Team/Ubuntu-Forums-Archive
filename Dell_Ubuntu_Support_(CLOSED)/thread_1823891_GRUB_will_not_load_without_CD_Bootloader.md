---
title: "GRUB will not load without CD Bootloader"
date: 2011-08-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wsmccusker on 2011-08-12
I am trying to complete a Multi-boot system with Windows, Mac OS X, Ubuntu and Fedora.
I am doing this to experiment with operating systems and programming before I go to university in October.

I planned to install them in this order:
Mac OS X - Done
Windows 7 - Done
Ubuntu - Done
Fedora - Not Done.

I was following a guide from insanely mac forums and it didn't work as planned. 
[http://www.insanelymac.com/forum/index.php?showtopic=165899](http://www.insanelymac.com/forum/index.php?showtopic=165899)
It says to install Chameleon bootloader, but when it comes to trying to erase the EFI in step 4, it doesn't work So I can't continue with that,

I can use an SLBoot123 CD (Chameleon on disk) and it allows me to boot into Windows, Mac OS X and GRUB2 (when I use the linux option). 
From there I can boot into Linux, Linux Safe mode, Windows and Mac OS X 32&64 Bit.

So Now I want to use GRUB but I cannot get my laptop to boot to GRUB without using the bootloader CD.

Any Ideas on how to get it to default boot to GRUB??

---

### Post by wsmccusker on 2011-08-12
> **x-D said:**
> _**THE METHOD I'M ABOUT TO SHOW YOU CAN BE DONE FROM:**_

. A LIVE DISK/CD/DVD
. A LIVE USB
. ANY OTHER LIVE MEDIA
. AN INSTALLED VERSION OF UBUNTU (KUBUNTU, XUBUNTU, EDUBUNTU, UBUNTU, LUBUNTU, ETC, ETC)

The absolute EASIEST WAY, to (re)install GRUB is to use a little program   called Boot-Repair. It does all that work to do with commands in the   Terminal to reinstall GRUB for you, and it's really noob friendly, with a   simple GUI, that you merely have to indicate which OS you want as your   main Operating System etc, IF YOU WANT TO! This is all under advanced   options, but really, it's not so advanced, anyway to get Boot-Repair:[U][B]

Do this in the Terminal:[/B][/U]

```

sudo add-apt-repository ppa:yannubuntu/boot-repair

sudo apt-get update && sudo apt-get install -y boot-repair-ubuntu

```Now, run the program (search for it in Unity, or go to: System   ----> Administration ----> Boot Repair, in Gnome 2/ Classic Mode   in 11.04 Natty Narwhal)

Then, once the program is done reinstalling GRUB (should take at max 2 minutes), do this:

```

sudo update-grub

```This is probably not necessary, but it will just eradicate the potential for any errors, whatsoever!

_**Inf****o for this can be found by:**_

a) going to: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
b) messaging me here.

Hope this helped...

x-D :guitar:
Got it from this. Now I can boot to all my Operating systems

---

### Post by haqking on 2011-08-12
The easiest way was to install Operating System of choice then use Virtualisation like VMware or Virtualbox ;-)

---

