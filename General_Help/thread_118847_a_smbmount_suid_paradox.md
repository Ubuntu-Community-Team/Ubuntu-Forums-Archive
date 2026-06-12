---
title: "a smbmount suid paradox"
date: 2006-01-17
forum: General Help
---

### Post by lapsey on 2006-01-17
[edit: couldn't change the title.... hmm]


In the absence of a good gnome samba mounter, and because fstab is a royal pain in the butt; i have taken to keeping a folder on my desktop with a launcher in it. 

Double clicking that launcher mounts a samba share to that folder, hiding that launcher until it is unmounted.
Here is how to get this going...

Installing the software and setting permissions ----------------------------------

apt-get install smbfs
sudo +s /usr/bin/smbmnt

(and just in case it is suid root, do sudo -s /usr/bin/smbmount)

note: make sure not to confuse "smbmnt" with "smbmount" :)

----------------------------------------

in the launcher, put:

smbmount //"your samba server machine's hostname or IP address"/"the samba share" "location of the folder with the launcher in it" -o "all the lovely samba options as found under man smbmount"

and there you go!

---

### Post by geco on 2006-09-11
> **lapsey said:**
> [edit: couldn't change the title.... hmm]


In the absence of a good gnome samba mounter, and because fstab is a royal pain in the butt; i have taken to keeping a folder on my desktop with a launcher in it. 

Double clicking that launcher mounts a samba share to that folder, hiding that launcher until it is unmounted.
Here is how to get this going...

Installing the software and setting permissions ----------------------------------

apt-get install smbfs
sudo +s /usr/bin/smbmnt

(and just in case it is suid root, do sudo -s /usr/bin/smbmount)

note: make sure not to confuse "smbmnt" with "smbmount" :)

----------------------------------------

in the launcher, put:

smbmount //"your samba server machine's hostname or IP address"/"the samba share" "location of the folder with the launcher in it" -o "all the lovely samba options as found under man smbmount"

and there you go!
maybe you mean 
sudo **chmod** +s /usr/bin/smbmnt
and
sudo **chmod** -s /usr/bin/smbmount
???

---

