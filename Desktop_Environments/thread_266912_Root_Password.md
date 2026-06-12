---
title: "Root Password?"
date: 2006-09-27
forum: Desktop Environments
---

### Post by Zargoon on 2006-09-27
I'm brand new to Ubuntu.  It's a little different that Suse but I'm really impressed so far, but I have one issue.  I can't log in under root.  Is the super user different in Ubuntu?  I thought that I made the root pass the same as mine in the install.  I tried the four most common passwords that I use and none of them worked.  I also tried no password.  Is there a way to 'probe' the root password and find it out? 

Thanks.

---

### Post by meng on 2006-09-27
Root password is not enabled by default. Use sudo instead:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by randell6564 on 2006-09-27
> **Zargoon said:**
> I'm brand new to Ubuntu.  It's a little different that Suse but I'm really impressed so far, but I have one issue.  I can't log in under root.  Is the super user different in Ubuntu?  I thought that I made the root pass the same as mine in the install.  I tried the four most common passwords that I use and none of them worked.  I also tried no password.  Is there a way to 'probe' the root password and find it out? 

Thanks.
Hi!
You are not crazy, you are correct, you cannot login as 'root'. BUT, only by default!
There are actually a few different ways that you can get things done as 'root' though!
One easy way from your desktop is to just hit '**Alt+F2**', then type '**gksudo nautilus**' and hit '**Enter**'!  This will open up a window that WITHIN that window will allow you root priviledges!

OR, in order to achieve the option to LOGIN as 'root', go to **System>Administration>Login Window**, click on the **Security** Tab and check the box that reads, "**Allow Local System Administrator Login**".  Then close the window and go to **System>Administration>Users** **And Groups**, double-click on '**root**' and choose "**Set Password By Hand**".  Enter your password, click '**OK**', and BAM.,you can now logout and login again as root user!

---

