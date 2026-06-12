---
title: "ubuntu problem at login screen"
date: 2010-08-29
forum: Desktop Environments
---

### Post by dokyounder on 2010-08-29
I've been using ubuntu for 2 days, and it worked fine just few hours ago.

I turn the computer on, it takes me to the login screen, and I type the password then click login. Then it seems it's taking me to the main screen but the screen goes black and takes me back to the login screen again. I type the password again and again, but it's still taking me to the same spot. It's like I'm on a time-machine.

When it was working, I did make some changes.
First, I installed Dropbox, then rebooted. so I think there's no problem with that.
Then, I made some changes on the keyboard layout using this method ([http://ubuntuforums.org/showthread.php?t=30981](http://ubuntuforums.org/showthread.php?t=30981)).
I think that's the problem, but I don't know how to restore it nor fix the problem.

any suggestions/comments/help are greatly appriciated. Thanks.

oh yes and I'm using ubuntu 10.04 netbook edition.

---

### Post by varunendra on 2010-08-30
There seem two possible reasons:

[LIST=1]
[*]Your default keyboard layout might have been changed, thus typing different characters when you enter your password. To confirm this, you may try using 'On-Screen-Keyboard' at login screen (as told [here]("http://www.clickonf5.org/linux/keyboard-problem-ubuntu-1004-login-vmware/7163"))
[*]Some error in any of the essential applications or system modules. In this case, try booting in 'Recovery Mode' (press & hold 'Shift' key while booting) and selecting 'dpkg' there.
[/LIST]
Also, while in 'Recovery Mode', can you log in as **root** (last in the Recovery Menu)?

Any further attempts would depend upon the results you get while trying these.

---

