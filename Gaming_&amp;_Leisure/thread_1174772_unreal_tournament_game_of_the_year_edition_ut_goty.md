---
title: "unreal tournament game of the year edition ut goty on ubuntu 9.04"
date: 2009-05-31
forum: Gaming &amp; Leisure
---

### Post by adsbaer12 on 2009-05-31
i was really frustrated when i run into a lot of troubles trying to install and play ut goty on ubuntu 8.04. many of the guides in the internet did not work for me or at some stage i went into error messages.

so to whom it may concern /to anybody wanting to spare these troubles here is my guide that worked for me.

parts of this guide where taken from other guides from the net. thanks tho their respective authors!

------------


how to install and play /run unreal tournament game of the year edition /ut goty on ubuntu 9.04

the goty edition consists of two discs. you need both. you can use images, but you have to know how to mount/unmount them. make sure that both images and real physical discs have the right volume labels "UT_GOTY_CD1" and "UT_GOTY_CD2" so that setup can find them when requested!

1. download unreal.tournament_436-multilanguage.goty.run [6.7 MB (6974002 bytes)]
([http://www.liflg.org/?catid=6&gameid=51](http://www.liflg.org/?catid=6&gameid=51))

2. save file to /home/*yourusername*/

3. install 'libgtk' via system -> administration -> synaptik package manager

4. insert goty_cd1of2 into the optical drive

5. in terminal: 'sudo sh unreal.tournament_436-multilanguage.goty.run'
you see the setup menu appear, chose standard textures, no s3t-textures

6. start install progress, change to goty_cd2von2 when asked

6b (optional) download the official ut bonuspack into yout home dir and install via 'sudo sh unreal.tournament.official.bonus.pack.collection.run'

7. remember the path ut was installed to, close setup after completed successfully

8. in terminal: 'cd /usr/local/games/ut' then followed by 'sudo gedit playut'

9. paste this into it, and save (change *yourusername*!):

#!/bin/sh

cd /home/*yourusername*/ut

bash ut

10. in terminal: sudo chmod 755 playut

11. delete /home/*yourusername*/unreal.tournament_436-multilanguage.goty.run
(and the optional unreal.tournament.official.bonus.pack.collection.run [35.5 MB (37213789 bytes)])

12. run unreal tournament by double-clicking the 'playut'-file located in /usr/local/games/ut (you can create a shortcut/launcher if you like to)

------------


hope this helps.
greetings from adsbaer12 to everyone playing ut goty on ubuntu/linux! :)

---

### Post by Noirblanc on 2009-06-15
hey i got this as a responde:

```

```
 noir@Noir-desktop:~$ ./unreal.tournament_436-multilanguage.goty.run --keep
Creating directory unreal.tournament_436-multilanguage.goty
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 436-multilanguage.goty Installer....................................................................................

Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

Gdk-WARNING **: locale not supported by C library


the installer pops up though can't install it doesn't find neither .iso or the cd

---

### Post by diiphantom on 2009-06-17
ill do a video and post it here to show you how to install it.

---

### Post by Nixot on 2009-11-28
When I load it up there is no sound. Why is this?

---

