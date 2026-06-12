---
title: "Best Format?"
date: 2006-03-04
forum: Desktop Environments
---

### Post by OffHand on 2006-03-04
Hi,
I am about to re-install Ubuntu.
What format does it need to be to be able to share the disk with windows.
Ext 2??
And for my data discs? Fat 32 the way to go? Does making a disc fat32 have any negative drawback in windows? 
Greetings, 
Subsonic

---

### Post by incubus on 2006-03-04
subsonic,

Read this thread, especially the last posts:
[http://ubuntuforums.org/showthread.php?t=139423&highlight=fat32]("http://ubuntuforums.org/showthread.php?t=139423&highlight=fat32")

incubus

---

### Post by oscar on 2006-03-04
For your / linux partition it is probably best to go ext3.
There are programs that allow you to browse ext3 partitions from windows.

For your data disks (I assume you want to share them between both windows and linux) probably fat32 as it can be read and written by both linux and windows. Again there are tools that let you read and write ext3 for windows but it's not as nice as 'out of the box' support. I think one of the main disadvantages of fat32 is that is easily becomes fragmented.

---

### Post by OffHand on 2006-03-04
Thnx guys  :)

---

### Post by akiro.yamamoto on 2006-03-04
I would use ext3 for sharing with windows. You can install a driver into windows that
allows read / write access to ext2 / 3 partitions.
Personally I prefer to go that way as you have your files on a more robust file system
than the old fat32 scheme, and it is a journaled file system too :)

---

