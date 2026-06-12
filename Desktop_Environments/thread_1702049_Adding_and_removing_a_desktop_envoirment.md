---
title: "Adding and removing a desktop envoirment"
date: 2011-03-07
forum: Desktop Environments
---

### Post by ryuguns on 2011-03-07
Hello, I want to try out ubuntu with xfce, thing is, I don't know how to safely add and remove a desktop environment. Anyone know how to do this so I don't break ubuntu?:lolflag:

I don't want to install xubuntu, partially because I want to learn how to do this stuff myself.

What is a safe way of installing xfce and removing it if I didn't like it?

---

### Post by matt_symes on 2011-03-07
Hi

[https://help.ubuntu.com/10.04/config-desktop/C/other-desktops.html](https://help.ubuntu.com/10.04/config-desktop/C/other-desktops.html)
[http://blog.sudobits.com/2010/05/02/how-to-install-xfce-in-ubuntu-10-04/](http://blog.sudobits.com/2010/05/02/how-to-install-xfce-in-ubuntu-10-04/)
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

Kind regards

---

### Post by Veovis Muad'dib on 2011-03-07
```
sudo apt-get install xubuntu-desktop
```

To remove, replace install with remove.  To switch DE's, log out and switch.

---

### Post by Krytarik on 2011-03-07
Simply install the "xfce4" metapackage:
```
sudo apt-get install xfce4
```
If you want to remove it again:
```
sudo apt-get purge xfce4
sudo apt-get autoremove
```
@the others: "xubuntu" and "purexfce"? Didn't you read the initial post!?

---

### Post by ryuguns on 2011-03-21
Thank you all for your great replies, Ill be in the terminal soon :D.

One question, if I install xfce, will I get rid of gnome?

---

### Post by Krytarik on 2011-03-21
> **ryuguns said:**
> 
One question, if I install xfce, will I get rid of gnome?
Nope. After the installation, you should be able to choose the desired "Session" option at the bottom of the login screen, after clicking at your name.

---

