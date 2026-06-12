---
title: "Nvidia proprietary driver"
date: 2011-05-31
forum: Desktop Environments
---

### Post by gdesilva on 2011-05-31
Hi 

I did a clean install of Ubuntu 11.04 on my desktop which has a Nvidia GForce 7300LE card. Installation was successful, however, the moment I install Nvidia Current driver the system hangs. The only way I was able to get the system working was by doing a fresh install.

Any ideas? Thanks

---

### Post by mikewhatever on 2011-05-31
So, did the system hang right after the driver installation, or was it after the reboot?

---

### Post by gdesilva on 2011-05-31
after reboot....the desktop gets displayed (sort of) but no applications can be activated.

---

### Post by mikewhatever on 2011-06-01
Well, it's a known bug that involves Unity/Compiz and Nvidia. All Geforce 700 series of cards seem to be affected, however, reinstalling is a real overkill. You can just hit ctrl+alt+f1, login and restart xserver with **sudo service gdm restart**. That should bring you back to the login screen, where you can select the Classic session with no effects. That will give you a functional desktop environment, but no effects. Some have reported that installing nvidia-173 instead of nvidia current worked for them. You can do it with the following commands:
```

#remove nvidia-current if needed
sudo apt-get purge nvidia-current

#install nvidia-173
sudo apt-get install nvidia-173

```

---

### Post by gdesilva on 2011-06-01
Thanks Mikewhatever, after the reinstall I avoided installing Nvidia Current and it is currently on Nvidia 173 and have not come across any issues.

Good to know that it is a known bug - I thought I may have done something I should not have!

---

