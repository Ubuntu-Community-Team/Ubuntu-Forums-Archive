---
title: "password question"
date: 2009-02-21
forum: Desktop Environments
---

### Post by andrea000 on 2009-02-21
Hello all,

This is probably a easy question for someone who knows ubuntu better then me.how do i change the root password in ubuntu 8.04.

XOXOXO


Thank you all so much

---

### Post by adult swim on 2009-02-21
do you mean change the password that you enter in when you use the sudo command?

---

### Post by andrea000 on 2009-02-21
> **adult swim said:**
> do you mean change the password that you enter in when you use the sudo command?

Yes that one and the package manager.

thank you

---

### Post by adult swim on 2009-02-21
go to a terminal, Applications>Accessories>Terminal
enter in ```
sudo passwd username
``` and replace username with your username, so if your username was andrea, it would be sudo passwd andrea
youll have to enter the old password in once, and then you can enter in the new password

---

### Post by andrea000 on 2009-02-21
> **adult swim said:**
> go to a terminal, Applications>Accessories>Terminal
enter in ```
sudo passwd username
``` and replace username with your username, so if your username was andrea, it would be sudo passwd andrea
youll have to enter the old password in once, and then you can enter in the new password

Thank you so much adult swim your so sweet  

xoxoxoxo

---

### Post by mcduck on 2009-02-21
> **adult swim said:**
> go to a terminal, Applications>Accessories>Terminal
enter in ```
sudo passwd username
``` and replace username with your username, so if your username was andrea, it would be sudo passwd andrea
youll have to enter the old password in once, and then you can enter in the new password

you don't need "sudo" for that. Every user is able to change his own password.

Simple "passwd" works just great. ;)

---

### Post by binbash on 2009-02-21
> **mcduck said:**
> you don't need "sudo" for that. Every user is able to change his own password.

Simple "passwd" works just great. ;)

How can you change root password without sudo?

---

### Post by Armor Nick on 2009-02-21
sudo doesn't change you to root but temporarily gives a user root priviliges. It doesn't need the root password, consequently.

---

### Post by mcduck on 2009-02-21
> **binbash said:**
> How can you change root password without sudo?

It's not root password, it's normal user password.

Sudo doesn't use root password but the user's own password. If the user is member of the admins group he can then use sudo to do admin tasks (or other tasks he has been given permissions in /etc/sudoers).

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

edit: Of course you can't change the actual root password without using sudo (or recovery mode), but you shouldn't be doing that anyway, and it has nothing to do with the way admin tasks are handled by default in Ubuntu. As you are never supposed to actually log in as root, you don't need to mess with root's password either.

---

### Post by andrea000 on 2009-02-21
Not root password but i do need to 
change that one too.

---

