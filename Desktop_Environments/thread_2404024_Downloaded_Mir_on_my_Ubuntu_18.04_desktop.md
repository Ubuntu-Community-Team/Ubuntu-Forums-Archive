---
title: "Downloaded Mir on my Ubuntu 18.04 desktop"
date: 2018-10-18
forum: Desktop Environments
---

### Post by rbratcher on 2018-10-18
So I am thinking about doing a kiosk project, and downloaded Mir from the Ubuntu Software onto my desktop.  Now I have a screen with nothing on it and can't find out how to get out of it so I can uninstall it.  (Should have done more reading first, I know.) 
I am running 18.04 and when the login screen comes up it switches before I can log in and get a terminal or anything.

---

### Post by ajgreeny on 2018-10-19
Try **Ctrl+Alt+F2** at the login screen and you may get to a command line where you can login using your username and password, the latter of which will not show on screen so type carefully and hit Enter.

If you can manage to login there you can remove mir using ```
sudo apt purge mir
```
You may also need to remove other dependency packages with ```
sudo apt autoremove
``` and you can then try a reboot.
I do not know how or if mir affects the normal working of xorg so if you still can not get to a GUI wait for others who know more than me to respond.

---

### Post by rbratcher on 2018-11-04
I had been busy and it took awhile to get back to this issue.   Turns out mir-kiosk is a snap and the proper command is:  sudo snap remove mir-kiosk

Thanks for the help.   I purchase a Rasberry Pi to run my kiosk, so will be installing Ubuntu core on that, probably will need some help again.

---

