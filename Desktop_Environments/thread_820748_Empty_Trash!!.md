---
title: "Empty Trash?!?!"
date: 2008-06-06
forum: Desktop Environments
---

### Post by SirThom on 2008-06-06
I've been playing around with KDE.  In some ways it seems more solid then gnome, even though I still prefer the overall look and feel of gnome.
Here is the deal.  In KDE how do I empty the trash?  I've been going in via the terminal to ~/.local/share/Trash and doing it manually, and it's empty but the icon still shows full trash.  When I either left or right click on the trash icon in the menu bar I can't find any obvious options for emptying.  If I open the trash in a new window I don't see any options for emptying.  If I right click on the desktop I don't see any options emptying.  What am I missing?

---

### Post by .nedberg on 2008-06-06
When you left-click the icon in the system tray you should be given the option to empty the trash.

The reason for it still showing "full" is probably because KDE does not know that you emptied it. Have a look at ~/.kde/share/config/trashrc

Either delete that file or change it to
```
[Status]
Empty=true
```

---

### Post by SirThom on 2008-06-06
> **.nedberg said:**
> When you left-click the icon in the system tray you should be given the option to empty the trash.

The reason for it still showing "full" is probably because KDE does not know that you emptied it. Have a look at ~/.kde/share/config/trashrc

Either delete that file or change it to
```
[Status]
Empty=true
```

Oh it works now.  For some reason it was greyed out before so I didn't notice it, even though there was stuff in it.  Maybe it's because I needed root privileges to empty it?  I made a text document, put it in there, and was able to empty it successfully.

---

### Post by .nedberg on 2008-06-06
If root put something in there you would need root to remove it too. Good to hear that it is fixed!

---

