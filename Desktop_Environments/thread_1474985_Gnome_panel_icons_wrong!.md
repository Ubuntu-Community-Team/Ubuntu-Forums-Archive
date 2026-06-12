---
title: "Gnome panel icons wrong!"
date: 2010-05-06
forum: Desktop Environments
---

### Post by michel.smo on 2010-05-06
Sorry about my English.

I have a problem, when I turn on my computer with ubuntu 10.04 most of the times I have a problem with the gnome panel icons. They look like this picture:

[[IMG]http://img693.imageshack.us/img693/2051/pantallazolq.th.png[/IMG]](http://img693.imageshack.us/i/pantallazolq.png/)

Other times I have more icons wrong, but in this case the username icon is cut and the turn off icon does not appear.

The solution that I have found is to restart the graphical environment (ctrl+alt+del)

Anyone has the same problem or knows how to fix it?

---

### Post by bloodorange on 2010-05-06
I get this same problem.  Sometimes the panel icons seem to be corrupted.  I don't know how to fix it, though!

---

### Post by finlost on 2010-05-06
Try resetting the notification panel.  Not sure if that will work, but it seems a file(s) is corrupted.

---

### Post by michel.smo on 2010-05-07
> **finlost said:**
> Try resetting the notification panel.  Not sure if that will work, but it seems a file(s) is corrupted.

How do you do that?

---

### Post by Budoc on 2010-05-10
I have similar issues to the initial poster. 

I have tried resetting my panels using the following commands:

```
mkdir ~/.oldpanel
mv ~/.gconf/apps/panel ~/.oldpanel
gconftool-2 --shutdown
pkill gnome-panel
```

After this, I still get the same problem. I can only solve it by running the following command and then waiting for the panels to return:

```
killall gnome-panel
```

At the moment, I suspect that it is the weather and temperature function of the time that is doing it. I've not yet observed this if I do not display the weather and the temperature by the clock, but I am still testing this. I also observe this problem if I use the weather applet elsewhere on the panel.

Any ideas what is going on?

Edit: This appears to be a known bug in gnome according to this report: [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/439448]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/439448") I wonder why this hasn't affected me before Lucid?

---

### Post by michel.smo on 2010-05-11
> **Budoc said:**
> 
At the moment, I suspect that it is the weather and temperature function of the time that is doing it. I've not yet observed this if I do not display the weather and the temperature by the clock, but I am still testing this. I also observe this problem if I use the weather applet elsewhere on the panel.


I use the weather and temperature function too...

---

### Post by jasontan6 on 2010-05-12
Have the same problem too - weather and temperature were turned on.
Turned them off and the problem doesn't occur.
Turn it back on and the icons are garbled again.

Going to see if it's already reported as a bug now.

EDIT: Weather and temperature are off now, but there is a gap appearing randomly between the tray app icons and clock. (dagh!)

---

### Post by fromans on 2010-05-14
> **Budoc said:**
> I have similar issues to the initial poster. 

I have tried resetting my panels using the following commands:

```
mkdir ~/.oldpanel
mv ~/.gconf/apps/panel ~/.oldpanel
gconftool-2 --shutdown
pkill gnome-panel
```

After this, I still get the same problem. I can only solve it by running the following command and then waiting for the panels to return:

```
killall gnome-panel
```

At the moment, I suspect that it is the weather and temperature function of the time that is doing it. I've not yet observed this if I do not display the weather and the temperature by the clock, but I am still testing this. I also observe this problem if I use the weather applet elsewhere on the panel.

Any ideas what is going on?

Edit: This appears to be a known bug in gnome according to this report: [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/439448]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/439448") I wonder why this hasn't affected me before Lucid?

Thanks for the tip! I've had the same problem and have just been recreating my panel when it happens, but the ```
killall gnome-panel
``` fixes it immediately. Bravo!

---

### Post by mydoom5 on 2010-06-10
I still have a problem. Aside from the garbled icons, which can be fixed with the command mentioned above (thanks :) ), I noticed that the audio volume icon has disappeared! I tried to remove the notification area icons and add them once again from the panel menu, but it didn't solve the problem. Can you help please?
Edit: I almost forgot, I'm having yet another problem. It seems that the Empathy icon which is integrated with Lucid Linx also has disappeared.
Thanks.

---

### Post by mydoom5 on 2010-06-23
Bump

---

### Post by 45acp on 2010-08-13
Same problem here.

---

### Post by Spunner on 2010-08-26
This problem has been bugging me ever since I installed lucid...

Would like to know if there is a resolution...

---

### Post by soulShredder on 2010-08-27
Same here. On mine it also seems to randomly position all the icons too - they're in different positions each time you boot. I think that might be a separate issue though, as the killall command doesn't fix it - when the panel re-loads everything is in yet another different position! This only happens on lucid, I ran karmic for about 3 months and never had a problem like this.

---

### Post by bloodorange on 2010-11-26
I don't know whether how long this will last, but I changed my theme to Clearlooks and I don't seem to be getting the panel corruption any more.  Could it possibly be Ambiance and Radiance causing this problem?

---

### Post by battlemage04 on 2010-12-09
> **soulShredder said:**
> Same here. On mine it also seems to randomly position all the icons too - they're in different positions each time you boot. I think that might be a separate issue though, as the killall command doesn't fix it - when the panel re-loads everything is in yet another different position! This only happens on lucid, I ran karmic for about 3 months and never had a problem like this.

same problem for me, im running maverick, the position of the icons only recently "moved" not immediately but soon after a recent series of updates...  and while the location of my icons are pretty consistent, i do have to refresh the panel every time i reboot.

---

### Post by bvc on 2010-12-09
Ambiance and Radiance use the same engine. So that could be an issue. They both also have special settings for the panel, so what I would do is go into the gtkrc and disable the special panel settings to attempt to narrow down the problem. At the botton of their gtkrc you'll find ```
include "apps/gnome-panel.rc"
``` just add an # to it so it looks like this ```
#include "apps/gnome-panel.rc"
``` save the gtkrc and reset the theme to see if this helps.

---

### Post by Jotomicron on 2010-12-28
Another way to temporarily solve the problem, without killing the panel, is to right-click, select properties and "Show hide buttons". The panel needs to rearrange itself to accommodate the buttons and redraws correctly. Now simply remove the hidden buttons, if you want.

I do this, specially because I don't really like to kill applications, but I have to do it after every reboot...

---

