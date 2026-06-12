---
title: "Accessing Ubuntu files from a Windows box"
date: 2006-06-14
forum: Desktop Environments
---

### Post by Don Taylor on 2006-06-14
(I am a Linux newbie just starting the migration from Windows).

I have installed Dapper Drake (in a VMWare virtual machine) on my Windows XP box but I cannot see Ubuntu files from XP.

I have Samba installed and the Ubuntu system does show up in the Window's network.  When I click on the Ubuntu server I am asked to authenticate, I  then get a message in a 'Connect to ubuntu-base' dialog box that says I am connecting to Ubuntu-base, but the connection never suceeds - it just hangs there until I cancel it.

I can see Window's files from Ubuntu, I can use login to Ubuntu from Windows using FreeNX but I cannot see Ubuntu files from Windows.

Any pointers would be appreciated.

Don.

---

### Post by Don Taylor on 2006-06-14
It turns out that I needed to add a user to Samba:

sudo smbpasswd -a <user>

Don.

---

