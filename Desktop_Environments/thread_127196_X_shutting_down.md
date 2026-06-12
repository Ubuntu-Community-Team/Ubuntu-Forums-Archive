---
title: "X shutting down"
date: 2006-02-08
forum: Desktop Environments
---

### Post by Ramses de Norre on 2006-02-08
I've just found a solution for my clock running too fast, I changed my kernel line in menu.lst to ```
/boot/vmlinuz-2.6.12-10-386 root=/dev/sda1 ro quiet splash acpi=noirq noapic no_timer_check=0
``` but now X is shutting down sometimes, it happended allready 3 times in 20min.
Could it be because of that change? I've made it yesterday and it worked fine then..

---

### Post by Ramses de Norre on 2006-02-08
I found this in the last lines of /var/log/Xorg.0.log.old ```
 *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Fatal server error:
Caught signal 11.  Server aborting


Please consult the The X.Org Foundation support
         at http://wiki.X.Org
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

```

Anyone an idea what that's suposed to mean?

---

### Post by senning on 2006-02-08
I don't know of a solution, but you might find [http://www.bitwizard.nl/sig11/](http://www.bitwizard.nl/sig11/) useful.  the gist is that likely problems are in the hardware or in virtual memory.  Hope that helps.

---

### Post by Ramses de Norre on 2006-02-09
I deleted the ```
acpi=noirq noapic no_timer_check=0
``` from my grub menu.lst and didn't have any shutdowns untill now (hope it stays like that). I had to do a hard reset yesterday, I left the pc for a while and when I returned the display didn't un-standby'ed (don't know the right word, hope you understand me:p) and I couldn't change the num-lock button so he just didn't respond anymore..
But now my clock is running at double speed again..
Anyone an idea to solve this time problem without making X unstable?
It's pretty anoying when a lot of things are running at double speed..

---

### Post by Ramses de Norre on 2006-02-10
Bump

---

