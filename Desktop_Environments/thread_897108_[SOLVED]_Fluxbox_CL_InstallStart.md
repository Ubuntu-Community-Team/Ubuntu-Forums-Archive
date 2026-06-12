---
title: "[SOLVED] Fluxbox CL Install/Start"
date: 2008-08-21
forum: Desktop Environments
---

### Post by DGortze380 on 2008-08-21
Ok, so desktops and window managers are not something I've spent too much time on in the year I've been learning linux.  I'm trying to install fluxbox on top of a command line install of Ubuntu 7.10.

I've installed (via apt-get) xorg and fluxbox.
ran startfluxbox and got a couple errors about not being able to connect to xserver.
tried apt-get install xserver, said I needed xserver-xorg-core, tried that, said it was up to date.
ran start x. got a blank blue desktop with nothing else.

How do I get fluxbox to startup via the command line? How can I set it up to boot directly into fluxbox (or, what kind of log in manager do I need?)

---

### Post by tuxxy on 2008-08-21
Isnt that what fluxbox would look like, a blank screen before you configure it, eg menus

---

### Post by DGortze380 on 2008-08-21
> **tuxxy said:**
> Isnt that what fluxbox would look like, a blank screen before you configure it, eg menus

as stupid as it sounds, i never considered that. you're probably right. wiki-ing fluxbox config now.

what about running ti at startup? any ideas? And for a graphical log-in?

EDIT: I can post a screen shot if it will help, but after reading a number of tutorials, I don't believe fluxbox is starting correctly. the command startfluxbox only produces "Error: Couldn't connect to XServer"

---

### Post by kerry_s on 2008-08-21
```
startx
```

from command, it go's like this:

sudo apt-get install xorg fluxbox menu
sudo update-menus
startx

---

### Post by DGortze380 on 2008-08-21
> **kerry_s said:**
> ```
startx
```

from command, it go's like this:

sudo apt-get install xorg fluxbox menu
sudo update-menus
startx

But when I run startx it brings me to a blank desktop, no options, no way to get to a terminal that I can figure out.

---

### Post by kerry_s on 2008-08-21
> **DGortze380 said:**
> But when I run startx it brings me to a blank desktop, no options, no way to get to a terminal that I can figure out.

did you install fluxbox before you installed xorg?

since your just starting anyways, try again but install in the exact order, xorg always has to be installed first.

also, why 7.10? you might as well go debian.
[http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso)

at package selection, uncheck everything, that will give you a base to build on.
log in as root:
apt-get install xorg fluxbox menu
exit

log in as your user:
startx

---

### Post by tuxxy on 2008-08-21
What ahppens when you right click on the blank desktop

---

### Post by DGortze380 on 2008-08-21
> **kerry_s said:**
> did you install fluxbox before you installed xorg?

since your just starting anyways, try again but install in the exact order, xorg always has to be installed first.

also, why 7.10? you might as well go debian.
[http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso)

at package selection, uncheck everything, that will give you a base to build on.
log in as root:
apt-get install xorg fluxbox menu
exit

log in as your user:
startx

Yup, xorg was installed first. 

7.10 because this is a dry run (in a VM) for what will end up being an install on a powerbook, 7.10 is a relatively stable distro on that architecture, then again so is debian, I'll consider it if I don't get Ubuntu running soon.

EDIT: just to clarify, I'm having trouble with fluxbox on a command line 7.10 **i386** virtual install. Practice for when I install the powerbook.

---

### Post by DGortze380 on 2008-08-21
> **tuxxy said:**
> What ahppens when you right click on the blank desktop

nothing, no menu. I can ctrl+alt+backspace to restart x and go back to the CL interface. but that appears to be it.

---

### Post by DGortze380 on 2008-08-21
works on debian... \\:D/

now I just need to play around with is and find a stable debian powerpc release

---

### Post by kerry_s on 2008-08-22
> **DGortze380 said:**
> works on debian... \\:D/

now I just need to play around with is and find a stable debian powerpc release

powerpc is the same as you just did with i386, here's the ppc iso:
[http://cdimage.debian.org/debian-cd/4.0_r4a/powerpc/iso-cd/debian-40r4a-powerpc-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r4a/powerpc/iso-cd/debian-40r4a-powerpc-businesscard.iso)

here's the xfce4 install for ppc:
[http://cdimage.debian.org/debian-cd/4.0_r4a/powerpc/iso-cd/debian-40r4a-powerpc-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r4a/powerpc/iso-cd/debian-40r4a-powerpc-xfce-CD-1.iso)

just in case

---

