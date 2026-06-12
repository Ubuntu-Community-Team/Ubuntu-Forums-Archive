---
title: "how to restrict the HIBERNATE function in Gnome, KDE,..."
date: 2007-03-14
forum: Desktop Effects &amp; Customization
---

### Post by levente81 on 2007-03-14
Hi all!

I would like to restrict the hibernation on my computer. Users can log in (through VNC or simply at the computer), and they are able to hibernate the computer.

How can that be restricted? 

I could restrict the restart by changing the mode of restart and shutdown (in /sbin) to not executable, but this doesn't affect the hibernation.

Does anyone have an idea what can be done? :confused: 

Thanx!

---

### Post by Pigsflew on 2007-05-07
I also have this problem. I've just set up a xinetd Xvnc listener for screen :1 (port 5901) using GDM, and after some futzing around with font directories and XFIXES, it works fine. The only problem that remains is that I'd like to make it so that the logout dialog only offers "Lock Screen", "Logout", and "Switch User".

Right now it offers those three as well as "Suspend" and "Hibernate". How do I make those two not appear in the dialog if the user is connected via VNC? Is there a way?

Also, is there a way to make it ignore sounds played on a VNC session? Or (*crosses fingers*) forward them?

Any help is much appreciated ^_^

---

