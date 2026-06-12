---
title: "Trouble exporting gnome-terminal and Evolution"
date: 2009-07-24
forum: Desktop Environments
---

### Post by worik on 2009-07-24
Friends

I have been using my laptop as a terminal for my desktop for ages.  (X
over ssh) but lately after a bout of upgrades it has not worked so
well.

I can run emacs OK (exporting the display to my laptop) but when I run
gnome-terminal or Evolution they do not work.

gnome-terminal fails with...

Failed to get the session bus: Failed to connect to socket
/tmp/dbus-YTMEmBA64u: Connection refused
Falling back to non-factory mode.
Failed to contact the GConf daemon; exiting.

There are no /tmp/dbus-* anything.

Evolution just fails.  It does start, it is in the process table, but
no exported display.  Runs fine on the desktop machine.  After a while
it does struggle to put up an error dialog that says "An error
occurred while loading or saving configuration information for
Evolution Connector for Microsoft Exchange. Some of your configuration
settings may not work properly.".  There is a details section but I
have not managed to record that yet.  If I wait long enough, about 10
minutes, it puts up a new user dialog to guide me through setting up
an account.

I Googled the error and the only hint was that dbus and/or hal are not
running.  But they are!

baffled
Worik

---

### Post by worik on 2009-08-04
I have upgraded my laptop to 9.04 (same as desktop) and the problem persists.

It was not fixed by using -Y instead of -X in the ssh command.

worik@delilah:~$ gnome-terminal
Failed to get the session bus: Failed to connect to socket /tmp/dbus-EEPP1p04h5: Connection refused
Falling back to non-factory mode.
Failed to contact the GConf daemon; exiting.

When I run evolution it starts to make me a new account, very very painfully slowly!

This is very frustrating as I need to use my laptop as a terminal

Worik

---

