---
title: "Restart does not work"
date: 2009-05-13
forum: General Help
---

### Post by RM33 on 2009-05-13
I am using Ubuntu 8.10.

Shutdown works fine. But restart does not work. I see the Ubuntu logo on the screen but the PC just hangs there.

Is there something I can do to fix this?

---

### Post by pro003 on 2009-05-13
try this in terminal:

# sudo reboot

or

# sudo shutdown -hr now

an post back did it made your pc restart?

---

### Post by RM33 on 2009-05-21
> **pro003 said:**
> try this in terminal:
 
# sudo reboot
 
or
 
# sudo shutdown -hr now
 
an post back did it made your pc restart?
 
 
So I hit CTRL - ALT - F2 to get to the command line. Then I entered sudo reboot and nothing. What happens is that the screen shows the logo and just hangs there. I end up pulling the plug in order to shut down the computer.
 
My Ubuntu 8.10 does not reboot. It does not reboot if I use the pull down menu or at the command line.
 
What do I need to do to fix this.

---

### Post by pro003 on 2009-05-22
run this command in terminal, cause maybe there is some corruption in your installation:


```
fsck -y
```

this should repair all errors if any

---

