---
title: "System Settings wont affect the desktop"
date: 2005-12-13
forum: General Help
---

### Post by Txukie on 2005-12-13
Hi! Ive recently updated my KDE to 3.5 and have found several problems. The most annoying one is that when i configure my desktop under system settings, change my icons or the window layouts, the color scheme or anything like that, it doesnt affect my system in any way, everything remains exactly the same.
Other problems that i have is the famous system protocol problem with kicker, that doesnt bother me too much as i can easily overturn it.
Another problem that bothers me a lot is when i lock my session with the blue padlock icon in kicker, it gets locked for real! In fact when it prompts me for a password and i type it (my user password) it tells me that it cannot unblock! Please, help me use this otherwise excellent release!

---

### Post by asimon on 2005-12-13
[QUOTE=Txukie]
Another problem that bothers me a lot is when i lock my session with the blue padlock icon in kicker, it gets locked for real! In fact when it prompts me for a password and i type it (my user password) it tells me that it cannot unblock! Please, help me use this otherwise excellent release![/QUOTE]
I don't know your other problem but this seems to be [bug 20071 - Can't unlock session](http://bugzilla.ubuntu.com/show_bug.cgi?id=20071). You can find a workaround there until a fixed package gets uploaded.

---

### Post by Txukie on 2005-12-14
Found out what my problem was, i was dumb and two months ago or so changed the link to be launched as root, so system settings was changing the root user config, not my normal user :oops: :oops: 
Anyway ive fixed it now and can change all my config without any problems (except for transparency, damn ATI).
I'll take a look at that workaround u posted, asimon, hope they fix this and the system protocol problem in kicker soon.

---

### Post by teaker1s on 2005-12-14
the lock session bug i found was iceauthority in home folder-I renamed mine restarted the computer and a new one was created I now can lock screen and unlock

---

