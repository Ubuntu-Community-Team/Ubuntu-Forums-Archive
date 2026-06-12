---
title: "Advanced Mouse Features support in Ubuntu"
date: 2006-01-24
forum: Desktop Environments
---

### Post by DigitalDuality on 2006-01-24
Just out of curiosity's sake, i plugged up my Mighty Mouse to my PC with Ubuntu 5.10 installed and as i expected, the mouse works.. but..

The left and right buttons don't, and my scroll ball (not wheel) that should scroll left and right, along with up and down, does not work.

So i'm curious about 2 things, 

#1.  Is there already a known way to get this to work?

#2.  If i were to get another mouse... say a more advantaged Logitech 6 button mouse.. would that be configurable in anyway?

---

### Post by dcstar on 2006-01-24
[QUOTE=DigitalDuality]Just out of curiosity's sake, i plugged up my Mighty Mouse to my PC with Ubuntu 5.10 installed and as i expected, the mouse works.. but..

The left and right buttons don't, and my scroll ball (not wheel) that should scroll left and right, along with up and down, does not work.

So i'm curious about 2 things,

#1.  Is there already a known way to get this to work?

#2.  If i were to get another mouse... say a more advantaged Logitech 6 button mouse.. would that be configurable in anyway?[/QUOTE]
Do a forum search for "5 button" or "9 button" mouse and you should find the HOWTO (somewhere).

---

### Post by ahave2005 on 2006-01-25
Have a look at this thread: [http://www.ubuntuforums.org/showthread.php?t=65471](http://www.ubuntuforums.org/showthread.php?t=65471)

I got all my mouse buttons working and the multimedia keys on my keyboard, using xbindkeys and an altered org.conf.

Try to check out: [http://hocwp.free.fr/xbindkeys/xbindkeys.html](http://hocwp.free.fr/xbindkeys/xbindkeys.html)

As with everything else in Linux, it takes time. But in this case not too long.

Open a console and type>  xev if it's not installed, use synaptic to install it. Move your mouse cursor over the window, and press the buttons. If it gives a readout, you can make it work using xbindkeys and xbindkeys website.

/ahave

---

