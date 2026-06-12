---
title: "strategy for multi-user computer?"
date: 2005-08-05
forum: Desktop Environments
---

### Post by royg1234 on 2005-08-05
What are some good strategies on how to set up users, groups, permissions, user privileges, etc. on a computer that will be shared by roommates, and guests?  This computer will also have some stuff (mostly music) shared on the local network.

My main concerns are Evolution, Firefox, amaroK, amaroK's mySQL database, and the music files.

Thanks!

---

### Post by andlinux21 on 2005-08-05
I hope someone responds because I want to set up 6 computer network at a daycare for kids to use linux mostly for basic games and typing.

---

### Post by Sam on 2005-08-06
First of all [UbuntuGuide - Security](http://ubuntuguide.org/#security) !

---

### Post by wmcbrine on 2005-08-06
Huh, I never thought of this as something requiring a strategy. Just add users as desired -- the default setup should give them the ability to run whatever apps they need, without the ability to do any damage. Make sure they're not in the sudoers group, that's all.

Evolution and Firefox, like other Unix apps, are designed to work with multiple users, and keep each user's data separate, all automatically. You don't need to do anything, unless maybe you want to pre-install some Firefox extensions for the less experienced. (Extensions are normally installed in each user's profile, so different users can have different extensions, and they don't need root privileges to install them.)

For the music files, do you want anyone to be able to add to them, or just play them? The former is more complicated. For the latter, just put them under /usr/local/share or summat, and chmod 755 the directories, 644 the files.

---

### Post by C38a7r1zvl on 2005-08-06
Agree with the "why a special strategy"-bit. As long as you trust your users enough that you don't feel the need to "lock" them in some KIOSK-thingy, just add them. MySQL-Databases are secured with MySQL's very own access system and as wmcbrine pointed out every sensible *nix app is meant to work on a multiuser environment. If you don't want other users to read your personal files just make sure, they dont have access to them (chmod o= /home/bla -R).

---

