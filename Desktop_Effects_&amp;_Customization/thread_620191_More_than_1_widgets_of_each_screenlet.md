---
title: "More than 1 widgets of each screenlet?"
date: 2007-11-22
forum: Desktop Effects &amp; Customization
---

### Post by levis on 2007-11-22
I don't remember what i did but now 1 screenlet has more than 1 widgets on the screen, if i close all will be closed and all of it will automatically start if i enable this screenlet. Example now i have 4 clocks and 4 CPU meter  on the screen but i only want 1 widget of each screenlet. How can i delete 3 clocks other? Thanks!
Below is my desktop:
[IMG]http://img222.imageshack.us/img222/6041/screenshotfz0.png[/IMG]

---

### Post by martynp on 2007-11-22
Go to ~/.config/Screenlets/(screenlet name)/default and delete all the .ini files bar 1

That will fix it!

---

### Post by Forlong on 2007-11-22
Right-click on the screenlet you want to get rid of and choose **Delete Screenlet** (*not* Quit)

---

### Post by levis on 2007-11-22
> **Forlong said:**
> Right-click on the screenlet you want to get rid of and choose **Delete Screenlet** (*not* Quit)

Thank you, i've got it :guitar:

---

### Post by Forlong on 2007-11-23
Great. :)

Just one thing: please don't post huge screenshots directly in the forum, next time please.
Imageshack has a nice thumbnail feature, you can use. Thanks.

---

### Post by gusanto on 2008-05-31
> **Forlong said:**
> Right-click on the screenlet you want to get rid of and choose **Delete Screenlet** (*not* Quit)

I right click then choose delete to delete radio widget but it keeps appearing any time I login.  How to actually to delete it. Thanks.

---

### Post by Joeb454 on 2008-05-31
I think you'd be better creating a newer thread - screenlets have come a long way (even since November)

---

### Post by bapoumba on 2008-06-01
This thread is in the archive of the forums (still open for posting in support threads). Please give me a link to a new thread is the regular support area, and I'll redirect this one to it, thanks.

---

### Post by Forlong on 2008-06-01
> **gusanto said:**
> I right click then choose delete to delete radio widget but it keeps appearing any time I login.  How to actually to delete it. Thanks.
What version of Ubuntu are you using and how did you install Screenlets?

---

### Post by gusanto on 2008-06-03
> **Forlong said:**
> What version of Ubuntu are you using and how did you install Screenlets?

I run Ubuntu 8.04 and installed Screenlets from synaptic.

---

### Post by Forlong on 2008-06-03
What's the output of
```
ls $HOME/.config/autostart
```

---

### Post by gusanto on 2008-06-03
> **Forlong said:**
> What's the output of
```
ls $HOME/.config/autostart
```

ls /home/gusanto/.config/autostart/
> ACPIBatteryScreenlet.desktop    RadioScreenlet.desktop
avant-window-navigator.desktop  Screenlets Daemon.desktop
ClearWeatherScreenlet.desktop   SensorsScreenlet.desktop
ClockScreenlet.desktop          SysmonitorScreenlet.desktop
DiskusageScreenlet.desktop      TodayCalendarScreenlet.desktop
gdesklet.desktop                VolumeControlScreenlet.desktop
GmailScreenlet.desktop          WirelessScreenlet.desktop
pidgin.desktop


---

### Post by Forlong on 2008-06-04
You still have several Screenlets in your autostart.

If you want to remove them all (and thus, stop them from running on boot), run this in a terminal:
```
rm $HOME/.config/autostart/*Screenlet.desktop
```

---

### Post by gusanto on 2008-07-18
> **Forlong said:**
> You still have several Screenlets in your autostart.

If you want to remove them all (and thus, stop them from running on boot), run this in a terminal:
```
rm $HOME/.config/autostart/*Screenlet.desktop
```

Hello there, I'm back again.
I used to have several screenlets on my desktop that are automaticall loaded when booting. Recently, they don't appear anymore. I add the same screenlet again but I don't think it's the correct procedure. 
Below is output from 
```
ls ~/.config/autostart/ 
```
> ACPIBatteryScreenlet.desktop
awn.desktop
ChameleonClockScreenlet.desktop
ClearWeatherScreenlet.desktop
ClockScreenlet.desktop
GmailScreenlet.desktop
pidgin.desktop
Screenlets Daemon.desktop
SensorsScreenlet.desktop
TodayCalendarScreenlet.desktop
tomboy.desktop
WirelessScreenlet.desktop
Please teach me what should I do.
Thanks.

---

