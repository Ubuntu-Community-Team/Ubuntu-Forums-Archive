---
title: "Keep Plymouth Splash Running Longer Than Default"
date: 2015-05-23
forum: Desktop Environments
---

### Post by joseph62 on 2015-05-23
Hey All!

Quick question with hopefully enough background that my question may be easy to understand...

So the deal is, that I've recently been working on something of a personal distro based on an Ubuntu CLI install. At this point, I have plymouth managing the splash screen on boot > after boot the system does an automatic logon > and then automatically runs Xorg and a single application on top of Xorg. 

Or more specifically, the system boots with splash drawn by plymouth, plymouth exits (as set by default) and a special tty session that has been configured for auto-login processes the login, after automated login "/home/user/.bash_profile" runs basic "startx" command and Xorg runs a graphical program specified in "/home/user/.xinitrc" on top of Xorg.

My question to those of you who are smarter than I is simply this: is it possible to configure plymouth to continually display the boot splash until Xorg loads with the specific program on top of it? In a more visualized sense, in such a way that I could simply turn on the system and the splash screen would display up until the very point where the final application is loaded on top of Xorg?

If not, what could be another way to possibly accomplish this task? I've spent a good bit of time on our good friend Google, and I have yet to find what I am looking for... I appreciate all of your time, and look forward to your responses. If this question is confusing or not clear enough, please let me know and I will try to communicate the situation more succinctly. :D

---

### Post by dino99 on 2015-05-23
only my own thinking:
plymouth is deeply implemented into the system; even if it is used since a while now, lot of bugs are still around. So modifying its logic require huge skill and understanding all the crossed dependencies. And each time that package will be updated, it probably break the previous job done; well a nightmare i think.

some ideas here: [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
[http://askubuntu.com/questions/568040/show-custom-message-after-booting-process-finishes-and-displays-boot-log-instead](http://askubuntu.com/questions/568040/show-custom-message-after-booting-process-finishes-and-displays-boot-log-instead)
[http://askubuntu.com/questions/552802/how-to-customize-the-default-plymouth-theme-in-ubuntu](http://askubuntu.com/questions/552802/how-to-customize-the-default-plymouth-theme-in-ubuntu)

---

### Post by joseph62 on 2015-05-24
Appreciate the reply sir. :) My hopes were that I might be able to extend plymouth's run level from level 1 (boot) to run level 4 (rl 5 is when most of the gui components are called), and then use a script to end the plymouth process which could be triggered immediately before the desired program is called... However, I tried this idea using sysv-rc-conf and I didn't see any results = which simply means that it was coded well with a specified "on action" termination instead of "on runlevel". Thus I'll continue to look for any plymouth settings files, but it's a less than efficient way to go about it because the flag may very well be set in some random compiled python file. :( 

As for updates, the idea would be that an sh script could append modified files with the custom code when it notices that said files have been updated - not foolproof but if it were I wouldn't be able to work with it. ;)

---

