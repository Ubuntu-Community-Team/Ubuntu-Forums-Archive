---
title: "Intel x3100 graphics problems"
date: 2009-05-16
forum: General Help
---

### Post by Nerv68 on 2009-05-16
I have intel x3100 graphics (965gma chipset) on my acer laptop. I know compiz has the chipset blacklisted, but I can't even get normal visual effects to work.Im not sure if I even have any drivers installed. Is there a command I can type in to check? System > administration > hardware driver detects nothing. Any help would be appreciated.

---

### Post by Nerv68 on 2009-05-16
bumparoo

---

### Post by orlox on 2009-05-16
Even normal effects require compiz to work, and since your card is blacklisted, that wont happen.

Unleeeeesssss

you take away compiz checks. To do this, run:
```

gedit ~/.config/compiz/compiz-manager

```
And add to the file this:
```

SKIP_CHECKS=yes

```
Save, retry activating your desktop effects

Disclaimer: There is a chance your computer will freeze from time to time making you wanna kill yourself, but its not always like this, and in my personal experience, the freezes have been very scarce (like, ~1 per month)

---

### Post by Nerv68 on 2009-05-16
Thanks for the answer... but before I try that I'm wondering if it would be better to rollback to the intrepid driver as explained here > [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by orlox on 2009-05-16
As far as I know, this wont stop your card from being blacklisted. The blacklisting is done by compiz, not the intel drivers.

---

