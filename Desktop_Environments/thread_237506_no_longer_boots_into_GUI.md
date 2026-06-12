---
title: "no longer boots into GUI"
date: 2006-08-16
forum: Desktop Environments
---

### Post by jedimaster_mark on 2006-08-16
I was attempting to launch the FileBrowser from the menu, when I mis-clicked.  Whatever I clicked removed all the options from my desktop: no toolbar, just the icons on the desktop itself.  Unable to navigate in any way, I did a hard reboot.  Now, it only boots into command prompt.  It seems that it just isn't starting X by default... when it boots, I get the initial graphic with the boot status runnning below it, then I get the "waiting" mouse icon, then it just goes to command prompt.  Can anyone help?

---

### Post by wjp.reg on 2006-08-16
from the command prompt, logon as normal with your username and password and do the following:

```
sudo dpkg-reconfigure xserver-xorg
```

Just follow the bouncing ball.

Most likely you hammered your xwindows settings.

See how that works out anyway.

---

### Post by jedimaster_mark on 2006-08-16
Okay, I was unable to use sudo.  It seems that when I log in, my account cannot access /bin/bash, although after checking the permissions, there is no reason why I should not be able to.  I was able to su into root and run the reconfigure command, which I did.  However, it still boots into command prompt.

I am able to log in as root and then start x to get into the GUI.  Once there, I start looking at the logs.  This is in my daemon.log:

localhost gdm[10471] gdm_slave_greeter: Cannot start greeter trying default: /usr/lib/gdm/gdmlogin
localhost gdm[10471] failsafe dialog failed (inhibitions: 0 0)
localhost gdm[10471] gdm_slave_greeter: Error starting greeter on display :0
localhost gdm[10222] gdm_child_action: Aborting display :0

Is that any better as far as information goes?

Thanks,
Mark


> **wjp.reg said:**
> from the command prompt, logon as normal with your username and password and do the following:

```
sudo dpkg-reconfigure xserver-xorg
```

Just follow the bouncing ball.

Most likely you hammered your xwindows settings.

See how that works out anyway.

---

