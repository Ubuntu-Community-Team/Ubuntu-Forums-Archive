---
title: "Kubuntu - Kicks Back To Login Screen"
date: 2006-08-23
forum: Desktop Environments
---

### Post by AdamWarlock on 2006-08-23
Hey all, I have a problem and I hope someone can help me.

Whenever I try to log into Kubuntu, I supply my login and password and the screen turns black for a couple of seconds before kicking me back out to the login screen again.

Any ideas?

---

### Post by fakie_flip on 2006-08-23
What were the last changes you did to your system that could have screwed it up? Go into single user mode from grub and correct the problem.

---

### Post by AdamWarlock on 2006-08-23
My comp wouldn't allow me to install GRUB. I use LILO instead and that doesn't present me with any options. The last change I made to the comp was the Xorg upgrade.

---

### Post by AdamWarlock on 2006-08-24
BUMP ... Need an answer badly!

Also, I logged into using console mode and when I tried to reinstall kubuntu-desktop, it recieved a message about "broken packages". Any ideas?

---

### Post by fakie_flip on 2006-08-25
This is a known problem that's been happening to many many people. All you need to do is get to a command line interface and do these.

```
sudo apt-get update
sudo apt-get upgrade
```

To get to a command line interface, use grub to boot into first person mode. If you don't know how, just google it. There is plenty of information. Another tip. If you are using single user mode, you will be the only single user, root. You will not need sudo before your commands. Be careful. You could destroy your computer if you type in a wrong command because root can do anything. Another way to get to a CLI is to boot your computer and let X crash again like it did before. Then push control + alt + f1, then login, then enter the commands I gave you. After those are finished, Give one more command to restart your computer, so the changes can take place.

```
sudo reboot
```

You have installed a bad Xorg package with a bug by updating your computer. To fix the bug, you must do what I said, and you will be replacing the bad package with a newer one.

---

### Post by fakie_flip on 2006-08-25
Let me know if that fixes it. If not, I will need to see your lilo configuration.

---

