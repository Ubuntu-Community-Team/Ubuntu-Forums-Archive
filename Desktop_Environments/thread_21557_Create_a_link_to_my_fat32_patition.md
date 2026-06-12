---
title: "? Create a link to my fat32 patition ?"
date: 2005-03-22
forum: Desktop Environments
---

### Post by carlc on 2005-03-22
I would like to create a link to my fat32 partition in my home directory to save time. I have figured out how to right click and create links to regular files and folders but this option is not available on the mounted fat32 partition.  ](*,)

---

### Post by telmo on 2005-03-22
If you mount the partition under /media instead of /mnt you'll be able to create a link. (i think you need to do it as root) Then just copy it to your home folder. That's what i did.

---

### Post by carlc on 2005-03-22
OK, that makes sense. It is mounted as /media but I was not trying to create the link as root.

---

### Post by telmo on 2005-03-22
Don't worry. You'll still be able to write on it as user. ;)

---

### Post by carlc on 2005-03-22
I have never created a link using the command line.
Would it look something like this?

sudo ln -s /media/filez/ /home/carlc/filez/

---

### Post by bored2k on 2005-03-22
[QUOTE=carlc]I have never created a link using the command line.
Would it look something like this?

sudo ln -s /media/filez/ /home/carlc/filez/[/QUOTE]
 Why the sudo ? and wh dont you just add a bookmark to /media/filez o_.

---

