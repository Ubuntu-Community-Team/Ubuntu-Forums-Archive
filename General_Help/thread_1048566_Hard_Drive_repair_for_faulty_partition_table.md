---
title: "Hard Drive repair for faulty partition table"
date: 2009-01-23
forum: General Help
---

### Post by tripdr on 2009-01-23
I have a hfs hard drive that on the Mac will not mount, but does show up in the terminal from diskutil same as fdisk

On ubuntu live cd it shows up in fdisk -l and sometimes shows up as a file system with all directories intact. But trying to copy over files via the filesystem folder view to a different HD does not work. It starts and then craps out. I will have error logs later on. 

Right now it's having ddrescue slowly run on it to try and save something. But the fact that the filesystem will load randomly on reboot gives me hope that I can run a repair of some sorts after ddrescue back up. 

Might you have a suggestion that I could use to try and repair it? Or what steps I should take to tests symptoms from it?

---

### Post by cmnorton on 2009-01-24
I suggest you boot with the live CD; unmount the drive if it is somehow mounted; and then run fsck on the unmounted drive.

---

