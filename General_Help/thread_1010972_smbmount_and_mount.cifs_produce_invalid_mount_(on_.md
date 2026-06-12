---
title: "smbmount and mount.cifs produce invalid mount (on VMWare)"
date: 2008-12-14
forum: General Help
---

### Post by oranoran on 2008-12-14
I have Ubuntu server 8.04.1 running on VMWare player, with VMWare tools installed.

I run the following to get an SMB mount running:
sudo smbmount //mylaptop/Users/me/shared /mnt/shared -o username=DOMAIN\\me,uid=me,gid=me

The mount appears to be successful, but when running "ls -l" on /mnt the following line shows, with question marks instead of permissions:
d????????? ? ?    ?       ?                ? shared

Trying to further access this mount in any way fails. For example, "ls /mnt/shared" yields:
ls: cannot access /mnt/shared: No such file or directory

umount does work ok and removes this mount properly. repeating the same mount with mount.cifs instead of smbmount fails the same way.

The samba version is 3.0.28a-1ubuntu4.4 - it's not the latest, but higher versions did not install properly on my machine (apt-get failed on some unsatisfied dependencies).

any ideas?

---

### Post by oranoran on 2008-12-18
Same happens in Xubuntu 8.04.1 even though here there was no problem while installing smbfs.

---

### Post by oranoran on 2008-12-18
Aha!
I played a little more with sharing permissions on the Windows side, and this just went away. Used "advanced sharing" in Vista to get the directory exported, as opposed to the regular share.

---

