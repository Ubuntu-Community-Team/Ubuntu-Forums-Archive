---
title: "Update Manager doesn't ask for password (11.10 32-bit)"
date: 2012-01-20
forum: Desktop Environments
---

### Post by lucacerone on 2012-01-20
Dear all,
since a while when Update Manager pops up to notify me of new updates,
it doesn't ask me for the password any more.
This is ok for my laptop where I'm the only user,
but I don't like it for my desktop.
So is there a way to control whether Update Manager asks for the
password or not? Is it possible to set that by default it should
ask for the password?

Thanks a lot for your help!
Cheers, -Luca

---

### Post by hansdown on 2012-01-20
Hi, lucacerone.

11.10 doesn't ask for password for packages that are installed and updating.

Installing new packages will need authentication.

---

### Post by lucacerone on 2012-01-20
Hi, thanks for your reply!

How can I possibly revert the behaviour to the 11.04 one?

---

### Post by mc4man on 2012-01-20
You can revert (disable) this feature by editing com.ubuntu.desktop.pkla, but before posting how you should note that this only applies to an admin user, standard users will not be able to update thru U-M without an admin password.

So you may want to check out whether there is any need to do this,  - like if you're letting other users use your login or another user account in the 'admin' group

---

### Post by lucacerone on 2012-01-21
> **mc4man said:**
> You can revert (disable) this feature by editing com.ubuntu.desktop.pkla, but before posting how you should note that this only applies to an admin user, standard users will not be able to update thru U-M without an admin password.

So you may want to check out whether there is any need to do this,  - like if you're letting other users use your login or another user account in the 'admin' group

Thanks this was helpful :)
Just another question.. where is the com.ubuntu.desktop.pkla file to edit?

I guess I'm the only admin so there shouldn't be any need.
I was just wondering why on my laptop it asks for the password and on my desktop it doesn't. (It's probably due to the fact that on the laptop I made an upgrade and on the desktop a fresh install I guess).

Thanks again

---

