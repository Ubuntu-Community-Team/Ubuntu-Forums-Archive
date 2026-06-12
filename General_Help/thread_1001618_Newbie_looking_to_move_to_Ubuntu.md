---
title: "Newbie looking to move to Ubuntu"
date: 2008-12-04
forum: General Help
---

### Post by admac21 on 2008-12-04
First off, I'd like to say that about a year ago I installed Ubuntu on a whim, completrely deleting windows altogether... big mistake. I have since reinstalled windows and not really looked at linux since then. But after looking through the internet I'd like to install Ubuntu again, but in a more controlled manor. 

I have a few things I'd like to do, but I just want to make sure/get help with doing it so that I don't end up doing something I regret. I'd also like to mention that I have a live CD of the latest Ubuntu release.

First, I'd like to know the best version (kubuntu, ubuntu, xubutu) For me. I have a fairly powerful computer, and like to customise my UI quite a bit. So which one offers the best customisation options (easiest, coolest) and best compatibility/programs for an average computer?

Second, I'd like to dual boot with windows, but have a seperate partition where I can access my files from both OSs. I read somewhere that this is possible, I just want to check if it actually is, and how I'd actually go about doing it.

Third, I have a few accessories and programs that I'd like to use and was wondering if it is possible; my wacom tablet, with screen mapping, my webcam, MSN, or equivelent program that allows webcam aswell as access to my MSN friends list, and Photoshop CS3. I read that the latest wine release supported photoshop, but I wasn't sure what version, or if it was fully supported.

EDIT: Fourth, what is the difference between gnome, and kde? I've had a look through the forums but still not entirely sure of the difference.

Thanks in advance for any replies :D

---

### Post by Peter09 on 2008-12-04
Download the LiveCD, it will allow you to install a dual boot Ubuntu and windows system. 

The Linux architecture is based around a core operating system call Linux. This does most of the 'computing'.

On top of this there are various 'window managers' which change the look and feel of the system. Ubuntu can be configured with various WM's, GNOME and KDE are the common ones.

My personal preference is for GNOME although KDE is ok. KDE is more 'windows' like then GNOME. My advice would be to go with GNOME as it is the 'standard' distribution for Ubuntu. You can always change later, or run a KDE virtual machine within UBUNTU to see what its like.

---

### Post by mick8985 on 2008-12-04
I prefer Gnome also, but I think given your description, you should go with KDE at first, and see what you think of Gnome later on, for example Kopete is KDE's messenger program, and it supports webcam, Gnome doesn't have a native messenger program that supports MSN and has webcam support. KDE has lots of easy configuration tools to configure the UI, Gnome is configurable but it hides more of its options to keep a cleaner UI.

---

### Post by ajcham on 2008-12-04
> **admac21 said:**
> 
First, I'd like to know the best version (kubuntu, ubuntu, xubutu) For me. I have a fairly powerful computer, and like to customise my UI quite a bit. So which one offers the best customisation options (easiest, coolest) and best compatibility/programs for an average computer?

Well, underneath they are all the same system, so issues with compatibility are the same.  As for UI customisation, in the past Kubuntu would have been your choice here, as KDE 3.5 was far more flexible in this area than Gnome.  With KDE 4 now released, this is no longer the case for the time being.  I would recommend installing the regular Ubuntu for now - you can always install other environments later if you want.

> **admac21 said:**
> 
Second, I'd like to dual boot with windows, but have a seperate partition where I can access my files from both OSs. I read somewhere that this is possible, I just want to check if it actually is, and how I'd actually go about doing it.


This is perfectly possible, and is a simple matter of defining an extra partition during the install.  However, this does mean you will have to edit partitions manually but armed with the right information this isn't as painful as it would seem.  However, be sure to backup your Windows drive first, just in case.


> **admac21 said:**
> 
Third, I have a few accessories and programs that I'd like to use and was wondering if it is possible; my wacom tablet, with screen mapping, my webcam, MSN, or equivelent program that allows webcam aswell as access to my MSN friends list, and Photoshop CS3. I read that the latest wine release supported photoshop, but I wasn't sure what version, or if it was fully supported.

