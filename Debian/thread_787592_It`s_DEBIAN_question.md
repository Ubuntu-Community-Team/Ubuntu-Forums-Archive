---
title: "It`s DEBIAN question"
date: 2008-05-09
forum: Debian
---

### Post by heatblazer on 2008-05-09
I have downloaded the DEBIAN iso from their official site. I got only the debian40Cd1.iso. Can you give me an info about what it includes? Is it enough for a working pc. There are over 8CDs or these are with all pakages? Sorry for asking.

---

### Post by polki@mac.com on 2008-05-09
It installs the basic system and then you can use apt-get/aptitude to get whatever you want afterwards. I usually use the netinstall cd to get a _very_ basic system, then download the rest of my stuff.
The installer will ask you if you have any more cd:s to feed it with, just say no and you'll be fine. But to get a working machine I always have to download things after installing, there's always this or that package missing...

---

### Post by p_quarles on 2008-05-09
Moved to Other OS Talk >> Debian.

It looks like you have disk 1 of the installation set. This is more than adequate if you want to install with a good, live internet connection. In fact, most people opt for the "network install" CD, which contains only a basic system, and takes up about 150 MB.

---

### Post by heatblazer on 2008-05-09
Forgive me for that question again, but is this CD packed with KDE?  Or I`have to apt-get it? It`s because I am planning to install few DEBIAN machinese around just for variation since I have more than 20 ubuntus. :)

---

### Post by odiseo77 on 2008-05-09
It seems what you need is the [debian-40r3-i386-kde-CD-1.iso]("http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-kde-CD-1.iso"). [Here's]("http://cdimage.debian.org/debian-cd/4.0_r3/i386/list-cd/debian-40r3-i386-kde-CD-1.list.gz") a compressed list of the CD contents. However, depending on what you're planning to use these machines for, it might be better to install [Debian Testing (Lenny)]("http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/debian-testing-i386-kde-CD-1.iso") (I'd strongly recommend you this if you're using these machines as desktops/workstations (not servers, I  mean)).

---

### Post by CREEPING DEATH on 2008-05-09
```
install=kde
``` is the cheat code for KDE IIRC.  The CD image you have will work fine if you have network access.  I use Lenny when I do Debian desktops, you can jigdo a Lenny CD or DVD in a few hours.

CD

---

### Post by markharding557 on 2008-05-10
the default desktop of debian is gnome however you can deselect that in the installation menu and then install kde on the command line.
as someone else said the net install cd is the most commonly used

---

