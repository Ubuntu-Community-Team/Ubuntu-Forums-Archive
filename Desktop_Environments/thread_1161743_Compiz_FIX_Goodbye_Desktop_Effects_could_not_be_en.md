---
title: "Compiz FIX Goodbye Desktop Effects could not be enabled"
date: 2009-05-17
forum: Desktop Environments
---

### Post by pippin418 on 2009-05-17
Compiz Check doesn't turn on compiz. I'll teach you how.

Open terminal, type "sudo gedit" type your password.

Now open /etc/xdg/compiz/compiz-manager in it.

add:
```
SKIP_CHECKS="yes"
```to the bottom of it. Save it. Close gedit. Log off. Log in. Enabled desktop effects. Fixed mine!;):D

---

