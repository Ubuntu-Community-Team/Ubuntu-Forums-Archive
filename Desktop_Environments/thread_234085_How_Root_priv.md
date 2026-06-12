---
title: "How Root priv"
date: 2006-08-10
forum: Desktop Environments
---

### Post by Branta on 2006-08-10
Ubuntu 6.06 LTS - the Dapper Drake

What command in **terminal** do I use to be **root** so I can go to /usr/local/lib and **create** the codecs **folder**?

I am the only user on this computer.


--- Bob ---

---

### Post by Dr. Nick on 2006-08-11
sudo [I]command
[/I]
more details here[I]
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[/I]

---

### Post by randell6564 on 2006-08-11
> **Branta said:**
> Ubuntu 6.06 LTS - the Dapper Drake

What command in **terminal** do I use to be **root** so I can go to /usr/local/lib and **create** the codecs **folder**?

I am the only user on this computer.


--- Bob ---
Type Alt+F2, then type in gksudo nautilus                                            . That will give you Temporary Root privleges.  Or you could go to System>Administration>Login Window, Click on the security tab, check the box "Allow local system administrator login"  Then go to System>Administration>Users and Groups, double click on Root and create a password.  That will allow you to log in to your box as Root.

---

