---
title: "How to make a folder on my external drive unlocked?"
date: 2009-03-28
forum: General Help
---

### Post by villainy on 2009-03-28
I have all of my music on my external hard drive. I put all of it in a folder called 'Music' and it's locked (the icon is over the folder) and I have no idea how it got that way. Sometimes I can download to the folder and, sometimes I can't. Usually from Firefox, I can't write to the folder but with Deluge, I can. Is there anyway to make this folder unlocked or all folders on my external unlocked for that matter.

I dualboot with Vista and my external has no problems with writing in Vista.

Thanks for any help :)

---

### Post by Chemical Imbalance on 2009-03-28
sudo chmod -R u=rwx /path/to/the/folder/here

---

### Post by villainy on 2009-03-28
> **Chemical Imbalance said:**
> sudo chmod -R u=rwx /path/to/the/folder/here

Thanks.

I tried this in terminal and in root and I get this:

mike@mike-desktop:~$ sudo chmod -R u=rwx /media/My Book/Music
[sudo] password for mike: 
chmod: cannot access `/media/My': No such file or directory
chmod: cannot access `Book/Music': No such file or directory

Seems as if it doesn't like the space, but that's what the path is. Any help on this? Is there something I should put in between My and Book?

Thanks.

---

### Post by arki on 2009-03-28
rename "My Folder" to "My.Folder".

---

### Post by ad_267 on 2009-03-28
It doesn't like the space in the path. Use:
```
sudo chmod -R u=rwx /media/My\ Book/Music
```
or:
```
sudo chmod -R u=rwx "/media/My Book/Music"
```

---

### Post by villainy on 2009-03-28
Thank you! That worked perfectly.

---

