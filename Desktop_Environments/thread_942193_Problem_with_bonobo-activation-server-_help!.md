---
title: "Problem with bonobo-activation-server- help!"
date: 2008-10-08
forum: Desktop Environments
---

### Post by CharonM72 on 2008-10-08
Whenever I start GNOME (regularly, not failsafe), the top and bottom panels don't appear, sometimes the desktop icons don't appear, and Nautilus fails with the error: "Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting Nautilus may help fix the problem."

Needless to say, killing bonobo-activation-server doesn't help (in fact it doesn't seem to exist). I also tried killing nautilus, ubuntu-desktop, and gnome-panel, without avail. I've reinstalled all the bonobo-related packages, and who knows what else. Also my date and time are all accurate. Any other advice?

I'm running Ubuntu 8.04 on a custom computer with an Intel 32 bit processor.

I know this problem has been brought up before but only ever for Macs it seems, and I've tried all of the suggestions and nothing has worked.

---

### Post by n2dabloo on 2008-10-16
I have the same _exact_ problem.  Is anyone working on this?  Please help.  The only way I can use Ubuntu right now is with the Failsafe Mode.

---

### Post by quidome on 2008-10-16
I've experienced this on both Hardy and Intrepid. I could not solve it. Even a new created user without an existing profile would not be able to use the regular gnome account (so rm .config* .gnome* is not a sollution).
For me the only way to fix this was a complete reinstall (I don't format /home and /opt, so I can keep most important stuff anyway). I proper fix would be very welcome as I use this laptop at work and colleagues already tell me to start using Fedora.

---

### Post by CharonM72 on 2008-10-16
I found that the problem had to do with a recent installation of SCIM. By uninstalling SCIM I was able to log back in normally. I was never able to find a solution to the problem so now I'm trying to get UIM to work, with limited success.
Try to think of the last thing you did before the problem occurred, and undo it.

---

### Post by nick.ncs on 2008-11-04
Ok guys..... facing this same problem this morning after i updated to 8.10.... tried searching for a solution but to no avail... did anyone get the solution btw....

---

### Post by polybius on 2008-11-16
I have exactly the same problem on two of my 4 machines.  Two others do not have it.  All are running Ubuntu.  Both machines with this problem are running 8.04, while the two that do not are running 7.10.  It is getting very annoying, and I haven't been able to find a solution.

I'm considering switching to KDE.

---

