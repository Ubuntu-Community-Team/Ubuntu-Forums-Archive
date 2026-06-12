---
title: "boarderless windows with compiz"
date: 2011-05-08
forum: Desktop Environments
---

### Post by T-bone24 on 2011-05-08
Hi,
Last night I installed compiz-config and tried to activate the desktop cube and made the mistake of clicking through the alert messages without properly reading them, and then all of a sudden my window boarders disappeared. So now I have no close, minimise or maximise buttons. no file, edit, view, etc options and I cant move any windows. I completey removed compiz and the window boarders came back, but then when I re-installed it and started it with "compiz --replace" the boarders disappear again (in a side issue, now when I log in I have to manually start compiz with "compiz --replace", if anyone could help me with making compiz start by default again that would be great).

I'm currently using Natty 64-bit and the problem only seems present on Ubuntu Classic, Unity and fail safe mode both seem fine.

I'm pretty sure the issue is in a setting stored somewhere in /home as I only did a clean install last week and have /home on a separate partition so re-installing Ubuntu seemed like a quick solution but even after that the problem is still there.

---

### Post by Durden on 2011-05-08
Remove .compiz in your home directory. Compiz is really bad in this version, nothing but trouble for me so far.

---

### Post by T-bone24 on 2011-05-08
> **Durden said:**
> Remove .compiz in your home directory. Compiz is really bad in this version, nothing but trouble for me so far.
Thanks, that was the first thing I tried but it didn't solve anything.

I've managed to fix it now though, I'm sure there is a much easier way to repair the problem so if anyone knows of one then please post it for anyone else with the same issue.

What I ended up doing was creating a new user, I checked the new user's account and there wasn't any problem's with it so in my normal user and run > sudo chown -R me /home/newuser then copied all the hidden files and folders across from /home/newuser to /home/me and that seemed to fix everything.

---

### Post by plo on 2011-05-08
Had similar problem on Natty with Classic dektop after trying to activate dektop cube i Compiz. I had still had my borders but I could not move, change size of any windows.

(Note. I am running Swedish version so the actual English names of the menu options below might not match 100%)

I started the Settings Manager for Compiz Config and choose the Settings option at the lower left.  In this menu I clicked on the button Restore to Standard in the Profile section. This restored everything for me permanently.

/Plo

---

### Post by Krytarik on 2011-05-08
The actual issue was most probably that the Compiz plugins "Window Decoration" and "Move Window" (and maybe more) have been disabled when you tried to enable the Cube.

Greetings.

---

