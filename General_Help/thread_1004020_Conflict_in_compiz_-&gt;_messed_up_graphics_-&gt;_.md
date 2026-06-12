---
title: "Conflict in compiz -&gt; messed up graphics -&gt; help!?"
date: 2008-12-06
forum: General Help
---

### Post by alexvasile on 2008-12-06
Hi guys,
I have a small problem. Umm...I was looking through the compiz settings about 5 mins ago on my ubuntu partition, and stupidly enough I enabled both the magnification tool and the other application that magnifies ignoring the "conflict" I was creating. (being used to windows and seeing no cancel button in the error message, I hit "ignore the conflict" thinking I will go back and uncheck the second magnification tool. Immediately after saying ignore, my graphics got all messed up and ubuntu brought me back to the login screen. I tried logging in a couple of times and I get in for 1 second just to see my graphics go wild and then I'm brought back to the login screen.

To make this simple, I f****d something up. How can I undo this? or get back to a previous state before I made the change?

Thanks,
Alex

---

### Post by eternalnewbee on 2008-12-06
Reboot in safe mode.
Open a terminal and enter ```
metacity --replace
```
Then go to your compiz manager, and deselect what messed up your system.

---

### Post by Forlong on 2008-12-07
In case you can only boot into a terminal, log in under your regular user and run this command:
```
gconftool-2 -s -t string /desktop/gnome/session/required_components/windowmanager metacity
```
This will disable Compiz on startup.

---

### Post by Wartender on 2008-12-07
same thing happened and was solved[here]("http://ubuntuforums.org/showthread.php?t=1001005"). (by these two guys who just posted)

---

