---
title: "Shutdown reboots system"
date: 2005-10-13
forum: Desktop Environments
---

### Post by lassel on 2005-10-13
I am planning on putting my box in to the attic so I can't hear it humming. That however requires that I can control it without touching it.

Right now when I select System > Log out > Shutdown in my menu the computer goes down and then reboots instead of closing.

I assume it has something to do with the ACPI support.

Is there any kernel options, modules or settings that I can try to make it work??

Thanks

/Lasse

---

### Post by SilentCacophony on 2005-10-13
On the software side, I don't know. I do know that my BIOS has settings which allow the user to select the behavior for standby, suspend, shutdown, etc...

Might be worth a check if you don't see anything else.

---

### Post by 5-HT on 2005-10-13
Hmm...not sure what's going on or how to remedy in terms of the GUI, but what about trying to shutdown from the CLI?

As a workaround, maybe this will work...

In a terminal type:

 ```
sudo shutdown -h now 
```

This will tell the computer to shutdown and power off starting "now".
You can always adjust the execution time, and if you really want automation, set it up as a cron job.

HTH

---

### Post by kvidell on 2005-10-13
You can also do```
sudo init 0
``` or ```
sudo halt
```

Those achieve the same effect.
- Kev

---

### Post by 5-HT on 2005-10-13
[QUOTE=kvidell]You can also do```
sudo init 0
``` or ```
sudo halt
```

Those achieve the same effect.
- Kev[/QUOTE]

Thanks for the tip, never knew about the halt command.

---

### Post by lassel on 2005-10-14
I am happy to report that this issue solved itself with the latest kernel update.

Ubuntu just rocks!

---

