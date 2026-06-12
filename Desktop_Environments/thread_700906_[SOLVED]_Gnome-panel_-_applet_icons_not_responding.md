---
title: "[SOLVED] Gnome-panel - applet icons not responding"
date: 2008-02-18
forum: Desktop Environments
---

### Post by imoatama on 2008-02-18
A little while ago my applet icons stopped working - that is, nm-applet, update manager, SCIM, etc do not respond to mouseover, single click or right click. The deskbar applet and volume control do respond however.

Ctrl-Alt-Backspace restarting X and logging back in fixes this problem, but i'm getting mighty sick of the log-in, restart, log-in routine i go thru every boot just to use tray icon applications like amarok and azureus.

Anyone got any ideas what could be causing this? What is the difference between the first X session and the second, surely they should be the same?

Edit: sorry, running 7.10 on a dell Inspiron 6400, with compiz master and ATI X1400M.

---

### Post by aysiu on 2008-02-18
Does the problem occur when you log in as another user?

Hint: if you are the only user, create another test user.

---

### Post by imoatama on 2008-02-21
The problem does not occur when I log in as another user.

It occurs only on the first login for my account. Loggin out and back in again, as well as Ctrl-Alt-Backspace and logging in again both fix the problem. I'm baffled - thought maybe it was sommething to do with gdm but if it's not happening in both accounts this is unlikely.

Any ideas?

---

### Post by imoatama on 2008-02-21
OK very weird but it seems i have fixed it, by removing the notification area and the re-adding it to the panel slightly rearranged.

Edit: OK problem recurs, but I have found the source. It was being caused by the input-shaping behaviour of freewins. Discussed in [ this thread]("http://ubuntuforums.org/showthread.php?t=668359&page=3")

---

