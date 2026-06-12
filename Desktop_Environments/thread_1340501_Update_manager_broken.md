---
title: "Update manager broken"
date: 2009-11-28
forum: Desktop Environments
---

### Post by raido357 on 2009-11-28
**SOLVED:**

[U]I had one PPA key missing and that broke update-manager. Although it could be nicer if update manager would work even without GPG key or could atleast display some sort of user friendly error message.
[/U]

When i try to run Update manager i get this error:

update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 108, in <module>
    app.main(options)
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 940, in main
    self.fillstore()
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 789, in fillstore
    self.update_count()
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 510, in update_count
    if self._get_last_apt_get_update_text() is not None:
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 474, in _get_last_apt_get_update_text
    ago_days) % ago_days
TypeError: not all arguments converted during string formatting

Using 9.10, update from alpha 5 -> alpha 6 -> rc -> beta -> stable

---

### Post by some-what-Gnu-2-networks on 2009-11-28
Can you "**sudo apt-get install update**" in the terminal? that's all I got to offer. If that works the problem is w/ the GUI, otherwise....umm...?...

---

### Post by whoop on 2009-11-28
> **some-what-Gnu-2-networks said:**
> Can you "**sudo apt-get install update**" in the terminal? that's all I got to offer. If that works the problem is w/ the GUI, otherwise....umm...?...

You just meant sudo apt-get update, didn't you?
or maybe sudo apt-get update && sudo apt-get dist-upgrade...

---

### Post by some-what-Gnu-2-networks on 2009-11-28
> **whoop said:**
> You just meant sudo apt-get update, didn't you?
or maybe sudo apt-get update && sudo apt-get dist-upgrade...
  
Yep, Thanks and sorry for the error.

---

### Post by whoop on 2009-11-28
> **some-what-Gnu-2-networks said:**
> Yep, Thanks and sorry for the error.

no worries...

---

### Post by raido357 on 2009-11-29
Executing **apt-get update** in console is working all the time, problem is with Update manager when some GPG keys are missing (as written in first post).

---

