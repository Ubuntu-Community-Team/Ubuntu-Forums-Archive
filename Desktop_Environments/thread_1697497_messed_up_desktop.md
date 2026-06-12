---
title: "messed up desktop"
date: 2011-02-28
forum: Desktop Environments
---

### Post by david-emm on 2011-02-28
OK I've messed up.
I deleted Panel from the main menu and now find that on start up I do not get to see the top and bottom tool bars. After opening a text window (CRTL-ALT-F1) I see the following:
Starting GNUStep distributed object mapper: start-stop-daemon: unable to stat /usr/bin/gdomap (No such file or directory)
Not starting jetty - edit /etc/default/jetty and change NO_START to be 0 (or comment it out)
However I can log in OK and all seems to work

I have found that if I install gnome-panel on the desktop and then open it, it installs the missing tool bars and all is working.

The question is what can I do to automate the process (or restore the missing links) so that all works on start up.

I don't want to reinstall Ubuntu if I can avoid it.

Thanks for any help. (and yes I messed up but its the only way to learn - isn't it)

---

### Post by ankith13 on 2011-03-01
probably i am little late in answering.... but if you are still stuck with the same problem you can try the following--
-->you can write down the steps in a .sh file and run it in the boo time...

let me know if still there is a problem..:)

---

### Post by david-emm on 2011-03-01
Thanks Ankith13, I'll do that is there is no other way.

---

### Post by david-emm on 2011-03-01
Found the way to put all right. Open System/Preferences/Applications and add gnome-panel to the Startup Programs. Case closed

---

