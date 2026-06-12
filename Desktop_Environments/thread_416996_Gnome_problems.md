---
title: "Gnome problems"
date: 2007-04-21
forum: Desktop Environments
---

### Post by daverave999 on 2007-04-21
I assume it  is a Gnome problem anyway.

From a base install of Feisty, I can install the Nvidia driver fine. I have tried both the built-in 'restricted' driver and using Envy to install the one downloaded from nvidia (in separate installs). After a reboot, everything comes up lovely.

However, any more reboots/restarts of window manager causes my title bar with minimise, maximise and close buttons to not be present in any window. Also, no open windows show up on the taskbar, and the windows cannot be moved. Clicking the 'show desktop' button gives an error message of 
"Your window manager does not support the show desktop button, or you are not running a window manager." I thus assume I was not actually running Gnome.

I looked in Synaptic and Gnome was not installed, so I installed it. This has not solved anything.

If anyone has any thoughts or suggestions, they would be gratefully received!

[EDIT] Running 'sudo dpkg-reconfigure xserver-xorg' either changes nothing or breaks the ability to go into a GUI.

---

### Post by Timokl on 2007-04-21
I am not an expert on this, but Gnome is a Desktop environment and no window manager. Gnome uses Metacity as a window manager. You can try re-installing metacity:

```
sudo apt-get install metacity
```

Hope this works.

---

### Post by extremecarver on 2007-04-25
I have this problem at least every 5-6 working hours.
I can solve it by enabling desktop effects and then disabling them again. Not satisfoctory not being able to close windows or move them nor to go to the desktop.

2. problem with gnome is that sometimes I can't close windows when clicking on x (trying to click on x deactivates the window --> background) and only possible to get window into foreground by clicking on the titlebar. Only by clicking File-->Quit can I then close the window.

---

### Post by daverave999 on 2007-04-26
I ended up sorting it by deleting ~/.gnome2/session
No idea why it worked but work it did!

[EDIT] Well, renaming it to session.old so a new one was created.

---

### Post by extremecarver on 2007-04-26
Hey thanks a lot - I just did it too and for the first time since 5 hours I can log into my x session without root access again - before it allways crashed. I hope the window problem is solved too now.

Otherwise I just enable and disable the desktop effects (compiz) to refind my window manager.
I must say for me feisty has been very very buggy since I installed it (random x crashes en mass when working with xinerama), and linux-phc still not working even with no-sources kernel.

Otherwise it does most things better than dapper drake and much better than edgy which never really wanted to run on my laptop.

---

### Post by firfin on 2007-04-27
> **daverave999 said:**
> I assume it  is a Gnome problem anyway.
However, any more reboots/restarts of window manager causes my title bar with minimise, maximise and close buttons to not be present in any window. Also, no open windows show up on the taskbar, and the windows cannot be moved. Clicking the 'show desktop' button gives an error message of 
"Your window manager does not support the show desktop button, or you are not running a window manager."

I am experiencing exactly the same problem. I will try your workaround of renaming / deleting the session. I wonder what is causing this though.

Know where I can find logs to help me figure this out?

---

### Post by extremecarver on 2007-04-27
> **daverave999 said:**
> I ended up sorting it by deleting ~/.gnome2/session
No idea why it worked but work it did!

[EDIT] Well, renaming it to session.old so a new one was created.

This seems to have solved it for me now - go to /home/username/
Then click on view - show hidden files - and then click on gnome2/ and rename session to session.old

Attention - maybe its called session21303294 (random numbers) - just look for the most recent entry and rename that one.

---

### Post by firfin on 2007-04-27
Yep, removing the session solved it for me too. 
Still curious where this all came from though. Because this way it can happen again at any time?
Anyone know of a log for the window manager somewhere?

---

### Post by TNPepper on 2007-05-07
I have the same symptoms but only the desktop effects work around will work for me. Deleting or renaming ~/.gnome2/session has no effect.

I have a ATI Mach64, the hardware information app reports it as Rage Mobility P/M AGP 2x

Fairly aggravating but at least there is a simple workaround.

---

### Post by firfin on 2007-05-25
The problem kept recurring for me. But deleting the session file fixed it every time (temporarily at least).
A permanent fix for me came from the latest metacity update, apparantly it was a bit bugged.

---

