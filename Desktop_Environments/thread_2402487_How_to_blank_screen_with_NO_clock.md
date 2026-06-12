---
title: "How to blank screen with NO clock ?"
date: 2018-09-30
forum: Desktop Environments
---

### Post by atthecoast on 2018-09-30
I upgraded 16.04 to 18.04.  I have the system set for no lock screen, just blank after 5 minutes. I would like to have the screen refresh with mouse movement allowing resumption of work. It is a nuisance to have to now "swipe up" to switch from the clock display to my previous work. Is there a setting that will have the system blank the screen after 5 or 10 minutes with no password lock and no clock - just blank the screen and then return to the same state when there is mouse movement or a key press? I have done some searching and have not found a method to do this. Seems this would be a common desire when no screen lock is configured.

---

### Post by Dennis N on 2018-10-01
Install and add **xscreensaver** to your startup applications. Select the "blank screen only" choice  when configuring rather than a screensaver. Also turn off the gnome lock screen.

---

### Post by #&amp;thj^% on 2018-10-01
This has worked for me on 16.04 17.10. I confess I have not tried it on 18.04. (I just use the XFCE4 DE now)

dconf-editor
"/org/gnome/desktop/lockdown/disable-lock-screen"
So if not installed open terminal run:
```
sudo apt install dconf-editor
```
Then navigate to the path I showed above.
EDIT: And if that dose not work then disable the inactivity curtain in gnome 3. Launch dconf-editor then drill down org > gnome > desktop> session. Find the key for idle-delay and change it's value to 0 .

Or  you can do it in once step by running the command:
```

gsettings set org.gnome.desktop.session idle-delay 0
```

---

