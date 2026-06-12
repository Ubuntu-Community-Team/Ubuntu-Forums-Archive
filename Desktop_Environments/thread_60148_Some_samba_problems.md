---
title: "Some samba problems"
date: 2005-08-26
forum: Desktop Environments
---

### Post by nianhbg on 2005-08-26
Hi I have some problems with samba

everytime i want to share a catalog with samba i have 
to restart samba with sudo /etc/init.d/samba restart

is there any solutions to this?

/Nicklas

---

### Post by glug101 on 2005-08-26
What do you mean by 'share a catalog'?  Are you talking about sharing a new volume/folder using samba?  

I know that smbd needs to be restarted every time that you add a new share, but I thought that Ubuntu restarted that for you when you use the graphical program.  If you are editing your smb.conf file manually then you will always have to restart samba.

---

