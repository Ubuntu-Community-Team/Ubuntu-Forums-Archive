---
title: "Possible GDM bug with login"
date: 2006-07-30
forum: Desktop Environments
---

### Post by glinsvad on 2006-07-30
I've been noticing that my Dapper install has a little quirk. After bootup when I go to type in username/password the very first keystroke is not registered. Let's say I'm trying to log in as "glinsvad" - basically the username will say "linsvad". This behaviour does not depend on the the username used (thus not a keyboard error) or personal typing screwups (other people have the same experience).

Is this a problem on my machine only or have you experienced the same thing on your Dapper installs?

---

### Post by fabiand on 2006-07-30
Hey,

gdm ist workinf fine for me.

---

### Post by glinsvad on 2006-07-31
Hmm I don't get what the problem is. It never happened in Breezy.

Perhaps I'll just have to get used to typing "gglinsvad"...

---

### Post by glinsvad on 2006-07-31
Bugreport exists but is yet unconfirmed:
[https://launchpad.net/distros/ubuntu/+source/gdm/+bug/46238]("https://launchpad.net/distros/ubuntu/+source/gdm/+bug/46238")

---

### Post by Tomosaur on 2006-07-31
Well, sounds like it's confirmed then :P

Seems like a problem with keyboard focus, hopefully it should be ironed out soonish if people are confirming it.

Try clicking within the text box before you start typing to gain focus.

---

