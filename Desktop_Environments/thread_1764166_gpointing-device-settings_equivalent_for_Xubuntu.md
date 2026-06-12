---
title: "gpointing-device-settings equivalent for Xubuntu?"
date: 2011-05-21
forum: Desktop Environments
---

### Post by Jarm1 on 2011-05-21
Hi everyone,

I'm running Xubuntu 11.04 on my MBP, and it seems to be working quite well except for some major use issues regarding the touchpad; specifically I'd like to get rid of all the frills except for 2 finger scrolling. Eliminating the side scrolling, tap-click, etc. 

It seems like gpointing-device-settings is the ideal app for someone, like me, who is still a bit weak on manually editing configuration files. Unfortunately any time I log out or reboot the machine, it loses all its settings. I assume this has something to do with the fact that it was made for Gnome, which I am obviously not running.

So does anyone know of an alternative to gpointing-device-settings that has similar noob usability but will maintain its settings through a reboot? Or a relatively straight forward config file change that will help me reduce the touchpad "features"?

Thanks in advance!

---

### Post by Copper Bezel on 2011-05-21
I hate to say it, but the simplest way I know to do this under XFCE involves a script. 

There's a command called synclient that can apply these settings, and we can put a script in your startup applications to set each of them individually.

If you run " synclient -l ", you can get the key names and current values for the settings, then make a list of commands like

 synclient VertTwoFingerScroll=1;

for the ones you want to set up and put them in a new executable text file, say, a hidden file called .touchpad-settings.txt in your home folder, that you can add to your Startup Applications. I think xfce-settings-helper might undo some of this, too, so you'll need a sleep command to delay your script launching until after the settings daemon does.

```
#!/bin/bash
sleep 30s;
synclient VertEdgeScroll=0;
synclient HorizEdgeScroll=0;
synclient MaxTapTime=0;
```

---

### Post by Jarm1 on 2011-05-21
Thats actually not a bad solution at all, all the googling I tried never came up with synclient! Not as polished as a GUI perhaps but the commands are straight forward and I'm *relatively* comfortable with making small scripts like that. I'm going to give it a shot and post back!

**Edit:** Worked perfectly, I added a few options to increase the touch sensitivity as well which has, as far as I'm concerned, made the trackpad actually better to use than it was in OS X! I also shortened the sleep time, just as an experiment, which seems to be working just fine as well.

---

### Post by ajgreeny on 2011-05-21
Synclient is a terrific utility, isn't it?

I run Lubuntu on my netbook and it was impossible to use as the touchpad was so sensitive that I was unable to stop the "tap for click" at every touch, and it was very frustrating.  Everything else on the touchpad was OK, and so I made a simple script called notap in /usr/bin
```
#!/bin/bash
synclient MaxTapTime=0
```and set it to run at boot, which in lubuntu means it goes in the list in /etc/xdg/lxsession/Lubuntu/autostart as
```
@nm-applet
@lxpanel --profile Lubuntu
@xscreensaver -no-splash
@gnome-power-manager
@pcmanfm --desktop --profile lubuntu
@/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
[COLOR=Red]@notap[/COLOR]
```

I thought I would add this info here even though it is not for xubuntu, as it is very good for others to know how it can be done in both DEs, xfce and lxde.

---

### Post by Jarm1 on 2011-05-21
It is just what the doctor ordered, I'll have to try playing around with it on my netbook as well. It's trackpad is literally unusable from the tap-click and it seems so sensitive it actually tracks the moisture evaporating behind my finger if my hands are a bit sweaty!

I'm actually downloading lubuntu as we speak, just to try to play around with it little this weekend. It looks pretty interesting, but I'm not sure I'm ready for a distro with such a low user count and more manual configuring, even compared to Xubuntu.

---

### Post by ajgreeny on 2011-05-22
> **Jarm1 said:**
> It is just what the doctor ordered, I'll have to try playing around with it on my netbook as well. It's trackpad is literally unusable from the tap-click and it seems so sensitive it actually tracks the moisture evaporating behind my finger if my hands are a bit sweaty!

I'm actually downloading lubuntu as we speak, just to try to play around with it little this weekend. It looks pretty interesting, but I'm not sure I'm ready for a distro with such a low user count and more manual configuring, even compared to Xubuntu.
Do try it!  I am sure you will love it;  come back to this thread with any more questions you may have about lubuntu, and I will help you out if I can with any configuration needed.

---

