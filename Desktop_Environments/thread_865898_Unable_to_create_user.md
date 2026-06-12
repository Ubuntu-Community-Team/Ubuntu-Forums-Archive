---
title: "Unable to create user"
date: 2008-07-21
forum: Desktop Environments
---

### Post by Diskdoc on 2008-07-21
I can't seem to be able to create a new user using the user administration tool. I enter the values for the new user and press "ok". The user GROUP seems to be created but nothing new in /etc/passwd and no homedir gets created.

How do I move foward?

*fixed*

Ownership and permissons on the /home:dir was wrong. Probably due to some of my earlier tampering. Should be root:root drwx-xr-x

---

### Post by stitchmysmile93 on 2008-07-21
sudo useradd -m -G users matt

su - matt 

passwd matt

---

### Post by stitchmysmile93 on 2008-07-21
Oh Matt is a good name :P

---

### Post by jingyinggong on 2008-07-29
what is the difference between useradd and adduser?
I am just a green hand on ubuntu!
thanks

---

### Post by ibutho on 2008-07-29
> **jingyinggong said:**
> what is the difference between useradd and adduser?
I am just a green hand on ubuntu!
thanks

Adduser is more interactive (i.e. it asks you the details) than useradd (you enter the details manually without any prompts or menu).

---

