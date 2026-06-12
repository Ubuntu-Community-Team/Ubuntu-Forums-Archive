---
title: "Missing Desktop for one user when upgrading to 14.04"
date: 2014-04-23
forum: Desktop Environments
---

### Post by anoe on 2014-04-23
Hi there. I upgraded my lubuntu distribution from 12.10 to 14.04. Something got broken in the process and now when loging in with my user to lubuntu environment i have no desktop nor lxpanel. When running lxpanel the panel shows up, but with none of my settings. When loging in lubuntu netbook environment everything is fine. I installed lxde meta package and when loging in lxde everything is fine too (but with default settings, of course).

when loging with other users in lubuntu environment everything is fine for those users, so i would say something is broken in the process of loading my lubuntu environment.

any help?

tx

---

### Post by bapoumba on 2014-04-23
How did you upgrade ? Regular upgrade path is from LTS > LTS, ie 12.04 > 14.04 or from release n-1 > n, ie 13.10 > 14.04.

Are the other users created after the upgrade or were these users already existing before the upgrade ?

---

### Post by anoe on 2014-04-23
> **bapoumba said:**
> How did you upgrade ? Regular upgrade path is from LTS > LTS, ie 12.04 > 14.04 or from release n-1 > n, ie 13.10 > 14.04.

Are the other users created after the upgrade or were these users already existing before the upgrade ?

Directly from 12.10 to 14.04. The others users existed before the upgrade, it's only one user who is affected (the user whose account i used to do the upgrade from).

---

### Post by bapoumba on 2014-04-23
I had tabs opened but I closed them.. Was to suggest a shot in the dark and look at your ~/.config/autostart file and see if there is any difference between users. I cannot find the link again where I saw that and what the culprit was..

---

### Post by anoe on 2014-04-25
> **bapoumba said:**
> I had tabs opened but I closed them.. Was to suggest a shot in the dark and look at your ~/.config/autostart file and see if there is any difference between users. I cannot find the link again where I saw that and what the culprit was..

hi there. Maybe you were referring to this link, [http://ubuntuforums.org/showthread.php?t=2084966](http://ubuntuforums.org/showthread.php?t=2084966)?

I did what it was saying there, but to no good. About the folder ~/.config/autostart, don't think the problem is there, because when logging with lubuntu netbook session everything is fine, the lxbar shows with my configuration. I think it's more a broken file or something that fails to load when choosing lubuntu session. As I stated before, lubuntu notebook and lxde sessions load smooth.

So, i'm gonna search for two things:

1) Log file where the load of the session is logged. That may give me some clue about the problem.

2) Information about the session load in lubuntu/ubuntu.

If anyone could point me to some information about this it would be very helpful.

and, bapoumba, thanks for your interest and your time

---

### Post by anoe on 2014-04-25
I am progressing. I moved ~/.config to ~/.config_old as suggested in another thread and now everything's back - but no settings for any program, nor for the task bar, of course. Gonna be copying and pasting different folders to see which is the troublesome one. I'll keep you updated.

cheers.

---

### Post by bapoumba on 2014-04-25
Possible that was the thread (from post #4), but I think I read the suggestion on the lxde forums.

Anyway, upgrading directly from 12.10 to 14.04 is not recommended as it can break things, as you have found out.
If now you are working on building a proper ~/.config, you may also want to compare with files from unaffected users. That may be quite a lot of work. Next time, you may consider a fresh install when you want to skip releases. And of course, back up all the important things you cannot afford to loose :)

---

### Post by anoe on 2014-04-25
Ok, so the problem was the file ~/.config/lxsession/Lubuntu/desktop.conf. I think it was corrupted somehow.

now i have to solve this freezing that is going on with the desktop since the upgrade...

cheers

---

### Post by bapoumba on 2014-04-25
Glad you see you found it, and thanks much for marking your thread as solved :)

---

