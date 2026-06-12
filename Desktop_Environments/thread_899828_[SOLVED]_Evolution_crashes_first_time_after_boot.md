---
title: "[SOLVED] Evolution crashes first time after boot"
date: 2008-08-24
forum: Desktop Environments
---

### Post by CameO73 on 2008-08-24
I have this annoying problem with Evolution. Everytime after a reboot, if I want to start Evolution, I have to do it twice.

The first time I see Evolution starting, then after a second or five it disappears. When I start it again it starts within a second -- sometimes without the preview window (which I have to enable again).

When I do this from the console, I get the following output:
```

cameo@lexx:~$ evolution
evolution-shell-Message: Killing old version of evolution-data-server...
Segmentation fault
cameo@lexx:~$ evolution
evolution-shell-Message: Killing old version of evolution-data-server...

(evolution:7080): camel-CRITICAL **: camel_object_is: assertion `o != NULL' failed

(evolution:7080): camel-CRITICAL **: camel_store_get_folder: assertion `CAMEL_IS_STORE (store)' failed

(evolution:7080): camel-CRITICAL **: camel_object_is: assertion `o != NULL' failed

(evolution:7080): evolution-mail-CRITICAL **: mail_tools_folder_to_url: assertion `CAMEL_IS_FOLDER (folder)' failed

```

I've tried reinstalling Evolution -- without any result. Any other possible solutions?

---

### Post by ctal on 2008-09-01
Same problem here.  Anyone have any ideas?  Thanks.

---

### Post by CameO73 on 2008-09-08
Somehow the problem seems to have been fixed by one of the latest updates (from 6 or 7 September 2008). I don't know which one (and I have a lot of development repositories active...) Most likely an updated shared library.

I'll wait a few days before I mark this thread as solved.

---

### Post by CameO73 on 2008-09-10
Well ... it's not a 100% solution. More like 50/50. So half the times I start Evolution after a reboot it will crash, the other half it will start fine (within a second). At least some progress is made :KS

---

### Post by CameO73 on 2008-11-01
Ubuntu 8.10 has fixed my Evolution problem. It starts and shutsdown much faster too! Thanks for the great work, guys!

---

