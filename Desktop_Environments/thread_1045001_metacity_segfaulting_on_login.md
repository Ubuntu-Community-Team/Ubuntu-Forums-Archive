---
title: "metacity segfaulting on login"
date: 2009-01-20
forum: Desktop Environments
---

### Post by blaq84 on 2009-01-20
Hey all,
For some reason, after installing the latest round of updates (of which i don't recall there being any for metacity) I can't log into gnome anymore.

I get the login screen and when I enter my username/password, I get the startup sound, but a blank desktop (a humanish-color, not my desktop background). The mouse works and I get a mouse pointer, but it just sits there doing nothing. A quick dmesg from a tty gives me:

[ 1063.540529] metacity[7447]: segfault at 0 ip 080abab3 sp bfde6fc0 error 4 in metacity[8048000+7a000]

Every time I kill X and try and login again I'll get another segfault appearing exactly as above, except for the 'sp' value changing (as well as the time, pid etc obviously).

I haven't recently changed any configuration parameters of metacity (not that there are many to begin with :P). I've tried clearing my metacity sessions (thinking perhaps it's falling over on some out of bounds parameter or something) from ~/.metacity/sessions/ but it's still not working.

Any ideas? I'd like to file a bug report but I'd like to get some more information (logs, configurations etc.) first. I don't know where metacity keeps its log files (if it does keep logs at all) to try and see where it's failing.

Since metacity doesn't seem to have a website or any mechanism where I can contact the developers directly, I thought it would be best to ask here.

For the record I'm on 8.10, metacity 2.24.0

Cheers,
Mike


Edit:
I've also tried creating a new user and trying to login under that thinking perhaps it's a user-level config problem, same thing happening.

I've also tried using an older kernel thinking perhaps it's the newer kernel causing it (as it's only started after the last update, which included a kernel update) but i still get the same problem.

---

### Post by adebree on 2009-02-04
I'm experiencing the same problems... I found some references to authentication problems, but unable to any fix. Did you find something or even fixed it?

[edit]
Found the following as well: [http://ubuntuforums.org/showthread.php?t=780179](http://ubuntuforums.org/showthread.php?t=780179)

Reinstalling dbus didn't fix it though..
[/edit]

---

