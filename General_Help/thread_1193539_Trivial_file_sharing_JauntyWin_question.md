---
title: "Trivial file sharing Jaunty/Win question"
date: 2009-06-21
forum: General Help
---

### Post by Icky_Ev on 2009-06-21
Have LAMP/SAMBA server with 2 drives. 

The 500GB drive is the one running the show and is not shared. 

The 1.5TB drive will be the shared drive. Clients are Win boxes of various flavors, 2000 forward. It will be just one giant partition due to the **large** file sizes we're working with. 

There seems to be a lot of conflicting thoughts on what the best format to use for the shared drive. 

1) NTFS ("Windows format files should be on a Windows-formatted drive")
2) ETX3 ("It's better to run Linux format with Linux. The Window boxes won't know and won't care")

What's the best answer- or does it really not matter? :KS

---

### Post by Cheesemill on 2009-06-21
As you'll be sharing over the network with Samba then the Windows boxes won't know and don't care what filesystem the disk uses. Go with ext3 as it's native to the OS that will be running Samba.

---

### Post by Icky_Ev on 2009-06-21
> **Cheesemill said:**
> As you'll be sharing over the network with Samba then the Windows boxes won't know and don't care what filesystem the disk uses. Go with ext3 as it's native to the OS that will be running Samba.

Thank you very much! That was the answer I was hoping for, and makes my life a heck of a lot easier.

---

### Post by blueridgedog on 2009-06-21
As an additional input, the Linux box will be strained to use any non-ext file system for the task as NTFS is meant for convenience, not production.  If the files are important and the "server" is tasked with protecting them, then the only choice is ext3 vs ext4.  Given the "newness" of ext4, ext3 is the logical selection.

---

