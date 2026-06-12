---
title: "Can't start apps after rsync"
date: 2009-03-05
forum: Desktop Environments
---

### Post by anash on 2009-03-05
I have two similar machines running Ubuntu 8.10 in two different locations.  Today I ran rsync from the home directory of the remote machine into the home directory of my local machine.  After this, I could not start any applications (from the task bar, browser, etc.).  For example if I click on the terminal icon, I see "starting terminal" at the bottom for a little while, then it goes away and nothing happens.

If I type e.g. xterm, I get:
No protocol specified
xterm Xt error: Can't open display: :0.0

I think that somehow I copied something from the remote machine that messed up some gnome or X file, perhaps one having to do with the local IP address or something like that.  I am lost and stuck.  Any suggestions?

I am afraid of logging out since right now I at least have some things up and running.  If I go to a text mode console, I can not log in as myself.  However, if I ssh I can log in. Perhaps I am wrong, but that's what seems to be happening.

---

