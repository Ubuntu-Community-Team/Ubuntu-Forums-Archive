---
title: "[SOLVED] Debian business iso install"
date: 2008-06-07
forum: Debian
---

### Post by Inxsible on 2008-06-07
I am trying to install the debian base on which I want fluxbox. But when I try to install debian from the us mirror, after the partitioner, it gives me this warning```
[!!]Install the base system
Debootstrap warning
Warning:
http://ftp.us.debian.org/debian/dists/lenny/main/binary-1386/Packages.gz was corrupt
``` I have two options ```
GoBack Continue
```Is it safe to continue?

---

### Post by kerry_s on 2008-06-07
no, go back and pick a different mirror.

---

### Post by Inxsible on 2008-06-07
> **kerry_s said:**
> no, go back and pick a different mirror.Alrite going back ..gave me 4 or 5 additional errors/warnings and i kept going back until one said "failed to install base system. please select installation of base system from the menu" which I did...now its retrieving packages -- but stuck at 0%.

It never gave me the choice to select a different mirror ....

---

### Post by Inxsible on 2008-06-07
ok. looks like it did eventually retrieve and install packages. Now I am at the Software selection "page", I deselected Desktop Environment because I plan to install fluxbox.

Its a laptop,so should I install the Laptop collection? Its always going to be on AC power - since the battery holds only 15% max. Also I plan to keep the computer on 24/7 apart from occasional shutdowns. Do I still need the Laptop collection?

and finally there is a 'Standard system' collection? What does that install? 

I actually want a clean slate...on which I will build my own system with fluxbox and the apps that I like.

Let me know....

Thanks

---

### Post by CREEPING DEATH on 2008-06-08
> **Inxsible said:**
> ok. looks like it did eventually retrieve and install packages. Now I am at the Software selection "page", I deselected Desktop Environment because I plan to install fluxbox.
Selecting "Desktop" will, by default, install Gnome.

> **Inxsible said:**
> Its a laptop,so should I install the Laptop collection? Its always going to be on AC power - since the battery holds only 15% max. Also I plan to keep the computer on 24/7 apart from occasional shutdowns. Do I still need the Laptop collection?
Yes!  It controls software-related power and cooling functions.
> **Inxsible said:**
> and finally there is a 'Standard system' collection? What does that install? 

I actually want a clean slate...on which I will build my own system with fluxbox and the apps that I like.

Let me know....

Thanks

Just check 'laptop' and 'standard system', finish the install, then install Xorg, fluxbox, and synaptic.

CD

---

### Post by Inxsible on 2008-06-08
Thanks CD.

Installed only the Laptop package. Still got some crap like xeyes and such..which I really have no use for (can't see who does)..Tried to remove it by ```
aptitude purge xeyes
``` it says no candidate found, but when I do a ```
which xeyes
``` it does give me the /usr/bin/xeyes path.

Well...its not really hurting me ..so I let it be.

---

