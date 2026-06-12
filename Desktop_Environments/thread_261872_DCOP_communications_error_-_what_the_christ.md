---
title: "DCOP communications error - what the christ?"
date: 2006-09-20
forum: Desktop Environments
---

### Post by hygraed on 2006-09-20
When I try to start a KDE app in GNOME (KolourPaint, Amarok), I get an error window saying

> There was an error setting up inter-process communications for KDE. The message returned by the system was:

Could not open network socket

Please check that the "dcopserver" program is running!
Then, if I try to save an image in KolourPaint or play music in Amarok, I get this:

> Could not start process Unable to create io-slave: Permission denied.

I've tried starting dcopserver through the terminal, but it doesn't help. This has never happened before; I've been using Amarok and KolourPaint for months without any problems. What's the deal?

---

### Post by hygraed on 2006-09-21
Bumping this thread, I really need help.

---

### Post by hygraed on 2006-09-21
Okay, I tried running it with sudo and it worked fine. No error messages, and I was able to save and restore files as normal (KolourPaint). It appears that the permissions for the KDE stuff it needs to open have changed, but I haven't the foggiest idea why.

---

### Post by beefcurry on 2007-01-21
Yeah, i have this exact error as well. Any ideas?

---

### Post by Canadia on 2007-02-19
I have the same problem as well, on a freshly installed edgy

---

### Post by Unterseeboot_234 on 2007-03-10
When I tried to install a free program to do UML Diagrams, it asked if I wanted DCOP server. I said no, it said "be sure to start DCOP when use UML Diagrammer". I ended up removing UML Diagrammer for that reason. This morning I let a system update happen. The Updater refused to update a DVD/CD rip because of some conflict. I did let it update Speech.

Now, I've got 

> There was an error setting up inter-process communications for KDE. The message returned by the system was:

Could not open network socket

Please check that the "dcopserver" program is running!

And now, a lot of software bounces a Warning dialog, Cannot understand File i/o, Cannot save .config. Warning Defaults will not be saved. I have to cancel a clutter of Warning Dialogs.

I've got too much work on my machine to reformat and re-install. WTF! What the F^^^K!

Does anybody have an answer on DCOP???

---

### Post by beefcurry on 2007-03-10
Well if you are really desperate open the program with sudo infront of it. I cant really remember how I fixed my problem sorry. I remember Google helped me fix it :).

---

### Post by ganglia on 2007-04-08
ok it's about permissions,
and it's i think also a bug.
because after i install kde applications on gnome created .kde folder in home directory is owned by root. Moreover no other permissions are given to neither groups nor others.
That's why a kde application wants to reach this file but apperantly it cannot then errors occur.
To solve this problem go to your home folder than;

```
sudo chown -hR [your login name] .kde
```

then enter your password, restart your kde application i hope it solves the problem,
at least it solved mine :)

---

### Post by AeroGT3 on 2008-04-27
> **ganglia said:**
> ok it's about permissions,
and it's i think also a bug.
because after i install kde applications on gnome created .kde folder in home directory is owned by root. Moreover no other permissions are given to neither groups nor others.
That's why a kde application wants to reach this file but apperantly it cannot then errors occur.
To solve this problem go to your home folder than;

```
sudo chown -hR [your login name] .kde
```

then enter your password, restart your kde application i hope it solves the problem,
at least it solved mine :)




That worked perfectly!!! Thanks so much!

Cheers,

-Robert

---

### Post by Blara on 2008-05-06
I just "upgraded" my kubuntu gutsy to hardy and I ran into the same problem, I've tried all fixes and sure the error message stops appearing... but KDE won't start, only a konsole window opens up, I can start programs from the konsole but I want my KDE back :(

---

