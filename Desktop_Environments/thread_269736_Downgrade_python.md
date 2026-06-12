---
title: "Downgrade python"
date: 2006-10-02
forum: Desktop Environments
---

### Post by elpuerco on 2006-10-02
I installed python 2.5 from a tarball as it was not in the repository.  I only did this as it was the latest version and thought it best to have this to start learning with.

However it turns out now that I need to revert to 2.4.

Can someone tell me how I do this please as 2.5 does not appear in Adept so I can't select it to remove it?

Thnx

---

### Post by pay on 2006-10-02
To remove packages that you compilled from source you need to cd to the directory where you compilled it (I compile in /usr/src) and the do```
sudo make uninstall
```to remove the package.

---

### Post by elpuerco on 2006-10-02
Hi, when I type sudo make uninstall I get the following?

make: *** No rule to make target 'uninstall'. stop

:confused:

---

### Post by bonzodog on 2006-10-02
were you doing that from the python dir where you built and installed it?
You need to make sure you use the original dir.

---

### Post by elpuerco on 2006-10-02
Hi, i ran it from the same directory where I unpacked the source files to, run the ./configure, make and make install which is on my data partition.

---

### Post by sidrit on 2007-12-11
did you end up sorting this matter out?

i have the same problem, since upgrading from 2.4 to 2.5 broke my deluge client.

and the uninstall command gives also the same output.

---

