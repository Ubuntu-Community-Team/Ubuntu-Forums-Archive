---
title: "root login without passwd!"
date: 2006-07-29
forum: Desktop Environments
---

### Post by stbub on 2006-07-29
Dunno if I messed something up, or whether ubuntu is messed up, but
when I:

<ctrl>-<alt>-<f1>

To go to a text console, I type root<ret>, and I get into a shell without a password...

Call me old fashion, but that seems undesirable...

---

### Post by ardchoille on 2006-07-29
The root account is disabled by default on Ubuntu for security reasons. Did you enable the root account? If so, please see this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by aysiu on 2006-07-29
Something's wrong with your installation. When I press Control-Alt-F1 and type ```
root
``` I'm prompted for a password even though I don't have the root account enabled.

---

### Post by carontis on 2006-07-29
Well, I use this way to enable the root , so the contrary should work too:
 System ==> Administration ==> Login Window and there go to Security and check for Admins Rights. There should be what you're looking for.

---

