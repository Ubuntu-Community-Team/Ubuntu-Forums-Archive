---
title: "Three login problems"
date: 2008-06-24
forum: Desktop Environments
---

### Post by wikityler on 2008-06-24
Since "upgrading" to hardy, I've been having the following three problems:

Note: Computer has two users. Users A and B. User A is always the first to login after boot.

#1:
When user A is done at the computer they lock the screen. When user B then wants use the computer they click 'switch user', and login. When user B is finished, they lock the screen. When user A wants to use the computer again, they switch users, only to discover that the previous session is gone, and they are not logged in any more. This happens almost every time, but once in a while user A will still be logged in after user B has used the computer.

#2:
Within the first 5-10 minuets of user B having logged in, or resuming a session, they will be logged out by the system, and brought back to the login screen, no matter what they were doing at the time. Once they log back in, this wont happen for a few days. This only ever happens to user B.

#3:
Sometimes after either user logs in, the system sound '/usr/share/sounds/question.wav' will play as an endless loop in the background. It persists through logouts, and switching users. The only way to stop it is a restart. The only system sounds that are used are login and logout, not question.

So srsly! Wtf?

Thanks to any who reply.

---

### Post by x1a4 on 2008-06-24
Hi,

You may want to start two instances of GDM at boot, and explicitly load X display 0 and 1 to always load on the same VT.

See [this HOWTO]("http://hex1a4.net/xubuntu/howto/03/") on how to configure virtual terminals.

---

### Post by wactuary on 2008-10-07
> **wikityler said:**
> 
#3:
Sometimes after either user logs in, the system sound '/usr/share/sounds/question.wav' will play as an endless loop in the background. It persists through logouts, and switching users. The only way to stop it is a restart. The only system sounds that are used are login and logout, not question.


I'm having the same problem as this.  Don't have #1 or #2.  Also using Hardy.  Very frustrating.  Not sure what to do to debug.  I've read very old threads (back to '05) refer to this as IRQ issues, but I didn't have any problems back then.  It just popped up intermittently with Hardy Heron AMD64.

---

