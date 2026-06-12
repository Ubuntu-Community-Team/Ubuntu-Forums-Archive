---
title: "top panel shows up at the bottom of the desktop!"
date: 2008-08-03
forum: Desktop Environments
---

### Post by discostu668 on 2008-08-03
i am having a weird problem where my top panel show up at the bottom of the desktop when i boot into ubuntu 8.04.  in order to get it back on top, i have to expand and then select to orient it on top.  if i don't, the option immediately toggles back to bottom.

is there anything i accidentally did to cause this? i recently installed AWN, but i had rebooted several times without any problems.

help!

---

### Post by sayakb on 2008-08-03
Just drag it and drop it at the top. Then restart X. Does it again appear at the bottom?

---

### Post by sayakb on 2008-08-03
Also try this: Orient the panel at the top and then, at a terminal:
```
rm ~/.gnome2/session
```
And then restart X.

---

### Post by discostu668 on 2008-08-03
yes, it does reappear at the bottom if i reboot, but i have not tried the drag and drop.

i rebooted and left the panel at the top, fully expanded and it remained at the top.  it's not a huge deal if i leave it expanded, but there should be no reason why the panel would have ended up at the bottom to begin with. 

i'm just confused as to why it would decide to do this.

---

### Post by discostu668 on 2008-08-03
> **LinuxIsInnovation said:**
> Also try this: Orient the panel at the top and then, at a terminal:
```
rm ~/.gnome2/session
```
And then restart X.

i just tried that - it tells me there is no such file or directory.

---

### Post by sayakb on 2008-08-03
Delete the panel (right click on it and select **Delete Panel**). Now create a new panel (right click on some other panel and click **New Panel**) and add applets to it. See if this works.

---

### Post by discostu668 on 2008-08-03
i couldn't delete the panel (for whatever reason), but i removed all of the items from it, re-installed them, rebooted and it seemed to have worked! the panel showed up at the top like it's supposed to do.

thanks for the help!

---

