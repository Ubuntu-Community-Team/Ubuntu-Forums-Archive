---
title: "screen rotation with xrandr does not work"
date: 2007-07-30
forum: Desktop Effects &amp; Customization
---

### Post by royalCS on 2007-07-30
hi everybody,
I would like to rotate my screen because i have got a tablet pc. The problem is that every windowmanager (beryl, standard feisty compiz, compiz5) except metacity does not react after the rotation.
To rotate the screen I use "xrandr -o right", the rotation works, but then the display stays unchanged.
(the system is still working. I can rotate back in normal mode and if I change the desktop the cube rotation animation works, too. but no normal action like open something is displayed until I change the desktop and them change it back. than the "normal action" I dit is done.)

So, are there other ways to rotate the screen? Or something else I can try?

I have got a HP tc4400 with Intel GMA 950 graphics and feisty fawn with compiz 5 working now.

thanks for every hint. royalCS

---

### Post by w4ett on 2007-07-31
I've not really played with the rotation toggles of xrandr, but here is a debian tutorial on the command usage:

[http://www.debian-administration.org/articles/201](http://www.debian-administration.org/articles/201)

>  xrandr -help
usage: xrandr [options]
  where options are:
  -display  or -d 
  -help
  -o 
            or --orientation 
  -q        or --query
  -s /x or --size /x
  -r  or --rate 
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen 
  --verbose

---

### Post by StephenG.Jones on 2007-10-09
same thing, almost: I can "xrandr -o 2" then "xrandr -q" and my orientation shows "left," but nothing's much changed, even when I ctrl-alt-bcksp to restart X Windows or whatever that is (I'm new to all this).  on a HP Slimline s7712n with the 945gm card. and yeah, that laptop card's my problem -- took forever to get the screen to rotate in Vista (I'm dual-booting for now) -- but want to find a way to work around it too, to work with my Samsung 970p Syncmaster monitor. I've really gotten used to a tall rather than a wide screen, I mean.

---

