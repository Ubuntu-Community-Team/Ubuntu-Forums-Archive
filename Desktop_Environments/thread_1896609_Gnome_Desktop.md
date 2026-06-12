---
title: "Gnome Desktop"
date: 2011-12-17
forum: Desktop Environments
---

### Post by TheRacerX on 2011-12-17
is there a way to basically restore the entire Desktop Environment  to its defaults without actually reinstalling the operating system or using a backup since i forgot to make one?

---

### Post by BC59 on 2011-12-17
If you are running Ubuntu 11.04 or 11.10 execute this:

```
unity --reset
```

---

### Post by TheRacerX on 2011-12-17
no im running Maverick Meerkat, 11.04 and 11.10 wont run on my computer, not enough power

---

### Post by BC59 on 2011-12-17
Then run:

```
killall gnome-panel
``` if it is not working

```
gconftool-2 --recursive-unset /apps/panel
killall gnome-panel
``` and if not

```
gconftool-2 --recursive-unset /apps/compiz
compiz --replace
```

---

### Post by TheRacerX on 2011-12-17
the problem seems to be that i cant right click on the background to add folders or change my back ground and my panels are stuck in 2D mode instead of having the shadows under the windows and panels

and i cant add icons to the desktop anymore

---

### Post by BC59 on 2011-12-17
Try this:

press Ctrl + Alt + F1 from your desktop. You will directed to a black screeen. Put your logon name enter then your password.

Next type this:
```
rm -r .gnome2 .gconf .gconfd .metacity
```
and this to rebbot
```
sudo reboot
```

---

### Post by TheRacerX on 2011-12-17
thank you that worked everything seems to be back to normal, i was worried i was going to have to reinstall my OS again for the 3rd time

---

