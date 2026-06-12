---
title: "Login"
date: 2006-03-01
forum: Desktop Environments
---

### Post by harley on 2006-03-01
how do i log in under root or owner if i did not set a password?

---

### Post by markymarknz on 2006-03-01
Ubuntu is setup not to really have a root account, just use sudo in your user account.
I have found though that if you <alt><ctrl><F1> to go to terminal then type
sudo su
password: xxxxx
then startx it starts up as root

hope this helps a bit

---

### Post by harley on 2006-03-01
once there how do i set file permissions for my main account?

and after i type startx i get a display zero is in use error..how do i fix this?

---

### Post by Ramses de Norre on 2006-03-01
I would advice not to login as root, use sudo instead.
Otherwise: you can just set a password using sudo passwd root

---

### Post by markymarknz on 2006-03-01
before startx try typing:
(as su)
/etc/init.d/gdm stop
(still as su)
startx

but yeah better to stay as user and just use sudo as ramses suggested
if you just want access to the file system there is an option to view file manager as root under the main menu then system tools or something
sorry not at my ubuntu box now :(

---

### Post by Ramses de Norre on 2006-03-01
sudo nautilus ;)
(beware on using it, deleting or modifying some files could break your system!)

---

