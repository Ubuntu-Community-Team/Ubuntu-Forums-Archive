---
title: "Different users, different screen resolutions ?"
date: 2006-07-31
forum: Desktop Environments
---

### Post by Jhongy on 2006-07-31
I have set up xorg to allow two resolutions - 1440x900 & 800x600.

But I can't seem to set up different resolutions on a per-user basis.

For example, I have 1440x900 working under User1. I can log out, then log in as User2, set the screen resolution to 800x600. But when I log out and back in as User1, their resolution has also changed to 800x600 -- argh!

I expect this has something to do with using gdm as the login manager (?).... any solutions? :confused:

---

### Post by RAOF on 2006-07-31
I don't think that what you want is possible, at least at the moment.  One active resolution per X server :).

I think what you want would need to be added to the gnome user profile stuff (and checked on switching user).  This is almost certainly a (fairly simple) programming problem, but I don't think that anything does it at the moment.

---

### Post by Jhongy on 2006-07-31
Thanks -- 

So I can't, say, kill and restart the X-server on logout / login?

Maybe there's a simpler way to do what I want then:

I want to run some programs (mythtv, DVD players) in 800x600. The problem is, when I chage resolution from 1440x900, full-screen apps seem still to fill the 1440x900 space, and I only get to see the top-left corner of them. 

I understand I can use something like *xrandr* instead, but, when I switch back to 1440x900 from 800x600, the Gnome desktop is totally farked -- things on the panels don't move back out to the edges.

There must be a simple-ish script I can bash out and make into a launcher for progs like Mythtv??

---

