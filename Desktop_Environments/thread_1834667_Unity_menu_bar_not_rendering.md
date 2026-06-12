---
title: "Unity menu bar not rendering"
date: 2011-08-27
forum: Desktop Environments
---

### Post by stair314 on 2011-08-27
My menu bar at the top of the screen in Unity under Ubuntu 11.04 doesn't have any text on it. The menu bar is present though. It is drawn as a bar that is purple on the left side, shades to orange and then a different shade of purple on the right. Right now using firefox I can click on this bar and get different dropdown menus to appear, but the menu heading still doesn't appear when I do this.

Also, there isn't a clock anywhere on my screen. I assume there's meant to be one on the menu bar.

Are there any settings or configuration files I should check to tell what's wrong?

Thanks in advance.

---

### Post by Frogs Hair on 2011-08-28
Open the terminal and try the following command .```
unity --reset
```

If that works and you are still missing a clock applet .```
sudo apt-get install indicator-datetime
```

Weather:
```
sudo apt-get install indicator-weather
```

You will need to restart before the applets appear on the panel . No text will appear on the panel except the currently active application and your user name

---

### Post by stair314 on 2011-08-28
Thanks, they are back after rebooting.

---

### Post by Frogs Hair on 2011-08-28
You're Welcome !

---

