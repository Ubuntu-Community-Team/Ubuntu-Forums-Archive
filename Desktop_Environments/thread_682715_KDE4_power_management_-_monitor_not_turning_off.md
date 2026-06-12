---
title: "KDE4 power management - monitor not turning off"
date: 2008-01-30
forum: Desktop Environments
---

### Post by NutMonkey on 2008-01-30
Since I installed KDE4 on Kubuntu, my monitor does not turn off automatically anymore.

According to the "Solid" configuration, power management uses the "HAL-Power" backend, but I can't find any information on how this works.  Any ideas where to look?

---

### Post by buddha001 on 2008-02-17
I'm having the exact same How/where does one configure all the power management capabilities?

---

### Post by VijayakumarK on 2008-04-24
I had the same problem when I switched to a fresh install of Kubuntu Hardy. Installing KPowersave gave some great power management capabilities.

On a HP dv6700z (AMD Turion X2), I'm able to suspend, hibernate, turn off LCD when system is idle, set power profile etc. :)

I understand KPowersave is not ported to KDE4 yet.

---

### Post by maestrobwh1 on 2008-05-11
I did the latest update with the gutsy ppa in my repo.  My internal and external monitors no longer suspend even with the option checked under "systemsettings --> display --> power option checked.  I have all things turned down to 10 minutes and I can see the backlight in both the internal and external monitors well after 10 minutes.  The power light doesn't blink on the external monitor anymore.

I have kpowersave installed and tried to use that to manipulate the settings... nada.

Lastly, I logged into root and checked off the boxes in systemsettings (oddly in gutsy, there IS STILL an issue with launching certain programs with kdesudo, sudo, kdesu... Qmutex deadlock warning pops up... how stupid is that?  This is still an issue after several months... and no fix I have found in the posts I have seen have has worked for me.  

I have kde4 installed alongside kde3 and kde3 still powers off the screens.

Is there a config file or an ownership issue?  I did a
sudo chmod 777 -R /home/(username)/.kde4/ just to make sure.

If this setting is in a config file, and i can change it manually, I am fine with that.

---

