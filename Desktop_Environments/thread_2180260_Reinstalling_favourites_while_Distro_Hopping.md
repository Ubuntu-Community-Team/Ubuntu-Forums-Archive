---
title: "Reinstalling favourites while Distro Hopping"
date: 2013-10-12
forum: Desktop Environments
---

### Post by b1ackcr0w on 2013-10-12
I quite frequently hop between a bunch of Debian based variants. For example, I'm on Mint 15 today, but I'm pretty sure I'll want to give 13.10 a go on or soon after realease, but soon after I'll be tempted by Mint 16, then I might have a go with #! and so on. I'm pretty happy to stay with 64bit. 

However, I also like to use a fair bit of software that's not in the standard build, and needs re-installing. And I also use a fair amount of software not in the repos (for instance Chrome Browser, Spideroak, Multisystem, Steam. This can rather suck the joy out of distro hopping. 

I am considering writing a shell script to do this, or maybe even a little python project. Before I do, I wonder if i'm reinventing the wheel and there's already a tool for this very purpose.

Has anybody got any suggestions?

---

### Post by newb85 on 2013-10-12
Such a shell script should be trivial, provided you're sticking with systems that use sudo and apt package management.

---

### Post by buzzingrobot on 2013-10-12
Stash deb's and other installation packages on Ubuntu One or Dropbox or someplace similar. When you install a new dsitribution, grab those files and install them Whether or not you need a shell script to do that depends, I suspect.

I use Dropbox for that purpose:  Fonts, background images, deb's I've built, exported bookmarks, etc.  I install and run Dropbox right after an install completes. I go make some coffee while it synchs the files. When I come back, I install the deb's, install the fonts, etc., and I'm done.

---

