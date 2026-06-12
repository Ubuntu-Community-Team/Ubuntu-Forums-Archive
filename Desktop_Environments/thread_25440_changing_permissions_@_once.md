---
title: "changing permissions @ once"
date: 2005-04-10
forum: Desktop Environments
---

### Post by ankitmalik on 2005-04-10
hi

i wanna change the permissions of all files in a directory 'Foo' and also its subdirectories' files from user 'root' to user 'ankit' ?

how do i do that?

---

### Post by Hinko on 2005-04-10
[QUOTE=ankitmalik]hi

i wanna change the permissions of all files in a directory 'Foo' and also its subdirectories' files from user 'root' to user 'ankit' ?

how do i do that?[/QUOTE]
 sudo chown -R foo ankit

---

### Post by matid on 2005-04-10
[QUOTE=Hinko]sudo chown -R foo ankit[/QUOTE]
Should be:
sudo chown -R ankit foo

---

### Post by ankitmalik on 2005-04-10
[QUOTE=matid]Should be:
sudo chown -R ankit foo[/QUOTE]
 yeah thanks for the command but also the files are read only... I will also like to change them to read-write...

thanks in advance

same folder foo
same user ankit
this time read write

thanks :-)

---

### Post by ankitmalik on 2005-04-10
[QUOTE=ankitmalik]yeah thanks for the command but also the files are read only... I will also like to change them to read-write...

thanks in advance

same folder foo
same user ankit
this time read write

thanks :-)[/QUOTE]

edit: I did some googling and found the answer to my query

chmod u+rwx -R Documents

---

### Post by Hinko on 2005-04-10
[QUOTE=matid]Should be:
sudo chown -R ankit foo[/QUOTE]


hehe, oops  :-? 

thanks man.

---

