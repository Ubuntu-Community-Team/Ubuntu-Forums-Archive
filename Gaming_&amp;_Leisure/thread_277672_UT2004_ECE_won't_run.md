---
title: "UT2004 ECE won't run"
date: 2006-10-15
forum: Gaming &amp; Leisure
---

### Post by JunySan on 2006-10-15
****Hi

I just installed UT2004 ECE & the megapack, however when I try to run the game I get this;

ReadFile beyond EOF 0+4/0

History:

Exiting due to error

Please can somebody help me with this ](*,) ."By the way I have XGL/beryl running and I can switch to Metacity.:confused:

---

### Post by Durd3n on 2007-03-22
I have the same problem.
Here's what I did:

1. Installed the game - copied linux-installer.sh to home directory,
> sudo sh linux-installer.sh
and installed to the usr/local/games/ut2004 directory. (I had to edit the /.ut2004/System permissions in order to play the single player game and save the profile.

2. Applied the patch - downloaded ut2004.megapack-english-2.run then
> sudo sh ut2004.megapack-english-2.run
and installed to the usr/local/games/ut2004 directory.

At this point, I'm unable to load the game. The loading screen comes up, then disappears. I even tried running the game as root to no avail. Here is the terminal output:

username@ubuntubox:/usr/local/games/ut2004$ sudo ./ut2004
Exporting CTF-BP2-Pistola.....Successful!
Exporting CTF-BP2-Concentrate.....Successful!
ReadFile beyond EOF 0+4/0..

History:

Exiting due to error
username@ubuntubox:/usr/local/games/ut2004$

Any help is greatly appreciated.

Relevant System Details:
Ubuntu 6.10 Edgy
MSI 865PE-Neo2
1GB Ram 3200
Nvidia 6600GT
SB Live! 5.1

---

### Post by Perfect Storm on 2007-03-22
Do not use the patch script it will bork ut2004. Instead get the tarball version of it and manually copy/moved it to ut2004 location.

---

### Post by Durd3n on 2007-03-24
Thank you for that.  It did indeed work.  One more thing if you don't mind.  I've played a few maps, and I've noticed for instance on DOM-Atlantis, the water wall texture isn't displaying as it should (or at least like it did in Windoze).  It's almost like the layer is non-existent (or at 90% transparency).  Other than that, the game works fine.  I haven't been able to find an answer on that and I'm probably asking this question in the wrong section. 

Again, thanks for any help.

---

