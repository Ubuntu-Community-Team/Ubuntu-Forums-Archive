---
title: "Kubuntu 15.04 and 15.10: no login"
date: 2015-10-24
forum: Desktop Environments
---

### Post by Trad_dog on 2015-10-24
OS: Kubuntu 15.04 and 15.10 64bits
Desktop: Plasma 5
Video card: Nvidia GTX 580



Hi,

I have had an issue with logging into the Kubuntu desktop for a while. I have done a complete install of Kubuntu 15.10 (without overwriting the /home directory).
The issue has not changed. I guess my settings are probably corrupted.
I have deleted the ~/.cache directory which seems to be a prime suspect in a number of thread as well as a few incriminated
.kde sub-directories. To no avail.
Could someone suggest which logs to read or which step to take next ?

Thanks 

Trad

---

### Post by firebadger on 2015-10-24
Could be a graphics driver issue. I had a problem after installing where I couldn't login to a graphical environment. I'd enter my credentials and just get bounced back to the login screen. To resolve I did ctrl-alt-f1 to get a terminal and then ran the following code to install the proprietary drivers...
```
sudo ubuntu-drivers autoinstall
```

---

### Post by Trad_dog on 2015-10-24
I just realised it got worse. I cannot access the terminal now.

---

### Post by Trad_dog on 2015-10-25
I did reinstall the latest version of 15.10 and that solved the problem. Nothing like a clean install.

---

