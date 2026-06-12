---
title: "[SOLVED] Create launcher from commandline?"
date: 2008-12-28
forum: General Help
---

### Post by dwasifar on 2008-12-28
If I want to create a desktop launcher for, say, Firefox, is there a way to do that from the commandline instead of the usual GUI operations?  (Note that I want a launcher, not a symlink.)

---

### Post by ibuclaw on 2008-12-28
Launchers are just desktop items, right?

```
cp /usr/share/applications/firefox.desktop ~/Desktop
```

Though, I suppose a simple application to create one may make sense...
It won't be difficult to create (all you do is take user input and store it in a file :))

Regards
Iain

---

### Post by dwasifar on 2008-12-28
Excellent.  Precisely what I needed.  I set up a lot of Ubuntu machines for new users.  I like to put launchers on the desktop for quick access to common apps, and I wanted to automate the process a little by scripting the launcher creation.  Never knew how they were stored; now I do.  Thanks!

---

### Post by ibuclaw on 2008-12-29
Thanks, no problem.

If you are setting up machines for users, and you want the exactly same information to be created for each new user your customers create, you may be enlightened to know that each new user is created from a skeleton folder in Linux (/etc/skel).
Everything you put in there will appear on all new users home folders when they first login.

So something along the lines of:
```

sudo mkdir -p /etc/skel/Desktop
sudo cp /usr/share/applications/firefox.desktop /etc/skel/Desktop/

```
May be very helpful to you also.

Regards
Iain

---

