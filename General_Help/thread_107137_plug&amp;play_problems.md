---
title: "plug&amp;play problems"
date: 2005-12-22
forum: General Help
---

### Post by kervel on 2005-12-22
hello,

when i insert an USB stick (i'm using kubuntu breezy), it seems like there are too many plug and play handlers:
         - konqueror opens at /media/sda, and the auto-mounting fails because:
         - somehow, the USB stick is already mounted at /media/256MB
         - in adition to this, a dialog appears asking what i want to do

for CDroms the same happens, and for music CD's, KSCD opens immediately, and the "do you want to play" dialog appears in addition to this.

i guess this is a configuration problem related to upgrading from hoary to breezy. Someone knows how i could solve this? which package i could reconfigure/reinstall ?

thanks,
frank

---

### Post by GoldBuggie on 2005-12-22
[http://ubuntuforums.org/showthread.php?t=90457](http://ubuntuforums.org/showthread.php?t=90457)

---

### Post by kervel on 2005-12-22
thanks !

now only the popup dialog appears (no more konq, no more automount).
only one problem remains now:

when i click "browse", konqueror opens, and apparently successfully mounts the volume, but fails to show the files (the wheel keeps running). when i hit refresh, konqueror apparently tries to mount the same volume again, which fails ("already mounted")

oh, and i'm using the KDE 3.5 packages

---

### Post by GoldBuggie on 2005-12-23
Well I did have that problem some time back. Don't have it anymore...don't remember what it was specifically that undid the prob...but to configure what kde does you can go to kcontrol->Peripherals->Storage Media
I've set it to do nothing on all media and under advanced i don't have "enable medium app sutostart after mount" enabled

also **groups hal** should return [B]hal : hal cdrom floppy plugdev

[/B]

---

