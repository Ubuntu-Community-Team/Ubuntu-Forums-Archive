---
title: "no protocol specified unable to open display 0.0"
date: 2008-11-02
forum: Desktop Environments
---

### Post by nanjil on 2008-11-02
hello:

in hardy 8.10

I opened a terminal as user 'b' in user b's desktop (gnome). then I 'su'ed'to user 'a'. then tried to, as user 'a' open a new terminal . then i get the message

no protocol specified

xt xterm error unable to display 0:0

what does this mean? how do i fix it?

thanx

---

### Post by stickboy2642 on 2008-11-02
What command did you use to sudo to that user.  If you simply typed 'su a' then that might be your problem.  Try 'su - a'.  The - tells su to take on the user's environment.  I have seen this problem while sudo'd to su, but have never tried with a different user.

---

