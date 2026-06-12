---
title: "reducing linux partition"
date: 2006-08-15
forum: Desktop Environments
---

### Post by uzusan on 2006-08-15
I have a ext3 partition that im using as my main partition on my ubuntu install an im looking for a way of reducing it.

Its sitting at 187gb and i want to reduce it to 87 and create a 100gb fat32 drive so i can share music etc between my ubuntu install and my windows install.

any ideas how i can do this? ive tried QTparted but the resize option is grayed out.

---

### Post by doris.houng on 2006-08-15
Try using the [Gparted Live CD](http://gparted.sourceforge.net/livecd.php).  :)

---

### Post by uzusan on 2006-08-15
hmm. any way i can do it without a livecd? im out of blank cd´s at the moment unfortunatly.

(if i cant get it to work, ill get some blank cd´s soon).

---

### Post by az on 2006-08-15
> **uzusan said:**
> hmm. any way i can do it without a livecd? im out of blank cd´s at the moment unfortunatly.

(if i cant get it to work, ill get some blank cd´s soon).

You cannot have any mounted partitions on the drive you partition.  That's why you need to run a live cd.

---

### Post by uzusan on 2006-08-15
> **azz said:**
> You cannot have any mounted partitions on the drive you partition.  That's why you need to run a live cd.

ahh. makes sense.

ill see if i can get some blank cds from somewhere.

---

### Post by uzusan on 2006-08-16
Cheers everybody for your help, i loaded the gparted livecd last night (i found a blank cd i had overlooked) and it worked brilliantly. (the resizing took quite a while, but i expected that).

---

