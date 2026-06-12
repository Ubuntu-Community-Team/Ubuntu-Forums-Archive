---
title: "delete partition add to primary"
date: 2007-05-27
forum: Desktop Environments
---

### Post by justincormier on 2007-05-27
is it possible to delete a partition and add it to your primary filesystem?

---

### Post by sonofusion82 on 2007-05-28
using gparted, you can delete the partition then resize to expand you primary partition. but i guess it depends the type of filesystem of the primary partition. as always, backup your data. recently i discovered clonezilla for harddisk imaging and it works well for me.

---

### Post by justincormier on 2007-05-28
thanks alot ill give that a try and see what happens!

---

### Post by justincormier on 2007-05-29
ok i have gparted but cannot change anything... anyone got any ideas?

---

### Post by merlinus on 2007-05-29
Are you booting from the Gparted live cd?

-merlin

---

### Post by justincormier on 2007-05-29
nope i installed Gparted..
 i installed Ubuntu and installed it on a small partition, cause im an idiot.  I have another partition that has 6 gigs that i would like to put to my filesystem and it wont let me edit it into it.  if that makes sense...

---

### Post by merlinus on 2007-05-29
You cannot change the size of a mounted partition, and you cannot unmount the ubuntu partition whilst you are using it.

So download the gparted live cd, and burn it as a disk image.  Then boot from it, and see if can you do the re-sizing.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Good luck!

-merlin

---

