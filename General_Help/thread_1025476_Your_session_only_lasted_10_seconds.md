---
title: "Your session only lasted 10 seconds"
date: 2008-12-30
forum: General Help
---

### Post by lordfrikk on 2008-12-30
Hi!

I have this problem - when I try to login, Ubuntu gives me the "your session only lasted 10 seconds" message. I read in other thread one of the solutions to this problem is to do "sudo chown [username] .ICEauthority", but when I try, Ubuntu gives me "Segmentation fault" because of sudo. I can't use any of other solutions because they need to be executed as root as well.

This is report given with the "lasted..." message:

/etc/gdm/Xsession: Beginning session setup
Setting IM through im-switch for locale = cs_CZ
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked /etc/X11/xinit/xinput.d/default
SESSION_MANAGER = local/lukas-desktop:/tmp/.ICE-unix/5789

EDIT

Also, after failed sudo, this is result of tail /var/log/messages

> Dec 30 30 12:03:31 lukas-desktop kernel : [98.643141] sudo [5720] : segfault at bf5f1480 eip b7f1733e esp 5f1480 error 6

---

### Post by rudihawk on 2008-12-30
Try a "Failsafe Session"?

---

### Post by lordfrikk on 2008-12-30
> **rudihawk said:**
> Try a "Failsafe Session"?

I did that immediately, "Failsafe Gnome" also gives me this message. I can only access "Failsafe Terminal".

---

### Post by gettinoriginal on 2008-12-30
In reading some other threads, it seems the /tmp folder somehow was reassigned root ownership.  By changing it to user ownership, they regained the use of their system.

---

### Post by rudihawk on 2008-12-30
If you can access the terminal try adding a new user and see what happens if you try login again.

```
adduser <username>
```

---

### Post by lordfrikk on 2009-01-01
I added new user under recovery menu (as I said previously sudo isn't working!) but the same error message popped up... I think something is seriously wrong. Any ideas?:(

---

