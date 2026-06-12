---
title: "Places &gt; Computer - File Browser Help!"
date: 2006-08-10
forum: Desktop Environments
---

### Post by GoLoGo on 2006-08-10
Hello,

I am having problems **displaying** 3 partitions that are mounted and have entries in the fstab respectively. I want to know how I can modify my Computer File Browser window, so it will display ALL my partitions, not just my NFTS and the core filesystem. The 3 partitions that are not displaying are each 50GB ext3 partitions, /dev/hdb5, /dev/hdb6 , /dev/hdb7, I have tried IRC and another thread, and searched the documents, but I cant find anything that can help me solve my problem. I want to be able to display those 3 above ext3 filesystem partitions in the Places > Computer - File Browser window, thanks.

Any help is appreciated. Thank you in advanced.

---

### Post by meng on 2006-08-10
Go to /home/shared/Owen and Add to Places (I think that's the right term, it's the equivalent of a Firefox bookmark).

---

### Post by GoLoGo on 2006-08-11
Thats not what I want, I wan my partitions to show NOT in a panel, but in the actual window, the Places > Computer - Filebrowser window. I still havent found out how to add em, or display em. Someone please give me some more feedback, thanks.

---

### Post by meng on 2006-08-11
Okay I understand your request, and also why you previously complained about your partitions "disappearing".

What you'll need to do is create new folders within your media folder.
e.g.
sudo mkdir /media/Owen
sudo mkdir /media/backup2
sudo mkdir /media/backup3

and change the mount points from /home/shared/Owen to /media/Owen, etc.

then the filesystems will appear in the window as you want them.

Almost anything can be solved once the question is clear.

---

