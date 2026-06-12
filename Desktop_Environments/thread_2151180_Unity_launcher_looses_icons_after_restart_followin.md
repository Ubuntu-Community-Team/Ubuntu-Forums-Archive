---
title: "Unity launcher looses icons after restart following 13.04 update"
date: 2013-06-03
forum: Desktop Environments
---

### Post by Calimo on 2013-06-03
I switched from 12.10 to 13.04 a few days ago. Since then, the launcher doesn't remember one of my icons after restart.

It is a custom .desktop placed in /home/xavier/.local/share/applications. What I do: I drag and drop it from Nautilus to the launcher. It works but when I restart, the icon isn't there any more.
After adding the icon to the launcher, I can check that it was added with dconf: in com/cannonical/unity/launcher the value contains my icon. But not after I restart. Some other icons I added to the launcher (but I didn't create) are just fine.

I tried a unity --reset-icons which wiped off the launcher. It restored the factory-default. I made my changes, and all of them are kept except this icon.

This starts to be annoying since I use this icon quite often.
What could be a cause of the disappearance of this icon? Any hint welcome.

---

### Post by deadflowr on 2013-06-03
Trying adding the launcher from the dash instead of nautilus.

---

### Post by zeljkojagust on 2013-06-04
This is happening to me also. One solution is:

Press Ctrl+Alt+T, a terminal window will pop up. Start Compiz manager by executing "sudo ccsm". In Search enter Unity and icon for Unity Plugin will pop up. It will probably be unchecked, so check (enable) it. You will probably get couple of warnings, you can just "Yes" on them all. If icons don't appear after that, do it all again. After second run you should have your icons and taskbar.

---

