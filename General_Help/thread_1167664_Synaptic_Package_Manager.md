---
title: "Synaptic Package Manager"
date: 2009-05-23
forum: General Help
---

### Post by dancil on 2009-05-23
Hi, please help.

 I am using LinuxMint which is based on Ubuntu Jaunty. My internet connection is very slow, so when installing packages I tried to use AptonCd but now the following appears and Synaptic Manager does not work either.


E: Problem parsing dependency Depends
E: Error occurred while processing checkinstall (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/APTonCD%20for%20ubuntu%20intrepid%20-%20i386%20(2009-04-09%2008:36)%20DVD1_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by Liolikas on 2009-05-23
sudo dpkg --configure -a
may be enouth already but more powa:
sudo apt-get update
sudo apt-get upgrade

---

### Post by dancil on 2009-05-23
> **Liolikas said:**
> sudo dpkg --configure -a
may be enouth already but more powa:
sudo apt-get update
sudo apt-get upgrade
Thank you.

sudo dpkg --configure -a did not help.

I can not connect to the Internet as apt wants to connect to a proxy even though a direct connection has been selecetd in network preferences.

---

### Post by dancil on 2009-09-04
Solved.

Thanks

---

