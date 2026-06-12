---
title: "Debian KDE install from netinst cd?"
date: 2007-10-19
forum: Debian
---

### Post by 67GTA on 2007-10-19
I  wanted to install a complete Debian KDE desktop using the netist CD. If I use the mirrors during installation, it will install Gnome. What command would I use to install the KDE desktop only? I know sometimes apps have different names in Ubuntu than in Debian. When I install and boot into CLI, what do I apt-get?

---

### Post by scrooge_74 on 2007-10-19
sudo apt-get install kde

(at least that is what synaptic calls the package)

---

### Post by bhagabhi on 2007-10-20
Sounds like you have a gnome netinstall cd - there are ones with pure KDE or XFCE - 

KDE here:
[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-kde-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-kde-CD-1.iso)

Check out this folder for the others:
[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/)

EDIT: oops - thought there was specific ones for KDE/XFCE too, but it seems like there isn't this alternative if you specifically want the netinstall... :(

---

### Post by scrooge_74 on 2007-10-20
One CD to install them all

---

### Post by kerry_s on 2007-10-20
> **67GTA said:**
> I  wanted to install a complete Debian KDE desktop using the netist CD. If I use the mirrors during installation, it will install Gnome. What command would I use to install the KDE desktop only? I know sometimes apps have different names in Ubuntu than in Debian. When I install and boot into CLI, what do I apt-get?

**apt-get install xorg synaptic kdm kde**
reboot(ctrl+alt+delete)

should install X, the login manager and all of kde, synaptic is the package manager.

you might want to go lighter

**apt-get install xorg synaptic kdm kde-core**
reboot(ctrl+alt+delete)

then you can just select the extra stuff you want after you login and see whats there.

---

### Post by plb on 2007-10-20
wrong wrong && WRONG! :)

When you get to the boot prompt on the netinstall CD do this:
> 
tasks=kde-desktop


Now when you choose desktop environment it will install KDE rather than GNOME...Cheers! Be sure to visit forums.debian.net =)

---

### Post by kellemes on 2007-10-22
> **plb said:**
> wrong wrong && WRONG! :)

When you get to the boot prompt on the netinstall CD do this:



Now when you choose desktop environment it will install KDE rather than GNOME...Cheers! Be sure to visit forums.debian.net =)

Cool little fact! :)

---

### Post by tdrusk on 2007-10-22
I just do an install, and when it asks what mirrors I select cancel. Then I reboot into a commandline and run the above apt-get command.

---

### Post by SkyNet2029 on 2007-10-23
I just do a base install, then UNselect desktop environment...then I let it run and apt-get install kdecore. Same diff I suppose.

---

### Post by tdrusk on 2007-10-27
> **plb said:**
> wrong wrong && WRONG! :)

When you get to the boot prompt on the netinstall CD do this:



Now when you choose desktop environment it will install KDE rather than GNOME...Cheers! Be sure to visit forums.debian.net =)
This doesn't work for me

---

### Post by someguy435 on 2007-10-27
> **tdrusk said:**
> This doesn't work for me

try:

> install tasks=kde-desktop

or

> install tasks="kde-desktop, standard"

The "install" part was just left off by **plb**. Hit F8 at the boot prompt to see this example.

---

