---
title: "File is not deleting !!"
date: 2009-03-20
forum: General Help
---

### Post by kushal.7 on 2009-03-20
Hi frnds,

I am unable to delete a file. when i tried to delete a file then it shows following error: 

Unable to trash file: Permission denied

How do i delete the file ??.....

---

### Post by taurus on 2009-03-20
Where is that file, in your $HOME?  Are you the owner of that file?

---

### Post by kushal.7 on 2009-03-20
> **taurus said:**
> Where is that file, in your $HOME?  Are you the owner of that file?

the file is in pen drive. actually it is a windows virus !!!

---

### Post by taurus on 2009-03-20
Is your pen drive a fat32 filesystem?  Post the outputs of these commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```
Otherwise, run nautilus with root privilege if you want to remove that file.

```
gksudo nautilus
```

---

### Post by bruno9779 on 2009-03-20
Code:

sudo -rm /filename

in the pendrive folder should work too

---

### Post by kushal.7 on 2009-03-20
running nautilus with root privilage works, thanks !!

---

### Post by taurus on 2009-03-20
> **bruno9779 said:**
> Code:

sudo **[COLOR="Red"]-[/COLOR]**rm **[COLOR="Red"]/[/COLOR]**filename

in the pendrive folder should work too

Actually, it won't work because you have an extra / in front of the filename.  If you are in the directory where filename it, then just use filename by itself.  Otherwise, it will look in / for filename which wouldn't be there.

---

### Post by Rallg on 2009-03-20
EDIT: I removed the advice I gave here, because it was solved by another post, above.

---

### Post by kushal.7 on 2009-03-20
> **rallg said:**
> edit: I removed the advice i gave here, because it was solved by another post, above.

thanks !!

---

### Post by bruno9779 on 2009-03-20
> **taurus said:**
> Actually, it won't work because you have an extra / in front of the filename.  If you are in the directory where filename it, then just use filename by itself.  Otherwise, it will look in / for filename which wouldn't be there.

ooops typo

---

