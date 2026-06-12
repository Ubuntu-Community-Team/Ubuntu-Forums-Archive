---
title: "(Ubuntu 12.04) Editing Desktop Environment List on Login"
date: 2012-10-14
forum: Desktop Environments
---

### Post by dci on 2012-10-14
Hi. Is there any way to remove desktop environments from my login screen in Ubuntu 12.04? I don't want to remove the desktop environment itself, I just don't want it to show on that list.

edit: If it makes any difference at all, I'm using Gnome classic and running Unity's dash/launcher inside of it. I want to remove Ubuntu and Ubuntu 2d from my login screen options.

---

### Post by Cheesemill on 2012-10-15
Take a look in the /usr/share/xsessions directory.

I believe that just renaming xxx.desktop to xxx.backup will remove the entry from your display manager (if not then just move the file somewhere else).

---

### Post by dci on 2012-10-15
thanks for the help. changing the file extension didn't work, so i just made another folder inside of xsessions and dumped the ones i didn't want listed in there and that worked fine.

---

### Post by Cheesemill on 2012-10-15
Glad you got it sorted.

Can you please now mark this thread as Solved.

---

