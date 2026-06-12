---
title: "HELP! My Screen Goes black right after the edgy Usplash!"
date: 2006-11-01
forum: Desktop Environments
---

### Post by BOBSONATOR on 2006-11-01
it just goes black, no gdm no nothing! I need help asap. thanks.

BTW, i just installed beryl, and rebooted to see this,,.

---

### Post by solarwind on 2006-11-01
> **BOBSONATOR said:**
> it just goes black, no gdm no nothing! I need help asap. thanks.

BTW, i just installed beryl, and rebooted to see this,,.

Ok, when your screen is blank, press these keys simultaniously:

Ctrl+Alt+F2 (or F3 or F4, try all of them)

---

### Post by BOBSONATOR on 2006-11-01
no go sorry....

---

### Post by BOBSONATOR on 2006-11-01
please help! i need this laptop tomorrow!

---

### Post by shingalated on 2006-11-02
Found this on the beryl howto:

Some users may be experiencing a black screen on restarting X because of eeprom loading before X. Simply comment out eeprom in /etc/modules and you may get everything fixed I would reccomend checking your xorg.conf changes first though, as many people will not need to mess about with this latest fix.

In bsm, leave "sync to vblank" on
Don't use "detect refresh rate"
And set your refresh rate to what it should be.
You can find this out using:
Code:

nvidia-settings -q all | grep RefreshRate

---

### Post by BOBSONATOR on 2006-11-02
> **shingalated said:**
> Found this on the beryl howto:

Some users may be experiencing a black screen on restarting X because of eeprom loading before X. Simply comment out eeprom in /etc/modules and you may get everything fixed I would reccomend checking your xorg.conf changes first though, as many people will not need to mess about with this latest fix.

In bsm, leave "sync to vblank" on
Don't use "detect refresh rate"
And set your refresh rate to what it should be.
You can find this out using:
Code:

nvidia-settings -q all | grep RefreshRate

Yea, i wish i could. I dont even get a command prompt.

---

### Post by BOBSONATOR on 2006-11-02
> **BOBSONATOR said:**
> Yea, i wish i could. I dont even get a command prompt.

Or even better, i just booted a edgy live cd, does anyone know where all the old files went? so i can just go in there and change my X11.conf?

---

### Post by taurus on 2006-11-02
Boot into recover mode from GRUB menu and at the prompt, try to reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```

---

### Post by BOBSONATOR on 2006-11-02
Tarus, i love you.

---

### Post by taurus on 2006-11-02
> **BOBSONATOR said:**
> Tarus, i love you.
Easy now, tiger...  :mrgreen:

---

