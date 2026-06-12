---
title: "panel volume control icon disappears"
date: 2006-03-03
forum: Desktop Environments
---

### Post by jezjones on 2006-03-03
Hi Everyone,

I have been missing my volume control on the panel for a while now.
I am not sure exactly when it dissappeared but it was around the time i upgraded to Breezy from Hoary.

I have just found it, and found with it an odd issue which seems to be only happening on my desktop install of breezy (apt-get dist-upgrade), my laptop does not have the same problem (download full ISO and clean install)....

The issue is that the icon only shows up in the smokey-blue icon theme.
I have installed a few themes i have got from freshmeat, but i have not done anything more than select a main theme, window borders and icons from the dialog boxes in gnome.

I have the following icon themes installed;-

Amaranth
Crux
Crystal SVG
Flat-blue
Gnome
Gorilla
Human
iKons
KDE-Classic
KDE-LoColor
Kids
Lush
Nuvola
Sandy
Slick Icons
Smokey-Blue
Smokey-Red
SphereCrystal
Wasp

It seems like when an icon theme does not have the icon for the volume control it will dissappear, when you switch back to one that has the icon it does not always pick up the missing icon.

So i don't have a problem now, but i thought i would put it up here to see if this is a common thing, something i might have done or even a minor gnome bug.

---

### Post by Mustard on 2006-03-14
I have to say I am glad you posted this, because I've been quite perplexed over this exact issue for an hour now. :)

The thing is though, I changed to crux theme, then changed back to my custom theme, and now it seems every theme I choose the volume icon is not visible.

---

### Post by Mustard on 2006-03-14
Ok after a bit of hunting around on Launchpad.net, I've found the discussion of this bug..

[https://launchpad.net/distros/ubuntu/+source/gnome-applets/+bug/23644](https://launchpad.net/distros/ubuntu/+source/gnome-applets/+bug/23644)

Unfortunately when I went to the link to the upstream information on this bug I got an error at [http://bugzilla.gnome.org/](http://bugzilla.gnome.org/) that didn't allow me to view the page.

---

