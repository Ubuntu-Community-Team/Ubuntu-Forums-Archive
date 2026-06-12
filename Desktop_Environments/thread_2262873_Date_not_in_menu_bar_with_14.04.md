---
title: "Date not in menu bar with 14.04"
date: 2015-01-27
forum: Desktop Environments
---

### Post by Camilia on 2015-01-27
Recently upgraded from ubuntu 12.04 to 14.04. Afterwards the Date and time were not in the menu bar. Checking if this problem was already posted and found other's had solved the problem with these commands:
sudo apt-get install indicator-datetime 
sudo apt-get install ntp
sudo dpkg -s gnome-session-flashback
sudo apt-get install indicator-datetime 
sudo apt-get install --reinstall indicator-datetime
setsid unity = the time in the menu bar.

Any other suggestions?

---

### Post by CantankRus on 2015-01-27
Try the command...
```
dconf write /com/canonical/indicator/datetime/show-clock true
```

---

### Post by grahammechanical on 2015-01-27
Try System Settings>Time and Date>Clock tab and tick Show a clock in the menu bar. There are also boxes where we can tick to show Weekday; Date and month; Year; 12-hour time or 24-hour time; and Seconds.

Regards.

---

### Post by Camilia on 2015-01-27
> **CantankRus said:**
> Try the command...
```
dconf write /com/canonical/indicator/datetime/show-clock true
```
pasted that and nothing happened 
Pasted sudo dconf write /com/canonical/indicator/datetime/show-clock true and nothing happened.

Followed instructions[ here ]("http://askubuntu.com/questions/45970/missing-date-time-applet-from-top-unity-panel") and now can see date and time.

---

