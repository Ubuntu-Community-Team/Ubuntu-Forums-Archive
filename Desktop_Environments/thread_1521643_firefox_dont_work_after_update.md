---
title: "firefox dont work after update"
date: 2010-07-01
forum: Desktop Environments
---

### Post by janrikard on 2010-07-01
After updating my 10.04 firefox doesnt work, the process is there but no nice browser shows up on the screen.

After renaming the ~/.mozilla/firefox firefox starts, but all my settings and stuff is gone.
Anyone know what to remove in the firefox directory to get firefox to start with my settings?

/Rikard

---

### Post by lovinglinux on 2010-07-01
Looks like removing the file **secmod.db** from your profile will do it. Nevertheless, I would try to update Firefox again, since some issues from yesterday morning update has been fixed already.

---

### Post by lovinglinux on 2010-08-07
I know is not a solution, but I have created a new Firefox extension that allows to delete secmod.db and compatibility.ini automatically when exiting Firefox, so you don't need to do it manually.

[http://profilecleaner-extension.blogspot.com](http://profilecleaner-extension.blogspot.com)

After installation, the extension will start without deleting the files by default and it will prompt for selecting the files you want to delete.

I have included compatibility.ini because that is causing the same issue here, with Firefox 3.6.8.

---

