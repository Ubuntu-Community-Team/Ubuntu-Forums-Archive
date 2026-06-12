---
title: "shutdown command"
date: 2009-01-16
forum: General Help
---

### Post by thefiestysoldier on 2009-01-16
is there any command I can run to completely turn off my computer in xfce?

---

### Post by Tim Sharitt on 2009-01-16
If you open a terminal you can run
```
sudo shutdown -h now
```

---

### Post by hikaricore on 2009-01-16
Does the shutdown menu on the toolbar not work?

---

### Post by thefiestysoldier on 2009-01-16
> **hikaricore said:**
> Does the shutdown menu on the toolbar?
I'm not sure I understand:confused:

thanks Tim I hope it works

---

### Post by hikaricore on 2009-01-16
> **thefiestysoldier said:**
> I'm not sure I understand:confused:

thanks Tim I hope it works

Sorry I must have clicked out of the text box while typing.

I meant, **Does the shutdown menu on the toolbar not work?**

*edit* On rechecking it doesn't seem on my xubuntu system that the "action menu" aka the shutdown menu offers a shutdown option.  Very strange.

---

### Post by adamlau on 2009-01-16
If by chance ```
sudo shutdown -h now
``` hangs during the shutdown process, you can always ```
sudo shutdown -r now
``` and depress your power button after the system reboots to shut the computer down. That is what I have to do for one of my boxes :( .

---

### Post by binbash on 2009-01-16
sudo shutdown -rh now

---

