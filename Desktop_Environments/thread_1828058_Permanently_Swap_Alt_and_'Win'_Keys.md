---
title: "Permanently Swap Alt and 'Win' Keys?"
date: 2011-08-18
forum: Desktop Environments
---

### Post by user2037 on 2011-08-18
```
setxkbmap -option altwin:swap_lalt_lwin
``` works well enough at start up with a "Startup Applications" entry. It sometimes fails to work when resuming from Suspend. So I have to run it again after awakening.

Adding a script in "/etc/pm/sleep.d" seems like it would work if it ran as my user.

---

