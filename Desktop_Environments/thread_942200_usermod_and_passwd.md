---
title: "usermod and passwd"
date: 2008-10-08
forum: Desktop Environments
---

### Post by Shwick2 on 2008-10-08
ubuntu 8.04

I want to user olduser to newuser and this command isn't working, it just brings up the command options:

sudo usermod -l newuser -d /home/olduser -m /home/newuser olduser

Also, I changed the password for my current(only) user but now it's the same password for sudo as well.  I changed the sudo password to something different, but it doesn't change, it stays the same as the password for the user.

Is there anyway to make the sudo password different than the priveleged user's password?

---

### Post by skullmunky on 2008-10-09
try

```

sudo usermod -l newuser -dm /home/newuser  olduser

```

it's -d <new directory>, and then -m but no arguments if you want to move files from the old directory.  i think.

for your sudo question - you'll have to edit your /etc/sudoers file.  it has an extremely flexible but really confusing syntax, so i don't remember offhand how you do this.  be careful with this because it's easy to mess it up and lock yourself out completely.

---

