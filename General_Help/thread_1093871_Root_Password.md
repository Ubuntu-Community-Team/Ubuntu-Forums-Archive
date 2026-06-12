---
title: "Root Password??????"
date: 2009-03-12
forum: General Help
---

### Post by ambdeep on 2009-03-12
I was truing to install a software(*.tar.gz)......in the instructions it asked me to enter su in my terminal...which then asks for a password....which is supposedly different from the usual password....when i enter my password it tells me to enter my root password....what is this????? and how do I find/change it?
Plzz HELP!!!!

---

### Post by MaxIBoy on 2009-03-12
If you used "sudo" or "gksudo," your normal password will work.

Otherwise, if you used "su" or "gksu," you need to set the password for the "root" user. In Linux there is always a "root" user, which is a special user that has permission to do *anything*. Think "administrator" combined with "god."

In Ubuntu, the first user you create has root privileges, but only through "sudo." This is to stop you from using root powers unless you really mean it. "sudo" is short for "super user do." The "sudo" command is used to give root powers to only one single command, you have to add it to the beginning of every command that requires root power. But if you don't understand what a command does, don't use "sudo," and it won't break anything. 

"gksudo" is like "sudo," only it's used if you're launching a graphical program from a terminal.


"su" is short for "super user," and it's the command to log into the root account. By default, Ubuntu doesn't set a password for the root user, because the idea is you're just supposed to use "sudo."


To set the root password, type in "sudo passwd root."

---

### Post by ambdeep on 2009-03-12
Thakns A LOT!!!!!!

---

### Post by MaxIBoy on 2009-03-12
You really should just use "sudo" at the beginning of every command that needs it.

---

### Post by mb_webguy on 2009-03-12
+1

Setting the root password is Very Not Good.  Use sudo for terminal commands, and gksu for GUI applications.

---

### Post by ubuntu27 on 2009-03-12
Previous post already explained what is Root and Sudo

NOw if you want to know why sudo is considered better, read [Root&Sudo]("https://help.ubuntu.com/community/RootSudo")

In that wiki article, it also presents the Advantages and Disadvantages

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)


Also, please take a look about [Security in Ubuntu]("http://www.psychocats.net/ubuntu/security") by Aysiu 

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

