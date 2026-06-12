---
title: "Xubuntu + Ancient System No Display"
date: 2007-08-28
forum: Desktop Environments
---

### Post by malura on 2007-08-28
MSI Motherboard Pentium III - 933-MHz.
Intel 82810E chipset consisting of:

* Intel 82810E GMCH (Graphics/Memory Controller Hub)
o Digital Visual Interface (DVI) header for optional card to support Flat Panel, Digital CRT or TV out
o Interface to ICH2 via the Accelerated Hub Architecture (AHA) interface for I/O support
----> o Integrated Video with AGP interface
+ Integrated 2D and 3D graphics engines
+ Integrated Hardware motion compensation engine
+ Complies with AGP specification revision 2.0

It's got built in video and sound. The problem I'm running into, is that when I try to use a separate PCI video card (mind you I've set the BIOS accordingly), I get the Xubuntu logo with a loading bar, and after it's done loading, the screen goes black. Not the system has been shutdown black, but "I'm planning on loading something else" black. Even after waiting ten minutes, nothing shows. The PCI video card being used is the Stealth 3D 2000 Pro. Now normally, when I boot up with integrated video (Bios set accordingly again), I'm treated with No Xubuntu logo or loading bar, and a black screen for about two minutes until the log on screen shows.

I'm looking for either of these solutions.
A) I'd like to be able to make complete use of the video card. Load up menus, logos, whole nine.
Or B) I'd like to get OpenOffice to work with the Integrated Video. Right now I've got it open, and the top menu is all glitched out. Any help would be Awesome! Thanks.

---

### Post by reset3x on 2007-08-28
Unfortunately some older motherboards let you choose PCI or onboard or auto,,,, The down side is that Ubuhntu sees both and gets confuzzled... Your best bet is to use your onboard,,,, It sucks but thats the only way I've ever gotten it to work... Older mobos with proprietary BIOS just downright stink.......

---

### Post by RedSquirrel on 2007-08-29
> **malura said:**
>  A) I'd like to be able to make complete use of the video card. Load up menus, logos, whole nine.

I don't know anything about that card. Sorry. Maybe try some searches for using that video card under linux and see what you can find.


> **malura said:**
> B) I'd like to get OpenOffice to work with the Integrated Video. Right now I've got it open, and the top menu is all glitched out.

You mean the window titlebar? Try changing your bit depth to 16.

```
gksudo mousepad /etc/X11/xorg.conf
```

find this line:

```
DefaultDepth    24
```

and change it to:

```
DefaultDepth    16
```

Logout. At the login screen press Ctrl-Alt-Backspace. Then login again.

---

### Post by mister_p_1998 on 2007-08-30
> **malura said:**
> MSI Motherboard Pentium III - 933-MHz.
Intel 82810E chipset consisting of:


It's got built in video and sound. The problem I'm running into, is that when I try to use a separate PCI video card (mind you I've set the BIOS accordingly), I get the Xubuntu logo with a loading bar, and after it's done loading, the screen goes black. Not the system has been shutdown black, but "I'm planning on loading something else" black. Even after waiting ten minutes, nothing shows. The PCI video card being used is the Stealth 3D 2000 Pro. Now normally, when I boot up with integrated video (Bios set accordingly again), I'm treated with No Xubuntu logo or loading bar, and a black screen for about two minutes until the log on screen shows.


Some of these onboard video chipsets have the option to choose "boot first with" you've got to choose your pc card in there rather than the onboard.

---

