---
title: "AfterStep"
date: 2007-11-18
forum: Desktop Environments
---

### Post by r.hall on 2007-11-18
I decided to try out AfterStep. Even though this whole thing seems really alien to me since I was previously using gnome, I sorta like it. It has a techy feel to it and the setup is more convenient than flashy, which I like.

I have a few questions though.

At the top, there's a row of square buttons with icons in them. It's like a dock, with the terminal, internet, email, etc. How do I edit these to run different commands, have different icons, and most importantly, how do I add a button to it?

Also, any tips would be appreciated.

---

### Post by Dean Powell on 2007-12-06
Hi:

The line of icons at the top that acts like a dock is called the "wharf".  To edit it, copy /etc/X11/afterstep/wharf to $HOME/.afterstep/wharf, then edit it from there.

The default is actually two wharfs (wharves?) -- The line of icons along the right hand side at the bottom is also a wharf and controlled from the same file.  The wharf along the right is referred to in this file as the MonitorWharf, but you can actually call it whatever you like.  The layout of the wharf file takes some getting used to, but it's easy to figure out once you look at it.

Hope this helps.

---

