---
title: "Keyboard shortcuts does not work (any of them)"
date: 2014-09-04
forum: Desktop Environments
---

### Post by adamitj on 2014-09-04
Hi! No one of the keyboard shortcuts are working in my Xubuntu 14.04 instalation. I had to install xubuntu-desktop package from a normal Ubuntu 14.04 instalation and cannot proceed with a fresh install because this is the computer I use at work (besides I have root access cannot reinstall due to tons of apps installed).

Is there any error log I can check when the keys are pressed? Or, is there a way to reset those key functions and make them work?

Running Ubuntu 14.04 64-bit with latest updates and using XFCE4 from xubuntu-desktop package.

---

### Post by Toz on 2014-09-04
Is xfsettingsd running?
```
ps -ef | grep xfsettingsd | grep -v grep
```

If not, what happens when you try to start it up?
```
xfsettingsd
```

---

### Post by adamitj on 2014-09-05
Hi Toz. The daemon is already running, as it appears in ps:

```
adamitj@adamitiago:~$ ps -ef | grep xfsettingsd | grep -v grep
adamitj   1940  1636  0 09:30 ?        00:00:00 xfsettingsd --display :0.0 --sm-client-id 229940fc5-d02f-40fb-83d5-0c8ad3625477
```

Trying to start it over, the result is nothing:

```
adamitj@adamitiago:~$ xfsettingsd 
adamitj@adamitiago:~$ 
```

I forgot to mention that yesterday by the end of day all shortcuts began to work after a reboot, but today as I turn on my PC no shortcuts worked again... it's a bit frustrating.

---

### Post by Toz on 2014-09-05
Try running the xfsettingsd daemon in debug mode from a terminal window:
```
XFSETTINGSD_DEBUG=1 xfsettingsd --replace --no-daemon
```
...and see what debug information is displayed. It might yield some clues.

When running in debug mode, remember to press some of the keyboard shortcuts to see what is captured.

Feel free to post back the debug information that is displayed.

---

### Post by adamitj on 2014-09-05
Thanks Toz, but I discovered other issues with Gtk and Qt apps that were already installed and fully functional before I installed xubuntu-desktop package,  and these issues forced me to get on my knees and beg for a brand new installment. Both XFCE and Unity stopped to work correctly, huge Window Decorator (X11) problems were detected in both.
After a day of work I reinstalled Xubuntu 14.04 and put it to work with the other apps, and now it's all running smoothly only with XFCE4.
Thanks for your patience and willing to help.

---

