---
title: "Question From A NoOMG WHAT IS THIS THING? (a.k.a, Universe repository w/o internet)"
date: 2006-10-06
forum: Desktop Environments
---

### Post by LightOfDay on 2006-10-06
Hello All,

I am a relatively new Linux user who has chosen Ubuntu as a first Linux operating system. Everything seems to be running well, until (with that absolute inevitability that I should expect from Linux by now) something crops up, as I try to make work that wonderful invention, the Internet.

I am the proud owner of a Broadcom BCM4318 [Air Force One 54g] 802.11g PCI wireless card, which just happens to be from the same Broadcom that has consistently refused to release its Linux binaries. Somewhat luckily for me, several guides are in existance, which seem to explain it rather nicely... nice GUI-intensive remedies, a little playing with that scary Console thingy, and... uh-oh... the Universe Repository.

Ok, install Universe repository. Wait. Must... be... connected... to... Internet.

The subtle irony of my situation mixed with frustration at the wasted hours in front of a computer screen (LinEpilepsy for Kernel 1.6), so now I seek help from the ranks of seasoned veterans.

Bad jokes aside, my request: does anyone know of a way and a place whereby I can download the Universe repository in a static form onto a USB or external hard drive over my Windows connecttion, and work it into Ubuntu? Your help is much appreciated.

In case it turns out more complicated than I expected:

_My Router:_ Dynalink RTA1025W
_My Distro:_ Dapper Drake Ubuntu, off LiveCD for now, dual booting later
_My Card:_ Broadcom BCM4318 for 802.11g<B>
_My Working Knowledge of Linux:_ Anything which happens to be documented over the Internet

Thank you,

LightOfDay

---

### Post by aysiu on 2006-10-06
The Universe repository is *huge*. I highly doubt you want or need to download the *entire* Universe repository.

What package are you looking for?

You can find packages and their dependencies here:
[http://packages.ubuntu.com](http://packages.ubuntu.com)

You can also browse the Universe repository here:
[http://archive.ubuntu.com/ubuntu/pool/universe/](http://archive.ubuntu.com/ubuntu/pool/universe/)

Ubuntu is a highly internet-dependent distro. Other distros have add-on disks with a lot more software. I think Debian has 14 disks. Mandriva has three. Fedora has... five? Seven? I forget.

Ubuntu has only one disk's worth of software.

---

### Post by blackened on 2006-10-06
Like aysiu said: first figure out what packages you need, then use Windows to download the debs, then use the terminal to install them with dpkg.

---

### Post by LightOfDay on 2006-10-06
Thank you kindly... 

Does all Linux-specific software end up in the Universe repository? Thus making it unnecessary to browse SourceForge/etc? 

LightOfDay

---

### Post by aysiu on 2006-10-06
Main is open source software maintained by the developers
Universe is open source software maintained by the community
Multiverse is closed source software maintained by the community
Commercial is... commercial... I forget how that differs from Multiverse
PLF stuff is basically illegal in the US packages

Some obscure SourceForge programs are not in the repositories--very few, though.

**Edit**: More info here:
[http://www.ubuntu.com/ubuntu/components](http://www.ubuntu.com/ubuntu/components)

---

