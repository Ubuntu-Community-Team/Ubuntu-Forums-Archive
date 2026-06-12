---
title: "Change Greeter / Login Box Color 10.10"
date: 2011-04-10
forum: Desktop Environments
---

### Post by Frogs Hair on 2011-04-10
I have tested this on Ubuntu 10.10 64 bit many times . Use at your own risk.

1. Enter command  in terminal.
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow

```

2. Close terminal and reboot .


3. Make changes to greeter box using appearance preferences by selecting a theme that supports color change . Use Customize > Controls > Colors to change colors of the box and text.
   
    
4. Close Appearance Preferences and log in . 

5. Enter command in terminal.
```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop

```

6. Close terminal and reboot .

---

### Post by Copper Bezel on 2011-04-10
Thanks for doing this - this seems to be the most sensible solution, much better than using the GDM2 Settings hack, and I'll link to it the next time the question comes up. I'll also add that the user should *not* change the icon theme in the login screen from LoginIcons, or Ubuntu-Tweak won't always be able to find and change the system logo, as Krytarik and I sussed out in another thread on the same subject. (The result is that, from default settings at least, the Computer icon from whatever theme is selected is used, and this can only be changed by dinking around in the gdm user profile folder.)

---

### Post by Frogs Hair on 2011-04-10
> **Copper Bezel said:**
> Thanks for doing this - this seems to be the most sensible solution, much better than using the GDM2 Settings hack, and I'll link to it the next time the question comes up. I'll also add that the user should *not* change the icon theme in the login screen from LoginIcons, or Ubuntu-Tweak won't always be able to find and change the system logo, as Krytarik and I sussed out in another thread on the same subject. (The result is that, from default settings at least, the Computer icon from whatever theme is selected is used, and this can only be changed by dinking around in the gdm user profile folder.)

You're welcome , The original instruction used logout in place of reboot after entering a similar link command , but this was unreliable for me , I found myself looking at a black screen . I then used reboot instead of logout and it worked every time .

---

### Post by Frogs Hair on 2011-04-28
Just tested this on 11.04 and it works fine .

---

### Post by Rasa1111 on 2011-07-13
Just did this on my 11.04 setup and it worked perfectly!
Thanks a lot Frogs Hair!  :D <3

---

