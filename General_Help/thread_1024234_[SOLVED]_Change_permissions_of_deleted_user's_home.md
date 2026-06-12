---
title: "[SOLVED] Change permissions of deleted user's home folder"
date: 2008-12-28
forum: General Help
---

### Post by DeMartini on 2008-12-28
My default (original) user was all messed up, so I created a new user gave it full permissions, however now I'm locked out of the original home directory which has ALL of my files/data/important work documents....please help, thanks

---

### Post by shad0w_walker on 2008-12-28
Easily enough solved. Open up a terminal (Applications > Accessories > Terminal) and run this command:

```
sudo chown -R $USER <path to old home>
```

You'll get a prompt for a password (It doesn't show anything whilst you type but it still works) Enter your password and hit enter, it may take a couple of seconds depending on how much is in the directory, but it will change the owner to your current user, which should give you full access again.

---

### Post by DeMartini on 2008-12-28
forgive my ignorance but i don't think i'm putting this in the terminal correctly, the exact path eludes me. Through nautilus i click on file systems then home, then jamie, jamie is the folder that needs its permissions changed....thanks in advance.

---

### Post by taurus on 2008-12-28
Assuming your new login name is martini and jamie is the old one.

You can either change the ownership of jamie to your new login name so you can access it anytime you want.

```
sudo chown -R martini /home/jamie
ls -la /home/jamie
```

Or you can change the permissions.

```
sudo chmod 777 -R /home/jamie
ls -la /home/jamie
```

---

### Post by DeMartini on 2008-12-28
Awesome thanks so much.....

---

### Post by pvfjr on 2008-12-31
Add another thanks, just saved my butt too.

---

