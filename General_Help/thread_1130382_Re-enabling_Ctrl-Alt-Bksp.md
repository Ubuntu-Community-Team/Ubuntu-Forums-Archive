---
title: "Re-enabling Ctrl-Alt-Bksp?"
date: 2009-04-19
forum: General Help
---

### Post by scott8035 on 2009-04-19
I noticed under Ubuntu that Ctrl-Alt-Bksp doesn't kill your X session like it does everywhere else. How do you re-enable it?
---scott

---

### Post by oleander on 2009-04-19
There's a page that addresses that on Ubuntu.com, it says that:

> Ctrl-Alt-Backspace is now disabled, to reduce issues experienced by users who accidentally trigger the key combo. Users who do want this function can enable it in their xorg.conf, or via the command dontzap --disable. 

You can check out the page here: [http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)

I hope this helped!

~Oleander

---

### Post by sisco311 on 2009-04-19
Add *Option          "DontZap"               "false"* to the *ServerFlags* section in xorg.conf.

[https://wiki.ubuntu.com/X/Config/DontZap]("https://wiki.ubuntu.com/X/Config/DontZap")

---

### Post by paradigm2 on 2009-04-19
> **scott8035 said:**
> I noticed under Ubuntu that Ctrl-Alt-Bksp doesn't kill your X session like it does everywhere else. How do you re-enable it?
---scott

For anyone else reading on Jaunty, you can do:

ALT GR (this is the RIGHT ALT key) + SYSRQ + K

to do what it did before.

---

### Post by malachi1990 on 2009-04-23
I've turned off dontzap  and neither of these work.  Are there any other ways to get the ctrl+alt+backspace effect back?

---

### Post by shafin on 2009-04-24
> **paradigm2 said:**
> For anyone else reading on Jaunty, you can do:

ALT GR (this is the RIGHT ALT key) + SYSRQ + K

to do what it did before.
This one works for me.
Thanks for the tip

---

