---
title: "Avant-Window-Navigator and AWN Manager"
date: 2007-08-12
forum: Desktop Effects &amp; Customization
---

### Post by phasee on 2007-08-12
Hi I am using Ubuntu Feisty 64-bit.

I installed the latest AWN using the bzr command. Everything installed ok except that I cant add launchers.

I click add and nothing happens. I searched on google found that others were having this problem and found out about AWN Manager. I installed it, tried to run it got an error but that was fixed by isntalling the latest version of AWN.

I had AWN Manager working for one session and I got a firefox launcher added. Now when I try to run AWN Manager, for some reason I am getting this error.

Traceback (most recent call last):
  File "./awnManager.py", line 194, in <module>
    awnmanager = AwnManager()
  File "./awnManager.py", line 92, in __init__
    self.launchManager = awnLauncher(self.wTree, self.AWN_CONFIG_DIR)
  File "/home/stephen/awn-extras/awn-manager/awnLauncher.py", line 65, in __init__
    self.make_model()
  File "/home/stephen/awn-extras/awn-manager/awnLauncher.py", line 123, in make_model
    self.refresh_tree(uris)
  File "/home/stephen/awn-extras/awn-manager/awnLauncher.py", line 133, in refresh_tree
    self.model.set_value (row, 0, self.make_icon (i))
  File "/home/stephen/awn-extras/awn-manager/awnLauncher.py", line 167, in make_icon
    if "/" in name:
TypeError: argument of type 'NoneType' is not iterable

Dont have a clue how to fix it. Tried searching but havent had any luck finding anything that helps.

Now I am posting here :) Any help is appreciated.
Thanks.

---

