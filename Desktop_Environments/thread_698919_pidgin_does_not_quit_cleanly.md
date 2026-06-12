---
title: "pidgin does not quit cleanly"
date: 2008-02-16
forum: Desktop Environments
---

### Post by gmoore101 on 2008-02-16
running Ubuntu 7.10 and have latest upgrades. On i386.

When I close pidgin, say by the upper right hand corner X -window button, the GUI goes away, but the process, pidgin, is still running.
I can `kill` this process, but subsequent running of pidgin will not display any GUI.
(although the password box may pop up, but then no GUI after typing in password)

As a workaround, I can start pidgin by doing this:
pidgin -mc /tmp/tempdir_01

Not sure if I need the -m , but the -c starts up a new configuration directory, and pidgin's
GUI will display. True I have to create my account again, but at least I get it running.

Rebooting the computer is another work around.

Closing pidgin by choosing from the menu, Buddies-->Quit, will cause
the GUI to go away and the process to stop. Subsequent running of pidgin
(without the -mc) will work successfully.

In summary:  Buddies-->Quit works differently/successfully than the "X" button in the upper right hand corner of the GUI.

Any ideas ?

---

