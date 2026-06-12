---
title: "Enemy Territory doesn't seem to allow server downloads."
date: 2008-03-19
forum: Gaming &amp; Leisure
---

### Post by hammertm on 2008-03-19
Enemy Territory doesn't seem to allow server downloads. loads up fine runs fine - sorted the sound. 

'gksudo nautilus' and changed the file permissions of the folder structure so that 'other' can read and write files but every time i goto a server running a mod or none std map it bombs out when it tries to download the missing paks.

Any ideas.:guitar:

---

### Post by hammertm on 2008-03-19
Ok - If I start enemy territory from root terminal

'et'

It downloads paks, but the sound is gone and then i get kicked by punkbuster for a violation. Update Punkbuster?

Is there any permanent fixes for ET sound?

I have searched forums but am getting a bit bogged down.

---

### Post by hammertm on 2008-03-19
Downloaded the appropriate punkbuster files and put them in the appropriate place. Changed .etwolf permissions for others to read and write files and now it downloads when ran from usr but now i get kicked for cannot download to hunksusage.dat.

Should i have installed this to my user and not in root, if so how do you do this?

---

### Post by almostlinux on 2008-03-20
Install ET as normal user (to a folder in your home) 
Update till 2.60b patch.
Update pb. (~/.etwolf/pb/pbweb.x86)


For sound, use ALSA -> [http://ubuntuforums.org/showthread.php?t=362231](http://ubuntuforums.org/showthread.php?t=362231)

---

