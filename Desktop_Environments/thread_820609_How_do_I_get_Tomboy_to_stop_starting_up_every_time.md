---
title: "How do I get Tomboy to stop starting up every time I log in?"
date: 2008-06-06
forum: Desktop Environments
---

### Post by Schalken on 2008-06-06
Now how do I remove this infernal thing from my startup?

No, it's not under System > Preferences > Sessions > Startup Programs.

Yes, it is under System > Preferences > Sessions > Current Session (just like every other open program) but has the "Reset" style. But every time I remove it, or set it to "Trash", or set it to "Normal", and click apply, it starts up on login and it's there in the list again set to restart!

No, I don't have "Automatically remember currently running applications when I log out" checked under System > Preferences > Sessions > Session Options.

No, Tomboy doesn't have any options in its preferences dialog with regards to automatic startup.

No, I'm not uninstalling it. I love this app and have many notes in it.

There has to be SOME way of figuring out what is starting this thing!

---

### Post by flowevd on 2008-06-06
i have this problem too

---

### Post by mannheim on 2008-06-06
This may be nothing to do with Tomboy per se. There is a bug with the session-saving stuff that means that, if you ever just once turn on auto_save_session, then you are doomed to have the same apps get launched at login, even after you have turned off the auto_save_session option. The bug is described [here]("https://bugs.launchpad.net/gnome-session/+bug/34321").

---

### Post by pt123 on 2008-06-06
You are not using the Tomboy panel applet?

---

### Post by Schalken on 2008-06-06
Aha! AHHHAHAHAHAHAHAAA!!!

I woke up this morning and asked myself "What could possibly depend on Tomboy running?"

Deskbar!

The plugin for Deskbar that lets you search your Tomboy notes needs Tomboy running (because it searches your notes via D-Bus), and starts it if it's not.

So disable the plugin and everything is rosy again. :popcorn:

---

### Post by brazilla ray on 2008-06-13
> **mannheim said:**
> This may be nothing to do with Tomboy per se. There is a bug with the session-saving stuff that means that, if you ever just once turn on auto_save_session, then you are doomed to have the same apps get launched at login, even after you have turned off the auto_save_session option. The bug is described [here]("https://bugs.launchpad.net/gnome-session/+bug/34321").

The fix in the bug report on launchpad worked for me- delete ~/.gnome2/session.

---

