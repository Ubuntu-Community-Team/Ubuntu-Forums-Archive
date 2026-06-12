---
title: "Taskbar is gone + Icons don't work"
date: 2013-02-16
forum: Desktop Environments
---

### Post by Gammop on 2013-02-16
I just very recently started using Linux, and I've somehow made it unusable, and I don't really want to reinstall the whole thing.

I wanted my GeForce 560 Ti graphics card to work, so I downloaded the drivers. I tried to go to additional drivers, and set a new driver that closest resembled the driver name that I had downloaded (like 4 different ones were in there for what appeared to be the same thing). Steam wouldn't re-open, so I reset the computer through the interface, and then when I get back, the screen resolution is really weird (slightly zoomed in, big black bars on the tops and sides of the screen) and the both the taskbars on the top and left side of the screen are gone.

Is there some sort of Alt+Ctrl command to get into the system settings panel, or is there something obvious that I've done to screw myself?

---

### Post by ThunderMoon99 on 2013-02-16
Haha this happened to me a while back as far as I know the only way to fix it is to just re-install everything and back all your important stuff onto a usb if possible. Be careful what drivers you download next time. You might want to try to restart Unity but I don't know what you press but don't try until you have everything backed up first

---

### Post by ThunderMoon99 on 2013-02-16
You can restart Unity by opening the terminal by pressing Ctrl+Alt+T then typing in the terminal
Stop
```
sudo stop lightdm
```
Start
```
sudo start lightdm
```
restart
```
sudo restart lightdm
```
and Reset
```
unity --reset
```
Let me know the results. Unfortunately at the time this happened to me I didn't know this so if this doesn't work you'll need to re-install Ubuntu. Goodluck :)

---

### Post by Gammop on 2013-02-16
I was afraid of that. Okay, I'll try to restart unity, and if that doesn't work I'll just reinstall everything. 

Thanks guys :D

---

### Post by JayKay3OOO on 2013-02-16
I found this on the internet that may un-fubar your graphics drivers as it sounds like a graphics problem when trying to install the driver for your 560 TI

[http://podzemski.com/2012/10/20/ubuntu-12-10-nvidia-drivers/](http://podzemski.com/2012/10/20/ubuntu-12-10-nvidia-drivers/)

More detail in the source:

[http://askubuntu.com/questions/202677/nvidia-driver-doesnt-work-in-12-10](http://askubuntu.com/questions/202677/nvidia-driver-doesnt-work-in-12-10)

---

### Post by Bashing-om on 2013-02-16
+1 on JayKay3OOO's advise. Concur on the Ask ubuntu link!

---

### Post by stinkeye on 2013-02-16
+2 solved my problem on 12.10 using the same gfx card.
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12338523&postcount=2") for the three commands to run.

Ps now using the nouveau drivers as they work fine, though I don't play games.

---

