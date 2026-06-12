---
title: "How to get the pidgin status to change to away when screensaver activates?"
date: 2008-12-09
forum: General Help
---

### Post by siersmak on 2008-12-09
I'm running Ubuntu 8.10, fully updated as of today, and would like to have my Pidgin status change to away when the gnome screensaver activates.  Empathy does this, but I'd rather use pidgin.  Is there something special I need to do to get it to work?

---

### Post by Moezzie on 2008-12-09
I guess the easies way to do this is to just set pidgin to go idle after the same amount of time the screensaver does.
If you go into Preferences > Status/Idle you will find an option saying "Change status when idle". You can set the time and status yourself. Just set it to the same as your screensaver.

---

### Post by siersmak on 2008-12-09
Ah, I already thought of that.  Both are set for 5 minutes.  I guess then the question may be why doesn't Pidgin go idle after I set "Change status when idle".

---

### Post by em4r1z on 2008-12-10
> **siersmak said:**
> Ah, I already thought of that.  Both are set for 5 minutes.  I guess then the question may be why doesn't Pidgin go idle after I set "Change status when idle".How do you know it doesn't? Pidgin returns to its previous state after the power saving features end. Ask a friend to check your status or check the changes made to ~/.purple/status.xml

---

### Post by siersmak on 2008-12-10
> **em4r1z said:**
> How do you know it doesn't? Pidgin returns to its previous state after the power saving features end. Ask a friend to check your status or check the changes made to ~/.purple/status.xml

I'm monitoring it with another account on another machine.  When the machine with pidgin goes idle, the status that I see on the other machine doesn't change.

---

### Post by siersmak on 2008-12-10
Another thing I've noticed is that pidgin never goes idle on it's own.  Even if I haven't moved my mouse into the pidgin window for hours, the status never switches to away.  I always have to manually switch my status to away.  

I've got these options set in the Status/Idle window of the preferences:

Idle: Report idle time:  Based on keyboard or mouse use
Away: Auto-reply: When both away and idle
Auto-away: Change status when idle (checked)
Auto-away: Minutes before becoming idle: 5 (same as screensaver)
Auto-away: Change status to: Away
Status at Startup: Use status from last exit at startup (checked)

---

### Post by siersmak on 2008-12-10
Okay, a little more testing- I found that if my status is set to Available, indeed it does switch to Away after the timeout I specify for idle.  But if I have it set to Do Not Disturb, it does not switch to Away when idle (never goes idle?).  

This is not the preferred behavior, imho.  I want to set it to Do Not Disturb, to discourage some, but not all, buddies from chatting.  I don't want it set to Available.  But I do want it to be set to Away when I go idle.  Is there any way to have what I want here?

---

### Post by em4r1z on 2008-12-12
Try playing with ~/.purple/prefs.xml The nodes *away, status* and *savedstatus* might help.

---

### Post by mrmikee on 2009-07-23
Have you tried:
[http://costela.net/projects/awayonlock/](http://costela.net/projects/awayonlock/)

Debian Package:
[http://packages.debian.org/sid/pidgin-awayonlock](http://packages.debian.org/sid/pidgin-awayonlock)

---

### Post by jhparizona on 2013-03-09
Thanks! I know this is a 4 year old thread.... but..... it helped me get auto-away working in pidgin on Fedora. The links for awayonlock were especially helpful. It did force me to install 27 additional packages (although some of them may not have been necessary due to the use of the * when install two of the development packages). And I especially like the fact that the software is "customized" for my platform via compiling from source. Now, maybe I should look into further customization via hacking the source code, but that is another day.....

---

