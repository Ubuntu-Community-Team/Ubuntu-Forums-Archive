---
title: "Making copies of important files on a fresh install!"
date: 2009-02-15
forum: General Help
---

### Post by Rytron on 2009-02-15
Hi.
I came across this on a site (lines below in bold). It makes sense to make backup copies of important files. Below are some files that a user should make copies when he/she does a fresh install. Does anyone have more to add to this list?

[B]sudo mkdir /etc/master_copies

sudo cp /boot/grub/menu.lst /etc/master_copies
sudo cp /etc/fstab /etc/master_copies
sudo cp /etc/hdparm.conf /etc/master_copies
sudo cp /etc/apt/sources.list /etc/master_copies
sudo cp /etc/ssh/ssh_config /etc/master_copies
sudo cp /etc/sudoers /etc/master_copies
sudo cp /etc/X11/xorg.conf /etc/master_copies
sudo cp /etc/X11/Xsession.options /etc/master_copies[/B]

---

### Post by x33a on 2009-02-15
/etc/network/interfaces

after a freshly configured working network.

---

### Post by Rytron on 2009-02-15
> **x33a said:**
> /etc/network/interfaces

after a freshly configured working network.

Thanks x33a.

---

### Post by Elfy on 2009-02-15
I guess any file that you've had to mod in some way would be good to have a copy of

Also if you're doing sources the the file in sources.list.d if you have one

---

### Post by bapoumba on 2009-02-15
Thread title edited as requested.

---

### Post by oldos2er on 2009-02-15
Use gedit; any files you alter are automatically backed up.

---

