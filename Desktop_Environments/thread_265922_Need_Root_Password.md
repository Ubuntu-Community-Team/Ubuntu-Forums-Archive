---
title: "Need Root Password"
date: 2006-09-26
forum: Desktop Environments
---

### Post by OldSeaDog on 2006-09-26
HELP!!!
My dumb machine has a problem; Ubuntu won't let me log in, in GDM or text mode at tty1.  There is something wrong I suspect eith bashrc or bash_profile.  It starts to let me in then cycles through.

When I try at tty1, this is what happens:
1.  I get all the licensing and stuff
2.  It tells me I have mail
3.  It starts the intro login line "Ununtu 6.06...)
4.  It prints my machine name and "Login:"
5.  I curse and swear :(.

What is the default root password (it is a new install and I haven't set it yet).

OldSeaDog

---

### Post by aysiu on 2006-09-26
There is no default root password. If you want to make some repairs, boot into recovery mode.

After you're in, I would create a new usable user and then use that user to repair your old user: ```
sudo adduser repair
sudo adduser repair admin
sudo reboot
``` And then log in as *repair* and try to fix your old user's account.

---

### Post by andypaxo on 2006-09-26
As far as I know, Ubuntu sets a random root password just so that you can't use it.
You should be able to alter anything on the system using sudo and your own password.
If you've managed to install Ubuntu without setting up your own account...

...well, that would make things difficult

---

### Post by OldSeaDog on 2006-09-26
Man did I write that badly!

When I try to log in by GDM, it dies.

When I try by tty1, I just go in the circle I described.

I can't log in as root to fix the problem.  I don't know the password.

OldSeaDog

---

### Post by aysiu on 2006-09-26
There is no password. When you boot into recovery mode, you *are* root.

---

