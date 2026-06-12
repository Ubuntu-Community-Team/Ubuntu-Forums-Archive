---
title: "[SOLVED] (May apply to all versions) Compiz Fusion: Desktop Cube"
date: 2009-01-03
forum: Desktop Environments
---

### Post by Aizawa on 2009-01-03
I have desktop cube/desktop rotation/3d windows enabled in compiz fusion. To begin with, my cube is not a cube. It's like a card that I can turn. I do have 4 workspaces enabled, I have tried changing them to 4 and reloading my window manager/restarting compiz.. But it doesn't work. 3D windows doesn't work either. I have my propriety (is that how it's spelled?) installed (Asus (ati) HD4850).. The desktop cube thing worked as late as yesterday in Sabayon (where compiz is pre-configured)..

Help is appriciated. Thanks in advance.

---

### Post by keithld on 2009-01-03
Do you have different programs open in the other workspaces????...

You need them all to have something running in order for there to be a Cube....

---

### Post by Aizawa on 2009-01-03
Huh, didn't need something running in every window in Sabayon..

I'll try what you said 1 sec

---

### Post by Aizawa on 2009-01-03
I don't think that's it. I avant window manager cannnot see more than 2 (???) workspaces either.

---

### Post by dje on 2009-01-03
In a terminal:
```
sudo apt-get install compizconfig-settings-manager
```
Open up System >> Preferences >> CompizConfig Settings Manager (for GNOME) or run the following in the terminal:
```
ccsm
```
Click on General options on the Desktop Size tab adjust the Horizontal Virtual Size slider to 4 or more!

hope that helps
dje

---

### Post by Aizawa on 2009-01-03
Oh, silly me. Thanks a lot!

---

