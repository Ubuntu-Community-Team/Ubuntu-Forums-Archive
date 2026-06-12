---
title: "[SOLVED] GUTSY - Create login session with XGL Disabled?"
date: 2007-11-18
forum: Desktop Effects &amp; Customization
---

### Post by ryth on 2007-11-18
Hi folks.

Just installed a clean version of Gutsy.  What i need to accomplish is the following:

* Establish a session that is selectable from the "sessions" menu at the login prompt that will allow me to log in to Gnome with XGL disabled.  Caveat being that I would like this to be a secondary option, so that normally when I log in XGL will be active.

This used to be possible on Feisty, but I'm unsure of how to implement it on Gutsy.  Reason being that as per **[this thread]("http://ubuntuforums.org/showthread.php?p=3794497#post3794497")**, MythTV will not run for me while XGL is active.

Thanks in advance.

R.

---

### Post by Forlong on 2007-11-18
The easiest thing would be creating a new user (only for MythTV) and disable Xgl for that one.
You can do that simply by creating the file```

~/.config/xserver-xgl/disable
```

---

### Post by ryth on 2007-11-18
Thanks Forlong!  I hadn't thought of that, with the easy user-switching thats a far superior way of handling the problem than what I had in mind.

Now if only I could get Myth working with XGL I'd be even happier.

Cheers.

R.

---

### Post by kooldino on 2007-12-05
I'll give this a whirl myself.

@ OP - what do you mean by "fast user switching"?  Is it supported in KDE?

---

### Post by Rohaq on 2007-12-11
Is there any way I can make a new session with XGL disabled for my current user account? It'd be much better for me than making a new user.

---

