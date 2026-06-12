---
title: "Unity is 100% unresponsive"
date: 2011-01-29
forum: Desktop Environments
---

### Post by Apv507 on 2011-01-29
I installed the Unity Desktop Env. to play around with it on my wubi installation of Ubuntu 10.10. I have the log in screen disabled as well as the grub menu so it launches right into Ubuntu. I logged out and logged back in under Unity and could move the mouse but nothing would happen. I have gnome-panels disabled as well so alt f2 wont work even in my gnome DE. By disabling the log in screen and the grub menu have I painted myself into a corner so to speak and made this installation completely unrecoverable?

---

### Post by bcbc on 2011-01-29
If you can right click on the desktop, then  create a launcher with command: [B]
/usr/bin/gnome-session-save --kill
[/B]
Then run it to log out

---

### Post by Apv507 on 2011-01-29
Left-clicking is a luxury I don't have. I can see the Unity panel as well as my AWN and everything else. I have gnome-panel disabled and the desktop. I can see everything but can click nothing. I've trapped myself haven't I? It's like some computer nerd twilight zone episode, I'm stuck in a beautifully customized OS but I can't do a thing.

---

### Post by mikewhatever on 2011-01-29
How about alt+ctrl+f1? That should drop you console, and restarting xserver might bring you back to the login screen. The commands to restart xserver are as follows:
```
sudo service gdm stop
sudo service gdm start
```

Don't forget to hit alt+ctrl+f7 after that.

---

### Post by bcbc on 2011-01-29
```
sudo nano /etc/gdm/custom.conf
```
Change AutomaticLoginEnable from true to false
```
AutomaticLoginEnable=false
```

---

### Post by Apv507 on 2011-01-29
Thanks to you both! Mike dropping to the command line worked, so I guess it was only 95% unresponsive. Sadly once I restarted gdm I was stuck with the same problem. I was logging back onto the forum to ask how to toggle automatic log in from the command and BCBC had already answered that. Thanks again! I'm back in and fully functional.

---

