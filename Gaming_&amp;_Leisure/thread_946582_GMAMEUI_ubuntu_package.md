---
title: "GMAMEUI ubuntu package"
date: 2008-10-13
forum: Gaming &amp; Leisure
---

### Post by megamaced on 2008-10-13
I couldn't find a ubuntu package for GMAMEUI so I created one myself.

Find it here: (version 0.2.6)
[http://www.zshare.net/download/20527216db566c2a/](http://www.zshare.net/download/20527216db566c2a/)

---

### Post by BigSilly on 2008-10-13
Hey that's bloody excellent and very cool of you! Thank you very much! :biggrin:

---

### Post by disturbedite on 2008-10-13
[FONT=Verdana]i'd also recommend checking out MAMEP GUI:
[http://www.mameworld.info/ubbthreads/showflat.php?Cat=&Number=158710&view=collapsed](http://www.mameworld.info/ubbthreads/showflat.php?Cat=&Number=158710&view=collapsed)
[/FONT]

---

### Post by megamaced on 2008-10-14
whoops, I forgot to add xmame-x | xmame-sdl as a dependency ](*,)

new package uploaded!

---

### Post by megamaced on 2008-10-14
hmmm, seems you have to manually set the mame executable path...

For those that don't know, the mame path is /usr/games/xmame.SDL

On another note, I can't seem to get my joypad to work. It worked fine with KXMame. It seems that under Default Options, the location for the joypad should be /dev/joy but that doesn't make any sense. I have created a simlink for dev/joy but still can't use my controller.

---

### Post by Prefix100 on 2008-10-14
What is this?

Could I get a description of the package, and what it does?

---

### Post by SunnyRabbiera on 2008-10-14
> **Prefix100 said:**
> What is this?

Could I get a description of the package, and what it does?

This is the GTK frontend to MAME: Multiple Arcade Machine Emulation

---

### Post by megamaced on 2008-10-14
BUG: this package won't install if you have gnome-lirc-properties installed

---

### Post by dphirschler on 2009-05-05
Anyone care to build a deb for 9.04?


Darryl

---

### Post by Grishka on 2009-05-05
> **dphirschler said:**
> Anyone care to build a deb for 9.04?


Darryl

[I do](https://launchpad.net/~thir/+archive/ppa).

---

### Post by binbash on 2009-05-05
> **Grishka said:**
> [I do](https://launchpad.net/~thir/+archive/ppa).

Thanks for the package

---

### Post by smeagol25 on 2009-05-18
Anyone care to build a .deb package for intrepid.  Tried building the latest version from the official site but ./configure is stuck at Cannot find libexpat.  Thanks

Nevermind found the solution to the problem, need to install apt-get install libexpat1-dev.

---

