---
title: "setting PATH for Gnome-session"
date: 2005-08-24
forum: Desktop Environments
---

### Post by twelvegates on 2005-08-24
Hello, 

I'm trying to set the PATH enrironment variable for the Gnome environment.
So I set *PATH=~/bin:"${PATH}"* both in .bashrc and in .bash_profile.
While this is visible in an Xterm and in a Termianl it is not visible to the Gnome environment.
I can verify this. I open the Run Application dialog and enter *echo $PATH >/tmp/p* and then *cat /tmp/p* in an Xterm. This yields:
```
/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games
```
How can I set the PATH environment variable for the Gnome environment?

-Hanspeter

---

