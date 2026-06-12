---
title: "How can I switch from KDE 3.5 to 4?"
date: 2008-09-09
forum: Desktop Environments
---

### Post by sambarluc on 2008-09-09
After a while I decided to give a try to KDE 4 on my Thinkpad T42, and I liked it so much that I would like to completely switch to the new KDE. Anyway, for hard disk space reasons, I would like to delete KDE 3.5 and keep the new one only. Is there any how to? Do you think there may be some limitation?

---

### Post by awakatanka on 2008-09-09
Think you can better wait till intrepid is ready, then you have kde4 and no more kde3.

Didn't hardy have a remix iso where it installed kde4? If it still exist you can use that one

---

### Post by Zorael on 2008-09-09
That's actually difficult. What I would do is to install KDE4 proper (like you already have) and then go through and uninstall known KDE3 packages until you hit a vulnerable spot and it pulls a whole lot of dependencies with it.

**kdm** is a given, then there's **kwin**, perhaps **kdesudo**, **kcontrol**, **systemsettings**, etc. **kdebase-bin-kde3** looks interesting, "core binaries for the KDE base module".

Just make sure to review your changes before applying them.

---

### Post by sambarluc on 2008-09-10
I tried this way, but could free up only little more than 100mb, so I think that I will wait for 8.10, as I do not think 100mb are worth the work...

---

