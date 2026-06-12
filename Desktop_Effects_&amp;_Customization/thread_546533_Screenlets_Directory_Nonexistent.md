---
title: "Screenlets Directory Nonexistent"
date: 2007-09-09
forum: Desktop Effects &amp; Customization
---

### Post by arbulus on 2007-09-09
I've installed Screenlets and I go to the terminal and enter "screenlets-manager" which brings up the screenlets manager.  But when I try to launch a screenlet, this is the error that I get:

```
dave@dave:~$ screenlets-manager
DAEMON FOUND!
Clock
Launching Screenlet from: /usr/local/share/screenlets/Clock/ClockScreenlet.py
Logging output goes to: $HOME/.config/Screenlets/ClockScreenlet.log
sh: cannot create /home/dave/.config/Screenlets/ClockScreenlet.log: Directory nonexistent
```

And nothing happens.

Anyone have any advice on what to do to rectify this?

Thanks in advance!

---

### Post by smartboyathome on 2007-09-09
Copy the folder "screenlets" from /usr/local/share to ~/.config
also, if you are using compiz fusion, try activating the widget plugin (in the same catagory as the destop cube plugin) and set all your screenlets as widgets. Now you can view them without all the hassle by just pressing F9.

---

### Post by arbulus on 2007-09-09
> **smartboyathome said:**
> Copy the folder "screenlets" from /usr/local/share to ~/.config
also, if you are using compiz fusion, try activating the widget plugin (in the same catagory as the destop cube plugin) and set all your screenlets as widgets. Now you can view them without all the hassle by just pressing F9.


Copying the folder did the trick.

Thanks for your help!

---

