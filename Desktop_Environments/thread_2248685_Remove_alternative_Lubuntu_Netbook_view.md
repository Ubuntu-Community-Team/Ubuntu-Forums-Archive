---
title: "Remove alternative Lubuntu Netbook view"
date: 2014-10-16
forum: Desktop Environments
---

### Post by SageOfSmeg on 2014-10-16
On my ultraportable notebook I have lubuntu 12.04.
 
At login it offers options for regular Lubuntu Desktop or for an alternative Lubuntu Notebook/Netbook view, which I rarely ever use.
 
Since I prefer to use the regular desktop view I was wondering if there is a way to remove the alternative Lubuntu Notebook/Netbook view, both from the options at the login screen and completely from the machine?
 
If it is possible to remove, would it save any disk space?
 
Thanks for any help.
 
---
lubuntu 12.04
ASUS Eee Pc 4g-bk026 7", 4GB SSD, 512MB

---

### Post by vasa1 on 2014-10-16
Go into /usr/share/xsessions using your terminal: do a simple **ls** there. You may see something like this:```
$ ls
Lubuntu.desktop          openbox.desktop
Lubuntu-Netbook.desktop 
$ 
```
Using **sudo** rename Lubuntu-Netbook.desktop to Lubuntu-Netbook.desktop.bak. The next time you login, you shouldn't see the netbook option.

As far as removing software which is unique to the netbook session, I haven't a clue although I feel it's possible to do some real damage chasing down this option.

---

### Post by SageOfSmeg on 2014-10-16
That did the trick. Thanks
Looking at the size of the *.desktop files, removing the Lubuntu-Netbook.desktop file would save no space as such, so I have just renamed it.

---

