---
title: "recovery of GRUB"
date: 2011-06-15
forum: Desktop Environments
---

### Post by Sodear on 2011-06-15
Desktop Ubuntu 10.04 with Win7 on separate hard drive.  System crashed while downloading updates probably due to processor overheat which is now fixed.  Ubuntu presents a garbled screen on boot up, cannot log in.  Starting in recovery mode results in an immediate rapid listing of checks and corrections (white text on black screen) and then it halts with a horizontal cursor blinking.  Nothing else happens.
I can get to a command prompt by pressing 'c' before selecting the recovery mode but I have no idea where to go from there.  How shall I proceed?  Is the only option to re-install?

---

### Post by rothux.j on 2011-06-15
Well it sounds to me like you are getting past GRUB and being handed to ubuntu. Meaning it is ubuntu that is the problem.

Personally, I would use a live CD to backup my data from ubuntu, and do a clean install. But feel free to wait for other people's advice - might/probably will be better.

---

### Post by kun21 on 2011-06-15
so,I think you could find the better ways.

________________
[Buy office 2007](http://www.buymsoffice2007.com)
[Buy MS office 2007](http://www.buymsoffice2007.com)

---

### Post by wildmanne39 on 2011-06-16
[QUOTE=Sodear;10943784]Desktop Ubuntu 10.04 with Win7 on separate hard drive.  System crashed while downloading updates probably due to processor overheat which is now fixed.  Ubuntu presents a garbled screen on boot up, cannot log in.  Starting in recovery mode results in an immediate rapid listing of checks and corrections (white text on black screen) and then it halts with a horizontal cursor blinking.  Nothing else happens.
I can get to a command prompt by pressing 'c' before selecting the recovery mode but I have no idea where to go from there.  How shall I proceed?  Is the only option to re-install?[/QUOTE
Hi, if you have root access with network in recovery mode run this command.
```
sudo apt-get update && sudo apt-get upgrade
```to get into recovery mode have a look at this link.
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by rothux.j on 2011-06-16
Oh!
When you get to the console/command prompt through recovery, type
```
sudo startx
```
Possibly just X is messed up? If from the login console it then loads up a garble, then you know its probably X. I don't know how to sort that, but I'm sure people are more likely to reply if they think it is an X problem, rather than a big problem.

I would also rename this thread to be "Garbled screen on login" or something similar to that.

Do this after what wildmanne39 suggested, thats a good shout. xD

---

### Post by Sodear on 2011-06-16
If I press C on the boot options page after highlighting recovery mode I get a prompt: grub> .  The sudo command is not recognized at all.  I am offered a list of optional commands, none of which makes sense to me.  I guess I will have to try recovery using the CD

---

### Post by rothux.j on 2011-06-17
When you get to the garbled screen, try pressing Ctrl + Alt + F1 or F2 or F3 etc.
This should load you into a text based login.

---

