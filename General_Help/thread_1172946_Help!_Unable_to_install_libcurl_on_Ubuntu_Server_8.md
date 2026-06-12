---
title: "Help! Unable to install libcurl on Ubuntu Server 8.04"
date: 2009-05-29
forum: General Help
---

### Post by TDK800 on 2009-05-29
sudo apt-get install libcurl4-gnutls-dev libgnutls-dev

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgnutls-dev: Depends: libgnutls13 (= 2.0.4-1ubuntu2.3) but 2.0.4-1ubuntu2.4 is to be installed
E: Broken packages

---

### Post by TDK800 on 2009-05-29
solved problem by upgrading ubuntu from 8.04 to 9.04

---

### Post by ActiveFrost on 2009-05-29
> **TDK800 said:**
> solved problem by upgrading ubuntu from 8.04 to 9.04

Actually, upgrading your whole system is not a solution :D Anyway, I'm glad you've found a way to /fix/ it :)

---

