---
title: "Not good... Failed to execute gksudo"
date: 2005-10-18
forum: Desktop Environments
---

### Post by SeanCallan on 2005-10-18
So this really can't be good.  When I go to Synaptic it tells me :

Cannot Launch Entry
Details: Failed to execute child process "gksudo" (No such file or directory)

On top of that.  If I restart, it instantly goes to terminal.  I have to manually type "sudo startx" to get GNOME up.

Any ideas?

---

### Post by adwait on 2005-10-18
Apparently there is some problem with gksudo. When you try to start it, does it ask you for a password? If not, maybe there's some problem wtih gksudo.....try installing it
```
sudo apt-get install gksudo 
```

---

### Post by SeanCallan on 2005-10-18
I'm not even logged in as the right user;  When I type that in I get this:

```
root@Doomspork:/root# sudo apt-get install gksudo
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gksudo
root@Doomspork:/root#

```

---

### Post by hunteramor on 2005-10-19
isn't it gksu?

---

### Post by SeanCallan on 2005-10-19
the gksu starts to install, but with all the repo problems, it gets 404 errors and cancels.

I guess I may try 5.04.  Breezy seems really buggy lately..

---

### Post by SeanCallan on 2005-10-19
Ok I finally, after many many apt-get updates got gksu to installed.

Now it tells me it can't copy over my login's Xauthorization file...

---

