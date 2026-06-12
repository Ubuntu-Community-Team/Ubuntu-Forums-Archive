---
title: "Just a little question regarding TV output"
date: 2008-07-14
forum: Desktop Environments
---

### Post by hector512 on 2008-07-14
How do I permanently disable it?

xrandr --output TV --off

This commands does the magic with a problem with my screen resolution caused by that output, but xrandr resets every log out or reboot so I need to know how do I disable it.

If you need more info let me know.

Thanks in advance.

---

### Post by Afkpuz on 2008-07-15
Well, I can teach you how to run that command at startup, if that helps at all.  You can run that command automatically every time you login.


System>Preferences>Sessions

Add a new entry and give it a name (ubuntu requires one), then, paste your command into the command box.  You don't have to add a comment unless you want to.  Also, I haven't figured out how to run commands that require sudo access.  The above method only works for commands that you have the permission to run.



Does that help?

---

### Post by hector512 on 2008-07-16
Thanks for your reply! Yes it did work and most of the problems are gone. Now I just need to figure a way to run the command BEFORE the login screen comes out to mark this topic as solved.

Any ideas?

---

### Post by Afkpuz on 2008-07-17
I don't know the answer to running before login, but I am curious as to why you would need to do that?  Isn't starting on login enough?

---

