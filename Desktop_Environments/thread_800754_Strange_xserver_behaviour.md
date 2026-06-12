---
title: "Strange xserver behaviour"
date: 2008-05-20
forum: Desktop Environments
---

### Post by krzywarp on 2008-05-20
Greetings

I am a Kubuntu 8.04 user. I have a problem with xserver. When I installed Kubuntu on my laptop (LCD screen 1280x800@60) with Nvidia GeForce4 Go 420, installer set my display as Plug'n'Play monitor and everything was fine. It had correct resolution. But when I attempted to play StarCraft via Wine in full-screen mode, after restarting the computer my resolution was set to VGA - 640x480 and I could not change it. I had to change the screen to Laptop LCD and now I have proper desktop resolution. But there is a problem with logging screen resolution. When I log out, the login screen sometimes appears with 640x480 resolution and sometimes it does not - I have black screen with nothing on it. Therefore I set up automatic login. How to make the login screen work?

I would be grateful for any help. If needed, I can post the xorg.conf contents.

---

### Post by Patb on 2008-05-20
Krzywarp, try reconfiguring your display.  First back up your present settings.  In a terminal type:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak1
```
Then try reconfigure your X settings
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
If that doesn't give you a workable screen resolution, try it without the -phigh option so that you can configure low priority questions:
```
sudo dpkg-reconfigure xserver-xorg
```
Use the settings you used at installation time.  

Cheers, Pat

---

### Post by krzywarp on 2008-05-21
It helped :). Now everything works perfectly :). Thank you very very very much indeed :).

---

