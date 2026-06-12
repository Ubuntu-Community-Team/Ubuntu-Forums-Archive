---
title: "notification daemon help"
date: 2009-11-14
forum: Desktop Environments
---

### Post by Amenotep on 2009-11-14
Hello, i just uninstalled notify-osd according to this tutorial in another thread:

> **gradinaruvasile said:**
> U can revert to the older style notification by (commands in terminal):

1. Install the notification-daemon package:

```
sudo apt-get install notification-daemon
```2. Rename the /usr/lib/notify-osd/notify-osd executable

```
sudo mv /usr/lib/notify-osd/notify-osd /usr/lib/notify-osd/notify-osd-original
```3. Create a symbolic link:

```
sudo ln -s /usr/lib/notification-daemon/notification-daemon /usr/lib/notify-osd/notify-osd
```4. Kill the original notification:

```
sudo killall notify-osd
```5. Launch the new notification - press alt+F2, type /usr/lib/notify-osd/notify-osd

6. Test:

```
notify-send test test
```With this older notification type u can use the notification-ptoperties tool to set the location of the notification pop ups

However i came accross 2 problems:

1 - it doesn't appear like it was suposed to (sort of a Comic dialog baloon above the time) it appears has a square above the bottom right corner of the screen.

2 - It doesn't appear when i change songs. However it does appear when i run notify-send test test.

Ideas?

Thanks

---

### Post by Amenotep on 2009-11-14
Problem 2 seems to be solved. Problem 1 is the one still residing.

---

### Post by Amenotep on 2009-11-14
Help anyone?

---

### Post by Amenotep on 2009-11-15
Problem wasn't yet solved... I still get those squares over my panel. Any1?

---

