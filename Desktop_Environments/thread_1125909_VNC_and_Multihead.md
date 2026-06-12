---
title: "VNC and Multihead"
date: 2009-04-14
forum: Desktop Environments
---

### Post by Zombie13 on 2009-04-14
Don't know if this is the right place for this or not, so Admins, feel free to move if need be (not that you need my permission).

What I want to do is this: share out one display on a multihead system.

Here's the deal, I have a multihead capable system, and I can setup Xinerama, and I can share out the *whole* thing.  Quite easily in fact.  What I want to do is share out only one of the 'monitors' as it were.  So, in X terms, I have Display :0.0 and :0.1.  One is a LVDS@1600x1050, the other is a VGA@1280x1024.  I want to share out the 1280x1024 so that from another machine (read HOME) I can connect to it and not have a 2960x1050 display that I have to scroll around.  

Does that make sense?

I know the windows version of RealVNC allows you to share out a specific 'monitor', but I have as yet not found a way to do this with Linux. 

I had thought an option to vino-server would be what I need, but I can't find one that works.

Any ideas would be most appreciated.

Thanks for your time.
Z.

---

### Post by Zombie13 on 2009-04-15
Nevermind.  I was incorrect in saying I had display :0.0 and :0.1.  The way 8.10 does multihead is to have 1 screen of large resolution spread across 2 (or more) monitors.  So, I only have display :0.0 which means I can't do what I wanted.  Oh well.

Z.

---

