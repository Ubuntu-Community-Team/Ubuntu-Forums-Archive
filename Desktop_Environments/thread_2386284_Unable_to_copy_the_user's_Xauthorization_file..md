---
title: "Unable to copy the user's Xauthorization file."
date: 2018-03-03
forum: Desktop Environments
---

### Post by petercartersr on 2018-03-03
I keep getting this message particularly when I am trying to use a back up program.
Failed to run /usr/bin/sbackup-restore-gtk as user root.

---

### Post by Frogs Hair on 2018-03-03
Hello and Welcome

Please provide some information about the computer and the Ubuntu version in use.

---

### Post by SeijiSensei on 2018-03-03
Run the program with sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by petercartersr on 2018-03-03
I'm running an HP Z 420. I have a 1tb hard drive partitioned of which I have allocated 640 gigs to Ubuntu. Currently less than a hundred gigs are being used. I am running Ubuntu 17.10 desktop.

---

### Post by Frogs Hair on 2018-03-03
Are you running the Ubuntu or Ubuntu on Xorg session.

---

### Post by petercartersr on 2018-03-03
Okay, I gave my user root access (I will post how I did it below) and I don't seem to be getting the massage anymore. However, I don't think that I should be running all the time in this mode. What should I do?
-----------
Here is how I ran the root account

Enabling the root account

IconsPage/warning.png
	

Enabling the root account is rarely necessary. Almost everything you need to do as administrator of an Ubuntu system can be done via sudo or gksudo. If you really need a persistent root login, the best alternative is to simulate a root login shell using the following command...
	

IconsPage/warning.png

sudo -i

To enable the root account (i.e. set a password) use:

sudo passwd root

Use at your own risk!

---

### Post by petercartersr on 2018-03-03
I am running a clean install of Ubuntu.

---

### Post by Frogs Hair on 2018-03-03
> **petercartersr said:**
> I am running a clean install of Ubuntu.

There are two sessions included and  either can be selected during login. Ubuntu and Ubuntu on Xorg.

---

