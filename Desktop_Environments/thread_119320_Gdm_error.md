---
title: "Gdm error"
date: 2006-01-19
forum: Desktop Environments
---

### Post by joselin on 2006-01-19
Hi,

I receive the messages in the attachs when i login into gdm. I receive it after the upgrade to breezy. Anyone know how can i restore the base session script?

Regards.

---

### Post by Sef on 2006-01-19
Can you update your system via the terminal?

sudo apt-get update

---

### Post by joselin on 2006-01-25
[QUOTE=Sef]Can you update your system via the terminal?

sudo apt-get update[/QUOTE]

Yes i can... i have all the updates, but i continue receiving the error.

---

### Post by aysiu on 2006-01-25
Maybe try marking GDM for complete removal in Synaptic. Apply the changes. Then mark it for installation and apply the changes again. Any difference?

---

### Post by Sutekh on 2006-01-25
Try```
sudo dpkg-reconfigure gdm
```
?

---

### Post by manicka on 2006-01-25
Maybe the Failsafe has accidently been set as the default during the upgrade. At the login screen click on the Sessions' button and reset your session to gnome as the default.

---

### Post by joselin on 2006-01-25
With dpkg-reconfigure appears the same error. And no, i tryed to select Gnome, but same error too.

I will try to reinstall the package.

---

### Post by joselin on 2006-01-26
After reinstall the gdm package i recieve the same errors.

I need help!!!!!!!

---

