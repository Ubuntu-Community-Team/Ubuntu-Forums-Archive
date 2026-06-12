---
title: "Permissions issue"
date: 2009-05-22
forum: General Help
---

### Post by CynicalPsycho on 2009-05-22
Ok, so i installed jaunty ubuntu onto my new HDD, and it seems be workin fine, aside from that it's overly controlling...

when i try to download something into my tmp folder i get an error saying that it cannot be done...

I tried a chown as root
```
chown myusername /tmp
```
but that didn't seem to work, and the owner of my tmp is still root.

the problem started when i tried to download a .deb and it gave me this error:

> /tmp/ubuntu-tweak_0.4.7.1-1~jaunty1_all.deb could not be saved, because you cannot change the contents of that folder.
now, i know i could just download it somewhere else, but that's not the point...

I guess my question boils down to 2 things:
How do I change the owner of that file?
and How do I execute programs as root from the GUI?

---

### Post by baseface on 2009-05-22
create a tmp dir in your home directory and use that.
also, to change ownership of a file or directory that you dont already own, you have to be root to do it.

---

### Post by CynicalPsycho on 2009-05-22
> **baseface said:**
> create a tmp dir in your home directory and use that.
also, to change ownership of a file or directory that you dont already own, you have to be root to do it.

did you even read my post?

---

### Post by oldos2er on 2009-05-22
/tmp is meant for system use, which is why it's owned (and should remain owned) by root.

---

### Post by Iowan on 2009-05-22
> **CynicalPsycho said:**
> did you even read my post?*Ordinarily*, "being root" on Ubuntu means using **sudo**. 
*Ordinarily*, lack of **sudo** in a command line - such as ```
chown myusername /tmp
``` *suggests* the command was not executed as root... although I realize there are ways to drop into "root mode" that don't require preceeding each command with **sudo**.

---

### Post by asmoore82 on 2009-05-22
what are the permissions on your /tmp?
```
ls -ld /tmp
```

it *should* be:
```
drwxrwxrwt 24 root root 4096 2009-05-22 21:32 /tmp
```

to restore this^:
```
sudo chown 0:0 /tmp
sudo chmod 1777 /tmp
```

---

