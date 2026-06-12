---
title: "Upgrade to Karmic 9.10 from Jaunty 9.04: Display Problems"
date: 2009-10-31
forum: Desktop Environments
---

### Post by vince.lupe on 2009-10-31
Hi, everyone,

I have just updated from Jaunty to Karmic. When I used Jaunty, the display would be perfectly fine, but - after upgrading to Karmic - I have no display at all, just weird blue, black, pink, yellow, orange - etc. colors - lines all over the screen. I can't see the panels, the menus, windows - I can't see the desktop at all. I can see everything fine up until after I log in to my username. Does anyone know the problem? I have an old Gateway 400SD (I think that's what it's called). I am currently logged into terminal via Ctrl + Alt +F1. Thank you for your kind help!

God bless,
Vince Lupe

---

### Post by gnu-buntu on 2009-11-01
> **vince.lupe said:**
> Hi, everyone,

I have just updated from Jaunty to Karmic. When I used Jaunty, the display would be perfectly fine, but - after upgrading to Karmic - I have no display at all, just weird blue, black, pink, yellow, orange - etc. colors - lines all over the screen. I can't see the panels, the menus, windows - I can't see the desktop at all. I can see everything fine up until after I log in to my username. Does anyone know the problem? I have an old Gateway 400SD (I think that's what it's called). I am currently logged into terminal via Ctrl + Alt +F1. Thank you for your kind help!

God bless,
Vince Lupe

I did the upgrade, too, and I have the same/similar problem, except that the screen usually goes blank after login.  

I logged a bug at [https://bugs.launchpad.net/bugs/465965](https://bugs.launchpad.net/bugs/465965).  You might want to monitor that, since others (and I) will be trying to solve the problem.  Also, some .xsession-errors files are attached to the bug report.  No doubt those files have strong clues, but I'm a desktop newbie, so I cannot easily decipher the files.

As a workaround, I made a 'live CD'.  If you decide to do that, you might want to download from a mirror outside the USA, as the servers there are bogged down due to recent release flurry.  I used Finland as the mirror source and got a fast download.
I'll try the Ctrl + Alt +F1 method you cite, to see if it works for me.  

If, meanwhile, you find a solution, please do post it.
Thanks, and I wish us both good luck in fixing this.

Cheers,
~Peter

---

### Post by vince.lupe on 2009-11-01
> **gnu-buntu said:**
> I did the upgrade, too, and I have the same/similar problem, except that the screen usually goes blank after login.  

I logged a bug at [https://bugs.launchpad.net/bugs/465965](https://bugs.launchpad.net/bugs/465965).  You might want to monitor that, since others (and I) will be trying to solve the problem.  Also, some .xsession-errors files are attached to the bug report.  No doubt those files have strong clues, but I'm a desktop newbie, so I cannot easily decipher the files.

As a workaround, I made a 'live CD'.  If you decide to do that, you might want to download from a mirror outside the USA, as the servers there are bogged down due to recent release flurry.  I used Finland as the mirror source and got a fast download.
I'll try the Ctrl + Alt +F1 method you cite, to see if it works for me.  

If, meanwhile, you find a solution, please do post it.
Thanks, and I wish us both good luck in fixing this.

Cheers,
~Peter

Peter,

Thank you, my friend. I'll try to install from a LiveCD and see if that changes anything - because, I upgraded to the Alpha 2 Beta before and it worked fine. I don't think it is a hardware problem for either of us. Have you tried to do a fresh install of 9.10? I wonder if that might work? I'm going to try it if I can. If you have things saved on your old Linux distribution (assuming that you have an old Linux distribution), I wonder if you can downgrade to 9.04? I'll let you know how the LiveCD install works, and I'll keep up on your bug report. Thanks again, my friend.

God bless,
Vince Lupe

---

