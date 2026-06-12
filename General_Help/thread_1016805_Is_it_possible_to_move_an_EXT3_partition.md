---
title: "Is it possible to move an EXT3 partition?"
date: 2008-12-20
forum: General Help
---

### Post by speedsix on 2008-12-20
The Gparted I tried (I forget from where, i.e may have been a bit older) but this didn't support moving EXT3.

I've heard so many different answers for this and I wonder if anyone has successfully moved an EXT3 partition and with what?


Thanks

---

### Post by M4rotku on 2008-12-20
Do u mean to move it from one hard drive to another or to move it left or right in gparted?

---

### Post by Elfy on 2008-12-20
yes - gparted wil do that, but if you try and do so inside your install the partitions will be locked probably.

You need to use a livecd - either a os install one or a partiton editor like gparted or partedmagic

---

### Post by bodhi.zazen on 2008-12-20
In addition to using a live CD you sometimes need to do things in steps as opposed to all at once. IE make space, apply changes, then move ...

---

### Post by speedsix on 2008-12-20
I basically have some free space at the beginning of my drive before the EXT3 partitions so I need to move them to the beginning filling the free space and then expanding them.

---

### Post by Elfy on 2008-12-21
Yea gparted will do that, select the partition in the top pane and move it - then apply.

Be aware that it could take a long time to do depending on the sizes of the partitions to move.

I would also move each singly rather than give gparted a list of edits to deal with.

---

