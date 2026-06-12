---
title: "Root password?"
date: 2006-02-08
forum: Desktop Environments
---

### Post by DZero on 2006-02-08
During the installation, Ubuntu asked me for a root password and I entered one. When I try to do something on my "normal" user and it prompts me for the password, I enter that password I gave and it works. But I can't "su -" to root of login as root with that password. What could the problem be?

Thank you,

Kevin

---

### Post by dickohead on 2006-02-08
There is no root password. Ubuntu asked you for the user password, it utilises the sudo principle. Want to access something a normal user can't? Instead of logging in as root, type:

sudo command
enter YOUR password

If you really do need to login as root type this:

sudo passwd
enter your USERS password
enter ROOT password
and again

Good luck.

---

### Post by towsonu2003 on 2006-02-08
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) may help grasp what's goin' on

---

### Post by DZero on 2006-02-10
Thank you. I didn't realize that.

---

