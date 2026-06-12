---
title: "Network problem related to OS"
date: 2005-12-10
forum: General Help
---

### Post by XeroXer on 2005-12-10
Hi there.
Recently I have had some problems getting access to my network using my laptop with ubuntu.
For a week ago I could get in without any problems.
I have changed no settings it just stopped working one day.

I can get in to the "Windows network" and I can see the MSHOME icon.
But when I click it I get error:
[CENTER]**_Error Dislpaying Folder_**
**The folder contents could not be displayed.**
Sorry, couldn't display all the contents of "Windows Network: mshome".[/CENTER]
(Error also attached as image!)

In my network there are five computers:
[CENTER]My laptop - Ubuntu Breezy Badger 5.10
My router - ClarkConnect Home Edition 3.0
Stationary 1 - Windows XP Prof.
Stationary 2 - Windows XP Prof.
Stationary 3 - Windows XP Home[/CENTER]

If I go through Smb4K I can access MSHOME and My router.
But still none of the Windows computers.
In Smb4k the error is this:
[CENTER]_**Error - Smb4K**_
An error occurred while trying to get the list of shares.
**Details:** *Connection to XEROXER failed.*[/CENTER]
(Error also attached as image!)

If anyone has any ideas or tips please tell me.
Would really like to get this working...

---

### Post by XeroXer on 2005-12-10
Now the problem just got bigger.
I was looking around checking if I could find anything to fix this mess.
I tried removing the host name from network settings and restarted.
My good now nothing works.
I get an error when I start and it tells me to look if I can do anything in the /etc/hosts file.
I searched a bit here and found how I could fix it.
I did just as it said but it still won't work.
I can't open the network settings or anything.
So I can't restore the mess I made.
Please help this poor newbie...

**/etc/hosts:**
```
127.0.0.1 localhost.localdomain localhost XeroXer-ubuntu
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

