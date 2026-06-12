---
title: "Gedit do not respect Samba permissions"
date: 2008-06-02
forum: Desktop Environments
---

### Post by josir on 2008-06-02
Hi folks, 
I have Mandrake 10 samba server as primary domain controller to assist 30 Windows stations network. Now, we start to experiment Ubuntu as Desktop.

Shares is working fine and user permission are being respected. 

When I create a file using the prompt or other applications (Java based or OpenOffice for instance), it respects the user/group permission.

But when I use Gedit, it saves the permission with Ubuntu uid/gid. After that, the file is locked until I update it using console or other application.

[root@linux04 Utilitarios]# ls -ls Bus* 
 4 -rwxrwx---  1 1000   1001   576 Jun  2 17:04 Busca2.sql*
12 -rwxrwx---  1 root desenv 10057 Jun  2 17:49 Busca3.odt*

Does somebody have any tip on how to fix it?
Thanks in advance.
Josir.

---

### Post by josir on 2008-07-02
Just to note: this is a gedit problem. Other applications works fine with the Samba permissions.

---

