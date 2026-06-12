---
title: "Issue with gnome panel and maybe startup issue?"
date: 2014-05-26
forum: Desktop Environments
---

### Post by masseylm11 on 2014-05-26
Hi,

When I log in as usual (under my own user name), the login screen and the lock screen both show 2 panels at the top, instead of one.  See picture attached. But it doesn't do this if I go to log in as a guest.
Also, upon successful login as myself, I get a dialog saying 'System error occured'. But it doesn't let me view any details.  This dialog never pops up if I log in as a guest.
I am guessing the problem(s) lie(s) in the way I configured my desktop, like a theme or something.  
Anyone know what might be going on here?  Thanks in advance for any help.
First image is when I choose myself to log in.  Second image is as guest.

---

### Post by ajgreeny on 2014-05-26
Gnome-panel? In Xubuntu?

Was that a typo that should have read xfce4-panel?

---

### Post by masseylm11 on 2014-05-26
Yes, xfce. Sorry bout that.

---

### Post by masseylm11 on 2014-05-27
I fixed it with this:
rm -r ~/.config/xfce4

and that worked nicely.  Idk what I did before to make the panel trip out before. haha. 
Marking as solved...

---

