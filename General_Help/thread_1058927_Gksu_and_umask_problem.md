---
title: "Gksu and umask problem"
date: 2009-02-03
forum: General Help
---

### Post by rexio8 on 2009-02-03
Hello!

I'm trying to make a system that will run xsane or gimp only after suplying a password. I have two users: **user1** and **scan**. Only **scan** is a member of the scanner group and can use the scanner. I've also made a shortcut that executes "gksu -u scan gimp" so that I can get a window that wants the password of user **scan** before gimp can launch. And everything works well. The thing is that I also want that the **user1** can have access to the scaned files (read and write access). That is why **scan** is a member of the group to which **user1** belongs too. I wanted to set the umask to *0002* so that I could accomplish my task. Unfortunately gimp started with the command "gksu -u scan gimp" saves a file with "rw-r--r--" permissions. I've put the "umask 0002" in /etc/profile and in /etc/gdm/Xsession but nothing seems to solve my problem. **Please help and tell me where to change the umask so that files saved with gimp (executed by "gksu -u scan gimp") will have "rw-rw-r--" permissions.** 
Thanks very much. My Ubuntu is 7.10.

---

