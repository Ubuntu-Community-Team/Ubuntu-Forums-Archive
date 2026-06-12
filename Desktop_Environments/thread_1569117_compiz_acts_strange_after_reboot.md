---
title: "compiz acts strange after reboot"
date: 2010-09-06
forum: Desktop Environments
---

### Post by fbicknel on 2010-09-06
Not even sure how to describe it.  

Pretty sure it's Compiz, as when it's acting up if I try something simple like switch workspace, things lock up.  A gdm restart can recover from that condition.

So after a reboot, log in and start something benign like Firefox (doesn't matter what you start).  The window will 'paint' from the bottom up over a period of a few hundred milliseconds.  A significant fraction of a second, though.  All window operations have this delay.  A small window near the top of the screen exhibits a delay as if the entire screen below it had to 'repaint' before it can be displayed.

If you then lock the screen and return to the same session, everything seems to work as normal.  Alternatively, you can log in as another user... same effect there... return to session 1 and everything is normal.  Return to session 2 and everything is normal.  

It seems that returning to gdm's login screen and back fixes it.

So just when you log in for the first time, this annoying paint issue appears.

As mentioned, if you try to use any sort of compiz effect, that session is frozen.

Usually, things are ok - even if you log out and back in - until the next reboot.

When this first started happening, I would log out/back in and the effect would sometimes fix itself.  But not always.  The key difference between that and the 100% fix above is that you don't log out above.  The session remains logged in.  Also, I tried switching to a console and restarting gdm.  That also works sometimes, but not always.  I would also try starting Nvidia X Server Settings tool before logging out and it seemed like that increased the chances of success.  But I'm not sure it did.  It does seem that once it's fixed, it stays fixed until the next reboot.

Sorry for the lengthy post, but I warned you I wasn't sure how to describe it.  :)

Some general things about my system; more gladly on request:

- AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
- 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux
- 00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2)
 
Package: compiz-gnome
State: installed
Automatically installed: no
Version: 1:0.8.4-0ubuntu15

---

### Post by ajgreeny on 2010-09-06
Install **compizconfig-settings-manager** if you don't already have it and remove the selection mark against "Animations" for a start.

You can play around enabling/disabling the various plugins and see if you have any luck.  Does the problem go away if you do not run compiz?  It would be worth trying that for a day or two, just to see if there is any difference.

---

### Post by fbicknel on 2011-05-13
This turned out to be the GeForce processor.  11.04 arrived and the new graphic interface is blacklisted.  It doesn't work under 11.04 with this chip for me.

By extension, that's got to be what's causing the Compiz problems for me under 10.10.

Gotta get a new video card.  :)

---

