---
title: "Rdesktop - can't exit from fullscreen mode"
date: 2007-10-19
forum: Desktop Environments
---

### Post by eoinmadden on 2007-10-19
I upgraded to 7.10 this morning. Since I upgraded, I've had a problem with rdesktop.
When I press Ctrl+Alt+Enter to leave fullscreen, it doesn't exit. It seems to 'blink'. That is, it seems to exit and then reenter fullscreen mode straight away.
Now my only way of exiting rdesktop is to kill it.

---

### Post by tommie_ on 2007-10-21
Hi I have the same problem.

The problem is caused by the extra or normal effects that are enabled under appearence.  

I was unable to find any solution...

---

### Post by fordi on 2007-10-22
I had the same problem. Try disabling legacy fullscreen support (workarounds) in compiz settings manager (ccsm). This did the trick for me.

---

### Post by memfiz on 2007-10-22
Thanks for help, I've just resolved the problem the same way...

---

### Post by paulstaf on 2007-10-22
Mine doesn't seem to have compiz installed.  It says it can't find ccsm.

I did go into appearance and set it to NONE of the special effects, and now all works fine.

It didn't work in the NORMAL or EXTRA modes at all either.

Thanks,
Paul

---

### Post by eoinmadden on 2007-10-23
Thanks fordi!
Disabling legacy fullscreen support worked for me.

---

### Post by eoinmadden on 2007-10-23
Paulstaf,
Try installing  compizconfig-settings-manager through the Synaptic Package Manager.
Then you should have ccsm.

---

### Post by okfdjg on 2007-12-19
> **fordi said:**
> I had the same problem. Try disabling legacy fullscreen support (workarounds) in compiz settings manager (ccsm). This did the trick for me.

Thanks a lot!!!!!!

---

