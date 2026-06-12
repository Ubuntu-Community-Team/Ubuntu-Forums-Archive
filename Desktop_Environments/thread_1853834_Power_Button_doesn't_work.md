---
title: "Power Button doesn't work?"
date: 2011-10-03
forum: Desktop Environments
---

### Post by ojdon on 2011-10-03
Hi there, I am using Lubuntu 11.04 on my Acer Aspire One A150/ZG5 the only issue I have come across is that the Power Button does not work in LXDE. 

Is there anyway to active LXSession-logout when the power button has been pressed?

---

### Post by kerry_s on 2011-10-03
Go to /usr/share/applications & launch power manager, there you can set the button options. 
It's gnome power manager which doesn't show in the menu but is installed & does work.

---

### Post by ojdon on 2011-10-03
I don't seem t have it installed. Is there a alternative that isn't GNOME based?

---

### Post by cavalier911 on 2011-10-03
gnome-power-preferences is on the Lubuntu live cd and is a default package on a Lubuntu hard drive install. 

Launch from terminal:
```
gnome-power-preferences
```

Add shortcut Menu/Preferences/Power Management:
```
sudo leafpad /usr/share/applications/gnome-power-preferences.desktop
```
Put # in front of this line:
OnlyShowIn=GNOME;XFCE;
Like this:
**#**OnlyShowIn=GNOME;XFCE;
Save/Quit

---

### Post by ojdon on 2011-10-03
It isn't currently installed, I'll install it if I really have to, but I was wondering if there was any way to do it in a GNOME-free environment.

---

### Post by kerry_s on 2011-10-05
> **ojdon said:**
> It isn't currently installed, I'll install it if I really have to, but I was wondering if there was any way to do it in a GNOME-free environment.

You can use xfce4 power manager to do the same thing, I don't have a computer anymore, so I can't give exact instructions.

---

### Post by ojdon on 2011-10-05
**Solution:**

I found a way of getting some form of function for pressing the power button to shutdown in LXDE, without the need of installing packages from other Desktop Environments. simply install acpid. Just open up the terminal and enter in:

> sudo apt-get install acpid

Now when the power button is pressed the computer will shutdown. That'll do for me. Thanks for your suggestions by the way everyone.

---

