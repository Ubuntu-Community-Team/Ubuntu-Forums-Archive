---
title: "cannot switch back to runing session after switch user"
date: 2007-01-01
forum: Desktop Environments
---

### Post by klausthorn on 2007-01-01
when a user wants to switch back to a running session after someone already switched users, he either

1) clicks on the panel  turnoff symbol -> switch user

which gets him to gdm and he is stuck!
He needs a "switch to running session" option in the menu 
of the gdm (greeter?), better a list with the running session

Pressing Ctrl-Alt-F7,F8,... is not feaseble for the users, they
are not linux-experienced enough and would forget it even if
I told them. besides there are hundrets of users in my network,
new ones every week; can't tell them all.

fast-user-switch-panel is no solution because
each user would have to add it to his panel and because
this panel applet also shows users not having a running session,
which are too many in my case. And it would be a distracting
waste of panel-space most of the time, when no other sessions
are running. The panel should be kept clean.
Besides, users would click on the shuitdown icon anyway,
because they are used to it and it has a big switch user symbol
and because they are used to it from windows (that switch user
is grouped with restart and such)


2) comes to a locked screen -> switch user

shows all users, not just the ones having a running session,
which is too huge a list. Worsening: users with a running
session are not distinguishable from others in this list


I've read a rumor that during Dapper Drake Beta there was a menu entry in the gdm menu to return to a running session. How can I turn it back on?!

running ubuntu 6.06 Dapper Drake LTS on x86

---

### Post by gabspeck on 2007-01-19
There's an "Exit" option in the lower left corner "Options" menu that takes you to the previous user... (the screen is locked, so if you have no screensaver set it's just black, so you must move your mouse to enter the password)

---

### Post by klausthorn on 2007-01-22
gabspeck: thanks for the hint. Indeed this works, but the users would never expect this behaviour from the Exit Button. Instead they expect it to trigger shutdown or similar things.

Since there are many users, who want to concentrate on their work, I'm not trying to teach them all this or any other workaround. Instead I need a fix that enables them to help themselves without additional "linux lessons".

For example when they click on Menu Panel -> turnoff-Symbol -> switch user they need to see a list of running sessions to choose from, which would be easy: just run gdmflexiserver instead of showing the gdm login page. Maybe someone knows a way to change this once for all users of one computer in some system/gdm settings?

---

### Post by tone33 on 2008-02-07
Was a solution found for this?  I also noticed the same thing when switching users...

---

