---
title: "Can't Gnome To Start Up After Install And Reboot."
date: 2013-06-16
forum: Desktop Environments
---

### Post by FMFCorpsman on 2013-06-16
I have downloaded Gnome Desktop Environments with Components in the Ubuntu 12.04 Software Manager, on reboot I still get a Unity desktop with no login menu.  I have also tried:

```
sudo apt-get install gnome-shell
```

with the same results. Do I need to do something to initialize it to get it running? I have looked around and can only find answers on how to install it, nothing to address if it doesn't start after reboot.

It also doesn't show up in the Dash Home or Unity menu bar. Not sure if it's supposed to, but thought i'd mention it.

Thank You.

---

### Post by Bashing-om on 2013-06-16
[COLOR=#000000]FMFCorpsman;

At the login screen, username box -> in that username box is a small orange ubuntu icon in the upper right corner, right click and ya should have the option as to which desk top to use.
To the best I recall, I have not used a login manager in a while now.[/COLOR][INDENT=3][COLOR=#000000]
just try'n to help

[/COLOR][/INDENT]

---

### Post by stinkeye on 2013-06-17
Do you have automatic login enabled?
goto system settings > user accounts
and click the unlock button to check.
Disable automatic login , to show the login screen.
or
You can just log out to the greeter and change your session as shown by Bashing-om.
It will continue to boot into the Gnome session until you logout and change it back.

---

### Post by FMFCorpsman on 2013-06-17
I don't know why I didn't think about that! It's always the simplest things. Thank you I'm all set.

---

