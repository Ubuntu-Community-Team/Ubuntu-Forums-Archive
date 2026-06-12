---
title: "How to export user settings"
date: 2008-07-11
forum: Desktop Environments
---

### Post by Chxta on 2008-07-11
Hi all,

I've installed and customised user settings for one user on my Ubuntu installation. I would like to know how to save those settings so that anytime I create a new user the settings would be repeated across without having to do it manually. Thanks.

---

### Post by Chxta on 2008-11-14
:bump:

I know that I am meant to do something to /etc/skel, but I have been cracking my brains figuring out what to do...

---

### Post by pennacook on 2008-11-14
It would be in /etc/skel
.bashrc for bash profiles
.profile for csh profiles (and ksh if you have it)

---

