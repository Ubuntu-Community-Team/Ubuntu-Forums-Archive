---
title: "changing permissions"
date: 2005-06-24
forum: Desktop Environments
---

### Post by lance_delacroix on 2005-06-24
How do I change permissions on existing files?  I have a FAT partition with all my data files that I created in Windoze.  I can read everything okay with Kubuntu, but I cannot write to those files or write new files to the partition.

I tried changing permissions using kdesu conqueror, and while it SEEMS like I am changing them, I am not.  I don't get any error messages or anything, but when I go back and check, the permissions have not changed.

Any tips?

Thanks.

---

### Post by z-two on 2005-06-24
What you want to do is set the permissions when it is mounted.
First open you /etc/fstab file in a text editor and find the entry for the partition you want to change.
Then in the options bit for that row add umask=000. I expect you'll find that at the moment it contains umask=some other number.
Make sure you backup your fstab file first, and be very careful as your pc might not boot if you edit something in there wrongly.

Anyway I think that should work for you, if you want more detailed instructions just ask.

---

### Post by lance_delacroix on 2005-06-24
[QUOTE=z-two]What you want to do is set the permissions when it is mounted.
First open you /etc/fstab file in a text editor and find the entry for the partition you want to change.
Then in the options bit for that row add umask=000.[/QUOTE]

Thanks for your help.  At the moment, the entry is:

dev/hda6       /data           vfat    defaults        0       0

Should I replace "defaults" with the string you gave?  Will I have to add anything else?

---

### Post by desdinova on 2005-06-24
One thing is that FAT has no idea of permissions as it is not a linux native filesystem - that said mind, you can set up so you can write to that partition - however you can't make files read-only etc on that partition

If you change "default" to users however you can write there

users  Allow every user to mount and unmount the file system.  

(if you "man mount" from a console or man://mount from konqueror - you'll get the help)

---

### Post by lance_delacroix on 2005-06-24
Okay, I tried both of these in /etc/fstab:

dev/hda6 /data vfat defaults, umask=000 0 0

dev/hda6 /data vfat users 0 0

Neither made any difference.

Any other ideas?

---

