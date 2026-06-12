---
title: "Quick question: Should metacity be a part of my startup programs?"
date: 2006-10-27
forum: Desktop Environments
---

### Post by mike41 on 2006-10-27
Is it normal for metacity to be a startup program? (ie, listed in system->preferences->sessions->startup)

thanks.

---

### Post by 3rdalbum on 2006-10-28
No, it's not normal. Gnome already starts Metacity before the Startup Programs get run. When you try to run the second instance, it just prints an error and quits.

In other words, it's perfectly safe to get rid of it from the startup programs.

---

### Post by mike41 on 2006-10-28
strange. After I installed EDGY, beryl was causing more startup crashes then usual, so I purged it (manually) by of course apt-get removing it, and then deleting every file output from 'locate beryl*'. Then, when I restarted, metacity wasn't loading anymore at startup. So I thought it was a problem with EDGY, so I reinstalled dapper, but had the same problem! then i added metacity to the startup list, and it all worked. So i reinstalled EDGY, and it still worked. then i installed beryl, and beryl was still messing up my startup, so i purged it (using aptitude purge). Then I tried installing the gandalfn's official compiz, but i dont seem to be able to get it to work, so i purged that. And now, when i restarted, metacity is loading, and everything works fine, but metacity is not in my startup list! So something i did broke it, and something I did magically fixed it. Im staying away from these 3d desktops for a while.  too buggy.

---

