---
title: "Xserver problems?"
date: 2007-05-19
forum: Desktop Environments
---

### Post by Vuddha on 2007-05-19
Hi all,

I just reinstalled Feisty on my D600.

Everything is working well, but it seems that the xserver is crashing (I think this is what's happening).

It's totally unpredictable when it will happen.  I might be using Open Office, or Lyx, or Firefox.  All of a sudden, a black screen with some text (which I can't read because it disappears just as quickly) will appear and I'll be at the login screen.

What's going on?  How can I fix this?

Thanks,
--Vu

---

### Post by trigun on 2007-05-19
you should read the log of the xserver  to see the problem;)

---

### Post by RedSquirrel on 2007-05-19
Have a look in /var/log/Xorg.0.log and ~/.xsession-errors.

```
more /var/log/Xorg.0.log
```

and

```
more ~/.xsession-errors
```

---

