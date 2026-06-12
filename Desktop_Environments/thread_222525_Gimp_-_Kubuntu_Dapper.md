---
title: "Gimp - Kubuntu Dapper"
date: 2006-07-25
forum: Desktop Environments
---

### Post by ColinG on 2006-07-25
I've just installed Gimp on Kubuntu (cannot work out why they substituted it with Krita). All is well but I have no printing support and understand that the print modules need to be loaded seperately.

Could some kind sole tell me what I need to install to get the printing working.

Many thanks :) 

Colin

---

### Post by philippe_carlo on 2006-07-25
maybe this helps:
```
sudo apt-get install gimp-print
```

---

### Post by ColinG on 2006-07-25
> **philippe_carlo said:**
> maybe this helps:
```
sudo apt-get install gimp-print
```

I've got gimp-print installed but get the following error.

"lp: Error - no default destination available"

I' have a printer installed, HP PSC 1510, and it works with Open Office etc. Something is awry:confused:

---

### Post by ColinG on 2006-07-25
Solved it. You have to define the print queue when setting up the printer in Gimp.

Thanks for your help - it made me look again.

Colin

---

