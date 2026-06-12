---
title: "Switching boot screen logo/art?"
date: 2006-09-13
forum: Desktop Environments
---

### Post by danielandrews on 2006-09-13
I, being a convert from the KDE world, thought I'd give Kubuntu a try - and I was going to install the ubuntu/gnome desktop too and check that out.  Now that I'm hooked on gnome, I want to a) remove KDe and b) replace the kubuntu boot screen with the ubuntu one.

I've already managed to remove the KDE packages, but the kubuntu boot screen remains.  Any quick way to swap that out?

---

### Post by Rmorris84 on 2006-09-13
D to the I to the T to the T to the O. What does that spell, DITTO!

Did the same thing... just kinda been dealing with it.

---

### Post by CatKiller on 2006-09-14
> **danielandrews said:**
> I've already managed to remove the KDE packages, but the kubuntu boot screen remains.  Any quick way to swap that out?

If you mean the first branded screen, while the computer is booting, but before GDM gives you the graphical login, then this 

[https://help.ubuntu.com/community/USplashCustomizationHowto]("https://help.ubuntu.com/community/USplashCustomizationHowto")

is probably what you want to look at. You may need to get the ubuntu-artwork package to get the /usr/share/pixmaps/grub/ubuntu-artwork.xpm.gz file that I **think** forms the basis of the default Ubuntu boot screen. I'm not exactly sure how you'd go from the .xpm.gz file to a working usplash, since I've only done this once, and I was following that HOWTO closely.

Perhaps the Ubuntu artwork forum will have some information that might help you. Or, if your mojo is better than mine, you could have a look at the install scripts to work out how it's done on initial install and emulate that.

It seems that the splash screen method may well change for the next version of Ubuntu, so you might just need to wait till you upgrade to Edgy, and then it'll be sorted out for you ;)

---

### Post by danielandrews on 2006-09-14
Thanks for the tip(s).  Yea, it's not a pressing matter ... I mean I reboot close to never, obviously.  It's just one of those nagging things I'd like to get sorted out if possible.  I'll take a look at the link you provided and see if I can make any progress.

Thanks again!

---

