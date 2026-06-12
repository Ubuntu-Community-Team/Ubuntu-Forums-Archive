---
title: "Stop the Unity launcher flashing"
date: 2012-09-14
forum: Desktop Environments
---

### Post by walkingbeard on 2012-09-14
Hi folks,

When I do certain things, like open a programme in Wine, or log in to a server using Remmina, the Unity launcher pops up in the background and the icon of active programme starts wobbling about. This is profoundly annoying and causes problems with some programmes in Wine. Does anyone know how to stop it? I've set up the launcher to plain old auto-hide instead of the frankly knuckle-headed intelligent hide or whatever.

Does anyone know how to completely disable the launcher pop up and flash behaviour?

Thanks,

Jack

---

### Post by zombifier25 on 2012-09-15
Install ccsm:
```
sudo apt-get install compizconfig-settings-manager
```
Then open it, choose "Ubuntu Unity Plugin", go to "Experimental" tab, and change "Launch Animation" and "Urgent Animation" to what you want (e.g. None)

---

