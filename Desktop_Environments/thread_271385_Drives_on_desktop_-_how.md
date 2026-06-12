---
title: "Drives on desktop - how?"
date: 2006-10-04
forum: Desktop Environments
---

### Post by Fingerlakes_Dave on 2006-10-04
How do I put a shortcut (?) to a drive on my  desktop.
These are my actual drives or partitions.  Most are Windows primary or logical partitons.

 I can access most in the system section, yet even there I can't get one to give me access.

 I hvae all my documents and programs on a seperate hard drive from my OS hard drive.  (Can't tell I'm an MS user, can you? ;) )

 Help appreciated

---

### Post by Ramses de Norre on 2006-10-04
```
gconf-editor /apps/nautilus/desktop/
``` and check volumes_visible.
Now all volumes mounted in /media will show up on the desktop automatically.

If you want to mount them somewhere else: ```
ls -s mounpoint  ~/Desktop/link_name
``` to create a symlink.

---

### Post by Fingerlakes_Dave on 2006-10-04
> **Ramses de Norre said:**
> ```
gconf-editor /apps/nautilus/desktop/
``` and check volumes_visible.
Now all volumes mounted in /media will show up on the desktop automatically.

If you want to mount them somewhere else: ```
ls -s mounpoint  ~/Desktop/link_name
``` to create a symlink.

 Thanks.

---

### Post by Fingerlakes_Dave on 2006-10-04
OK: tried gconf-editor /apps/nautilus/desktop

 1) I get an error message: incorrect command with ending / or similar. ??

 2) I then figured out I need to be in /apps, then /nautilus, then desktop.

 volumes_visible is already checked.  I still have only my C drive (windows xp ntfs) showing on my desktop.

  How do I mount my other drives/partitions on the desktop?

  And why are they not just detected by ubuntu?  :confused:

---

### Post by Ramses de Norre on 2006-10-05
Are the drives mounted? If so mount them in /media, if not: You'll have to add them in /etc/fstab.
I can tell you how if you give me some more info, like the filesystem and the output of sudo fdisk -l.

EDIT: and the last "/" in the gconf-editor command shouldn't be there =)

---

### Post by Fingerlakes_Dave on 2006-10-05
Thanks for trying.

  I have no idea why my drives didn't mount during install. Nada. :confused: 

  I found a turorial in another post (link) on how to mout drives.

  I think (my first mistake) I have the drives mounted.  I can at least access my music and photos now and documents.

  My understanding is I would have to save to the linux partition to save using a linux app?  Can't save to NTFS?

  Thanks again for trying.

---

### Post by Ramses de Norre on 2006-10-05
No, you can't write on ntfs.
And do you have your shortcuts on the Desktop now? If you show me the output of these commands I'll tell you how to get them: ```
cat /etc/fstab
sudo fdisk -l
```

---

### Post by Fingerlakes_Dave on 2006-10-05
> **Ramses de Norre said:**
> No, you can't write on ntfs.
And do you have your shortcuts on the Desktop now? If you show me the output of these commands I'll tell you how to get them: ```
cat /etc/fstab
sudo fdisk -l
```

  Yes thanks.  As I said, I found a complete set of instructions
in another post. And while he doesn't like his drives on the desktop (and my tastes could change also), I was able to change things enough to get them in /media/ and therefore on the desktop.

 Actually, the only one **NOT** on the desktop is root.  I'm assuming taht is for a reason. ;)

---

### Post by Ramses de Norre on 2006-10-05
Ow perfect, and you can get root on your desktop if you want;) 
In fact there is no real harm in it because you open it as regular user anyway so you don't have write premissions.

This will do it if you want it: ```
ln -s / ~/Desktop/root
```

---

