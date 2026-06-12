---
title: "k3b image burning question"
date: 2009-01-25
forum: General Help
---

### Post by omegaserpent on 2009-01-25
i have a image.000 file i'd like to burn to dvd
is there a way i can manually convert this to a .iso file? 
or do i simply burn it as is?
help me limit my production of coasters  :D

---

### Post by sanderj on 2009-01-25
If it's really an iso image, you can just burn it.

If it's not an iso image, you first have to find what it is, and then if/how you convert it to an iso image.

---

### Post by oldos2er on 2009-01-25
What type of file is it?

---

### Post by mb_webguy on 2009-01-25
According to FileXT, a .000 is (among other possibilities) an IsoBuster image file that should be accompanied by a .vc4 file that describes its contents, but that "if the *.VC4 file is corrupt or gone, IsoBuster can open the file and treat the file as a generic image".  This indicates to me that it's just a renamed ISO.  Try to mount it with the following commands:```
sudo mkdir /media/iso
sudo mount -o loop /path/to/image.000
```
If that works, then it's just a renamed ISO, and you can change the extension to .iso and burn it using k3b.  (But make sure you unmount it first with "sudo umount /media/iso".)

---

### Post by habtool on 2009-01-25
partimage cloning also uses .000 extension.

---

