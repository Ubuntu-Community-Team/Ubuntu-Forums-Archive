---
title: "xstroke 0.6"
date: 2005-09-27
forum: Deferred/Invalid Requests
---

### Post by 23meg on 2005-09-27
from [http://www.xstroke.org/](http://www.xstroke.org/) :

>  xstroke is a full-screen gesture recognition program for the X Window System. It captures gestures performed with a pointer device, (such as a mouse, a stylus, or a pen/tablet), recognizes the gestures and performs actions based on the gestures. xstroke has been developed on Linux systems, (i386 and StrongARM), but should be quite portable to any reasonable system with X.

it's the most commonly used handwriting recognition app in linux; a must have for tablet pcs. it used to be in debian unstable, but i think the package maintainer abandoned it and it was orphaned. 

i'm having no luck building it from source in Breezy, and an outdated .deb i've found does not work due to a known libxft version problem which it seems was fixed in this version.

---

### Post by 23meg on 2005-10-03
i've converted an rpm of xstroke that i found to deb, but it's not running stable at all. i'd love it if someone can build a deb from scratch.

---

### Post by 23meg on 2005-10-25
I've made another deb package, which has no dependencies and seems to work fine with Breezy. Attached.

---

### Post by Apex on 2005-11-23
[QUOTE=23meg]I've made another deb package, which has no dependencies and seems to work fine with Breezy. Attached.[/QUOTE]

Works beautifully, thanks for your hard work!

---

### Post by 23meg on 2005-11-23
Glad to help. Just noticed this isn't in Dapper so we can consider this deferred; shame on me. I'll put it up on [the Universe candidates list]("wiki.ubuntu.com/UniverseCandidates").

---

### Post by hoilinux on 2009-02-21
> **23meg said:**
> I've made another deb package, which has no dependencies and seems to work fine with Breezy. Attached.

hi, i download the file and install it, but cant find the executable file to start the program. 

running Utun 8.10, 
messages show install complete 
not found in start menu
cant start with shell command

please help 

:(

---

### Post by Favux on 2009-02-21
Hi hoilinux,

I'm not sure there is any development on xstroke anymore.  If you want a gesture recognition program I think you might want to check out Tom Jaeger's Easystroke.  There's a thread on it in Cafe.  He just released a beta of the new version and there are links to ppa's as the new version isn't in Synaptic.

If you want "handwriting" recognition you should check out CellWriter.

---

### Post by nutsyben on 2009-05-04
> **23meg said:**
> I've made another deb package, which has no dependencies and seems to work fine with Breezy. Attached.


Good JOB :::!!!!!

A first order script for tablet-linux user :p

THANKS-GRACIAS-MERCI-DANKE

---

