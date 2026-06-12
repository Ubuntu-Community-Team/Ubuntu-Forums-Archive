---
title: "Password for Xubuntu persistant USB"
date: 2012-01-07
forum: Desktop Environments
---

### Post by motorcity909 on 2012-01-07
Hi all

As and when I get a new PC, I'm looking at running Xubuntu on it so I've been playing around with it on a live CD and today have been trying to create a persistant USB, so I can make changes that are saved.

I used the installer from Pen Drive Linux on an XP machine to create the USB with a Xubuntu 11.10 iso file.

I'm using an old Dell laptop (no hard-drive) and it successfully boots initially from the stick but when I make changes and shutdown and restart it asks for a username and password.

I've tried ubuntu/ubuntu and xubuntu/xubuntu and I've tried 'password', 'sudo', left it blank and all the connatations therein but I can't get it to login.

Is there a password?  Or failing that, on that inital successful bootup, what change do I make so it just logins without asking for a password?

Many thanks as always
Dave

---

### Post by spacecheck on 2012-01-07
Had that happen to me, too, which I believe was because I changed the host name. "Root" was able to login w/o a password, so I reset the password for "ubuntu" but it no longer worked properly. I could login with correct user & password, but it would simply revert to the login screen each time. Added a new user, but the same thing occurred, so I gave up and reinstalled. Hasn't happened since (yet).

---

### Post by motorcity909 on 2012-01-08
Thanks spacecheck.

I've got round this by actually installing the OS to the USB stick, rather than just running it as a live USB.  So during the install process it asked me if I wanted auto-login and I ticked yes and now it restarts fine.

Really enjoying playing around with Xubuntu and can't wait to get a new PC to set it up properly.

Cheers
Dave :D

---

