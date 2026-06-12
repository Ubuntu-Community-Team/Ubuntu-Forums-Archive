---
title: "screen res problem!"
date: 2009-04-04
forum: Desktop Environments
---

### Post by apitsch on 2009-04-04
I have a problem with my screen resolution, the highest i can get is 832x624. nothing ever fits on the screen on websites and i just cant deal with it anymore. Im a complete beginner btw so step by step solutions would be great! I THINK it might be a graphics card problem? I've looked all over and cant find a way to fix it. Oh and also when i play any games online theyre always really slow and i never had this problem on xp. any help would be much appreciated!
Thanks in advance!

---

### Post by overdrank on 2009-04-04
Hi and welcome, what is the model of the graphics card? You may use the command lspci in the terminal which is located under applications, accessories. Look for VGA, you may also look under system, Administration hardware to see if any drivers are available.

---

### Post by andrea000 on 2009-04-04
welcome

What type of card and modal do you have?You could have 
the wrong driver or the driver may not be working very 
well with your card.Post the type of card and modal 
and i may be able to help you.

---

### Post by apitsch on 2009-04-04
i get this when i put in the lspci command

01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

I went to hardware drivers and it said no proprietary drivers are in use on this system.

thanks for the quick replies!

---

### Post by apitsch on 2009-04-04
heres the rest of the message from the terminal, if it helps

adam@adam-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:05.0 Modem: Motorola SM56 Data Fax Modem (rev 04)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

---

### Post by overdrank on 2009-04-04
> **apitsch said:**
> i get this when i put in the lspci command

01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

I went to hardware drivers and it said no proprietary drivers are in use on this system.

thanks for the quick replies!

Hi and I do not have a lot of experience with that chipset but you may look here [OpenChrome]("https://help.ubuntu.com/community/OpenChrome")

---

### Post by inobe on 2009-04-04
i would start with "Packages repository" from overdrank's link.....

> Packages repository

The subversion (SVN) repository will have the latest source code with fixes for the openchrome driver. A manual installation is required to use the latest driver.

To make installation of the driver easy, the openChrome project mantains a repository of contributed binary packages for different Linux distributions.

Warning: by the time they are published some binary packages may be out of date with respect to the distribution's own package and most probably with respect to the subversion repository.

[http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Collection+of+contributed+binary+packages](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Collection+of+contributed+binary+packages)

Download the .deb for your Ubuntu version and then install it 

```
sudo dpkg -i [package_name.deb]
```





that is possibly the easiest way !

i have the same chipset on another pc, i have failed installing the driver in the past' however with this documentation overdrank posted i will attempt it again ......

thanks overdrank :)

---

### Post by inobe on 2009-04-04
a side note: it is **important** to have your system fully updated prior to installing any driver !

have you ran the updates ?

if not' you should, in terminal type

```
sudo apt-get update
```

then hit enter, you should then see a red arrow up at top right next to connection icon, apply the updates and restart your computer......


typically these updates may fix your resolution and you may not need to install the driver mentioned in previous posts.

---

### Post by andrea000 on 2009-04-05
If you have a nvidia card  check out this [link]("http://albertomilone.com/nvidia_scripts1.html") but i say from what i read the 
Open Chrome would be your best bet.Envyng is only for NVIDIA cards 
from what i know Open Chrome seems to be the type of card you have sorry 
i do not know nothing about that card.I would start by looking for 
proprietary drivers and looking in the package manager is a good place 
to start. 

good luck

---

### Post by gjoellee on 2009-04-05
just do an xfix... read about it here: [http://kshoster.net/tuts?c=tuts/ubuntu/xfix](http://kshoster.net/tuts?c=tuts/ubuntu/xfix)

---

### Post by apitsch on 2009-04-05
i messed something up pretty bad trying the steps on the openchrome page. i got to part 4 and when i did the control alt F1 command i got stuck in the terminal, so i restarted. now when i start up it gets to the ubuntu loading screen and then goes black and i cant do anything from there. if i press escape right after i turn it on it brings me to a screen and asks me to choose one of the ubuntu things, like recovery mode or normal mode. i tried to go into recovery mode and it brought me to the recovery menu where it says resume normal boot, try to make free space, repair broken packages, file system check, drop to root shell prompt, and try to fix x server. normal boot gives me the black screen, try to fix x server says some stuff and then brings me back to the menu. is there something i can put in if i go to the root shell prompt? really need all the help i can get here cause my computer is pretty useless right now.

---

### Post by andrea000 on 2009-04-05
you may need to pick repair broken package I am not sure 
what all you have going on or what you have done.But here 
is a [link]("http://www.via.com.tw/en/resources/pressroom/pressrelease.jsp?press_release_no=2227") You should be able to search from there and find a driver.

---

