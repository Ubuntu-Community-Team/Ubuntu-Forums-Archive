---
title: "Steam doesnt work. 17.04"
date: 2017-07-22
forum: Gaming &amp; Leisure
---

### Post by tli332 on 2017-07-22
So, i installed steam and it worked for around 1 week before i wanted too boost my FPS. I installed CompizConfigSettingsManager and disabled some settings there, i read a tutorial how to boost so i disabled those.I also installed Oibaf's PPA and lxde.After reboot i choose lxde and try to start steam.It runs for a few seconds and crashes with System Problem Detected, i uninstalled the ppa reinstalled steam, switched back to Ubuntu and still crashes, please help me.


EDIT:Found out that if i run steam through terminal it shows up this
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"
Installing breakpad exception handler for appid(steam)/version(1500335472)
[0722/184237.706896:ERROR:sandbox_linux.cc(344)] InitializeSandbox() called with multiple threads in process gpu-process.
Reinstalling the modules does nothing.

---

### Post by tli332 on 2017-07-22
Forgot to get notified on so i make a new post for that

---

### Post by deadflowr on 2017-07-22
Moved to *Gaming and Leisure*

---

### Post by again? on 2017-07-30
Have you tried purging Oibaf's grahics ppa?(ppa must still be enabled for ppa-purge to work)
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:oibaf/graphics-drivers
```

---

### Post by BloodyIron on 2017-08-15
Are you using STEAM through the main repos, or through a third-party PPA, or something else? When I upgraded to 17.04 I didn't see STEAM break quite like this, and I know a lot of work has gone into the main repos to make it a seamless experience.

It looks like some libraries are either missing or broken from the upgrade.

Are you still stuck?

---

