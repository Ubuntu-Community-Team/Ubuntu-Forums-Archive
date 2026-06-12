---
title: "Steam games outside /home"
date: 2015-05-04
forum: Gaming &amp; Leisure
---

### Post by slepowidzacy on 2015-05-04
Hi, I'm about to buy a second drive to my computer. I'm going to have my music, photos, videos on my old hdd formatted entirely as an /home. But I found out that steam writes data in /home and wouldn't like to use a slow and 'singing' hdd for gaming. (The witcher is coming :) ). Is there any way to change the path to "/" ? Will steam run properly on root privilleges?

---

### Post by TheFu on 2015-05-04
Don't do that. root is for administration, not running games.  Running end-user programs as root is a huge security issue and can easily lead to a broken system.

If you know the directories where steam wants to write data, you can use **symbolic links** to have the data written anywhere, on any partition you prefer, provided the user permissions are correct. 

Linux is a multi-user OS from the ground up and file/directory permissions are at the core of the security model.  Create a /games/{userid} directory on whatever disk you like and make the owner the userid you want. Wikipedia will explain symbolic links.  File permissions are a little harder to understand, but there are tutorials. A web search for "linux permissions tutor" will find some.

---

### Post by slepowidzacy on 2015-05-05
Thanks for quick and explaining answer to a linux n00b. :D

---

### Post by elaurens on 2015-05-09
Hey slepowidzacy,

As TheFu wrote I would use symbolic links to solve your "issue". If I were you I'd just leave /home on your SSD and create a symbolic link to the Documents, Downloads, Music, Pictures and Videos folders which you created on your HDD. This is how I did it:

mount /dev/sda1 (HDD) on /mnt/DATA
```
ln -s /mnt/DATA/Documents ~/Documents
ln -s /mnt/DATA/Downloads ~/Downloads
ln -s /mnt/DATA/Music ~/Music
ln -s /mnt/DATA/Pictures ~/Pictures
ln -s /mnt/DATA/Videos ~/Videos

```

Works very well for me ;)

---

### Post by TheFu on 2015-05-09
Shouldn't need **sudo** for symlinks if the file/directory permissions are correct.

---

### Post by elaurens on 2015-05-09
> **TheFu said:**
> Shouldn't need **sudo** for symlinks if the file/directory permissions are correct.

True. Bad habit of me overusing sudo for what I consider to be safe operations.

---

### Post by TheFu on 2015-05-09
> **elaurens said:**
> True. Bad habit of me overusing sudo for what I consider to be safe operations.

Actually, it can be dangerous to use sudo improperly - especially with things in $HOME. I've had to help a few users after they did things that took over key files as root in their HOME and they couldn't run any gnome programs anymore due to it.

---

### Post by elaurens on 2015-05-09
Edited my first post in this thread to avoid other ppl making the same mistakes I make :)

---

### Post by oldfred on 2015-05-09
Someone posted a long time ago a mini-script to mount them all. Mine are mounted at /mnt/data so that is what example below uses.

 #Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

---

