---
title: "sudo autocompletion"
date: 2008-02-08
forum: Debian
---

### Post by maybeway36 on 2008-02-08
When I install Debian with sudo and a locked root account (using expert-mode installer), I can autocomplete commands in bash (TAB) after sudo. For example:
```
sudo dpkg-re
```
pressing TAB gives fills in the rest (as is the case on Ubuntu also.)
However, when I install Debian with a root account and no sudo, then add sudo later and put myself in /etc/sudoers, this autocompletion doesn't work.
/etc/bash_completion is the same in both cases.

---

