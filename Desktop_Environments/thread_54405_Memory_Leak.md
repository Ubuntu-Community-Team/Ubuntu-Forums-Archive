---
title: "Memory Leak?"
date: 2005-08-04
forum: Desktop Environments
---

### Post by Ubunted on 2005-08-04
I'm running 5.04 on an IBM A22m P3 1Ghz laptop with a 30GB hard drive and 512MB of PC100.

Practically the only programs I ever use are Firefox, GAIM and the Folding@Home Linux client, in addition to Update Manager once a day and the GNOME weather widget in the top toolbar. I replaced the 386 kernel with the 686 via Synaptic, if that matters.

The problem is, my memory usage slowly but steadily creeps up over time. It will start around 98MB on boot, then over a few days creep up until it fills everything and the system runs like junk.

I can close everything and it still doesn't clear it. Nothing but a hard reboot solves it. There is nothing that I can see in System Monitor's All Processes tab that would account for this - it's as though there's a phantom process that wont fully shut down or something.

I'm behind a router and I have Firestarter installed via apt-get, so I doubt it's a hacker.

Any ideas?

---

### Post by neocon2005 on 2005-08-04
Linux is doing exactly what it is supposed to be doing! Linux uses all the RAM at its disposal. The portion of RAM not used by apps is used as cache (it should not have affected your system performance though). To view 'true' free RAM available for use by newly launched apps, use
#free -m

Read the excellent post about Linux memory management at
[http://forums.gentoo.org/viewtopic.php?t=175419](http://forums.gentoo.org/viewtopic.php?t=175419)

Hope that helps.

[QUOTE=Ubunted]I'm running 5.04 on an IBM A22m P3 1Ghz laptop with a 30GB hard drive and 512MB of PC100.

Practically the only programs I ever use are Firefox, GAIM and the Folding@Home Linux client, in addition to Update Manager once a day and the GNOME weather widget in the top toolbar. I replaced the 386 kernel with the 686 via Synaptic, if that matters.

The problem is, my memory usage slowly but steadily creeps up over time. It will start around 98MB on boot, then over a few days creep up until it fills everything and the system runs like junk.

I can close everything and it still doesn't clear it. Nothing but a hard reboot solves it. There is nothing that I can see in System Monitor's All Processes tab that would account for this - it's as though there's a phantom process that wont fully shut down or something.

I'm behind a router and I have Firestarter installed via apt-get, so I doubt it's a hacker.

Any ideas?[/QUOTE]

---

### Post by Ubunted on 2005-08-04
Ah, of course, I forgot all about the cache.

Makes sense, except that Firefox doesn't really seem to start any faster, and when it gets "full" it takes forever to start anything. Might just be me though, I'll have to test this out more.

---

### Post by amanda on 2005-10-19
I am looking for a gnome weather widget and I can't find it or figure out how to find it in the "add programs" dialog. Any leads?

---

