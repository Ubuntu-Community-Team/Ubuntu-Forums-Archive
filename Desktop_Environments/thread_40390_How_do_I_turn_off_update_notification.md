---
title: "How do I turn off update notification?"
date: 2005-06-08
forum: Desktop Environments
---

### Post by watchitman on 2005-06-08
I HATE it and I want it to go away and never be seen again. That little red icon with the exclimation mark sitting in the notification area next to the clock tells my brain that something is severely broken. If I want to update the system, I'll do it when I want to - I don't want to be nagged by that demon icon! How do I get rid of the beastly little monster?

---

### Post by Gtaylor on 2005-06-08
I can't remember since it's been a while, but you should be able to right click it and select one of the options to disable it.

---

### Post by watchitman on 2005-06-08
Nope. No such option.

---

### Post by spartas on 2005-06-08
The easiset way is to remove all references to .update-notifier in your home directory.  Warty never had an update-notifier directory in the home directory, and since I upgraded from warty it was never added.  I'm update-notifier free.  I hate that thing anyway.

It's in a hidden subdirectory, but I don't remember which one because I don't have it anymore.  Try the following in a terminal to find it:

```

locate update-notifier | grep home

```

---

### Post by watchitman on 2005-06-08
I deleted it and it reappeared after I rebooted. And that evil icon is still there! And Synaptic won't let me uninstall it without uninstalling "ubuntu-desktop" and I think I might need that - "killall update-notifier" shuts it down but I have a feeling the little monster will be back if I reboot.

---

### Post by spartas on 2005-06-08
[QUOTE=watchitman]I deleted it and it reappeared after I rebooted. And that evil icon is still there! And Synaptic won't let me uninstall it without uninstalling "ubuntu-desktop" and I think I might need that.[/QUOTE]

Did you delete every mention of it in that was listed?  You could always install warty and upgrade (just kidding).  You may want to do a search in your hidden files for mention of it in a text file somewhere.

If killing the gnome-panel shuts it down then you removed the part where it's supposed to reload, just not the part where it loads upon startup.  Is it listed in the Start Up tab of System->Preferences->Sessions?

---

### Post by watchitman on 2005-06-08
[QUOTE=spartas]Did you delete every mention of it in that was listed?  You could always install warty and upgrade (just kidding).  You may want to do a search in your hidden files for mention of it in a text file somewhere.

If killing the gnome-panel shuts it down then you removed the part where it's supposed to reload, just not the part where it loads upon startup.  Is it listed in the Start Up tab of System->Preferences->Sessions?[/QUOTE]

I saw only the hidden directory named .update-notifier. I'll try a text search.

---

### Post by watchitman on 2005-06-08
I'm not finding anything that looks like it's causing it to start up. Obviously, something is but I'm no linux guru.

---

### Post by watchitman on 2005-06-08
I figured out a way to get rid of it! I went to System > Preferences > Sessions and deleted "update-notifier" from "Current Session," created a new session and saved it. Now when I boot into Gnome, the update-notifier daemon doesn't start!

---

### Post by spartas on 2005-06-08
Alright!

---

### Post by xerosis on 2005-06-09
on the other hand, my update notification seems to have disappeared, i didn't actively delete it, how can i ge it back? :-P

---

### Post by pizpot on 2008-02-20
The update popup sucks although I am not complaining, it was free. I was in a game of Warsow, after booting, and up comes the popup which I had to quit the game to click and have it go away. :-(

---

### Post by Cheesehead on 2008-07-18
Under 8.04,
TO GET FEWER UPDATE NOTIFICATIONS, open update-notifier (from the command line: update-notifier) and make the notifications more restrictive.


TO ELIMINATE ALL UPDATE NOTIFICATIONS, use Synaptic to remove the following packages: update-notifier, update-notifier-common. You can always reinstall them from Synaptic, of course. 

After removing the packages, if you want updates you must launch Update Manager from the menu - the system will no longer remind you. I recommend a weekly or monthly routine. You can use your Evolution calendar (or a cron job) to remind you to update your system.

If you're not afraid of the command line, the commands to remove or install the packages are (in order):
```
sudo apt-get remove update-notifier update-notifier-common
sudo apt-get install update-notifier update-notifier-common
```


IF YOU AREN'T GETTING NOTIFICATIONS, BUT YOU WANT THEM,
1) Check your toolbars. You need a notification area (or a system tray in Xubuntu) for the icon to show up in.
2) Start the application (on the command line: update-notifier), and see if it shows up in the application area. Check the settings - you may have made them too restrictive in the past.
3) Start the Update Manager - if no updates are available, the icon usually won't show up, anyway.
4) Use Synaptic to completely uninstall (including config files) and reinstall. On the command line, it's called 'purge' instead of remove.

---

