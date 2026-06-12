---
title: "Firestarter startup problems"
date: 2006-01-15
forum: Desktop Environments
---

### Post by stuart-newtoubuntu on 2006-01-15
Hi 

I think I might not be the only person with this problem, as can be seen here:

[http://www.ubuntuforums.org/showthread.php?t=84761&highlight=firestarter](http://www.ubuntuforums.org/showthread.php?t=84761&highlight=firestarter)

I did add a post to the bottom of this thread, but I shouldn't have as it was about xfce and not Gnome. 

Anyway my problem is.

I have had firestarter installed on my system for the last couple of months and everything has been working fine. 

In the last few days after I log in I am greeted by a dialogue box telling me I have insufficent privilages to run firestarter, even though it is already running in the notification area. 

So I thought, I'll remove it from the startup (system->preferences->settings) I don't really need to see policy violations. Strangely next time I logged in I received exactly the same firestarter dialogue box warning of insufficent privilages, this time firestarter wasn't in the notification area. 

The details in my sudoers file are correct, but the problem persists. 

Could the problem lie with the fact that I used to have firestarter 0.9.3 and now I have 1.0.3? Does anyone have any ideas on whats going wrong?

---

### Post by Mr_Grieves on 2006-01-15
Hmhm.. and this is just after a fresh boot? What happens if you start/stop firestarter manually with sudo, add rules?

---

### Post by stuart-newtoubuntu on 2006-01-15
The error happens every time I log into gnome. I have restarted firestarter and the problem is still there. I haven't tried adjusting the rules, which ones should I adjust?

Stu

---

### Post by darkpoet on 2006-01-31
I also am getting the same error.  It runs normally but at every Gnome login, it would pop up the privilege error.

---

### Post by mcduck on 2006-01-31
try this: Make sure firestarter isn't running, log out of gnome and check the 'save current setup' box.

---

### Post by byen on 2006-01-31
see if this link helps... goodluck!
[http://ubuntuforums.org/showpost.php?p=663298&postcount=4](http://ubuntuforums.org/showpost.php?p=663298&postcount=4)

---

