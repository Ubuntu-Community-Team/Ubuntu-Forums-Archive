---
title: "Why removing AbiWord removes xubuntu-desktop too?"
date: 2006-08-15
forum: Desktop Environments
---

### Post by xp_newbie on 2006-08-15
I am using XFCE, not Gnome.

While searching for a convenient way to switch between keyboard layouts, I installed kkbswitch, using Synaptic. It then installed the entire world and its wife (AbiWord, lots of KDE libraries, etc.)

I then discovered that I can simply install xfce-xkb-plugin to switch keyboard layouts "the XFCE way".

Since I don't like unnecessary packages installed on my hard drive, I decided to uninstall KKBSwitch and AbiWord.

Well... KKBSwitch uninstalled without any problems and without uninstalling any other dependencies. However, marking AbiWord for removal marks xubuntu-desktop for removal as well. :???: 

Why?

Why should removing AbiWord necessitate the removal of the xubuntu-desktop as well?

And how do I go ahead with my plan to remove AbiWord, without removing the xubuntu-desktop?

Thanks!
Alex

---

### Post by reacocard on 2006-08-15
xubuntu-desktop is a metapackage. its only there to simplify installing xfce. it can be safely removed without affecting your system.

---

### Post by meng on 2006-08-15
xubuntu-desktop is a metapackage, with abiword as a dependency. You will not lose anything else by agreeing to uninstall xubuntu-desktop.

The metapackage provides a simple way to install XFCE plus a bunch of apps. Think of it as a box containing several components. You don't really need the box, just the components. Unfortunately, when you want to throw out a single component, you have to throw out the box, and that's where my analogy falls to pieces.

---

### Post by EnderTheThird on 2006-08-15
> **meng said:**
> Unfortunately, when you want to throw out a single component, you have to throw out the box, and that's where my analogy falls to pieces.

Haha, I really enjoyed that.  :)  But yeah, don't worry if, when uninstalling something, it also uninstalls ubuntu-desktop, kubuntu-desktop, and/or xubuntu-desktop.  It won't affect anything.

---

### Post by aysiu on 2006-08-15
Here's another analogy.

Let's say you have a six-pack of beer, and it has a big label on it called "six-pack of beer." Well, once you take one of those beer cans away... it's no longer a six-pack.

Well, when you take one of the default components away, it's no longer the default *xubuntu-desktop*.

---

### Post by meng on 2006-08-15
> **aysiu said:**
> Here's another analogy.

Let's say you have a six-pack of beer, and it has a big label on it called "six-pack of beer." Well, once you take one of those beer cans away... it's no longer a six-pack.

Well, when you take one of the default components away, it's no longer the default *xubuntu-desktop*.

What you ought to have said was, "Here's a better analogy." :razz:

---

### Post by dmacdonald95 on 2006-08-15
Here's an even better one:

Let's say you've bought several items from a store. They came in a single bag. If you want to return any of the items, you also need to return the bag.

(Not really, but hey. I always bring back the origianl bag.)

---

### Post by CarVac on 2007-06-03
This is a similar problem to what I'm having on Gnome. The .odt filetype automatically opens with AbiWord, which was installed when I added the xubuntu-desktop package. However, I want to use OpenOffice Writer for its own type. I tried to uninstall AbiWord, but with it goes the packages 'gnome' and 'gnome-office'. I definitely do want Gnome but can't get rid of AbiWord.

---

### Post by reacocard on 2007-06-03
> **CarVac said:**
> This is a similar problem to what I'm having on Gnome. The .odt filetype automatically opens with AbiWord, which was installed when I added the xubuntu-desktop package. However, I want to use OpenOffice Writer for its own type. I tried to uninstall AbiWord, but with it goes the packages 'gnome' and 'gnome-office'. I definitely do want Gnome but can't get rid of AbiWord.

Right-click an odt, go to properties, open with, and select 'OpenOffice Writer'

---

### Post by thesoothsayer on 2007-06-09
After removing xubuntu-desktop, the next time I run aptitude it asks to remove all the xfce packages linked to xubuntu-desktop. Anyway to get around this?

---

### Post by Virgilius on 2007-07-08
Well, I'm having the same problem and wanting to install a nwer version of Abiword, but through Synaptic and Mark For Removal, this comes up:

To be removed
GNOME
GNOME-Office
and says the same for Complete Removal. So what am I to do? :(

---

### Post by reacocard on 2007-07-08
> **Virgilius said:**
> Well, I'm having the same problem and wanting to install a nwer version of Abiword, but through Synaptic and Mark For Removal, this comes up:

To be removed
GNOME
GNOME-Office
and says the same for Complete Removal. So what am I to do? :(

those are just metapackages, ignore it. None of your software aside from Abiword will be removed.

---

### Post by Virgilius on 2007-07-09
I've tried doing it on Complete Removal and it worked like a charm, thanks heaps reacocard! :D

---

