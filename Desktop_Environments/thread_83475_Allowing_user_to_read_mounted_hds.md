---
title: "Allowing user to read mounted hds?"
date: 2005-10-28
forum: Desktop Environments
---

### Post by Temple on 2005-10-28
I am trying to open my hdb1 (where my music files are) but everytime I try to open it, it says:

"You do not have the permissions necessary to view the contents of "hdb1"."

I tried using root to give my user access to view contents, but I can't. Any help on how I can do this? Thanks

---

### Post by jasmuz on 2005-10-28
Open a terminal and type sudo mkdir /media/Music and then 
sudo gedit /etc/fstab

And add this to the end

/dev/hdb1       /media/Music  ntfs    nls=utf8,umask=0222     0       0

Save and close.
Now type sudo mount -a (wich will reload the filesystems without mounting) and now you should have your partition mounted at every boot in /media/Music

---

