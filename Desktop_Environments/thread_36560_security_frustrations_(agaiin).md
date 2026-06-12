---
title: "security frustrations (agaiin)"
date: 2005-05-23
forum: Desktop Environments
---

### Post by Curlydave on 2005-05-23
I just installed UT2k4 and want to patch it. It's pulling the security garbage again. How do I get around it? Thanks!

PS: will entering 

> 
sudo it's myfuckingcomputerletmewritetothedamnHD


work?

---

### Post by DJ_Max on 2005-05-23
> security garbage
Care to elaborate?

---

### Post by Curlydave on 2005-05-23
No permission.

---

### Post by DJ_Max on 2005-05-23
I haven't installed UT2k4, but sudo will give you proper permissions for installing software.

---

### Post by angkor on 2005-05-24
[QUOTE=Curlydave]It's pulling the security garbage again. How do I get around it? 
[/QUOTE]

Please man, do some reading on GNU/Linux in general before you start ranting about security and permissions having no use. Maybe you'll figure out that the people who created the OS know more about security than you do.

You can check the permissions of files and directories with the command ls -l.

Read up on the commands 'chmod' and 'chown' to change file ownership and permissions. You can always use 'sudo' if you are trying to write to a directory that needs root permissions. It's possible to set things up so that you won't even have to enter a password, since you wrote in an earlier thread you didn't want to be bothered by that  :???: 

Read [www.ubuntuguide.org](www.ubuntuguide.org) carefully to be able to set things up just the way you like it, but be prepared to bork up your system if you do not wish to know / deal with the difference between regular user and root access.

---

### Post by nocturn on 2005-05-24
[QUOTE=Curlydave]I just installed UT2k4 and want to patch it. It's pulling the security garbage again. How do I get around it? Thanks!

PS: will entering 



work?[/QUOTE]

<sarcasm on>

sudo chmod -R 777 /

might do it.  Offcourse, then read/write/execute is open for everyone. :roll:

<sarcasm off>

---

