---
title: "getting rid of that brown background."
date: 2005-11-26
forum: Desktop Environments
---

### Post by bb002 on 2005-11-26
I would like to know how to change that brown background color that you see between the xserver starting up and gdm appearing, as well as the one after logging in.

Since I don't know anything about where this change is located, I'll take this chance to let you know I want this change to be global and affect all users whether they exist yet or not.

---

### Post by X-scream on 2005-11-26
to change the color after logon just goto System>Administration>LoginScreenSetup and Change the GTK+greeter color.. 
But unfortunately this doesn't change anything on that brown splash/loading thingy :( 
And I can't see any options that disable it :???:

---

### Post by bonzodog on 2005-11-26
You need to: 

```
sudo apt-get install gnome-splashscreen-manager
```

That will enable you to change the brown 'splash' screen. :)

---

### Post by stalefries on 2005-11-26
You can change your background by right-clicking it, and selecting something along the lines of "Change Desktop Background". Unfortunately, Ubuntu only comes with that background, so you'll need to download more. Iwould sugest starting at art.gnome.org, which has a whole lot of excellent backgrounds.

---

### Post by bb002 on 2005-11-27
Thanks X-scream that is exactly what I was after.

---

