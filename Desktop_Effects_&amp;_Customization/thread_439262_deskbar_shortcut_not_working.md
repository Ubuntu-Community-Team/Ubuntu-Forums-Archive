---
title: "deskbar shortcut not working"
date: 2007-05-10
forum: Desktop Effects &amp; Customization
---

### Post by db9s on 2007-05-10
solved!

---

### Post by jbro on 2007-05-10
When you say that Deskbar stopped working, what exactly do you mean? 

I too am running Beryl and I have noticed there are some focus issues with Beryl and Deskbar. In particular, I could hit my hot key, and the Deskbar GUI appears, but the focus remains on the currenty focuses application, which means I would have to manually click on Deskbar before I could type anything. This basically defeats the purpose of Deskbar for me (not having to use the mouse.) 

Reading around I found that the Beryl focus-stealing prevention causes problems with Deskbar (and some other applets.) In Beryl Settings Manager->General Options I changed the "Level of Focus Stealing Prevention" from Low to None. This seems to have solved the problem. I did not have to add a Deskbar shortcut key to the Beryl window manager. I'm still seeing if I actually miss the focus stealing prevention feature. If this sounds like your problem, you should try this out.

Regards,
jbro

---

### Post by geetarista on 2007-06-10
So how did you solve it?

---

### Post by jbro on 2007-06-11
If you refer to solving the not-getting-focus-problem, the answer is the following:

> **jbro said:**
> Reading around I found that the Beryl focus-stealing prevention causes problems with Deskbar (and some other applets.) In Beryl Settings Manager->General Options I changed the "Level of Focus Stealing Prevention" from Low to None. This seems to have solved the problem. I did not have to add a Deskbar shortcut key to the Beryl window manager.

---

### Post by geetarista on 2007-06-12
I was actually responding to db9s, but I didn't even know what the problem was since they just edited their post instead of replying to it.  I'm actually not having a problem with focus, but with deskbar crashing.  I filled out a bug report, but they said that it was a duplicate and that it has already been resolved.

So why is it still crashing...  :)  Doesn't make sense to me!

---

### Post by geetarista on 2007-06-20
Well, I disabled the tracker plugin for deskbar and now everything seems to work.  I'm not sure if this is a deskbar or a tracker problem, but hopefully it is fixed soon because I love them both!

---

