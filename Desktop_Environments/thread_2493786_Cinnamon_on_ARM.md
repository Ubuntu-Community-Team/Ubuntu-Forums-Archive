---
title: "Cinnamon on ARM"
date: 2023-12-25
forum: Desktop Environments
---

### Post by msknight on 2023-12-25
I'm running Ubuntu on Raspberry Pi 5 and I prefer the cinnamon desktop.

I did an apt install cinnamon and all the packages installed well, but on logging out and selecting cinnamon, it failed to launch the desktop and returned me straight to the logon.

On reboot, it started to boot and I was getting the usual messages, but then it failed to go to the logon screen and flickered the boot text updates very quickly on the screen. If I hit the power button, I got all the appropriate messages and it shut down.

I'm guessing at this point that cinnamon isn't properly supported on Arm and I should just find some, "tuning," instructions to make it look more like cinnamon, without actually installing cinnamon.

But I thought I'd check first in case I'm missing something.

---

### Post by ActionParsnip on 2023-12-27
Try:
```

sudo apt install cinnamon-desktop-environment

```
Then reboot

---

### Post by msknight on 2023-12-27
Same thing. Also, didn't want to know either with Cinnamon, or Cinnamon software rendering. Both bounced immediately back to the logon screen. Fortunately, I logged back on with the Ubuntu desktop before rebooting, so at least it reboots OK... but I believe that if I hadn't done that and left Cinnamon as the last attempted desktop, it would probably have done the same boot hang again.

---

### Post by ActionParsnip on 2023-12-27
If you install lxde with
```

sudo apt install lxde

```
Then log in to the LXDE session, is that OK?

---

### Post by msknight on 2023-12-27
Nope, that fails also. Gnome classic works, I can log in with that, but LXDE is also returning straight to logon.

---

### Post by #&amp;thj^% on 2023-12-27
Have you ever run this:
```
sudo update-alternatives --config x-session-manager
```
You pick the DE from that command, and reboot after.
And then try again logging in to your wanted DE.

---

### Post by msknight on 2023-12-28
Same thing. Can't get past logon screen.

Also tried to create a new user so there were no other config files around... and again, same thing.

---

### Post by ActionParsnip on 2023-12-28
Well at least we know it isn't the Cinnamon DE specifically. Are you selecting Wayland or Xorg, try both

---

### Post by #&amp;thj^% on 2023-12-28
If you're interested in trying different desktop environments, starting with Raspbian Lite is probably a better approach.

I'm still on a Pi 4 and have no issues. Note I have not used  Cinnamon or Gnome on it. (Just not my cup of tea)
Mate, XFCE4,  LXDE all work on mine.
Good Luck though.

---

### Post by msknight on 2023-12-28
Thanks for the help. I think I'll stick with the Ubuntu desktop that I've "cinnamoned" a bit. Things will catch up in due course.

---

