---
title: "NO root password given!!?"
date: 2005-05-22
forum: Desktop Environments
---

### Post by mfischer on 2005-05-22
hi,

i have installed kubuntu yesterday,now i tried to setup my DSL connection via PPPOEconf.the system asks for my root login with password! during installation nobodys ask me to setup a root/password so what can i do to fix this problem?

please help i am new to Linux&Kubuntu but what i ve seen yet is really good

thanks

Marco

---

### Post by themelvin on 2005-05-22
Hello

there is no need for root password. Try to write this:

sudo pppoeconf

enter usernames password (your password)

and this is it :)

---

### Post by mfischer on 2005-05-22
Hi,

It works!  :)  thanks for your fast and friendly Help!!

Marco

---

### Post by Samer on 2005-05-23
Is is possible to set up a root account in Kubuntu?

---

### Post by Firetech on 2005-05-23
Yes, but not recommended according to the developers: [http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)
I have one, but I rarely use it. It's mostly for backup when I screw up /etc/sudoers and such.

---

### Post by sancho on 2005-05-24
just to add to those comments....

If you WANT a root account you can issue a command or you can do a fresh install using 'expert' and it will create the root account during install.  

From the FAQ:

If you wish to use the root account in more traditional UNIX fashion, you can set the root password by typing sudo passwd root. This will allow you to use su or login as root on the console.

If you need a shell with root privileges, run sudo -s.

---

### Post by loon on 2005-05-24
[QUOTE=sancho]just to add to those comments....

If you WANT a root account you can issue a command or you can do a fresh install using 'expert' and it will create the root account during install.  

From the FAQ:

If you wish to use the root account in more traditional UNIX fashion, you can set the root password by typing sudo passwd root. This will allow you to use su or login as root on the console.

If you need a shell with root privileges, run sudo -s.[/QUOTE]
 What is the command to revert back?? (disable root once installed)

Forgot.

Thx

---

### Post by Spleenie on 2005-05-25
One simply types, in the terminal:

sudo passwd -l root

This should do the trick

- Spleenie

---

