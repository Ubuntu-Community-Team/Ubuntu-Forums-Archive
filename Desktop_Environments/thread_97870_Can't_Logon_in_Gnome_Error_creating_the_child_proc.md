---
title: "Can't Logon in Gnome: Error creating the child process for this terminal?"
date: 2005-12-01
forum: Desktop Environments
---

### Post by bcleesha2000 on 2005-12-01
Help! I'm a relative newbie regarding ubuntu.. and I recently tried going through an update to Breezy. Everything went smoothly, but now I find that when after typing in my username and password on the gnome logon screen, I get a blank screen with a terminal window in the top left corner, and an error dialog that reads:

"There was an error creating the child process for this terminal".

.. I'm completely befuddled. I can do alt-ctrl-F1, etc, to switch to the regular console mode and logon there, but I'm otherwise feeling quite trapped...

I searched for this problem in other places, and people have recommended uninstalling and reinstalling udev, amongst other things.. I've tried that, but the problem persists. 

If I try logging in under a failsafe mode, it literally freezes in place and I need to force a reboot from one of the other ttys.

Anyone have any idea what's going on? Or at least how I can fix this? :)

---

### Post by ChrisNiemy on 2006-11-18
I have the same error message when starting gnome-terminal.

Under edgy eft, but the mysterious thing is:
the error only occurs with self-compiled kernel.

Even different self-compiled kernels, 2.6.18 and 2.6.17, both with ck-patchset.

Booting with the 2.6.17-10-generic from ubuntu, it works. Otherwise it won't.

Strange, isn't it? Anyone an idea?

Regards,
Chris

EDIT:
Regarding to my self compiled kernel, it could be connected with some codepage options. Or maybe a "sudo dpkg-reconfigure console-setup" will help

PS: xterm refuses to start also

---

