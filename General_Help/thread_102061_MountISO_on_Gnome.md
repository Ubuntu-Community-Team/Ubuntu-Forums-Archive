---
title: "MountISO on Gnome?"
date: 2005-12-11
forum: General Help
---

### Post by CodyJarrett on 2005-12-11
Hi, is there any way to get MountISO to work under Gnome. I mean, it installs fine, but what then? Under KDE it can be used while right-clicking and choosing actions, but what do I have to do under Gnome?

Any help greatly appreciated!

cheers

---

### Post by [Rui] on 2005-12-11
The Archive Manager opens ISOs just fine.

---

### Post by MetalMusicAddict on 2005-12-11
I dont think he just wants to open them. I think he wants to mount them like a virtual cd-rom. Right? If so I would like to see this work also.

---

### Post by M3ta7h3ad on 2005-12-11
im sure its a command of mnt.

something like...

> 

blah@bob: mkdir tempMount
blah@bob: mount ~/isos/example.iso ./tempMount



Not sure if that works, or if it sorts out read-write access to it..but yeah, thats damn similar to something I used to use to mount iso's as drives.

---

### Post by M3ta7h3ad on 2005-12-11
Try this after a quick google if the above didnt work.

> 
mount -o ro loop example.iso /mnt/iso 

Your contents of the disk will be in /mnt/iso

---

### Post by MetalMusicAddict on 2005-12-11
Im actually making a iso now so I cant test. Can this be made into a script? Im wondering if it would be able to use the disk label for the mount and come up like a physical cd/dvd.

---

