---
title: "Issues with LXDE"
date: 2017-09-05
forum: Desktop Environments
---

### Post by drakeskywing on 2017-09-05
So I have recently run into an issue with loading into LXDE on Lubuntu 16.04, I keep getting the following error when I attempt to login:
```

unable to launch "/usr/bin/lxsession -s Lubuntu -e LXDE" X session --- "/usr/bin/lxsession -s Lubuntu -e LXDE" not found; falling back to default session.
```

This was after I reset my machine due to issues with my wireless card (I fiddled with the config for some stuff to do with airmon and stuff and from time to time it sticks in Device not ready, and I can't be bothered debugging it, so I do a controlled reboot to fix it), and when logging in after the reboot (which was done through the shutdown interface), it started giving me this error, and not loading my desktop.

Now I am aware this is similar to [https://ubuntuforums.org/showthread.php?t=2267128](https://ubuntuforums.org/showthread.php?t=2267128) and reviewed the actions carried out.

I have checked my /usr/share/xsessions/ folder, and it matches the same file found (Lubuntu.desktop), as found in the previous thread, minus the comments.

I have done ```
sudo apt-get install --reinstall lxsession
``` to no avail.

I find I am able to login using openbox (which subsequent logins to LXDE seem to roll back to openbox, when before they just stayed on the background without anything else), and once on the desktop, if I open a terminal, and try to use lxsession -s Lubuntu -e LXDE it loads up (admittedly I know this is not the best case, as it overlays over the other Desktop Environment), but it says to me something is going on with the environment variable on login, but I have no clue how to debug this.

Any assistance would be greatly appreciated :)

---

