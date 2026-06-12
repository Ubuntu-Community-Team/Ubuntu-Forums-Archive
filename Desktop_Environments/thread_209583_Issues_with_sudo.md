---
title: "Issues with sudo"
date: 2006-07-05
forum: Desktop Environments
---

### Post by CA_Warren on 2006-07-05
I've been using the same user as I first created on install for a while now, and everything works just fine. However, I recently created a new user (to use for work and projects/keep separate from my 'Home').

So I went through the 'Add' dialog under the users section of System Settings, created the new user, and logged into it (it asked I change the password upon initial login, so I did).

Now the problem comes in: I need to use Apache2, MySQL, etc. under the new user, and I need root privileges to install varying packages and the like. So I do things like attempt to launch Adept, it asks for the password, and I give it the administrator (original account) password, but Authentication fails. So I try giving it the new user's password, and the password that was originally the new user's password, but no dice.

I'm guessing I missed some option to enable sudo privileges or something for this new user, but I'm pretty new to Ubuntu/Kubuntu and haven't the slightest idea what the problem is. Any help would be much appreciated - thanks!

---

### Post by halfvolle melk on 2006-07-05
You may have more luck with this. Open a terminal (Accessories -> Applications -> Terminal). Then with the user for which sudo works, type the following:
```
sudo adduser <the-new-one> admin
```
That should add <the-new-one> to the sudoers, ie admins.

---

### Post by CA_Warren on 2006-07-05
Thank you!

Worked beautifully.

---

