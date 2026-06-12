---
title: "Reinstall but keeping /home folder"
date: 2006-07-08
forum: Desktop Environments
---

### Post by rem on 2006-07-08
Hi everybody,

I was wondering, what would be the best method to do a clean system reinstall but keeping the /home user files same time? I have separated partitions set up for /root and /home and I'd like to refresh a bit :) I looked for a good tut on that but didn't find a reliable one... I'd need some exact info, don't wanna erase my /home stuff..

Thanks a lot in advance!

---

### Post by Max Luebbe on 2006-07-08
If you seperated the partitions the first time around you should be fine.
An install wont overwrite the /home, just make sure you setup the mount points for the drives correctly (use your old / as / and old /home as /home!)

If you want to be extra cautious, make your initial user account with a unique name that wasnt on your old /home, so theres no chance of the folders being overwritten.

---

### Post by aysiu on 2006-07-08
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) walks you through it.

There, I mount /documents instead of /home, but it's the same principle.

---

### Post by rem on 2006-07-08
Thanks a lot guys, really appreciate it! With your help I should be able to do it the right way :) 

My best!

---

### Post by brandonjp on 2007-10-25
> **Max Luebbe said:**
> If you want to be extra cautious, make your initial user account with a unique name that wasnt on your old /home, so theres no chance of the folders being overwritten.

I did this, but now I can't access my old home folder:

[INDENT]```
"smb://bra...Documents" cannot be copied because you do not have permissions to read it.
```[/INDENT]

any suggestions?
thanks
--bp

---

