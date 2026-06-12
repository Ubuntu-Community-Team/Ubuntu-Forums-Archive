---
title: "How do I Switch User in Enlightenment?"
date: 2008-03-02
forum: Desktop Environments
---

### Post by keratos on 2008-03-02
Hi

I'm using the Enlightenment 0.16.999.041 as a DM on my OpenGEU (ubuntu fork - unofficial!)

Enlightenment does not have a Switch User capability as in KDE or Gnome (or rather I cannot find it if its there)

I've managed to login to a virtual console vty4 and issue the command
```

startx -- :1

```
which fires up another virtual Enlightenment session.

However, I want to automate this from a menu option in Enlightenment.

I know how to add the menu but I dont know how to accomplish the vty login and startx command.

Any ideas.

Thanks

---

### Post by _mrv on 2008-03-28
Hi,

I would also like to know how to accomplish this. Most of the time either me or my wife is logged in and I really don't want to log out if my wife wants to check her facebook profile :)

I would like to lock my session and then my wife could just press "switch user" button and log in.

---

### Post by keratos on 2008-03-29
I ended up going back to xfce4.

---

### Post by _mrv on 2008-03-29
Does anybody know if it would be possible to replace Enlightenment's "lock" application with gnome-screensaver or similar? I would really like to participate in developing E17 by using it, reporting bugs etc., but without multi-user login support it's no joy...

---

### Post by smartboyathome on 2008-03-31
There isn't a way right now. The lock app is hard-coded.

---

