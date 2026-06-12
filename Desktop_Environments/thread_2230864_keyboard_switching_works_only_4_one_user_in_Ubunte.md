---
title: "keyboard switching works only 4 one user in Ubunte 14.04/64"
date: 2014-06-21
forum: Desktop Environments
---

### Post by skaiser on 2014-06-21
Hello, I have a problem with Ubuntu 14.04, 64 bit version (and my wife) - she is suddenly stuck with a UK keyboard and I cannot change it.
My user (admin) can switch without problems, but she is stuck, - the same keyboard, the same machine, AND it has worked properly now for over 2 weeks.
Where should I look to solve the riddle?

Thanx,
Siegfried

---

### Post by papibe on 2014-06-21
Hi skaiser.

A couple of questions:
[LIST]
[*]Does the shortcut not work? (note that the default shortcut changed from 12.04 to 14.04. Now it is super+space)
[*]Does she see the layout icon on the top bar?
[*]Is she not able to click it (is it gray out)?
[*]
[/LIST]
An idea:
In order to change keyboard layout, the program has to have access to the users directory. If for some reason there one of the settings directories changed ownership (because of a wrong sudo command, or a GUI app ran as sudo), it won't be able to save the setting. 

Try this as the administrator:
```
sudo chown -R username:username  ~username
```
replace 'username' for the actual username (your wife's).

Hope it helps. Let us know how it goes.
Regards.

---

