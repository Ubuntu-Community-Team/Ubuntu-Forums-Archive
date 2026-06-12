---
title: "Let non-power user turn off computer"
date: 2010-05-23
forum: Desktop Environments
---

### Post by eyelessfade on 2010-05-23
In 8.04 even a non-power user could turn off the computer even if other people was logged in, not anymore. How do I enable it again. I don't want to let all my user be power-users, but I will let them turn off the computer locally even if someone else is logged in.

---

### Post by eyelessfade on 2010-05-24
anyone? Is there a special power group?

---

### Post by eyelessfade on 2010-06-25
Not possible?

---

### Post by BigJules on 2010-06-25
Sure is a way - use sudoers to allow non-root to issue the shutdown command. A very useful thing all round, sudoers, worth looking at in detail sometime.

Meanwhile for you, as root enter: visudo -s

At the end of the file being edited enter the line:

%user  ALL=(ALL) NOPASSWD:/sbin/shutdown, /sbin/reboot

at 'user' insert your user-name. This will allow instant shutdown or reboot. I use two separate launcher icons on the top panel and threw away the usual one with the menu etc. The first (reboot) invokes the command as an application, not in a terminal:

sudo shutdown -r now

The second (power down) :

sudo shutdown -P now

Neat, fussless, and your choice of cool icons...

---

### Post by eyelessfade on 2010-06-25
Thanks should have thought about visudo :)

---

