---
title: "beryl probs, installed everything, but no difference -among other."
date: 2007-07-14
forum: Desktop Effects &amp; Customization
---

### Post by skaspud on 2007-07-14
right now i have a mil things wrong with ubuntu
big ones:
1. i can't get beryl to work
2. i can't get wine to work
3. i can't get windows on my other harddrive to boot

1. i have beryl fully installed using [http://wiki.beryl-project.org/wiki/I...eisty_with_ATI](http://wiki.beryl-project.org/wiki/I...eisty_with_ATI)
i have the driver for my ati x850 pro working fine and everything
the lil beryl icon just sits up top and chills there not doing anything, i've rightclicked-window manager and tried switching to beryl from gnome and it would reload the windows and everything but nothing happened...

2. i've got wine all downloaded and installed, i have it installed but i can't get it to start up,it's not in the applications menu.

3 this is a big one...
i installed ubuntu 6.06 on a second hard drive in my computer, using this i was easily able to switch from ubuntu and back to windows by just switching the bios when booting up. but after i installed 7.04 i tried booting the windows bootup from the bootup menu that ubuntu shows, it starts the windows splash screen but then it doesn't work, it tries loading up GRUB. then says error17 (i think). I can access my C: partition from ubuntu when its hooked up, but i need the stuff from my other partitions. especially the programs and such.

Thanks (hopefully) in advance :]

edit:
i installed my graphics driver using envy- in case it helps...
i saw this thread too:
[http://ubuntuforums.org/showthread.php?t=339426&page=2](http://ubuntuforums.org/showthread.php?t=339426&page=2)
that seemed exactly what i needed but, then i got to the part whenre the xorg confg thing is and i have an ATI so...

i get this too:
skaspud@skaspud-desktop:~$ beryl manager
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

---

### Post by skaspud on 2007-07-14
som1 answer PLEASE...

---

### Post by ittiam on 2007-07-14
I can help you with beryl i guess.

For ATI cards Composite is by default disabled. look [https://wiki.ubuntu.com/AcceleratedX](https://wiki.ubuntu.com/AcceleratedX)

It says feisty has some problems with ATI video boards. An excerpt from that site

> 
As feisty development progresses (but before Beta Freeze is announced) a final decision will be made on whether Composite will effectivelly be disabled for ATI modern video boards (the ones which are only supported via the proprietary driver), or if this decision can be reversed. Please note that this decision will be made based on purely technical aspects, and specifically speaking, the level of functionality of the ATI proprietary driver. The current problems this driver has are:

    *

      No support, or limited support for Composite
    *

      Driver instability after suspend/resume cycle



If you want to proceed trying with it (I use beryl with intel graphics card so cant say how it works, maybe someone using ATI will see it and reply)  you can edit xorg.conf and enable composite by adding the following in that file

> 
Section "Extensions"
Option "Composite" "Enable"
EndSection

Since it appears you are using AIGLX you should go through this tutorial  [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_AIGLX)

---

