---
title: "Wesnoth for Hoary?"
date: 2005-10-17
forum: Gaming &amp; Leisure
---

### Post by DirtDawg on 2005-10-17
I've been getting into Battle of Wesnoth lately. I'm using ppc Hoary, but noticed my pre-packaged Ubuntu Hoary version is 8.1.1 while the newest version of Wesnoth is around 1.0. I looked at the notes per versions and they've changed and balanced a ton.
So I wondered, if I downloaded the pre-packaged Breezy Wesnoth and tried installing it on Hoary, would it work or is there a good chance it would "break" my install?
Otherwise, maybe it'd be easier to build/compile (something I've never done before successfully)?
I don't want to switch to Breezy yet as my Ubuntu box is working great (if it ain't broke...).
Any insight would be most appreciated. 
Thanks!

---

### Post by Harleen on 2005-10-17
The breezy build might work on hoary, but you won't be able to install it without breaking package dependencies. I really wouldn't recommend it.
When I was using hoary I compiled wesnoth without any problem. If you are new to compiling programs it might cause a bit trouble to get all needed packages, but once installed, compiling will be no problem anymore.
To compile wesnoth, you will need to have the packages build-essential, libfreetype6-dev, and libsdl1.2-dev installed. And maybe more...

After that just unzip the source and do the usual steps:
./configure
make
sudo checkinstall

Maybe the configure will complain about some missing dependencies. If you cannot solve them on your own, you will find someone on this forum, who can.

---

### Post by DirtDawg on 2005-10-17
Thanks I'll give it a shot. :mrgreen:

---

### Post by DirtDawg on 2005-10-17
I have a problem now.
I'm the kind of guy with no internet on my Ubuntu box. I tried to configure the Wesnoth file, but got a complant about no C compiler on the $path. I found out from searching the forum that I needed to install build-essential package.
So I've been in dependancy hell since then (dependancy Satan says "hi".)
THE REAL PROBLEM:
When I try to install **g++-3.3_3.3.5-8ubuntu2_powerpc.deb**, the machine complains that it's dependant on **libstdc++5-3.3-dev**, which hasn't been compiled yet.
But when I try to install **libstdc++5-3.3-dev_3.3.5-8ubuntu2_powerpc.deb**, the machine complains that it's dependant on **g++-3.3**, which hasn't been compiled yet.
:confused: :confused: :confused: :confused: :confused: :confused: 
What's a fool to do?

---

### Post by Harleen on 2005-10-18
The build-essential package is included with the standard install media, so if you have that handy, you should be able to use apt-get for installing it.
As for the errors of dpkg I cannot be much a help, as I'm fairly new to ubuntu and have only used an rpm-based distribution before. Maybe passing both files will solve your problem:

```
dpkg -i g++-3.3_3.3.5-8ubuntu2_powerpc.deb libstdc++5-3.3-dev_3.3.5-8ubuntu2_powerpc.deb
```

But without install-CD or a permanent internet connection it will become a real pain to collect all the needed packages.

If it hasn't to be the latest version of wesnoth, you may try the version 0.9.3 from the backports: [http://de.archive.ubuntu.com/ubuntu/pool/universe/w/wesnoth](http://de.archive.ubuntu.com/ubuntu/pool/universe/w/wesnoth). It's at least more current that the original hoary version and will work guaranteed for you.
Or you may try the statically linked version from the wesnoth page. That's got to be new there. At least I didn't notice that link before... [http://www.wesnoth.org/wiki/Download#GNU.2FLinux](http://www.wesnoth.org/wiki/Download#GNU.2FLinux)

---

### Post by DirtDawg on 2005-10-18
Hey, thanks!
It didn't take me long to figure out compiling was a bad idea with no internet, so I gave up on that. I would use the normal .deb file for version 1x, but I've read bad things about using .debs not intended for Ubuntu.
But I will use the 9.x version you pointed me to! It's not the most up-to-date, but it'll do. I always wondered what "backports" were.
Thanks again :mrgreen:

---

