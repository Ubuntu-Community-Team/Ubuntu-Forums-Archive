---
title: "kde expert needed"
date: 2006-11-06
forum: Desktop Environments
---

### Post by garba on 2006-11-06
hello, i hope some kde guru is listening and can help me out ;) i'm deploying KDE on my LAN and i am desperately trying to find a way to prevent my users from deleting removing etc some items from the desktop (namely, links to devices such as cd rom drives, nfs shares and so on, no i am not using HAL because it sucks bad and it's an endless source of trouble), anybody knows if it's possible to amend their .desktop files to remove the above mentioned actions from the drop down menu? the documentation about .desktop files is terribly lacking, any help would be greatly appreciated! regards, andre

---

### Post by Joe_CoT on 2006-11-06
Not a KDE expert ( i use gnome ), but this might help

Look [here](http://docs.kde.org/userguide/customizing-kde.html). My suggestion would be to add the shortcuts to apps/kdesktop/Desktop, and give them only read permissions. Would that not accomplish what you're looking for?

---

### Post by muishkin on 2006-11-06
Can't you just set the owner:group of all those device files to root:root?

---

