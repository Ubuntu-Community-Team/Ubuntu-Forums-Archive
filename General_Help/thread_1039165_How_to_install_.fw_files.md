---
title: "How to install .fw files?"
date: 2009-01-14
forum: General Help
---

### Post by ZweeK on 2009-01-14
I am trying to install a firmware for my TV tuner. I have an extracted file with .fw extension. It is suppose to be installed in the lib/firmware folder. I tried dragging the file in there but it says permission denied. Please help, thanks.

---

### Post by Ayuthia on 2009-01-14
You have to move the files using admin privileges.  I think you can accomplish this by using 'gksu nautilus' (without the quotes) at the Terminal and it will bring up the file manager window in admin mode.  You will then be able to copy the file over.  Once you are done, remember to close the window so that you don't accidentally copy or move other files by accident (since you are in admin mode).

---

### Post by ZweeK on 2009-01-14
Thanks. Worked perfectly!

---

