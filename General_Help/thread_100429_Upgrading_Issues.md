---
title: "Upgrading Issues"
date: 2005-12-07
forum: General Help
---

### Post by mcescher on 2005-12-07
Just a quick question.

I just got done installing the previous version of Ubuntu and haven't even begun the process of customizing it at all (the look and feel / packages and whatnot).

Do you guys feel it would be easier/less time consuming to follow the upgrade directions or should i just download a copy of the newest version of Ubuntu and do a clean install over the previous version?

---

### Post by endersshadow on 2005-12-07
Clean version?  Just easiest to do a sudo apt-get dist-upgrade, but make sure that you change your sources.list file to say breezy instead of hoary (or warty, if that's what you have).

Here's a detailed way:
```
sudo gedit /etc/apt/sources.list
```

Change all instances of either hoary or warty (depending on your install) to breezy, then save it and close it.  Again in the terminal:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

You should be all set!

---

### Post by aysiu on 2005-12-07
With a broadband connection, a *sudo apt-get dist-upgrade* will probably take about forty minutes.

With a broadband connection, downloading the entire ISO of Breezy takes a few hours.

It's really your call.

What I would do? Start the ISO download before going to bed. Then, it's ready to go in the morning. Just do a clean install. Having the CD of the newest version is handy in case you ever have to reinstall or want to use the CD to install on another computer.

---

### Post by mcescher on 2005-12-07
Well I did download the latest .iso of Breezy and to save the hassle and risk of messing something up or having conflicts....I think I'll just re-install. I really haven't invested too much time in Hoary as it is so I would have to customize it as well.

I have a copy of hoary on DVD and it seems like it installs alot more by default than a standard CD copy. Can you guys point me to a link for the DVD download of Breezy or does that exist?

Can you guys point me to a walk-through of adding all important repositories to my set-up under breezy? Or is it just as easy as finding the old "How-To" under Hoary and just changing the names to Breezy?

Thanks for the fast replies!

---

### Post by aysiu on 2005-12-07
[QUOTE=mcescher]
Can you guys point me to a walk-through of adding all important repositories to my set-up under breezy? Or is it just as easy as finding the old "How-To" under Hoary and just changing the names to Breezy?[/QUOTE] See the first link of my sig.

---

### Post by mcescher on 2005-12-07
Nice!

Thanks for the How-To.

---

