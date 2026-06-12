---
title: "Cannot remove Wine"
date: 2006-07-19
forum: Desktop Environments
---

### Post by harryhoudini66 on 2006-07-19
I am having trouble with wine. I want to start from scratch but cannot do so. I have uninstalled it a few times. I cannot remove it from /home. It shows with a lock on the folder.

When I try to delete it, it says it does not exsist. I can clearly see it. I also tried via the terminal and it did not see it.

---

### Post by harryhoudini66 on 2006-07-19
This did it for me.





sudo rm ~/.wine -Rfv

---

