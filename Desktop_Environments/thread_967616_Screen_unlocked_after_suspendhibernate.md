---
title: "Screen unlocked after suspend/hibernate"
date: 2008-11-02
forum: Desktop Environments
---

### Post by pp77 on 2008-11-02
Using the latest Xubuntu 8.10, screensaver options are set to lock screen but after resuming from suspend and hibernation the screen is unlocked and that poses a grave security risk. Anyone having the same problem, any workarounds? Thanks.

---

### Post by florentx on 2009-03-22
> **pp77 said:**
> Using the latest Xubuntu 8.10, screensaver options are set to lock screen but after resuming from suspend and hibernation the screen is unlocked and that poses a grave security risk. Anyone having the same problem, any workarounds? Thanks.

I worked out this issue with ubuntu Jaunty.
I use uswsusp for suspend and hibernate

Just drop file 00custom-lock in /etc/pm/sleep.d/
and set executable bit

```

user@jaunty$ sudo chmod ugo+x /etc/pm/sleep.d/00custom-lock

user@jaunty$ cat /etc/pm/config.d/01custom-uswsusp
# The sleep/wake system to use
SLEEP_MODULE="uswsusp"

# Suspend module for the wifi card
#SUSPEND_MODULES="ath_pci ath5k"

# Disable verbose logging
HOOK_BLACKLIST="00logging"


```

---

