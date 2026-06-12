---
title: "Mount Samba without sudo"
date: 2005-03-10
forum: Desktop Environments
---

### Post by matgorb on 2005-03-10
Is it possible to mount samba without being su.
My problem is that at work, the people are nice enough to allow me to choose my environment, so i got ubuntu, of course. However I have to connect to a samba share and I have a little problem.

I have a login password to access a share, and in this share I have the right to modify only in one sub directory. I can access the share without problem with a Run Application
smb://server_name/share_name, as it ask for my login and password and give me the right rights. But i want to mount it as root and allow to have this righs

Edit: I just found this
sudo mount //192.168.0.1/linux /media/sharename/ -o username=myusername,password=mypassword,dmask=777,fmask=777

so I will try tomorrow.

One last question: Is it possible in any way to see all the share of a server, windows style, because nautilus doesn't allow it?

---

