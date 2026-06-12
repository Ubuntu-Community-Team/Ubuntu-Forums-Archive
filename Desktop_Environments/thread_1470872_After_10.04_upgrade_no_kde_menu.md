---
title: "After 10.04 upgrade no kde menu"
date: 2010-05-03
forum: Desktop Environments
---

### Post by igorvc on 2010-05-03
Hi,

 I was using Kubuntu 9.10 when I upgrated using the upgrade menu.

 When it finished and reboot my computer, KDE initialize in "black screen", without menus.

 Interesting that Gnome starts fine.

 I try:

[LIST]
[*]reinstall KDE: no success
[*]reconfigure KDE: no success
[*]aptitude dist-upgrade: no success
[*]remove $HOME/.kde and restart: no success
[*]init in runlevel 3, startx kde:
[LIST]
[*]error: "xterm" error
[*]try to find xterm references in xorg and KDE conf files, comment, and the errors presist
[/LIST]
[/LIST]

 That's it ... some idea :confused:?

 Thanks,

---

### Post by jennil on 2010-05-03
Hi,

Is KDM starting up OK (do you get a login screen) but everything goes blank when logging in? If you do a friend of mine got similar problems we solved it by creating a new user. 

Logging in as the new user worked fine and as we didn't have the time figuring out what was the cause of the problem (probably some config file in the home directory but not .kde/ as it was the first thing we tried) he just continued to use the new user.

If you don't even get a login prompt maybe you can find some clues about what is wrong in either 
/var/log/kdm.log or /var/log/Xorg.0.log.

I hope you get it up and running, I installed Kubuntu 10.04 a few days ago myself (clean install) and I'm very happy with it!

Regards
jennil

---

### Post by Untitled_No4 on 2010-05-03
If you press Alt+F2 do you still get krunner? If so, try typing in plasma-desktop and see if everything comes up.

---

### Post by igorvc on 2010-05-04
> **Untitled_No4 said:**
> If you press Alt+F2 do you still get krunner? If so, try typing in plasma-desktop and see if everything comes up.

Hi all,

 First thanks for the help.

 I tryed t add new user, without success.

 When I was trying to press ALT+F2 I receive a notification that my KDE did not have language support and aked if I want to install it. I've install and did not solve the problem.

 I tryed to execute "plasma-desktop", but this command was not fount!

 So I execute:** apt-get install plasma-desktop** and solve my problem :D

 Thanks

---

