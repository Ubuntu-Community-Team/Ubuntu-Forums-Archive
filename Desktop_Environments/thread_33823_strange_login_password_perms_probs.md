---
title: "strange login password perms probs"
date: 2005-05-12
forum: Desktop Environments
---

### Post by lepetitalbert on 2005-05-12
Hello everybody,

yesterday morning, I booted my box and ended up with a console instead of the gdm login screen !

I tried to log in, but no way !! ( Yes, I'm SURE it's the right pwd)

i put an empty pwd, rebooted log in and found (in the user's home dir) hidden dirs and files (like .ICEauthority, .gnome) owned by root !!!
(Forget to say that I could start X only under root)

I gave them back to the user, rebooted, gdm back, everything seemed fine.

Later, my screen was locked by the screensaver, and I could not unlock it !!!!

DENIED

( Yes, I'm SURE it's the right pwd)

I really don't understand what's happening.

The last change made to the system was installing xmms.

If anyone has an idea

Have a nice day

---

### Post by lepetitalbert on 2005-05-12
Hello again,

and now I can't use sudo !!!!!

i used it just before I rebooted.

How can I log in (with the first and only account created) and
my pwd been refused by sudo ???

---

### Post by lepetitalbert on 2005-05-12
Hello again,

I discovered that from the console (X session killed) I could use sudo.

So I changed the user's pwd (again).

The pwd change is effective in the console, but if I start a xsession (as user) 
again I can't use sudo.

?!?!

Have a nice day.

---

### Post by bored2k on 2005-05-13
I barely understand this thread but I'll try covering all areas I can.

- To change user password, restart ubuntu from the recovery console, here you will get root access. Once "root", go to your desired user directory and hit ```
chown username -R /home/rafael/*
``` That command will make your user owner of everything in the dir you point it at [the user being /home/rafael/].

Now to change the files to your user's group, hit ```
chgrp rafael -R  /home/rafael/*
```
Same here.

- Now to change your user password, hit
```
passwd rafael
```

That's it.
** rafael is the username i used for this example.

[http://ubuntuguide.org/#gainrootwithoutlogin](http://ubuntuguide.org/#gainrootwithoutlogin)
[http://ubuntuguide.org/#gainrootinstallcd](http://ubuntuguide.org/#gainrootinstallcd)

Good luck,
rafael.

---

### Post by lepetitalbert on 2005-05-13
Hello,

thanks bored2k, but I already done  this.

But it still didn't work !

Today sudo worked in a xsession, but not in the console !!

Yesterday it was the opposite !!!

I rechanged the pwd with 'passwd' and now I can't login !!!!


As nobody seem to have a clue about what's happening, I'll reinstall.

Have a nice day.

---

