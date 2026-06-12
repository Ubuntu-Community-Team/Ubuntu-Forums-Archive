---
title: "Kubuntu probs: brightness, battery life, fn keys"
date: 2007-09-30
forum: Desktop Environments
---

### Post by maxclimber1w on 2007-09-30
alright, I just switched to kubuntu from ubuntu. I am running on a toshiba laptop, and I am finding no way to adjust the screen brightness. How do I get something similar to the applet in gnome?

Also, what are some other ways to increase the battery life? There doesn't seem to be a power managment control panel that I can find.

One last thing, what do the Fn+F1-F12 keys do? I experimented with them, but somehow locked the screen and couldn't log in...

thanks for the help!

Max

---

### Post by pbcartwright on 2007-09-30
install and run powertop. once installed, open a terminal window and run powertop.
It gives you parameters to change to use power better.

CTRL-ALT-F1 gets you to a text-based logon window. when you go to the text window you should be able to get back to your GUI by doing CTRL-ALT-F7. if you switch users and login with another user, that would be CTRL-ALT-F8, so you could either use the menus or toggle between users using CTRL-ALT-F7....

---

### Post by maxclimber1w on 2007-09-30
I was talking about the Fn-f1-f12 commands, not ctrl-alt-f1-f12. I'll try the powertop thing....

---

### Post by rosegarden78 on 2008-01-19
Try typing the following command in a terminal:

xgamma -gamma 0.75

If that doesn't work you need to install xgamma from the repos.

I have posted my own solution here on setting it up:

[http://ubuntuforums.org/showthread.php?p=4168042#post4168042](http://ubuntuforums.org/showthread.php?p=4168042#post4168042)

P.S.  Battery life is limited to 300-1000 charges or 1-3 years ... period.

---

