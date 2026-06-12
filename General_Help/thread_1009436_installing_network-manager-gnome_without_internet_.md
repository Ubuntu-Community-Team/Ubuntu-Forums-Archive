---
title: "installing network-manager-gnome without internet connection"
date: 2008-12-12
forum: General Help
---

### Post by turna on 2008-12-12
i un-installed network manager gnome and want to re-install it. i dont know how to do it. dep packages needs some dependencies. should i download them one by one ? what is the simple way to do this ?

---

### Post by albinootje on 2008-12-12
In a terminal type :
sudo apt-get install network-manager

---

### Post by turna on 2008-12-12
i have no internet connection since network manager is not installed...

---

### Post by albinootje on 2008-12-12
If you're using Ubuntu 8.10, then you need these 2 packages in /var/cache/apt/archives/ to install it :

network-manager_0.7~~svn20081018t105859-0ubuntu1_i386.deb
network-manager-gnome_0.7~~svn20081020t000444-0ubuntu1_i386.deb

If those 2 packages are there, you can install them without having an internet-connection.
You can also search for them on the install-cdrom, and copy them into /var/cache/apt/archives/ and then run :
sudo apt-get install network-manager

GL!

---

### Post by turna on 2008-12-14
it give error because of dependencies.

---

### Post by albinootje on 2008-12-14
Did you do : sudo apt-get update
first ?
And can you locate the network-manager packages on the installation cdrom ? (I assume you have an Ubuntu installation cdrom used for your installation).

---

### Post by turna on 2008-12-14
i put the deb packages to /var/cache/apt/archives/

then try to install. but it starts to try download some lib... packages...

---

### Post by albinootje on 2008-12-14
I think it's a good idea to start a new posting describing the problem, so that more people can look at your problem.

And mention :
* which Ubuntu release you are using (e.g. Hardy or Intrepid)
* that you have no internet-connection

---

