---
title: "Terminal doesn't launch from Dock or key shortcut"
date: 2020-01-17
forum: Desktop Environments
---

### Post by agnieszka2 on 2020-01-17
I cannot launch terminal from the Dock, favourites or by Ctrl+Alt+T. However, I can click the right mouse button on the desktop and choose Terminal and then it opens. What might be wrong?

---

### Post by Frogs Hair on 2020-01-19
What Ubuntu version and desktop are you using and is the system up to date?

---

### Post by agnieszka2 on 2020-01-20
The system is up to date,I am using Ubuntu 18.04 LTS and Gnome

---

### Post by CelticWarrior on 2020-01-20
Just to make sure, open the terminal as you've been doing and run ```
sudo apt update && sudo apt full-upgrade
```

Then try again to open the terminal the usual way.

Note: You can also run it from the TTY with CTRL+ALT+F3

---

### Post by agnieszka2 on 2020-01-23
It hasn't changed anything.

---

### Post by tea for one on 2020-01-23
> **agnieszka2 said:**
> I cannot launch terminal from the Dock, favourites or by Ctrl+Alt+T. However, I can click the right mouse button on the desktop and choose Terminal and then it opens. What might be wrong?

Ubuntu 18.04 uses Gnome-shell 3.28.4 and a right click on the mouse does not open a terminal.

Right click provides a popup window with 3 options:-

Change Background
Display Settings 
Settings

What is your Gnome-shell version?

Have you added another Desktop, Window Manager, Dock or anything that may cause some conflict?

Did you try **Ctrl Alt F3** as suggested by CelticWarrior?

---

### Post by agnieszka2 on 2020-01-31
My Gnome-shell version is 3.28.2, right click on the mouse on the desktop gives me "Open the Terminal" option. I haven't add anything but I played a bit with different python versions, might that cause any problems? I can open tty with ctrl+alt+F3 but that's not what I need, I just would like to be able to quickly open terminal without going back to the desktop (so either from the dock favourites or by ctrl+alt+T)

---

### Post by agnieszka2 on 2020-01-31
For future reference: solution from this post helped [https://askubuntu.com/questions/1086509/ubuntu-18-terminal-not-opening](https://askubuntu.com/questions/1086509/ubuntu-18-terminal-not-opening)

---

### Post by CelticWarrior on 2020-01-31
If you mentioned you had changed/updated the python version I'm sure someone would have provided a solution in this thread already. Please keep that in mind next time you need help :)

---

