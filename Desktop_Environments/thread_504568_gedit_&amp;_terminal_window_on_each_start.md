---
title: "gedit &amp; terminal window on each start"
date: 2007-07-19
forum: Desktop Environments
---

### Post by NorQue on 2007-07-19
Need help! Some time ago I seem to have shut down Ubuntu with an active gedit window which I started from terminal - and now each and every time I start Ubuntu an empty gedit and a terminal window pops up.

This is really getting annoying, since I have to type my keyring password for WPA protected WLAN on each boot, too. Every time I try to enter my key part of it lands in one of the other windows, which get loaded afterwards.

I'm using Ubuntu 7.04.

---

### Post by taurus on 2007-07-19
Go into System -> Preferences -> Sessions and remove those two apps from the list.  Save the session.  Log out and back in again and see if they still pop up.

---

### Post by NorQue on 2007-07-19
Nope, they're not there, unfortunately.

Hum, me thinks this would've better been posted in the "absolute beginners" section (even though I use Ubuntu for 10 months now ;) ).

---

### Post by taurus on 2007-07-19
Do you see them in ~/.config/autostart?

```
ls -la ~/.config/autostart
```

---

### Post by RockDoctor on 2007-07-19
Whenever I have the problem of unwanted apps starting by default and the above advice fails, I edit the ~/.gnome2/session file directly to remove the unwanted apps. Crude, but effective (at least for me)

---

### Post by NorQue on 2007-07-20
They weren't in ~/.config/autostart, but editing ~/.gnome2/session got rid of these pests! :D Boot process is much faster now, too.

Thank you very much, both of you. :)

---

