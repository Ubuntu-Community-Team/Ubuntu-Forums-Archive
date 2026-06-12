---
title: "Unwanted monitor suspend"
date: 2005-06-27
forum: Desktop Environments
---

### Post by lukeweb on 2005-06-27
I've switched off all of the settings I can find that are relevant to disabling power management and making my monitor go into low-power mode after x minutes, yet still after approx 10 minutes (perhaps more) my monitor goes black.
It's very infuriating - what am I missing? :P

---

### Post by SGC on 2005-06-27
Actually you need to enable the power management mode to disable the screen from going into low-power mode!

Right click on the desktop and choose "configure Desktop" then go to "Display" then to "Power Control" tab

Check "Enable display power management" and drag the three slides to the left until they become "Disabled".

---

### Post by lukeweb on 2005-06-27
Haha, that's bizzare
Thank you! :)

---

### Post by wisemanleo on 2008-03-06
This isn't working for me. I have monitor suspend set to Never under the Power Management setting, but that doesn't work. After about 10 minutes, the monitor will go to sleep. I can still wake it, but I just don't want it to do this in the first place. I'd prefer it to stay in screensaver mode. 

Any ideas?

---

### Post by der_joachim on 2008-03-06
Are the following lines in your /etc/X11/xorg.conf?
```

    Option         "BlankTime" "10"
    Option         "StandbyTime" "30"
    Option         "OffTime" "60"

```

Try setting these values to 0. AFAIK that will disable X's built-in power management features. If these lines are not in your xorg.conf, add them in the ServerLayout section. Make sure that you have backed up your xorg.conf file first. Restart X and it should work. 

Good luck.

---

