---
title: "Compiz Randomly Freezing Up"
date: 2014-04-20
forum: Desktop Environments
---

### Post by Garchomps on 2014-04-20
Compiz will randomly crash with the follwing error on Ubuntu 14.04, taken from .xsession-errors
```
init: update-notifier-crash (/var/crash/_usr_bin_compiz.1000.
crash) main process (1610) terminated with status 127
```
This can potentially cause to me lose a lot of work, thanks for in advanced for any possible answers as to why this happens. It's a rather serious issue for me.

---

### Post by Garchomps on 2014-04-20
After messing with some settings it seems this only happens when I use my nvidia card, that's the last of what I know. It's a laptop with primus and you can switch the card in use for rendering X with the intigrated graphics.

---

### Post by deadflowr on 2014-04-20
The file **/var/crash/_usr_bin_compiz.1000. crash**
is a crash report.
If you navigate to it in nautilus and double click on it, it will open a crash report window.

As far as the nivida primus issue, are you using nivida-prime or is bumblebee, maybe?

Also, when it crashes, does the system become completely unusable, or does it bounce back after a minute?

If it bounces back, then it's a somewhat normal behavior of compiz, it would be compiz just restarting but the crash report system considers that a crash. It can also make your system seem frozen, (among the many things a compiz restart looks like)

If completely unusable then it's probably a problem with the driver/switcher tool.

Anyway, those are my two cents.

---

