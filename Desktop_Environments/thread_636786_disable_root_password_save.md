---
title: "disable root password save"
date: 2007-12-10
forum: Desktop Environments
---

### Post by KDB9000 on 2007-12-10
Not sure if anyone has asked this, doesn't appear anyone has, but I was wondering if I can disable the root password save? What I mean by that is if I login with my password to do something root, it saves it for a while, So someone can come in and access root stuff without the password. So is there any way to stop this from happening?

---

### Post by Jussi Kukkonen on 2007-12-10
Adding something like
```
Defaults:<your_username> timestamp_timeout=0
```
in /etc/sudoers removes the "saving" altogether (read *man sudoers* for full details).

The other alternative is to use "sudo -K" to empty the timestamp when you leave your computer.

---

### Post by KDB9000 on 2007-12-10
OK, I got it to work. The man didn't show what you told me to put but your way worked. Thank you.

---

