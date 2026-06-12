---
title: "deletion of further dated KES7091 shorcut"
date: 2009-03-20
forum: General Help
---

### Post by ivanc on 2009-03-20
Hello,
i have an issue with this name of a shortcute that appears to have a date further that today's date. The problem is that this shortcut is not anymore located on its original folder. But, it shows on the search results if i seach by >3/20/09. So I cannot delete it or change it. 

Any help on how to get rid of this as it prevents me to open a software for which i have a membership.

many thanks,
i

---

### Post by ajgreeny on 2009-03-20
I don't quite understand the problem.  You say you can see it when you do a "by date search" but can not delete it.  Perhaps you are not the owner and you need to delete it as root.  If so, either use the terminal ```
sudo rm /path/to/KES7091
```or open nautilus as root with gksudo nautilus and delete it that way.  Whichever way you choose, make sure you get the right file as you can do a lot of system damage with rm or nautilus as root.  Also be certain that the "shortcut" is not important for something before you delete it.

---

