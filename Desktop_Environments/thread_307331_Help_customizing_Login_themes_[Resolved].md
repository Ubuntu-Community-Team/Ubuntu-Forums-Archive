---
title: "Help customizing Login themes [Resolved]"
date: 2006-11-26
forum: Desktop Environments
---

### Post by sdb2028 on 2006-11-26
I have been trying to customize my login themes, without much luck. I would like to learn to write my own. Does anyone have any tips and tricks to help me? Thanks in advance.

---

### Post by aysiu on 2006-11-26
Try this link:
[Creating GDM Themes mini HOWTO](http://julian.coccia.com/blog/index.php?p=51&more=1)

---

### Post by sdb2028 on 2006-11-26
Thanks for the link. I try'd it and it worked for the most part. I still can't get a screen shot though. Any Ideas? I try'd the way outlined in the link you sent and cant seem to get ahold of the website owner.

---

### Post by aysiu on 2006-11-26
There's a much easier way to get a screenshot. First of all, install *xnest*: ```
sudo aptitude update && sudo aptitude install xnest
``` Then launch it: ```
gdmflexiserver --xnest
``` You should now have a login screen within your session. Take a screenshot by pressing **Alt-PrtScrn.**

---

### Post by sdb2028 on 2006-11-26
Thanx for the info. Installed xnest, launched it and this is what I got---

---

### Post by aysiu on 2006-11-26
Based on [a search for your error](http://www.google.com/search?hl=en&q=you+do+not+seem+to+have+the+authentication+needed+for+this+operation+perhaps+your+xauthority+file+is+not+set+up+correctly&btnG=Google+Search), I came up with [this thread](http://ubuntuforums.org/showthread.php?t=85945), which seems to indicate that you'll have problems running that command as root (which you seem to be logged in as).

---

### Post by sdb2028 on 2006-11-26
Worked fine from a normal user terminal, thanx.

---

