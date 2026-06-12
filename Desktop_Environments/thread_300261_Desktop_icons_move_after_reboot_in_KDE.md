---
title: "Desktop icons move after reboot in KDE"
date: 2006-11-15
forum: Desktop Environments
---

### Post by chriscrutch on 2006-11-15
I'm running Kubuntu Dapper with KDE 3.5.5.  I have arranged my icons on the Desktop to my liking.  I personally like to group them by function (all internet programs together in one section of my desktop, all multimedia programs together, etc.).  I have the option to arrange icons off, but the option to align them to a grid on.

After restarting, the icons that were any lower than the top row will all shift up one row.  After another restart, they'll shift up again, and so on, until all of my desktop icons are in the highest row possible, and aligned to the left as much as possible.  Turning on the option to lock the icons in place has no effect on this behavior.

Any ideas on how to stop this?  Thanks in advance for thinking about this.

--chriscrutch

---

### Post by Kalinda on 2006-11-22
I'm also experiencing this issue with Edgy... it might be some sort of KDE bug, although I didn't get it when I was using 3.5.5 in Dapper.

I'm pretty sure the best way to fix it is to delete the contents of the KDE config file that has information about the desktop icons. This will then erase your icons and you can do it again and hopefully it won't screw up. I say this because I've installed Edgy on two other computers and I don't experience this problem with either of them... so maybe killing the desktop config file will do it.

The problem is that I dunno which one handles icons. I deleted the contents of kdesktoprc and all that did was reset my wallpaper to the default. Anyone know which config file it could be?

---

