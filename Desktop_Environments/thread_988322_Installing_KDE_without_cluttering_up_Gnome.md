---
title: "Installing KDE without cluttering up Gnome"
date: 2008-11-20
forum: Desktop Environments
---

### Post by joey-elijah on 2008-11-20
Is there a simple method to install KDE without having Gnome's menus populated with Kthis and Kthat? 

(Yeh i could always uncheck them from mainmenu, but just wondering if there's a simpler installation.)

---

### Post by snova on 2008-11-20
Install the kde-core package instead of kde or kubuntu-desktop.

I also suggest this because kde somehow depends on a MySQL server and kubuntu-desktop depends on Kubuntu branding, which I don't like over brown Ubuntu.

---

### Post by simtaalo on 2008-11-20
> **snova said:**
> Install the kde-core package instead of kde or kubuntu-desktop.

I also suggest this because kde somehow depends on a MySQL server and kubuntu-desktop depends on Kubuntu branding, which I don't like over brown Ubuntu.

will this give you the option to boot into either gnome or kde on startup?

---

### Post by snova on 2008-11-20
Yes. There's a menu to choose what DE you want to use when you login.

Remember the default is whichever one you used previously.

---

### Post by olejorgen on 2008-11-20
> Install the kde-core package instead of kde or kubuntu-desktop.
That's probably a good idea, but doesn't solve the problem?

Back when I was using kde/gnome I was wondering the same myself but couldn't find a solution.

---

### Post by SuperSonic4 on 2008-11-20
Yeah, you can dual boot ubuntu and kubuntu. This would be the cleanest way but there'd be no app interaction

---

### Post by snova on 2008-11-20
> **olejorgen said:**
> That's probably a good idea, but doesn't solve the problem?

Back when I was using kde/gnome I was wondering the same myself but couldn't find a solution.

*Is* there a problem? I'm confused. This package depends on a minimal installation of KDE, including Plasma and everything else needed to use it, and hopefully not much else. This is what the OP wanted, and answers his request as far as I can tell.

'kde' depends on several other metapackages that eventually install all the Kthis and Kthat the OP didn't want. kubuntu-desktop depends on even more.

Dual-booting two installations of Ubuntu is be pretty pointless from my point of view, since most of it would be precisely the same. The *only* difference between Ubuntu and Kubuntu is the default set of packages installed. By removing some and adding others, it is possible to go from one to the other.

---

### Post by olejorgen on 2008-11-20
The problem as I see it is that we don't want eg. koffice entries in the menu when we're using gnome. Installing a minimal set of packages is better than notthing, but doesn't solve the problem

---

### Post by snova on 2008-11-20
I must have misunderstood the original question. I thought he was trying to get a minimal KDE install, not separate the menus.

If you're trying to keep KDE programs only on the KDE menus, I don't know what to do. The Gnome and KDE menus are syncronized, although I think you can edit one without changing the other.

Oops.

---

### Post by kdw on 2008-11-20
> **joey-elijah said:**
> Is there a simple method to install KDE without having Gnome's menus populated with Kthis and Kthat? 

(Yeh i could always uncheck them from mainmenu, but just wondering if there's a simpler installation.)
Depends on your definition of "simple method"  :-)  To clean up after installing KDE, here's a link to a tutorial with a script "menu-cleaner.sh". 

[http://ubuntu-tutorials.com/2007/07/18/removing-kde-icons-in-gnome-remove-gnome-icons-in-kde/](http://ubuntu-tutorials.com/2007/07/18/removing-kde-icons-in-gnome-remove-gnome-icons-in-kde/)

Ran fine on 8.0.4.  Haven't tried it on 8.10 yet.

---

### Post by olejorgen on 2008-11-20
Not very nice, but good enough I guess. Thanks

---

