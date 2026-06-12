---
title: "Samba: Individual User Access"
date: 2009-03-08
forum: General Help
---

### Post by Lutrova on 2009-03-08
I have been searching the forums and all over the Internet with no direct answer to what I would assume is a very simple thing I'd like to accomplish.

I'm running Ubuntu Server 8.10 on a brand new machine I just put together last night. Using Samba and nosing around documentation, I successfully created a Public folder that anyone can read/write to for the house to just share files between machines. Now, **I want to be able to give users individual private folders only they have access to so that when they access it from their Windows machines they are forced to enter a username and password.** This mostly for personal backup purposes.

**What would be the simplest/easiest way to do this?**

My smb.conf file has not been modified from the original except to add a public share, hosts allow and hosts deny, and to uncomment 'security = user'.

---

### Post by Iowan on 2009-03-08
IF you have created accounts for them, both in Ubuntu AND Samba, there's a section in /etc/Samba/smb.conf that builds individual shares (in [homes] - that may need to be uncommented).

---

