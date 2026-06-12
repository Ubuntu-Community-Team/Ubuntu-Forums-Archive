---
title: "Ububtu 8.04 - Applications wont start up"
date: 2008-04-26
forum: Desktop Environments
---

### Post by Touchstone on 2008-04-26
Have just updated from 7.x to 8.04 through the software update mechanism. No errors reported during the update.

After re-booting, no applications will start up. Example - after clicking Terminal from the menu it briefly appears in the taskbar but then just disappears and the terminal never appears. Same happens with Firefox and other applications. Even pressing the button that brings up the shutdown/restart dialog box doesn't work. Any ideas?? thanks

(running on standard desktop; Ubuntu in its own partitions; version 7.x worked fine)....

---

### Post by Linja on 2008-04-26
Maybe your path got messed up? Can you post the output of echo $PATH? You'll have to work from the console if you can't get gnome-terminal to launch (Ctrl + Alt + F1, then Alt + F7 to get back to your GUI or shutdown -h now to shut down). 

Upgrading is always a tricky business. Personally, I make my backups and I go for a clean install. The more you have customized, the more likely it is that something will go wrong.

---

### Post by vt100 on 2008-04-26
Can you press <ctrl> + <alt> + <F1> and see if you get a terminal login screen. then try to run an application (non-XWindows) like pine or ftp ect. 
(you can get back to the GUI with <ctrl> + <alt> + <F7>). This will tell you if you problem is with Gnome (assuming a standard ubuntu install) or with any path or permission issues.

Type "dmesg" or "dmesg | more" and see if there are any errors in the startup log. also /var/log/messages

Not sure if there is a gnome startup Log generated....

I'm going to guess you have rebooted more times than you know what to do.

It is all togeather possible that the upgrade failed and you will have to re-install from scratch (you can recover files with a live CD if need be), but I would try and see if it can be fixed. 

hope this can help get you to a good place.

P.S. My upgrade went fine this time, but I have had issues in the past depending on what software you have installed and any custom configurations you have made.

---

### Post by Touchstone on 2008-04-26
Thanks for offering your help so quickly.

I've rebooted several times since installation and got this problem each time. I switched on again to try out your advice and it just worked !! :-S

So, all's well that ends well :-)

---

