---
title: "xp file recovery"
date: 2009-01-05
forum: General Help
---

### Post by chrimaliz on 2009-01-05
I'd like to use the linux side of my dual boot xp/ubuntu machine to restore a folder w/ 40gigs of data in it. 

i have an external hdd w/ an ntfs partition ready to go if that would make it any easier. 

thanks for any help.

---

### Post by iaculallad on 2009-01-05
> **chrimaliz said:**
> I'd like to use the linux side of my dual boot xp/ubuntu machine to restore a folder w/ 40gigs of data in it. 

i have an external hdd w/ an ntfs partition ready to go if that would make it any easier. 

thanks for any help.

Try looking for [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec").

---

### Post by bumanie on 2009-01-05
You have the options of testdisk, photorec or using ntfsprogs and use ntfsundelete. You do need to save the information to another partition or device, otherwise you risk overwriting data you are trying to save. > sudo apt-get install ntfsprogsthen sudo ntfsundelete <partition name> eg. /dev/sda1. Here's the [man page]("http://http://man.linux-ntfs.org/ntfsundelete.8.html") for ntfsundelete There is also possibility with sleuth kit and autopsy

---

### Post by chrimaliz on 2009-01-05
What do you think would be easiest for this noob? gui preferred. thanks!

---

### Post by bumanie on 2009-01-05
Photorec and testdisk (written by the same person) have a very basic GUI, ntfsundelete is command line. Read the tutorials on the testdisk site for both testdisk and photorec. Testdisk should work if the fiesystem is OK if the filesystem is wrecked, photorec is better - read the documentation and decide which one suits your exact problem the best.

---

### Post by blazemore on 2009-01-05
File recovery isn't for the "noob" to be honest.
TestDisk is by far the most powerful, there are a few tutorials on here which can probably help you.

---

