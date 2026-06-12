---
title: "Kernel Panic"
date: 2005-04-29
forum: Desktop Environments
---

### Post by johnyeros on 2005-04-29
I dont know if this is the place to post this. But I need help..
Problem: Last night, I Want inkscape .41 (apt-get only show .40) and so I download a debian package from the debian site to force an install.. I also install a few other package that .41 wanted. such as Libc6..
problem is that after i force the libc6 install. Synaptic report broken package.
I can't go back to the libc-6...blah..ubuntu so i was stuck with the latest version of it, which piss ubuntu off. I restart my system, and I get:

kernel panic - chroot error while loading shared libraries: /lib/tls/libc.so.6 file too short ...etc

so i download the live cd.. i log on and i can't seem to mount my root partition

what i did

su
mkdir hd1
mount /dev/hda2 hd1

when i did this, it just freeze the system...
i want to mount it to fix the problem.. i figure if i can mount it, and access it, i can extract the lib6...blah..ubuntu package into where it suppose to be.. to fix it.. or apt-get.. whichever work.. please help me

---

### Post by az on 2005-04-29
Do not mix debian and ubuntu repositories.

Heed the warnings when apt tells you that breaking libc6 is a bad thing.

You are screwed.

---

### Post by az on 2005-04-29
I would reccommend you compile the app from source.  You should use the debian source packages if it is available in Sid.  This is how backports are made.

I do not know why you cannot mount your root partition.  Perhaps it was dammaged when you crashed your system?

---

### Post by GTKpower on 2005-04-29
azz is right.  Trust me, I learned the hard way when it came to wanting the newest, shiniest (and unstable) packages.

The Ubuntu repositories, with Universe/Multiverse/Restricted enabled are all you will ever need.

They are VERY extensive, and can fill most, if not all, of your needs.

If you want a new version of whatever app, just wait until the Ubuntu repos are updated.  Certainly not worth messing up your system.  Plus, the 6-month (max) update cycle isn't so bad when you think about the stability you'll be getting.  

Anything else you want should be compiled from source.

---

### Post by johnyeros on 2005-04-30
yeah i realize it's bad..
i reformatted and try foresight.. that thing is slow and crappy.. take like hours to install..
so i'm back to ubuntu.. all gravy now

---

