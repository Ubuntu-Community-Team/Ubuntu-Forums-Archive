---
title: "Samba + folder names = Confused as heck!"
date: 2008-12-21
forum: General Help
---

### Post by Darth_tater on 2008-12-21
I desperately need help.  Below are two thumbnails, one is from my ubuntu box and the other is from my xp laptop.  Note that they are of the same folder, but the XP box has funky names for most of the folders and the ubuntu box does not.

Logically, it must be samba that is screwing up the names.  My question is why and how can I fix this?

Thanks for your help


my XP box as it sees the samba share:

[URL="http://img132.imageshack.us/my.php?image=xpph0.png"] [IMG]http://img132.imageshack.us/img132/5518/xpph0.th.png[/IMG]
[/URL]


and here is how the *SAME* folder is seen by a root nautilus on my ubuntu box:

[[IMG]http://img166.imageshack.us/img166/1202/ubuntufb7.th.png [/IMG]](http://img166.imageshack.us/my.php?image=ubuntufb7.png)

Thanks to ImageShack for [Free Image Hosting](http://imageshack.us)


EDIT::::

Something just occurred to me.  The only folder that does not have a weird name also has a short name – its only 18 characters long.  Is samba automatically renaming the folders if they are too long for the samba protocol?  How can I fix this, as they folder names cannot be changed, or else, my podcast client will not work!

---

### Post by kidders on 2008-12-22
Hi there,

Your directories are being given randomly generated names because the real ones contain characters not supported by Windows.

---

### Post by Darth_tater on 2008-12-22
mm, that would explain the behavior.  I use rhtymbox as my podcast client, and i *can not* change the folder names...

now i have to figure out a different podcast client - one that will let me customize the location and names of the folders where the files are saved.

---

