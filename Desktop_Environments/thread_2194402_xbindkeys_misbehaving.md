---
title: "xbindkeys misbehaving"
date: 2013-12-18
forum: Desktop Environments
---

### Post by pbean on 2013-12-18
I am using "xbindkeys" to set up my keyboard's media keys to work with Spotify (just some dbus commands). However, when my PC starts, xbindkeys is started automatically, but the media keys do not actually work at all (nor any other shortcuts I have configured). If I kill it, and launch xbindkeys again, everything does work properly.

My xbindkeys configuration is in "/home/pbean/.xbindkeysrc". The full command which is launched on log-in is "xbindkeys -f /home/pbean/.xbindkeysrc", which I think should be correct, yet it doesn't work. If I kill that instance, and run it again using just "xbindkeys" (no arguments), it works just fine.

I also cannot really find out how xbindkeys is started, actually. I didn't add it to any script myself, and it's not in my session configuration. I don't know what starts xbindkeys, or how. If I could somehow change it, I would try to have it launch just "xbindkeys" without arguments.

Any ideas?

PS. I am running Xubuntu 13.10.

---

### Post by ajgreeny on 2013-12-18
As you have already found, but I suspect no realised the significance of, you simply need to just start xbindkeys with that command in your settings autostart dialogue; yopu don't put the configuration file pathway in the autostart list as it just that, a configuration file not an executable shell script.

For you info, here is an .xbindkeysrc file I used to need to enable side buttons on my mouse to be set to forward and backward in nautilus, but no longer needed so I only have this as a backup now.
```
# Entries to enable forward & backwards navigation in nautilus with mouse buttons.

#sudo apt-get install xvkbd xbindkeys x11-utils.
#Ubuntu versions before 9.04 (Jaunty Jackalope), the x11-utils package needs to be swapped for xev.

#Terminal command:-
#xev | grep ', button'         Press mouse buttons and note output, eg

#state 0x10, button 8, same_screen YES
#state 0x10, button 8, same_screen YES
#state 0x10, button 9, same_screen YES
#state 0x10, button 9, same_screen YES

#Back in terminal, we need to create a new file for configuration of xbindkeys.

#gedit ~/.xbindkeysrc

#This will load up Gedit to add content to the new file. This file needs to contain the following:

#"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
#  m:0x0 + b:8
#"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
#  m:0x0 + b:9

#Notice the “b:8&#8243; and “b:9&#8243; portions of the text. This is where I configure my mouse buttons. So, if your mouse buttons are 6 and 7, then you need to change “b:8&#8243; and “b:9&#8243; to “b:6&#8243; and “b:7&#8243;, respectively.

#Set **xbindkeys** to autostart at session start in System->Preferences->Startup Applications.  (Settings-Manager ->Session & Startup ->Autostart in Xubuntu)

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9

```

Note all the commented out lines, starting with #, are just as reminders to myself how to do this; the important lines are the bottom four.

---

### Post by pbean on 2013-12-18
Hi ajgreeny, thanks for your inup.

I suspect you might have misunderstood the problem I have. xbindkeys is already launched on log-in somehow, using the command-line argument "-f /home/pbean/.xbindkeysrc" (so the full command being run is "xbindkeys -f /home/pbean/.xbindkeysrc"). So xbindkeys is running, but not actually working.

If I then just run "xbindkeys" (or add that to my session start-up for that matter), it will do nothing, because another instance of xbindkeys is already running. I first have to kill the already running, automatically launched xbindkeys before I can start it again to get my keys working. So the problem has several aspects:

- xbindkeys is launched automatically and I don't know how; and
- it doesn't work until I kill it and restart it

---

### Post by ajgreeny on 2013-12-19
If you simply start xbinkeys with that simple one word command in your startup applications list it will find the .xbindkeysrc file and use it by default, so that is why I said you should try replacing your current command with **xbindkeys** and it should do what you want.

However you say that is not happening, so you need to figure out what is starting xbindkeys when you start a new session or boot the computer.  Have a look in:-

[LIST=1]
[*]/etc/xdg/autostart
[*]/etc/xdg/xdg-xubuntu/autostart
[*]/usr/share/autostart
[/LIST]
 to see if it appears in any of those.  If not I am a bit baffled, unless you have your sessions saved automatically at shutdown.

---

### Post by pbean on 2014-01-13
I checked all 3 of those locations, but "xbindkeys" appears in none of them ("/usr/share/autostart" doesn't even exist on my system). I also double-checked my session settings, and there is no "xbindkeys" in the session settings, nor is "automatically save session on logout" checked. :(

---

### Post by brainwash on 2014-01-13
Should be /etc/X11/Xsession.d/98xbindkeys. According to this file you can create ~/.xbindkeys.noauto to prevent this autostart behavior.

---

### Post by pbean on 2014-01-20
> **brainwash said:**
> Should be /etc/X11/Xsession.d/98xbindkeys. According to this file you can create ~/.xbindkeys.noauto to prevent this autostart behavior.

You are right, that file starts it.

Doesn't really explain why it doesn't work correctly when it's automatically started, but does work properly when I start it manually, though. :(

---

