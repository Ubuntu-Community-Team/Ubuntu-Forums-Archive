---
title: "BSOD login timing problem"
date: 2012-06-30
forum: Desktop Environments
---

### Post by Nick Payne on 2012-06-30
I'm running Ubuntu 12.04 amd64 using Nouveau driver and nVidia dual head video card with two monitors. Standard Unity desktop. If I login immediately the login GUI dialog appears, then about one time in three I just get a blank black screen with a mouse pointer that I can move around, but nothing else, and no response to keystrokes or mouse clicks. Sometimes I can salvage the situation by Ctrl+Alt+Fn to a text login screen, then login and stop and start the lightdm service, but often I can't even get Ctrl+Alt+Fn to switch me to another screen.

If I don't try to login immediately the login screen appears - eg I switch the PC on and come back 10 minutes later to login - then I don't get the blank black screen problem.

---

### Post by msammels on 2012-07-04
I'm not sure you want to be using noveau and nVidia's drivers at the same time. As for switching to another tty have you tried:

```
CTRL+ALT+F1
```

To get back to the default tty it's:

```
CTRL+ALT+F7
```

---

### Post by Nick Payne on 2012-07-05
I'm not using the nVidia driver. I'm using an nVidia video card with the Nouveau driver, principally because the nVidia driver doesn't allow two monitors with one rotated unless they are separate X screens, which is a PITA.

Ctrl+Alt+Fn (with n=1, 2, 3 etc) is what I said usually didn't work in this situation.

---

