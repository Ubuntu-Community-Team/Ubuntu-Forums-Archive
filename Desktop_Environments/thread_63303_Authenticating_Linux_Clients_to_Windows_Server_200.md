---
title: "Authenticating Linux Clients to Windows Server 2003"
date: 2005-09-07
forum: Desktop Environments
---

### Post by sinbad782 on 2005-09-07
Hi All,
  I know there are plenty of guides out there for people who are running Linux as a server and want to allow MS Windows clients to be able to authenticate and share files and printers, use roaming profiles etc. , BUT.....

I need a simple guide on how to do the opposite: Use Linux (Ubuntu or otherwise) clients authenticating with a Windows server running Windows Server 2003. 

Any info would on this would be great. I'm not a big expert in LDAP or Kerberos etc. and so please keep it relatively simple.

Thanks, PJS.

---

### Post by mlomker on 2005-09-07
I guess I don't understand what you're trying to accomplish.  If you try to map a drive to a Windows machine (using smbclient or Konqueror in KDE) you'll be prompted for your username/password.  You can set even set a default in the control panel.

I'm an MCSE, so if you clarify what you're looking for then I could probably answer your question.

---

### Post by sinbad782 on 2005-09-11
Hi,
 If possible, the ideal situation would be to have all the user's home directories stored as a profile on the windows server and only allow access to a user account via the gdm login screen. 

My college uses NetWare for some accounts at the moment and there is a client for Windows which does a similar thing. 

Thanks, Paul S.

---

### Post by jworr on 2005-09-19
I have the same problem,

I have a windows 2000 server pdc that stores profiles, usernames, and passwords and I want ubuntu clients to be able to authenicate on it via the X login screen

I think samba, winbind, and PAM are needed to do this but I can't quite get it all to work

Any help would be awsome

---

### Post by jworr on 2005-09-19
this might help:


[http://www.ubuntuforums.org/showthread.php?t=5409&highlight=login+windows+server](http://www.ubuntuforums.org/showthread.php?t=5409&highlight=login+windows+server)

---

### Post by Abhi Kalyan on 2006-10-20
Hope i can join in here.
having the same problem
!! waiting for an answer
Please some one help;
mean while amtrying out the links provided

---

### Post by armnpsycho on 2007-06-30
There is a nice wiki page in the forum topic that jworr put down.

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

---

