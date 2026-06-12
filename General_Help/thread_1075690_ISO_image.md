---
title: "ISO image"
date: 2009-02-20
forum: General Help
---

### Post by cowboy7305 on 2009-02-20
I am using Ubuntu 8.1 using k9copy i can copy files to audio and video files but no ISO file .K9copy set up to make Iso file 
Also have copied files using K3b just copied every thing over all went well and fitted on disk sound ok on computer dvd ,but no sound on from home dvd player ,also no interaction to control commands 
any help 
i cam use shrink but rather use K9copy if i can

---

### Post by taurus on 2009-02-20
Did you burn the ISO file as an image file with k3b?  Before you burn it to a DVD, see if you are able to play with (sound and video) vlc since vlc can handle ISO video files just fine.

```
vlc filename.iso
```

---

### Post by digitalbenji on 2009-02-20
if you are uncertain about making the .iso, I create my ISO's this way:```
dd if=/dev/dvd of=~/filename.iso
```
This gives you a bit for bit copy of the dvd, just change /dev/dvd to /dev/cdrom if you are using a cd.  You can then just drag and drop the .iso into vlc, or do it as taurus suggested.

---

