---
title: "Can guest accounts unlock their screen in Xubuntu?"
date: 2012-05-22
forum: Desktop Environments
---

### Post by jgor on 2012-05-22
I see that Xubuntu 12.04 has an option to log in as a guest account, which I think is a great idea.

There is just one big issue that I can't seem to find any information on. [FONT="Courier New"]**xscreensaver-command -lock**[/FONT] requires the user to have a password entered in order to unlock their screen, and as far as I know guests have no password.

If you try to enter without a password xscreensaver will tell you: "assuming null password means cancel.". [FONT="Courier New"]**xscreensaver-command**[/FONT] is the default screen locking program in Xubuntu and I can just imagine the extreme frustration of someone using a guest account and out of habit they lock their screen and are unable to unlock.

Am I missing something? Or have I uncovered something that needs to be fixed? As far as I know in Xubuntu 12.04 the only way to switch users with the default GUI is to lock the screen first and then choose "New Login" but you can't do that as a guest because locking the screen means you will never beable to unlock.

---

### Post by zombifier25 on 2012-05-23
Wait, you can't choose New Login as a guest?

---

### Post by jgor on 2012-05-23
> **zombifier25 said:**
> Wait, you can't choose New Login as a guest?

You can choose New Login, but from what I see you might as well just log out because once you lock the screen as a guest you are never allowed back in. Is there another way of choosing New Login without locking the screen that I don't know of?

Ideally xscreensaver should be able to accept null passwords, I see no reason for this lack of functionality. If that is impossible I should think that by default someone without a password shouldn't be able to lock their screen.

---

### Post by phil02 on 2012-05-28
Choosing new login and then the guest account again does not work.  It brings you back to the XScreensaver unlock screen.

Is there a work around to disable the screensaver from locking?

Is there a bug for this in launchpad?  I did not find one with a quick search.

---

### Post by rai4shu2 on 2012-05-28
At the moment, lightdm does not properly support xscreensaver. Ergo, do not use guest account if you expect to have to use xscreensaver. Disable guest account and create a new user if you need one.

---

### Post by zombifier25 on 2012-05-28
> **rai4shu2 said:**
> At the moment, lightdm does not properly support xscreensaver. Ergo, do not use guest account if you expect to have to use xscreensaver. Disable guest account and create a new user if you need one.
When people install xscreensaver, they usually follow a tutorials that had xscreensaver startup at login for ALL users. I simply add xscreensaver to only my Startup and done. Guest accounts can not lock their screen.

---

### Post by rai4shu2 on 2012-05-28
People don't install xscreensaver in Xubuntu. It comes standard. The session default is:

```
xfconf-query -c xfce4-session -p /startup/screensaver/type
```

---

