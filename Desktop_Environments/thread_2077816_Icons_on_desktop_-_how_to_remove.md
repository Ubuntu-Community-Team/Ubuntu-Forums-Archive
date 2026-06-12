---
title: "Icons on desktop - how to remove ?"
date: 2012-10-29
forum: Desktop Environments
---

### Post by George Heine on 2012-10-29
Hello, using 12.04 with default Unity desktop.

Powered up this morning and discovered all my top-level folders and files displayed as icons on the desktop.  Never use these icons and would prefer to be rid of them, to avoid accidentally clicking on one, and also just to get them out of the way.

Installed 12.04 about a week ago and this did not occur until today.  Perhaps the following is related:  before powering down yesterday, deleted a number of empty folders from my home directory, including "Desktop" (also "Music" and "Documents" and a few others).   Recreating Desktop and rebooting did not solve the problem.

How can the blank desktop be restored?  Looked in System Settings\Appearance, also in dconf-editor, but didn't immediately see anything of relevance. 

Thank you for any assistance.

---

### Post by George Heine on 2012-10-29
Found a solution.  Edit the file ~/.config/user-dirs.dirs,  to include the following line: 
 ```
XDG_DESKTOP_DIR="$HOME/Desktop"
```Then reboot, and only items in the "Desktop" folder will be displayed.  At least this worked on my system.

---

