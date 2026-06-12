---
title: "[SOLVED] Authentication Failed at GDM Login"
date: 2007-09-19
forum: Desktop Environments
---

### Post by glennric on 2007-09-19
I am having trouble logging in at the gdm login screen.  I enter my username and password and it pops up a window that says, "authentication failed."  I managed to set the gdm settings to autologin and then I can get gnome going.  I also can login in a console.  Does anyone know how to fix this?

---

### Post by por100pre1 on 2007-09-19
Restart in recovery mode and then

```
passwd YOUR-USER-NAME
```

type your new password (nothing will be seen)

```
reboot
```

**EDIT: sorry, wrong answer; seems gdm is hosed:**

try this instead:


```
sudo dpkg-reconfigure gdm
```

---

### Post by glennric on 2007-09-19
```
sudo dpkg-reconfigure gdm
```[/QUOTE]

I already tried that.  It doesn't help.

---

### Post by fiatguy85 on 2007-10-22
Try this:

[http://ubuntuforums.org/showpost.php?p=3605925&postcount=4](http://ubuntuforums.org/showpost.php?p=3605925&postcount=4)

---

