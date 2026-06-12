---
title: "problema with SAMBA"
date: 2005-06-09
forum: Desktop Environments
---

### Post by cristianommxp on 2005-06-09
My computer has 2 users: "cris" and "caixa"


Using "cris" I installed SAMBA:

-------------------------------------------------------------------
$ sudo aptidute install samba
$ sudo aptidute install smbfs
$ sudo chmod u+s /usr/bin/smbmnt
-------------------------------------------------------------------
(obs.: I follow the tutorial in 
[http://www.ubuntulinux.org/wiki/SettingUpSamba](http://www.ubuntulinux.org/wiki/SettingUpSamba))

so, I mounted a folder:

-------------------------------------------------------------------
$ smbmount //zezinho/sistema /opt/msdos/servidor
-------------------------------------------------------------------

ok, it works fine. If I use "ls" command in "/opt/msdos/servidor" I'll see //zezinho/sistema directory.

BUT, when I try to mount the same folder using another user ("caixa"), it doesn't work. I can't mount the folder. Linux tell me was not possible to mount the folder.

Please, what's wrong?


Cristiano

---

### Post by Markrian on 2005-06-09
What command are you using to mount the share using the caixa user? caixa must exist in the /etc/sudoers file (like cris would be) in order for the user to use sudo.

---

### Post by superdexter on 2006-07-14
[]("http://ubuntuforums.org/member.php?u=12547")cristianonmxp,

[COLOR=Red]**> sudo chmod u+s /usr/bin/smbmnt**[/COLOR]

This was the command that I had to issue again just after the update manager updated samba.  After that my Smb4K worked just fine again.

Glad this post was still out here *phew*.  Hooray for Ubuntuforums.org AGAIN!!!

---

