---
title: "Username not containing '.'"
date: 2005-12-14
forum: General Help
---

### Post by Fergal1982 on 2005-12-14
Is there any reason that Ubuntu wouldnt accept a username with a period in it? when installing it refused to accept firstname.lastname.

Thanks
Fergal

---

### Post by Sutekh on 2005-12-22
Quoting 
```
man chown
```
```
... If the user name is followed by a colon or dot and a group name 
(or numeric group ID), with no spaces between them, [b]the group ownership 
of the files is changed as well[/b]. If a colon or dot but no group name follows 
the user name, that user is made the owner of the files and the group 
of the files is changed to that user&#8217;s login group.  If the colon or dot and 
group are given, but the user name is omitted, only the group of the 
files is changed; in this case, chown performs the same function as chgrp.
```
Long story short, you would have some issues if you ever tried to chown (change ownership) files using a user name with a '.' in it.  

For example if some user called **john.smith** tried to take ownership of **/<some_files>**, things would get messy

```
chown john.smith /<some_files>
```
Would change the ownership of /<some_files> to the user **john** and the **group **ownership to the group **smith**.

It wouldn't give ownership of /<some_files> to the user john.smith

---

