---
title: "How to Install Mate on Ubuntu 14.04LTS"
date: 2014-05-11
forum: Desktop Environments
---

### Post by hitman2k9 on 2014-05-11
I have learned from the sources on the internet that mate has been officially put into ubuntu repos since 14.04LTS . I would like to know how to go about installing it as I couldnt find a way to do so without adding an external PPA . Any help will be highly appreciated .
Thanks in advance.

---

### Post by Drone4four on 2014-05-11
Did you come across a guide called "[Install MATE 1.8 desktop in Ubuntu 14.04]("http://www.itworld.com/software/412022/install-mate-18-desktop-ubuntu-1404")"?

---

### Post by hitman2k9 on 2014-05-11
> **Drone4four said:**
> Did you come across a guide called "[Install MATE 1.8 desktop in Ubuntu 14.04]("http://www.itworld.com/software/412022/install-mate-18-desktop-ubuntu-1404")"?

Yes , thats what I said its by adding a repo. If its official then why would i need to add a repo to install it to my base setup ?

---

### Post by buzzingrobot on 2014-05-11
Several Mate 1.6 packages are available in Trusty's Universe repo. I do not believe all of Mate is there yet.

The repo pointed to in that piece, and many identical pieces, is an archive of the current Mate release, 1.8, prepared by the Mate developers. They have not moved it to their customary repos because, I understand, Debian and, hence, Ubuntu, are missing a few dependencies Mate 1.8 requires. I've installed 1.8 on 14.04 from that archive.  The menu editor  and the user management GUI tool do not work.

---

### Post by MartyBuntu on 2014-05-11
> **buzzingrobot said:**
> The menu editor  and the user management GUI tool do not work.

Pretty much, yeah.

Using Ubuntu Studio 14.04 right now with MATE desktop.

---

### Post by hitman2k9 on 2014-05-11
> **buzzingrobot said:**
> Several Mate 1.6 packages are available in Trusty's Universe repo. I do not believe all of Mate is there yet.

The repo pointed to in that piece, and many identical pieces, is an archive of the current Mate release, 1.8, prepared by the Mate developers. They have not moved it to their customary repos because, I understand, Debian and, hence, Ubuntu, are missing a few dependencies Mate 1.8 requires. I've installed 1.8 on 14.04 from that archive.  The menu editor  and the user management GUI tool do not work.
eaxctly I saw a few mate packages on the universe repo and read about the support but saw it didnt have the basic mate-core and mate-desktop packages to start the desktop leave alone adding other dependencies. Hence I asked .

---

### Post by buzzingrobot on 2014-05-11
> **hitman2k9 said:**
> eaxctly I saw a few mate packages on the universe repo and read about the support but saw it didnt have the basic mate-core and mate-desktop packages to start the desktop leave alone adding other dependencies. Hence I asked .

Yeah, there was a story some time back making the rounds that Mate 1.8 would be accepted into the Trusty repos.  That seems, I guess, to have been taken to mean 1.8 would be installable on Trusty's release.  I imagine they'll all be there as the Debian folks make them available.

---

### Post by vermontbear on 2014-05-12
When I did a first test install of 14.04, I also installed Mate 1.8 using the guide referenced in the posts above. Initially that seemed to work reasonably well, but when I tried to get Compiz configured thereto, Mate 1.8 crashed irretrievably; you know, like the desktop came up flashing interminably. I could get out of it by doing Ctrl-Alt-Del and then holding my cursor over the "Shut-Down" button and clicking about as frantically as the desktop was flashing on and off. When the co-incidence co-incided, then the machine shut down.

On the Mate forum site, there are discussions about dependency problems with Mate and Debian.

If I were going to want to run Mate seriously, I might wait till the Linux Mint folks finished debugging version 17 and released it. Then, go for it.

Meantime, I'm having very nice results running Ubuntu 14.04 with Gnome Flashback Compiz.

---

### Post by hitman2k9 on 2014-05-12
Yeah am thinking of doing the same . But my only reason for mate is that its light on my laptop while gnome/fallback gives an occasional lag. And mate 1.8 is incompatible with compiz ,I moved to arch for setting up mate+compiz but got disappointed again.
> NOTE: Development of MATE (the 1.9 branch) in ArchLinux is now focussing  on GTK3. I doubt this issue is going to be resolved until after MATE is  properly running with GTK3.
This is was the reply I got on my thread.

---

### Post by buzzingrobot on 2014-05-12
Mate and Compiz seem to have a history of not liking each other.  I know Fedora's Mate 16 spin enables Compiz by default, so maybe things are different over there.

As I understand things, building Mate 1.10 as GTK3 or GTK2 will be a compile-time option, so each distribution can make the choice for itself.

---

### Post by oldrocker99 on 2014-05-13
> **buzzingrobot said:**
> Mate and Compiz seem to have a history of not liking each other.  I know Fedora's Mate 16 spin enables Compiz by default, so maybe things are different over there.

As I understand things, building Mate 1.10 as GTK3 or GTK2 will be a compile-time option, so each distribution can make the choice for itself.

On the first point, too true. On the second, interesting...I may grab the 1.10 source and see what it takes to compile.

---

