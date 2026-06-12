---
title: "Server to Kubuntu"
date: 2008-05-26
forum: Desktop Environments
---

### Post by kshane on 2008-05-26
I recently installed Hardy Server on another partition to "play" with.  I decided I to put the KDE4 desktop on and everything went smoothly, but when I tried to log on after the installation, it would not accept my password.  I even set up a new account and it would not accept the password to the new account.

Any one got an idea as to what's going on?

Kevin

---

### Post by kshane on 2008-05-26
bump...

---

### Post by kshane on 2008-05-26
bump

---

### Post by Xiong Chiamiov on 2008-05-27
What about after changing the password with passwd?

---

### Post by kshane on 2008-05-28
> **Xiong Chiamiov said:**
> What about after changing the password with passwd?

No difference.

---

### Post by jombeewoof on 2008-05-28
Might be your users are not a member of a group allowed to run startx.

Drop to a command line and kill KDM.

sudo /etc/init.d/kdm stop

Then try startx

It may or may not give you some errors to work with.

---

### Post by kshane on 2008-05-29
> **jombeewoof said:**
> Might be your users are not a member of a group allowed to run startx.

Drop to a command line and kill KDM.

sudo /etc/init.d/kdm stop

Then try startx

It may or may not give you some errors to work with.

Thanks.  I'll make a note of your reply for future reference.

I got a little frustrated and nuked the whole setup and just added it to my current Hardy version as another session.  Works great and was a minimum of hassle.  Now to try it out and see how KDE4 does for me....

Kevin

---

