---
title: "cannot login to any users only root"
date: 2007-10-23
forum: Desktop Environments
---

### Post by working41chemy on 2007-10-23
I try logging in to my user account and the monitor says no signal. i ctrl-alt-backspace and log out and it comes back. i've tried deleting and re adding the user but i get the same thing. however i can log in under root without issues

---

### Post by aysiu on 2007-10-23
There must be something wrong with your user preferences with regard to screen resolution. Log in as root and create a new user: ```
adduser *newusername*
``` and log in as that user.

---

