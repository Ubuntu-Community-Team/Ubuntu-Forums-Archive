---
title: "Difference between Gdesklets &amp; Adesklets"
date: 2005-11-24
forum: Desktop Environments
---

### Post by AthlonMDK on 2005-11-24
Hi

I was looking for a desklet application. I found 2:
- Gdesklets ([http://gdesklets.gnomedesktop.org](http://gdesklets.gnomedesktop.org))
- Adesklets ([http://adesklets.sourceforge.net/](http://adesklets.sourceforge.net/))

I have tried Gdesklets and was wondering what the difference is between them.
I looked on google and on the sites but found them (imho) identical.

so what is the difference?:confused:

---

### Post by andlinux21 on 2005-11-24
There doesn't appear to be much of a difference although i am sure there has to be i visited both sites and looked at the screenshots. I hope someone can provide some insite into this....:rolleyes:

---

### Post by Xian on 2005-11-24
Gdesklets has heavy requirements in terms of library dependencies. In fact, gDesklets still requires a fair part of the GNOME environment to be installed, plus specialized libraries such as gnome-python. Adesklets has very limited library dependencies. It uses the Imlib2 library for all graphic-related operations. No window toolkit used whatsoever; the program relies directly on xlib. 

Adesklets uses minimal disk space, memory footprint and CPU usage. Typically, on glibc 2.3.4 Linux 2.6 x86, a unique executable is less than 130 KB on disk, takes less than 3 MB of virtual memory per desklet right after initialization, and almost no processor cycles (including cycles from a Python interpreted script) when idle.

Gdesklets is generally easier to run for a new user since it employs a desklet manager with a nice GUI that can also be used to install and sort the desklets which are installed. Also, most of the desklets have configuration GUI's. The same can not be said for Adesklets, and naturally many consider this to be an attribute.

---

### Post by oskude on 2005-11-24
well, i have no idea (eg, never used them) but looking at the faq of adesklets```
As on adesklets 0.4.12, supported window managers in that category are:

    * KDE: for versions >= 3.4.1 (earlier versions untested). You need to turn on “Control Center -> Desktop -> Show icons on desktop -> Allow programs in desktop window”, or to turn off the “Show icons on desktop” altogether1.
    * Nautilus
    * ROX-Filer: only preliminary support for now
    * Xfce4
    * xffm-desktop: only preliminary support for now

```
and not seeing gnome there, i could think its g(nome)desklets...

---

### Post by AthlonMDK on 2005-11-25
ThnX that clarifies a lot! so adesklets it will be for me...:KS

---

### Post by Cethy on 2006-11-03
> **oskude said:**
> well, i have no idea (eg, never used them) but looking at the faq of adesklets```
As on adesklets 0.4.12, supported window managers in that category are:

    * KDE: for versions >= 3.4.1 (earlier versions untested). You need to turn on “Control Center -> Desktop -> Show icons on desktop -> Allow programs in desktop window”, or to turn off the “Show icons on desktop” altogether1.
    * Nautilus
    * ROX-Filer: only preliminary support for now
    * Xfce4
    * xffm-desktop: only preliminary support for now

```
and not seeing gnome there, i could think its g(nome)desklets...

Nautilus ==> Gnome, no ?

---

