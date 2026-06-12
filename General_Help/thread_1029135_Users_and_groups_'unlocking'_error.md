---
title: "Users and groups 'unlocking' error"
date: 2009-01-03
forum: General Help
---

### Post by Admiral Yi on 2009-01-03
Hello,
Yesterday when I tried to unlock my user in users and groups I got an error message saying that "an unexpected error has occurred". Today i tried again and it still doesn't work. I click on unlock, and after a minute or so it comes up with the error. I tried running it in the terminal (using the command 'sudo users-admin') and got this message in the terminal:

** (users-admin:9357): CRITICAL **: Unable to lookup session information for process '9357'

The users and groups thing came up, but 'unlock' was greyed out. What can I do?

---

### Post by mike2357 on 2009-01-03
I wish I had some advice for the problem you're experiencing.  However, there are command line equivalents you can run, such as adduser, deluser, usermod, addgroup, delgroup and groupmod.  You can learn about the options by running, for example:

man adduser

Each would have to be run as root, as in:

sudo adduser

---

### Post by alanbrodbeck on 2009-11-04
I, got the same error message when attempting to unlock Users and Groups; and got very similar error with sudo users-admin (and was still unable to edit user settings).
The solution for me was 

Applications => Accessories => Terminal
When the terminal window appears type:
$ passwd

after being prompted to change my password I was able to properly unlock Users and Groups.

---

### Post by gerryg001 on 2010-01-23
After quite a bit of searching, it appears that a number of different issues can cause the same symptom. I've tried about a half-dozen "solutions" thus far, with no luck. When this first happened about two weeks ago, another user suggested a reinstall of dbus, which fixed it. Now it's back again, and that no longer works.

I really wish that somebody familiar with gdm or gnome and policy-kit would give some clues on tracing this issue. I don't see anything related in the log files. So, when you see

"Unable to lookup session information for process"

where do you look?

---

