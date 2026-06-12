---
title: "Fonts, desktop, screens ... Everything messed up after restart"
date: 2014-06-12
forum: Desktop Environments
---

### Post by xmbwd on 2014-06-12
Not sure what happened here, but things got weird fast.  I've been working in Ubuntu 14.04 for a few weeks, mostly all good.  Tonight, I restarted and all of a sudden the fonts are off in the clock, the File menus, and also in Nautilus.  Instead of being Ubuntu, they are some variant on Courier.  Also, the general Unity theme is gone -- it's like I'm using a different desktop.  

Here is a pic from FireFox, where the File menu and clock are in a weird font.  Also, as you can see, the normal Unity theme for FireFox has been replaced by a grey theme (sorry for the whitespace, but I couldn't get the file menus unless I took the whole screen):  

[IMG]https://dl.dropboxusercontent.com/u/13392425/1.png[/IMG]

Here is a pic of a warning window, again all weird fonts (in the body, the heading is the correct font for some reason):

[IMG]https://dl.dropboxusercontent.com/u/13392425/2.png[/IMG]

I've restarted a few times, but nothing changed.   I had noticed this font issue once before, when I had been messing with grub to try and get brightness to work on my laptop, but it had been resolved for a while.   And I didn't change/update grub recently.

In case it is relevant, just before this happened, I restarted and opened by Kubuntu install.   I have installed Ubuntu 14.04 on a separate partition from a Kubuntu install and also a Windows 8 install.  All three work fine and can be selected at the Grub menu.  Kubuntu and Ubuntu share a swap drive, but that's it. 

Anyone have any idea what's going on here?  Or a solution???

---

### Post by rahul4557 on 2014-06-12
[http://ubuntuforums.org/showthread.php?t=454303&p=2719733#post2719733](http://ubuntuforums.org/showthread.php?t=454303&p=2719733#post2719733)

Good Luck..

---

### Post by xmbwd on 2014-06-12
This is not solved, but I rebooted into the Windows partition, then back into Ubuntu 14.04, and everything is back to normal.  I have no idea why, and I am sure it will revert again at some point.  So in the interest of resolving the issue, I would love to know what you folks think happened.  Here are the same pics as above, but with the correct fonts/theme:

[IMG]https://dl.dropboxusercontent.com/u/13392425/3.png[/IMG]And: 

[IMG]https://dl.dropboxusercontent.com/u/13392425/4.png[/IMG]

---

### Post by xmbwd on 2014-06-12
Thanks, but it really was more than the fonts -- it was the windows/themes too (compare the tabs in FireFox on the two pics I posted).  

In case it is relevant; I also noticed that I no longer have rw access to my shared network drives -- now only sudo does.   The error given when I try to mount/unmount it is "only sudo can mount/unmount <shared drive>."

> **rahul4557 said:**
> [http://ubuntuforums.org/showthread.php?t=454303&p=2719733#post2719733](http://ubuntuforums.org/showthread.php?t=454303&p=2719733#post2719733)

Good Luck..

---

### Post by xmbwd on 2014-06-12
Ok.  Now it went back to not working.  Again, it's like I have a totally different theme/desktop. Here is a pic of Terminal (with tabs) side by side with FireFox preferences:

[IMG]https://dl.dropboxusercontent.com/u/13392425/5.png[/IMG]

You can see that things are messed up.  I am using Konsole instead of terminal, and the prefs for that look like FireFox's.

Can someone PLEASE help???  I don't want to have to reinstall Ubuntu.   There must be an actual reason this is happening. ....

---

### Post by xmbwd on 2014-06-12
Not sure if this will help --- but when I reboot, the login screen has the **correct** font for the clock.  Something happens between the login screen and actually logging in that causes the problem.

Also, I tried logging in as Guest -- and the Guest had the correct fonts/theme.

---

