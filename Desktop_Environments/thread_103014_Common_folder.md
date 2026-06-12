---
title: "Common folder"
date: 2005-12-13
forum: Desktop Environments
---

### Post by entner on 2005-12-13
I want to share a folder with other users on the same computer, where everyone can create, change, delete every file he/she or even someone else created.

I suppose I have to mount a folder with special options to achieve this, or is there another way?

Thanks,
Burt

---

### Post by earobinson on 2005-12-13
you should be able to open up the folders propeties and set its permissions that way. or you could use chmod (man chmod for more info not on ubunut right now :()

---

### Post by entner on 2005-12-13
Hmm, seems not to work 100%.

I set 777 and GID and UID and Sticky to the folder (7777).
Everyone can then create a file inside, but when I edit it, he cannot delete it anymore.

---

### Post by earobinson on 2005-12-13
did you change the permisions, each file will have its own permissions. Im unsure of a way that you can make a folder that forces permisions on its contence. So each file needs to have the permisions set.

If i find a better soultion ill let you know.

---

### Post by entner on 2005-12-13
That is the thing I am not sure if it is possible with the regular Unix file permission system.

Creating a folder where everyone can do everything inside, no matter what.  So that for example a family can share a folder where everyone can copy, modify, delete whatever file is inside.

---

### Post by earobinson on 2005-12-13
It is possiable. Make all users part of a group, and set every file permisions so any uses in that group can read write and run. It is just that the owner of each file needs to set the permisions. I do not know of a way that you can make a folder that forces the permisions of the files inside it, but if I find one ill let you know.

---

### Post by entner on 2005-12-13
[QUOTE=earobinson]...It is just that the owner of each file needs to set the permisions. ...[/QUOTE]

That is exactly what I want to avoid (thinking of my mother-in-law)

---

### Post by earobinson on 2005-12-13
How many people need to read / write to this folder?

You could use root to change the permisions yourself, Is this a seperate HD? If so you could also format it as fat32 and mount It so all users had read write permisions (Fat 32 dose not support unix file permisions so every user will be able to modify any files on that HD)

There also may be a way to change what the default permisions of a file created by a user are, but that would affect all her files not just the filles in this shared directory.

---

### Post by entner on 2005-12-13
FAT32 was also one of the first things which came to my mind.  But I want to avoid using an extra partition.  

I can imagine that there is a way to mount a folder via bind into another folder and set the mount options to some miraculus values to do the trick.

---

