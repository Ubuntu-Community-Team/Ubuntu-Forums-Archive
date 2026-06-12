---
title: "How to log off through virtual terminal"
date: 2010-10-30
forum: Desktop Environments
---

### Post by adit on 2010-10-30
The gnome session crashed.  The window manager, mouse are not responding.  However I can get the virtual terminal by pressing Ctrl+Alt+F1.  I want to log off.  What command should I issue?

---

### Post by FlameReaper on 2010-10-30
```
sudo service gdm stop
```

That should do it.

---

### Post by KdotJ on 2010-10-30
or if you need to reboot the machine, 

```
sudo reboot
```

if you need to shut the machine down:

```
sudo shutdown -h now
```

---

### Post by adit on 2010-10-30
```
sudo service gdm stop
```
I issued the above command from tty1.  Then I pressed Ctrl+Alt+F8.  I expect some graphical login screen.  But there is only a blank screen with a cursor blinking at the top left corner (not able to get even a terminal).  Whatever key I type there is no response.
I know simply rebooting the system will solve the problem.  But I want to know what exactly is happening here?  What is expected when I press Ctrl+Alt+F8.

---

### Post by FlameReaper on 2010-10-30
> **adit said:**
> ```
sudo service gdm stop
```
I issued the above command from tty1.  Then I pressed Ctrl+Alt+F8.  I expect some graphical login screen.  But there is only a blank screen with a cursor blinking at the top left corner (not able to get even a terminal).  Whatever key I type there is no response.
I know simply rebooting the system will solve the problem.  But I want to know what exactly is happening here?  What is expected when I press Ctrl+Alt+F8.

Try to restart the gnome session via issuing the command

```
sudo service gdm start
```

in tty1 instead.

Your "Ctrl+Alt+F8" does not exist for me, so can't really tell what's there when you did that..

---

