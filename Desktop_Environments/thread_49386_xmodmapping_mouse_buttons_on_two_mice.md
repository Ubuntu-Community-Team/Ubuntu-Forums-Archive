---
title: "xmodmapping mouse buttons on two mice"
date: 2005-07-16
forum: Desktop Environments
---

### Post by One Quick Question on 2005-07-16
(I guess I'll ask my quesiton on these forum... None of the other forums fit... and I do enjoy Kubuntu.)

After lots of Googling, I found this page which is exactly my problem: [http://lists.freebsd.org/pipermail/freebsd-questions/2005-March/082724.html](http://lists.freebsd.org/pipermail/freebsd-questions/2005-March/082724.html)

Essentially I need to remap my Send Core Events mouse buttons, but apparently xmodmap only remaps the Core Pointer mouse.

(And I can't change which mouse is Core for reasons that aren't important or very interesting)

Anyone know a solution or alterative?

---

### Post by One Quick Question on 2005-07-16
Ah. I think I've figured out a solution.   I suppose I should post it in case anyone else has the same trouble.

xsetpointer changes which is the Core Pointer, so I've added this to my xinitrc script:
```
xsetpointer "*[Secondary mouse]*"
xmodmap -e "pointer = 1 2 3 8 9 10 11 12 6 7 4 5"   
xsetpointer "*[Primary mouse]*"
```
and the remapping to the secondary mouse is remembered fine.

Hurrah.

---

### Post by fatespeaks on 2008-02-29
I've tried adding similar commands to xinitrc on Ubuntu 7.10 and it doesn't seem to work.

I have been running this command manually after each login:
```
xinput set-button-map kensington-isa0060/serio1/input0 3 6 1 7 2
```

And this set of commands seems to work as well:
```
xsetpointer "kensington-isa0060/serio1/input0"
xmodmap -e "pointer = 3 6 1 7 2"
xsetpointer "HP USB Mouse-usb-0000:00:1d.1-2/input0"
```

But this script in /etc/X11/xinit/xinitrc doesn't seem to do the trick:
```
#!/bin/sh
# $Xorg: xinitrc.cpp,v 1.3 2000/08/17 19:54:30 cpqbld Exp $

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)
. /usr/bin/xsetpointer "kensington-isa0060/serio1/input0"
. /usr/bin/xmodmap -e "pointer = 3 6 1 7 2"
. /usr/bin/xsetpointer "HP USB Mouse-usb-0000:00:1d.1-2/input0"

# invoke global X session script
. /etc/X11/Xsession
```

I tried other variations of this script and even tried modifying other files in the startup process though at this point I don't really remember what I have tried.

Any other suggestions on how to remap buttons on 1 of my 2 mice at startup?

Cheers,
Aaron Ahlemeyer

---

