---
title: "Does the DVD installer include drivers that the Live CD doesn't (Fedora 8)"
date: 2008-07-26
forum: Fedora/RedHat and derivatives
---

### Post by Redrazor39 on 2008-07-26
Is this true? I don't have any blank DVDs or a big enough flash drive, so I was going to just make a live CD and install fedora like that. I want fedora 8. 

If this is true, where can I get the drivers after installing with the Live CD? 





And what about packages? Like programs and codecs and all the useful stuff. What's on the DVD that's not on the CD? Where can I get it?

---

### Post by mthei on 2008-07-26
Fedora will not include nonfree drivers with any release, so if it's not on the liveCD for that reason, it won't be included with the DVD, and only through additional repositories.
To the best of my knowledge (I've only installed with the LiveCDs), the DVDs do contain more, but only from the [Fedora reposotories](http://download.fedora.redhat.com/pub/fedora/linux/releases/9/Fedora/i386/os/Packages/). Check that list to see if it includes what you're looking for.

Edit: Although for what it's worth, it may be better to install with the DVD anyway, as you get to choose what gets installed on your computer, and with the LiveCD, there's less to be removed/added and you won't have to disable the services that you don't need. But as mentioned, I may be wrong as I've never used the DVD installer.

---

### Post by Redrazor39 on 2008-07-26
Thanks for the reply. I think I'll just install with the live CD now.

---

### Post by dca on 2008-07-28
I think the LiveCD(s) only take a hit on the pre-installed app end.  ie:  Live consists of Abiword instead of complete OOo...

---

### Post by mthei on 2008-07-28
I think that was only to save room on the liveCD, as there needed to be extra room for SELinux, the firewal configuration tool, and whatever else administration tools there are compared to the other majors. At least it's not too much of a pain to add and remove whatever you need (depending on the mirrors you're given for the yum session). My real gripe with the liveCD is the number of services running in the background. But much like unneeded software, it's easy enough to stop what you don't need.

---

