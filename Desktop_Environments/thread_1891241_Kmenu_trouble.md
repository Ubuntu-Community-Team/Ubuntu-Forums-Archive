---
title: "Kmenu trouble"
date: 2011-12-05
forum: Desktop Environments
---

### Post by inkrypted on 2011-12-05
I hope I'm posting this in the right section. I am using a fresh install of Kubuntu KDE 4.7.2 and found that I was unable to edit the Kmenu. When I do my changes cause the entry to disappear and sometimes the parent section. I have tried checking the permissions on ~./local/applications and ~./local/desktop-directories, ~./config/menus, ~/.kde/share/config. Also tried renaming ~/.local/share/applications and ~/.kde/share/config/kmenueditrc with a .bak extension and ran kbuildsycoca4 to rebuild. The end result is I am still unable to make changes or the entries disappear or the parent disappears. I tried running kmenuedit in a terminal and when I saved this came up. 
X Error: BadWindow (invalid Window parameter) 3   Major opcode: 20 (X_GetProperty)   Resource id:  0x5c000b9

If anyone has and advice or suggestions I would really appreciate it.
Thanks.

---

### Post by kio_http on 2011-12-05
> **inkrypted said:**
> I hope I'm posting this in the right section. I am using a fresh install of Kubuntu KDE 4.7.2 and found that I was unable to edit the Kmenu. When I do my changes cause the entry to disappear and sometimes the parent section. I have tried checking the permissions on ~./local/applications and ~./local/desktop-directories, ~./config/menus, ~/.kde/share/config. Also tried renaming ~/.local/share/applications and ~/.kde/share/config/kmenueditrc with a .bak extension and ran kbuildsycoca4 to rebuild. The end result is I am still unable to make changes or the entries disappear or the parent disappears. I tried running kmenuedit in a terminal and when I saved this came up. 
X Error: BadWindow (invalid Window parameter) 3   Major opcode: 20 (X_GetProperty)   Resource id:  0x5c000b9

If anyone has and advice or suggestions I would really appreciate it.
Thanks.

Hmm seems to work fine here but I'm on KDE 4.7.3. Could you try updating to that? (See instructions on kubuntu.org) Also try going to the home folder and doing "rm -rf .kde" in a console session (NOTE: This will reset all KDE settings to default!)

---

### Post by inkrypted on 2011-12-05
I would gladly upgrade if it solves my problem. Is it in the backports?

---

### Post by inkrypted on 2011-12-05
Ok giving the upgrade a try. Thanks for the advice.

---

### Post by inobe on 2011-12-05
[http://www.kubuntu.org/news/kde-sc-473](http://www.kubuntu.org/news/kde-sc-473)

i just add the ppa

---

### Post by inkrypted on 2011-12-05
The update did indeed fix the problem. Many thanks for the advice. I guess it's just a KDE 4.7.2 bug.

---

### Post by wieman01 on 2012-01-03
I tried the suggested solution, installed the PPA packages, but still cannot add shortcuts, no matter what I do. This is frustating.

---

