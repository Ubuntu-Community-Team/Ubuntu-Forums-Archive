---
title: "Login screen won't accept input"
date: 2011-01-26
forum: Desktop Environments
---

### Post by lhbradley on 2011-01-26
Ubuntu 10.10. 

When I try to switch to another user, the login screen show the user selection list, but I can't enter anything - when I click on a user name, the computer just beeps. I have to reboot to get out of this.

Fortunately, my own account is set for automatic login.

This is a bit annoying!

Any thoughts?

Larry

---

### Post by w3rt on 2011-01-26
Have you recently upgraded the distro? I remember having a problem like that when I upgraded from one version to the next, but I think that may have been a gdm problem, not sure if your case is the same though

---

### Post by Krytarik on 2011-01-26
You may try another display manager, like "kdm", "wdm", xdm". The packages are called respectively. I'm curious if it works. I have a similar issue at my mum's machine, not really tried to fix it so far. I kept on believing that it's an issue with the video driver.

---

### Post by lhbradley on 2011-01-29
No, this is a totally new install. If I do anything to get the login screen, when I click on a user, I just get a BEEP

Larry

---

### Post by Krytarik on 2011-01-29
Do you have the most recent upgrades?
```
sudo apt-get update
sudo apt-get upgrade
```
If that doesn't help, try another display manager, as I suggested in my previous post.

---

