---
title: "Burning Crusade Problem"
date: 2007-04-19
forum: Gaming &amp; Leisure
---

### Post by ohmycar on 2007-04-19
Hey everyone, I am having a problem with my world of warcraft: the burning crusade install.

I am running ubuntu 6.10 and i just installed the lastest wine.
I put in the cd's and installed regular wow, then i put in the cd's to install burning crusade.

After I finished installing the game , I run it and it starts off into the opening cinematic.
After the cinematic is done, it goes back to my desktop and nothing happens.

Can anyone figure out why It does not start the actual game?

Laptop Specs:

CPU: Intel Centrino Duo
GPU: Intel GMA950
1gb RAM
80gb HD

thanks.

- ash

---

### Post by ohmycar on 2007-04-20
Anyone know? I have searched and edited the files for it to run in opengl and everything and it still does not come up after the cinematic. :(

---

### Post by rudeboyskunk on 2007-04-20
Try using cedega instead of wine.  Best $5/month you'll ever spend.  [http://www.transgaming.com](http://www.transgaming.com)

---

### Post by hikaricore on 2007-04-20
> **rudeboyskunk said:**
> Try using cedega instead of wine.  Best $5/month you'll ever spend.  [http://www.transgaming.com](http://www.transgaming.com)

Or the user having problems could give more detail about their setup, error codes from terminal, and other useful information instead
of you trying to pass them off to transgaming where they'll have the same problems and be paying for it.

ohmycar: check to see if your video drivers are working properly with direct rendering


```
glxinfo | grep rendering
```

Sometimes those intel chipsets can be tricky, while they can pull off running games like WoW,
the linux drivers (which were developed by intel and linux community effort) fall short in some
cases.  Many users can sucessfully run with with a few tweaks and lower graphic
settings/resolution under linux using intel chipsets, there are just alot of variables to come into
play on this issue.

Have you looked through the community howto on WoW yet?

[http://help.ubuntu.com/community/WorldofWarcraf](http://help.ubuntu.com/community/WorldofWarcraf)

---

### Post by max.diems on 2007-04-20
Does the WINE page say it supports WoW? If so, does it support burning crusade? If the answer to either of these is "no", there's your problem.

---

### Post by hikaricore on 2007-04-20
It supports both.. where have you been?

[http://appdb.winehq.org/appview.php?iVersionId=6482](http://appdb.winehq.org/appview.php?iVersionId=6482)

---

### Post by ohmycar on 2007-04-20
it says:

ashgx@ashgx-laptop:~$ glxinfo | grep rendering
libGL warning: 3D driver claims to not support visual 0x5b
direct rendering: Yes


so i guess it does have direct rendering.
I am going to look through how-to's and other such things to figure this out.
I know it works with WINE because my friend had it running on his laptop with wine smoothly.

---

