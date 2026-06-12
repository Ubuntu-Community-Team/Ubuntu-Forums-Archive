---
title: "setting user PATH in Xfce"
date: 2007-02-15
forum: Desktop Environments
---

### Post by r.stiltskin on 2007-02-15
I put a line
export PATH=$PATH:[additional directory]
in a user's .bash_profile file.

It works as expected for a terminal (or ssh) login, but it isn't being applied in an Xfce login.  This is my first time using Xfce (it's a new Xubuntu installation).  Is there some other place that Xfce wants to find the PATH statement?

---

### Post by taurus on 2007-02-15
Put it in ~/.bashrc instead.

---

### Post by r.stiltskin on 2007-02-16
Thanks for your help.  I'll try that next time I'm there (next week).

---

### Post by dabd on 2007-02-21
I also tried puting it in bashrc but it still doesn't work.
In my case when I start Emacs through the XFCE panel it doesn't source the bashrc file either.
Is there some way to define the PATH before the XFCE panel, or Xorg, for that matter, starts?

Thanks

---

