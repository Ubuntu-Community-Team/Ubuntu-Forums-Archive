---
title: "Civilization: 'Call To Power' Linux version"
date: 2006-05-04
forum: Gaming &amp; Leisure
---

### Post by Poldi on 2006-05-04
hi all.

while I can play the Windows Civ 3 version in Ubuntu just fine with Wine, I fail to play the Linux (Loki) version of Civ:CtP I have since my SuSe days.

the installer works, I can start CtP, but when I try to launch the actual game from the world customization screen, the game exits to the desktop.

anybody having more success?

(and yes, I know: Civ3 actually is much better than CtP, but it offends my to own an actual native Linux game and not being able to play)

kind regards,
Poldi

---

### Post by Perfect Storm on 2006-05-04
Any error outputs when running it in the terminal?

---

### Post by Poldi on 2006-05-08
in a german Ubuntu-forum I found the suggestion to apply the last available patch to Civ:CoP. this seems to have worked for several users with similar problems.

now, where to get the patch? the old link on Lokis site and all tested Google-links are broken. the game seems to old to be relevant on the net any more...

can anybody proviede me with the latest Civilization:Call to power patch?

thanks and regards,
Poldi

---

### Post by ELD on 2006-05-08
[QUOTE=Poldi]in a german Ubuntu-forum I found the suggestion to apply the last available patch to Civ:CoP. this seems to have worked for several users with similar problems.

now, where to get the patch? the old link on Lokis site and all tested Google-links are broken. the game seems to old to be relevant on the net any more...

can anybody proviede me with the latest Civilization:Call to power patch?

thanks and regards,
Poldi[/QUOTE]

Loki is actually no more try looking on [www.icculus.org](www.icculus.org)

---

### Post by englebert on 2009-01-19
Even though this thread is over three years old, it is the best result returned for "linux call to power". So I thought I would update it with what I found for any others looking to get this game working on modern distributions. All the old loki patches for Civilization: Call to Power for Linux can be found here: [http://lokifiles.tuxgames.com/patches/civctp/](http://lokifiles.tuxgames.com/patches/civctp/).

---

### Post by englebert on 2009-01-19
Do 'export _POSIX2_VERSION=199209' on the commandline before running the patches if you get an error similar to 'Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory'.

---

### Post by englebert on 2009-01-19
Turns out those patches don't work either, neither does loki_updater due to changes in commandline program syntax. However! The update located here works: [http://lokifiles.tuxgames.com/updates/civctp/civctp-1.2a-english-unified-x86.run](http://lokifiles.tuxgames.com/updates/civctp/civctp-1.2a-english-unified-x86.run)
I just watched the intro. I'm not sure if that was worth the headache, but at least I got it to work eventually.

---

### Post by thewarlock on 2010-12-22
Civ:CTP install instructions



do a manual install via the readme.



then 



sudo _POSIX2_VERSION=199209 linux32 sh ./civctp-1.2a-english-unified-x86.run 



if you're running 64bit. if not, remove the linux32 parts.

if you want the movies, manually copy them over.

as of right now though, there is no sound in 10.10 as there was in 10.04
no idea why.

---

### Post by Cousjava on 2010-12-22
Is there any way of getting Civ3 complete edition to work? I've had the game a while but not been able to get to run - or even install fully - under wine.

---

