---
title: "Torrents not working in Debian, X is crashing"
date: 2007-12-25
forum: Debian
---

### Post by kevCast on 2007-12-25
I recently did a Debian netinstall. However, two things have kept Debian from replacing my Ubuntu install. First, I can't connect to any trackers when I download a torrent. It doesn't matter what torrent app it is, it won't connect. Could it be that I need to open some ports? If so, how? Also, when I switch from the etch repo to the testing repo in my sources.list and do an apt-get update && apt-get dist-upgrade, after the reboot, xorg crashes. I know Ubuntu uses a more update to date xorg, and when I do an Ubuntu server install, xorg crashes there too. How is it that xorg can work wonderfully in detecting my screen in Ubuntu but not Ubuntu server/Debian testing? Should I copy my xorg.conf and paste it into my Debian xorg.conf?

Any help is appreciated, thank you.

*Edit: The xorg.conf copy/paste worked. I just need to know now how to get the torrents going and I'll be a full-time Debian user!*

:)

---

### Post by cprofitt on 2007-12-26
Curious what made you decide to switch from Ubuntu to Debian... I am leaning towards Debian myself... and just curious.

---

### Post by odiseo77 on 2007-12-26
I've used a torrent client on Debian Lenny without problems (don't remember which torrent client, though). You probably must open some ports. The easy way I've found to do this is to install firestarter (open a terminal as root and type: ***apt-get install firestarter***). After you're done with the installation, open firestarter (I think, on Debian you can find it on 'System>Administration' and 'Applications>Internet', if you're on gnome); you will be prompted to configure firestarter, after you're done with that, go to the 3rd tab ('Rules' or something like that), then right-click on the second field (the white space at the bottom), on the pop up menu, select "Add rule" (the '+' symbol), other window will appear; in the "Service name" field select "BitTorrent" and click on the "Add" bbutton (here, you could also specify which IP address you allow to connect to your machine, if you wish). This should allow you to use bittorrent :)

Greetings.

---

### Post by kevCast on 2007-12-27
> **indigo196 said:**
> Curious what made you decide to switch from Ubuntu to Debian... I am leaning towards Debian myself... and just curious.
Because I can tweak, because it's fast, and because I like their mindset. Also, I've found it to be a great deal more stable than Ubuntu, even though I'm using the testing repos. The thing I like is that when I'm using testing, it's like a rolling release. My Debian system gives me enough room to tweak without any headaches.

> **odiseo77 said:**
> I've used a torrent client on Debian Lenny without problems (don't remember which torrent client, though). You probably must open some ports. The easy way I've found to do this is to install firestarter (open a terminal as root and type: ***apt-get install firestarter***). After you're done with the installation, open firestarter (I think, on Debian you can find it on 'System>Administration' and 'Applications>Internet', if you're on gnome); you will be prompted to configure firestarter, after you're done with that, go to the 3rd tab ('Rules' or something like that), then right-click on the second field (the white space at the bottom), on the pop up menu, select "Add rule" (the '+' symbol), other window will appear; in the "Service name" field select "BitTorrent" and click on the "Add" bbutton (here, you could also specify which IP address you allow to connect to your machine, if you wish). This should allow you to use bittorrent :)

Greetings.
Thank you. I can't try it now, because I can't seem to connect to the Debian repos, but once I can, I'll see if this works.

---

