---
title: "How to undo a command"
date: 2009-01-17
forum: Desktop Environments
---

### Post by billytalent on 2009-01-17
Hey guys, i typed the following command into terminal and it made my screen huge, everything is over the top, how can i undo it?

```
sudo ln -sf /etc/fonts/conf.avail/10-autohint.conf /etc/fonts/conf.d/
```

---

### Post by fsierra3 on 2009-01-17
You can try deleting the symbolic link you created:
sudo rm /etc/fonts/conf.d/10-autohint.conf

---

### Post by billytalent on 2009-01-17
> **fsierra3 said:**
> You can try deleting the symbolic link you created:
sudo rm /etc/fonts/conf.d/10-autohint.conf

I love you!!!!!!!

---

