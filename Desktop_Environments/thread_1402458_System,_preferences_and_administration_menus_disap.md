---
title: "System, preferences and administration menus disapeared"
date: 2010-02-09
forum: Desktop Environments
---

### Post by HandleWithCare on 2010-02-09
Hi all,

just a minute ago the menus prefereences and administration under System vanished as well as all the items under Applications. I managed to fix the latter by deleting (moving actually) /home/username/.config/menus/applications.menu All of the changes I made are gone though. But the other two manus are still gone. Also the edit menus function (when rightclicking on the menus) doesn't react when clicking on it. After some searching I could only find remotely related problems and fixed imply resetting the whole desktop, not really a solution, more a drastic last cry for help. Has anyone encountered this before and knows hoe to fix this and/or does anyone know what might have caused this problem?

---

### Post by HandleWithCare on 2010-02-09
To give you all a heads up and since no reactions were posted so far, I found a solution. Besides moving (or deleting) application.menu I had to move settings.menu as well. Something was going wrong with alacarte which pointed me to the ~/./config/menus folder. I didn't know there was a settings.menu. After deleting that file all menus are back and alacarte runs fine again.

---

