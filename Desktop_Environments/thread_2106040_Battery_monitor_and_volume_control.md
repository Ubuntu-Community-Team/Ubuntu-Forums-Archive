---
title: "Battery monitor and volume control"
date: 2013-01-17
forum: Desktop Environments
---

### Post by Claudio Bogado Pompa on 2013-01-17
Hello.
How do I put a battery monitor and a volume control on the taskbar of lxde?
Greetings from Paraguay.
Claudio Bogado Pompa.

---

### Post by mysteriousdarren on 2013-01-23
I'd install the xfce package for power manager for Xfce desktop, and added lxde's own volume control. It's something i've always done since the birth of Lubuntu.

---

### Post by Claudio Bogado Pompa on 2013-01-23
Thank you very much.
I did install xfce4-power-manager and appended to /etc/xdg/lxsession/LXDE/autostart.
It works great!

---

### Post by Claudio Bogado Pompa on 2013-05-08
I tryed to do the same thing in another computer but is not working.
I also installed xfce4-power-manager and appended to /etc/xdg/lxsession/LXDE/autostart as @xfce4-power-manager.
What is wrong?
64 bit has another autostart file?
A newer version has another autostart file?

---

### Post by Archit88 on 2013-05-08
> **mysteriousdarren said:**
> I'd install the xfce package for power manager for Xfce desktop, and added lxde's own volume control. It's something i've always done since the birth of Lubuntu.
I am facing very serious issues of crashing Xfce on Ubuntu 13.04 :(

---

### Post by ShadowVegan on 2013-05-26
I'm not sure on power manager, but on volume you have a few options. The reasiest option is to right click anywhere on the menu bar, go to 'add/remove panel items', then go to 'panel applets' then 'add'. From there choose 'volume control'.

I have had some issues with this volume control software--my headset is not always recognized and the maximum volume is very quiet. If you have these issues or for any other reason want the same volume control that is used in Gnome, you can add that to the menu bar instead. This is by far my preference, just a bit more complicated. To do this, open the terminal and type the following commands:
```
sudo apt-get install lxpanel-indicator-applet-plugin

sudo apt-get install indicator-application-gtk2

sudo apt-get install indicator-sound-gtk2
```
After installing all three packages, right click the menu bar, go to 'add/remove panel items', go to 'panel applets', go to 'add', and select 'indicator applets'. After adding indicator applets (while still in the panel preferences box), select 'indicator applets' on the list, then click 'edit'. From there check the box that says 'sound menu'

At this point, you should have the Gnome version of volume control on the menu bar. Much nicer than the default LXDE versions.

If any of this was unclear or you want any part of it in more detail, PM me, I might not check back here but I can give a more detailed walkthrough or screenshots if necessary.

---

