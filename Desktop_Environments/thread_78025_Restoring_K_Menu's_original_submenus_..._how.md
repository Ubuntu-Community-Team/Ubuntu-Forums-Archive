---
title: "Restoring K Menu's original submenus ... how?"
date: 2005-10-17
forum: Desktop Environments
---

### Post by vastuk on 2005-10-17
So, the newbie (me) got a little OCD on organizing submenu items in the K Menu.  As a result of renaming these submenus, when I now choose to 'Add Applications', a program will install successfully, a dialog box will tell me where it placed a shortcut to the executable ... but, of course, with the original submenu's name missing, the link is not created. :???: 

Any ideas for restoring the original submenus?  (NOTE: I'm not referring to KDE Menu Editor's > Settings > Configure Shortcuts > Defaults > OK solution.)  Instead, we're talking about clicking on the K Menu and the restoring the original submenu names which appear under "All Applications."  Maybe an easier solution is, what are those original submenu names again?

Thanks in advance.

---

### Post by SGC on 2005-10-17
To restore the orginal kmenu delete this file:
~/.config/menus/applications-kmenuedit.menu

---

### Post by vastuk on 2005-10-17
Thx, SGC --> it worked.  :) Removing the file you suggested, then removing the K Menu-Menu from the taskbar, logging out ... all achieved what I wanted.  Thanks for the accurate and expeditious reply.

---

### Post by Zyphrexi on 2005-11-03
i'd just like to mention that i love this post, and think it should be added to a guide or something. KDE has a tendency to not want to update the menus, in fact i think i'll add a rm command to my sidebar. You don't need to reboot btw, or even logout of Kde. Pretty nifty stuff.

---

### Post by PokerFacePenguin on 2005-11-14
My favorite thread on finding those "lost apps" that one installs with the package installers is found at:

[http://ubuntuforums.org/showthread.php?t=32220](http://ubuntuforums.org/showthread.php?t=32220)

---

