---
title: "Changed my display manager to light-gtk-greeter. Now I can't login."
date: 2013-08-31
forum: Desktop Environments
---

### Post by marinecomm on 2013-08-31
Last night I edited the default-display-manager file and changed my default display manager from lightdm to lightdm-gtk-greeter. Then I edited the lightdm-gtk-greeter config file and changed the wallpaper. Now, when I reboot the computer I get a whole string of messages where the computer is booting up but it freezes and won't boot into the system. It just hangs there. How do I get back into my system? I'm running Xubuntu 12.04 64-bit.

---

### Post by steeldriver on 2013-08-31
Can you get to a virtual terminal (Ctrl-Alt-F1 etc.)? if so, you should be able to revert the changes from there

I've never messed much with greeters but shouldn't the lightdm-gtk-greeter line have gone in /etc/lightdm/lightdm.conf ('greeter-session=lightdm-gtk-greeter'), rather than in /etc/X11/default-display-manager? That should stay as /usr/sbin/lightdm surely?

---

### Post by marinecomm on 2013-08-31
I don't know how to get to a terminal. Like I said, the system goes through a string of commands while loading up then freezes/hangs up. It doesn't stop and go to a command prompt. i'm not sure how to stop the system from loading and get to where I can enter commands.

---

### Post by steeldriver on 2013-08-31
It's in my previous post - key combination Ctrl-Alt-F1 (or Ctrl-Alt-F2, ... etc. - Ctrl-Alt-F7 usually returns you to the screen it's trying to start the GUI on)

If that doesn't work then you will need to boot into 'recovery mode' from the grub menu

---

### Post by GwL3eNC on 2013-08-31
Hi,

let the system load. If you think the ponit of hang is arrived press, like steeldriver told CTRL+ALT+F1, we must
first know if you can reach a terminal with it.

---

### Post by marinecomm on 2013-08-31
If I can get to a virtual terminal what commands do I issue?

---

### Post by marinecomm on 2013-08-31
Ok, I'll try and see if I can get a virtual terminal and then let you know.

---

### Post by steeldriver on 2013-08-31
I would suggest running a package reconfiguration

```
sudo dpkg-reconfigure lightdm
```

which I *think* will re-insert lightdm as the default display manager  automatically, and possibly restore other default lightdm configs. Then check if the default-display-manager looks OK

```
cat /etc/X11/default-display-manager
```

If it didn't get reset to /usr/sbin/lightdm for some reason, then you can do that manually either by editing using nano

```
sudo nano /etc/X11/default-display-manager
```

(once you've made your changes, press Ctrl-o to save and Ctrl-x to exit); or (maybe easier) just run the following one-liner

```
echo "/usr/sbin/lightdm" | sudo tee /etc/X11/default-display-manager
```

---

### Post by marinecomm on 2013-08-31
When the grub screen came up I decided to try to see if I could get in under recovery mode. I choose to boot in safe graphics mode. However, instead of booting in recovery mode it looped back and took me back to the recovery mode options screen. I opted for a normal boot. This time, when the system hung up I hit Ctrl-Alt-F1 and I was able to get a virtual terminal and sign in. I'll try those commands and see what it comes up with.

---

### Post by steeldriver on 2013-08-31
Thinking about it some more, it may be enough just to start lightdm manually from the Ctrl-Alt-F1 screen

```
sudo service lightdm start
```

(it shouldn't matter in this context that it's not the *default* DM) - if that works, and gets you back to your regular session, then you can revert your changes in whatever favorite GUI editor you used before, if you prefer.

---

### Post by marinecomm on 2013-08-31
Issued the command:

sudo dpkg-reconfigure lightdm

It changed my display manager back to lightdm and allowed me to log in. I'm back in business now. Thank you for all the help.

---

### Post by steeldriver on 2013-08-31
Great. Happy to help.

---

