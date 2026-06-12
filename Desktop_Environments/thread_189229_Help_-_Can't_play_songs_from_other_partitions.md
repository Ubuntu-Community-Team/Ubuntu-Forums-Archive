---
title: "Help - Can't play songs from other partitions"
date: 2006-06-04
forum: Desktop Environments
---

### Post by gizzmoe on 2006-06-04
I recently moved to Dapper from Breezy and now I'm unable to play mp3's that I have on a shared fat32 partition. I can browse the partition...and read and edit text files and whatnot...but it absolutely will not play songs from the drive. 

If i copy them to the partition that linux is installed on, they work just fine. But the whole point of having my music on a shared partition is so i don't waste space having one copy on my windows partition and one on my linux partiton.

I'm wondering if this would have anything to do with the way Dapper handle's partitions? They're owned by root, but have a group of 'plugdev'....so everyone who needs access to the partitions needs to be in that group....but i'm using the default account which is in that group so i shouldn't have any issues, right?

Any ideas would be great!

---

### Post by gizzmoe on 2006-06-05
bumping this up to try to get more views

I've been googling this since i've posted and still no success. Anyone know what might be happening here? I can't play these files with XMMS or AmaroK.

---

### Post by gizzmoe on 2006-06-05
I figured out my issue but I don't know how to solve it.

Lots of programs don't understand the 'system:' protocol that ubuntu uses. If i travel to the directories using /media/hda# it works fine.

Any way to disable the system: protocol so that when i go to the storage media section and double click a drive it will open as /media/hda1 or /media/hda2?

---

### Post by gizzmoe on 2006-06-05
If anyone bothers to read down this far:

This is a KDE specific issue dealing with the KIO Slaves.. To fix it, you have to put a %f after the command that starts the application in the shortcut files (desktop config files).

I <3 Google ... even if it did take me all day to finally find the answer.

---