I can't say for certain, but my hunch is your tablet and webcam should work fine. MSN will not work, but there are compatible programs, such as Pidgin. Unfortunately, to my knowledge, none have yet added a video chat feature. Photoshop CS3 is not fully supported in Wine, at the moment.  It requires quite a bit of jiggery-pokery and even then will not run well.  CS2 runs flawlessly according to the Wine AppDB.


> **admac21 said:**
> 
EDIT: Fourth, what is the difference between gnome, and kde? I've had a look through the forums but still not entirely sure of the difference.

Gnome and KDE, are simply different desktop environments, tailored to operating your PC in slightly different ways. My advice is to try them both out, and see which one your most comfortable with, and also try some of the others such as XFCE. (Assuming the Live-CD is a regular Ubuntu one, you will have probably already tried Gnome).  Personally, I prefer Gnome at the moment - I used to prefer KDE, but since the move to v4 I'm less keen.

For the most part which desktop environment you run will not affect your other programs, although some are designed to integrate better with a particular environment.

---

### Post by Grolsche on 2008-12-04
My advice with regards to kubuntu xubuntu etc, is to stick with the gnome desktop  until you're fully comfortable with navigating and you have everything set up and working. As previously said, Kubuntu,gnome, xubuntu etc are just all graphical user interfaces and have no impact with regards to compatiblilty. In the end it will just come down to which desktop feature you like best and feel comfortable with.

My suggestion is to install the default gnome that comes with ubuntu. Once you feel happy everythign is working as is and you don't need to ask for lots of help or you feel you know where everything is then update to kubuntu or xubuntu etc.

If you ask for help on here most people will probably explain where to go using Gnome interface.

Just my tip anyway. But hey, it's your desktop, your computer so play around and do what suits you best.

---

### Post by admac21 on 2008-12-04
Thanks a lot guys :D Your help is much appreciated. I just need some help with setting up the partitions and I'll be good to go. Basically I'll need 3 of them, One for Windows, one for Ubuntu, and one for all my files. I have a 200GB HD and I would like to know the best size to allocate each partition, also, what program would be the best to use. I know the Live CD has a partition editor with it, but should I use that? Or do it from within windows?

---

### Post by theozzlives on 2008-12-04
I don't like the way KDE handles my network, I use GNOME and it's very customizable. as you can see from my screenshot, I've changed mine quite a bit:

---

### Post by Grolsche on 2008-12-04
dont forget to make a swap partition too.

---

### Post by admac21 on 2008-12-04
A swap partition? Is that the one that would be used by both OSs?

---

### Post by theozzlives on 2008-12-04
> **admac21 said:**
> A swap partition? Is that the one that would be used by both OSs?

No, Windows uses a swap file on your Windows partition.... the swap partition is foe Ubuntu.

---

### Post by admac21 on 2008-12-04
Ah ok, thanks. So I've decided to go with 39GB for each OS, 2GB for the swap, and 120GB for the shared. Would that be sufficient space for each partition?

---

### Post by theozzlives on 2008-12-04
> **admac21 said:**
> Ah ok, thanks. So I've decided to go with 39GB for each OS, 2GB for the swap, and 120GB for the shared. Would that be sufficient space for each partition?

On my laptop with 2 GB RAM, I have 30 GB for Windows, 10 GB for root (/), 512 MB for swap and the rest /home. BTW: 150 GB HD.

---

### Post by meindian523 on 2008-12-04
more than enough.You might want to separate the 39 GB for Ubuntu into a 15GB to be mounted at /,and the rest to be mounted at /home.That way you can install a later version,or a completely new distro without losing your data.For MSN,I would recommend aMSN.

---

### Post by piousp on 2008-12-04
[This link]("http://www.psychocats.net/ubuntu/kdegnome") explains a bit the difference between KDE and Gnome, you may want to take a look at it.

---

### Post by theozzlives on 2008-12-04
Defrag windows before re-sizing the partition

---

### Post by Grolsche on 2008-12-04
Agreed with theozzlives.

Windows uses its own swap within the same partition but linux uses a different partiton for swap. It will also need to be set as a swap partition once you have allocated some space for it.

---

### Post by jmszr on 2008-12-04
admac21,
          I suggest reading this: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) . It is an extremely good resource for those setting up Ubuntu.

---

