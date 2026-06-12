---
title: "Desktop Settings"
date: 2013-09-08
forum: Desktop Environments
---

### Post by manikinxvx on 2013-09-08
Recently I updated and added a few packages to my system; one of which, I believe, may be the culprit for interfering with my desktop settings as my icons for "Filesystem", as well as external drives have disappeared from being displayed on the desktop. Now they are only present in the File Manager. Additionally, my desktop picture has vanished and I can't restore it, nor get *any* image (pre-installed or my own) to appear. Does anyone have any idea of a package responsible for this? I really don't even recall what I updated/added at the time this began happening. I'm just wondering if anyone else has experienced such a problem and found a resolution to it.

Thank you for taking the time to read this.
--M

---

### Post by Toz on 2013-09-08
Check to see if xfdesktop is running (xfdesktop is what manages the Xfce desktop). From a terminal window, run:
```
ps -ef | grep xfdesktop | grep -v grep
```
If it returns a line, then it is running and something else might be the problem. 

If it is not running, then Alt+F2 and run:
```
xfdesktop
```

---

### Post by manikinxvx on 2013-09-08
Just great... WTH did I do/install now?! }:-/ 

** (xfdesktop:5518): WARNING **: xfdesktop: another desktop manager is running.

Time to again pick through every package installed and see if I can see one that might be related. Thanks for this action plan, Toz.

---

### Post by Toz on 2013-09-09
Is it nautilus:
```
ps -ef | grep naut | grep -v grep
```

If so, kill its process and then start up xfdesktop.

---

### Post by manikinxvx on 2013-09-09
Thank you, Toz! Yes, Nautilus was/is the issue. All desktop icons and image automagically reappeared after killing the process and starting xfdesktop. 

This leads me to a multi-part question as well: a) Since "Nautilus is the official file manager for the GNOME desktop", as described in Synaptic, is it safe to mark it for complete removal, given that I have "Start GNOME Services" enabled? b) Is there a way to suspend Nautilus from starting up with the system to further test issue-resolution upon rebooting? c) If the issue is resolved upon reboot with Nautilus suspended [if possible] is there a way to stop it from over-riding the settings manager if complete removal is not safe with GNOME Services enabled?

---

### Post by Toz on 2013-09-09
> **manikinxvx said:**
> a) Since "Nautilus is the official file manager for the GNOME desktop", as described in Synaptic, is it safe to mark it for complete removal, given that I have "Start GNOME Services" enabled?
Yes it is safe. According to [here]("http://docs.xfce.org/xfce/xfce4-session/preferences"), "gnome services" only starts the keyring daemon. 
> b) Is there a way to suspend Nautilus from starting up with the system to further test issue-resolution upon rebooting? 
The easiest way to do this is to clear your sessions cache. If you are using Xubuntu 13.04 (Xfce 4.10) or greater, then there is a "Clear Saved Sessions" button in Settings Manager -> Session and Startup -> Session tab. If you have an earlier version, you'll have to:
- log out of the gui
- go to the first console (Ctrl+Alt+F1)
- log in to the text console
- issue the following commands:
```
cd .cache
rm -rf sessions
```
- go back to the gui login (Ctrl+Alt+F7)
- login and test.

**Also make sure that nautilus is not in your autostartup (Settings Manager -> Session and startup -> Application autostart).
> c) If the issue is resolved upon reboot with Nautilus suspended [if possible] is there a way to stop it from over-riding the settings manager if complete removal is not safe with GNOME Services enabled?
I've never used nautilus, but I understand ([man naultilus]("http://manpages.ubuntu.com/manpages/precise/man1/nautilus.1.html")) that there is a --no-desktop parameter that you can pass to it that will prevent it from taking over the desktop. If you run nautilus from the command line, this is easy - just run:
```
nautilus --no-desktop
```
...but if you start nautilus via the menu, you'll need to change the nautilus .desktop file in /usr/share/applications and append "--no-desktop" to the end of the Exec command line.

---

### Post by manikinxvx on 2013-09-09
Because I was able to uninstall Nautilus without adverse interference, I just took that route rather than the investigating the testing models I noted. Thank you for you information, Toz. Greatly appreciated.

---

