---
title: "network sharing login"
date: 2005-12-15
forum: General Help
---

### Post by linrasta on 2005-12-15
I have 2 ubuntu boxes and 2 winxp computers, all communicating with a ubuntu server.  I have them all on the same "Windows workgroup" (named "planet") and I have file and printer sharing enabled.  Problem 1:  I can see my linux boxes in the network places on my xp boxes, but when I click on one to browse the files, it prompts for a username/password.  I try root uname/pword, regular uname/pword, win uname/pword, but it is never correct.  What username and password is it looking for and how do I disable it for file sharing.  Problem 2:  on my linux boxes, when I click on network servers to view the "neighborhood" (my xp boxes) it also prompts for a username/password.  Again, I try every one I can think of but none of them are correct.  What is the problem?  Is it a server configuration prob.?  I just don't understand, please help.  Thank you kindly

---

### Post by zoiks on 2005-12-15
Simple: Samba has its own password database.  (Samba is the set of programs that allow CIFS filesharing, which is also the protocol that windows uses.)  For a user to access a samba share, first it must be one of the users on the system.  Second, you have to add a special samba-only password for that user using a command like

```
sudo smbpasswd -a username
```

replacing "username" with the username.  (Check out "man smbpasswd".)  Note: I doubt it's a good idea to add "root" as a samba user.  Note also that samba needs to be configured correctly for sharing (which you may have already done).

---

### Post by linrasta on 2005-12-15
Ok, what you say makes sense.  But just to clarify, for example:  Say I want to access files on an xp machine FROM a ubuntu workstation.  When I go to the "network servers" in my places menu, it prompts for username/password before I can even see my workgroup.  So do I need only to set the uname/pword on the samba server on the ubuntu box, or do I need to set something up on xp?  I guess, what I am really saying is: Why does my ubuntu box require a password simply to view the network neighborhood, and my xp mahcines don't require a pword to view the neighborhood?  and also: Is there a way to disable the password, so all computers on the network can share freely?

---

### Post by zoiks on 2005-12-15
I don't know why you are asked for a password to see the network.  Maybe it has something to do with an NT domain.  (?)  The way I use shares is I have a shared drive (actually each user of my network has their own share) on a linux server with samba.  Windows and Linux clients use the share with no problem (all are password protected).

Try connecting to the share directly.  One way to do it is hit <ctrl>-L in the "network places" browser, and type in "smb://hostname/sharename" of your windows shared folder.  It should allow you to access your files that way.

I don't think exporting shares without a password is a good idea, though (note with XP home you don't have a choice but to share sans password - niiiiice!).  At a minimum make sure you have good firewalling on such systems, though I still don't recommend it.

---

### Post by sabitha on 2005-12-15
maybe i guest you want to disable the network login to acces the network places on your nautilus like Hoary 5.04

---

### Post by sabitha on 2005-12-15
maybe i guest you want to disable the network login to acces the network places on your nautilus like Hoary 5.04. 
if that what you want i want that way too ;)

---

### Post by scarter on 2005-12-20
So far, I've come across at least 25 topics raising the same issue (mystery username and password required to access some, but not all, Windows XP computers) , and nobody seems to have come up with an answer.  Aargh! :confused:

---

### Post by usererror on 2005-12-20
maybe someone can help me with this network problem.

i've got a debian webserver running (192.168.1.200) with server name "etarqsrv01"

i can ping etarqsrv01 and via IP from windows but from ubuntu i can only ping with the IP not the server name.  am i missing something on my ubuntu machine? if so what is it??  :confused:

---

