---
title: "root and password and samba config"
date: 2005-12-26
forum: General Help
---

### Post by xylene2301 on 2005-12-26
I'm brand new on ubuntu and no Linux expert anyway.

My project is to set up Samba so I can share Ubuntu's files on my Windows LAN.

I installed Samba, no problemo...and then tried to edit the samba config file but it won't save; a permissions problem?  So I figured I'd login as root and do whatever.
Maybe I was asleep but I don't remember ubuntu asking me for a root password during the install, only a user name/password.
So now I realize I can't login as root.

---

### Post by S1l0 on 2005-12-26
You should use **sudo** before edit the fstab
like this:

**sudo vim /etc/fstab**

or use **su** and give the root passwd

---

### Post by Iandefor on 2005-12-26
This is a classic problem users from other distros have when moving to Ubuntu. Ubuntu disables the root account by default; instead, sudo is set up to use your user password, meaning that to perform an action as root, you use the command sudo and enter your user password. The rationale for this can be [found here]("https://wiki.ubuntu.com/RootSudo?"). If you want to enable root, you can do it using the Users and Groups dialog.

---

### Post by xylene2301 on 2005-12-26
Aha!
Any suggestions on how to proceed with getting the Ubuntu machine to access the LAN?
It seems to know its dhcp address and the domain name of the LAN but asks for a username/password to logon.

---

