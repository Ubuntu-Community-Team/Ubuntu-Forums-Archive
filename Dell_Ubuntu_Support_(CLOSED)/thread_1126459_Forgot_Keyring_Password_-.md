---
title: "Forgot Keyring Password -"
date: 2009-04-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ArKay on 2009-04-15
I set up my Mini9 with 8.10 and thought I had an easily remembered keyring password... but I'm wrong  :oops:

Anyone know how to recover the keyring password so I can actually log on to my keyring info ?

Mind you, not the system password - that I know. The _keyring_ password is what I'm trying to recover.

Thanks in advance.

---

### Post by bigbrovar on 2009-04-15
[http://bigbrovar.wordpress.com/2009/01/10/resetting-keyring-in-intrepid/](http://bigbrovar.wordpress.com/2009/01/10/resetting-keyring-in-intrepid/)

---

### Post by ArKay on 2009-04-16
Grand !

That is exactly what I was looking for. Thanks.

---

### Post by bigbrovar on 2009-04-17
welcome ;)

---

### Post by vdawg on 2009-07-15
Well I have the same problem, but I'm not using WPA or anything.

I deleted the login.keyring file and then re-logged on and fired up SSH but nothing happened :(

Edit: I don't care about anything in the keyring itself, I just checked and I don't have a ~/.gnome2/keyrings/default.keyring file either :(

---

### Post by vdawg on 2009-07-15
FIXED. So all I did was rename that login.keyring file to default.keyring and then I could use my login password as my keyring password :)

---

