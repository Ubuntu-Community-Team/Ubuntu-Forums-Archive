---
title: "Scripting?"
date: 2011-09-11
forum: Desktop Environments
---

### Post by DanHorniblow on 2011-09-11
Hi, All of my files that I use daily I store on a home server, which I access via sshfs. I just simply mount my "/home/dan/Documents/" on my laptop to "/home/dan/Documents/" on my home server.

Now this is all good apart from every time I boot up my laptop I have to type a command into terminal.

Could the command be put into a script file, that I just run when I login?

---

### Post by An Sanct on 2011-09-11
crate a sh file (bash script), make sure it is runnable and put it into the startup applications list.

---

### Post by nothingspecial on 2011-09-11
One way of doing this would be editing /etc/fstab, here is a guide

[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

---

