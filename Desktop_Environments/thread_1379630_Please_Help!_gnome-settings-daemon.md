---
title: "Please Help! gnome-settings-daemon"
date: 2010-01-12
forum: Desktop Environments
---

### Post by Barriehie on 2010-01-12
Edit: Doh! Since I've got a working session I saved it and then powered off and rebooted and everything works.  Have no clue!  I think maybe time for a new install and install from my app. list and restore home dir.  Whatever the issue was it was system wide!  Any thoughts anyone???

Hey all!  So when I get to the desktop via GRUB recovery mode, resume normal boot, Failsafe GNOME session, I have no desktop for quite some time.  Any other way and I get an error message about the gnome-settings-daemon had an error loading and some things might not work.  Specifically my internet connection.  The network monitor is showing packets going back and forth but nothing is resolved via my username, or roots, or my testuser.  By resolved I mean FF can't connect, ping doesn't work, etc.  

Can someone please help me in resolving this!!!  I have a backup of /home, /etc, and /var/www but I'ld really rather not go there!  I looked in synaptic and there is no option to reinstall the gnome-settings-manager, you can only uninstall it along with a BUNCH of other apps.  Doable I guess if all is done in the same session.

Also, when it does finally get to a desktop it takes a LONG time for apps to load and some of them just drop out without running.

Anyone seen this before???

TIA,
Barrie

---

### Post by Barriehie on 2010-01-12
Okay, I'll have to mark this solved.  I saved ~/.gnome2/session to ~/.gnome2/session.save_my_b***  and did [[color="blue"]this[/color]](http://ubuntuforums.org/showpost.php?p=3776732&postcount=15) and made a note about manually starting the GSD.

TIA :)

---

### Post by Barriehie on 2010-01-13
Spoke to soon!  Formatted everything and did a clean install of 8.04.3  That gnome-settings-daemon issue started coming back on every boot. :(

---

### Post by Barriehie on 2010-01-15
This is just yanking my last chain!  Looking for a gnome replacement. :evil:

---

### Post by Barriehie on 2010-01-17
Xclient script or Xfce4 and am defaulting to fluxbox login.

---

### Post by CrammitTheFrog on 2010-01-24
I believe I'm getting the same error, but I have not found a solution, yet.  The error message I'm receiving is

> 
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.


My desktop comes up only a few seconds later than it does normally, but my desktop settings are set to default.  If I go to change the settings by going to System --> Preferences --> Appearance, I receive the following error message:

> 
Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.


This lead me to see if I do have another settings manager installed, but I do not.  Strangely after about 5 to 10 minutes, everything starts to load properly.  This happens everytime I bootup.  Seeing on how I can work around this problem, I will try to find a fix and post it when I do.

---

### Post by Barriehie on 2010-01-24
Only fix I could find was to either boot into xfce or fluxbox.  I'm not realling missing gnome now.  Fluxbox is VERY fast and has way fewer process' going on...
```

05:13:37 /home/barrie $ >> clear; ps -u barrie

  PID TTY          TIME CMD
 6603 ?        00:00:00 gconfd-2
 6605 ?        00:00:00 gnome-keyring-d
 6606 ?        00:00:15 fluxbox
 6768 ?        00:00:00 seahorse-agent
 6772 ?        00:00:06 xscreensaver
 6774 ?        00:00:13 gnome-terminal
 6780 ?        00:00:00 bonobo-activati
 6811 ?        00:00:00 gnome-pty-helpe
 6812 pts/0    00:00:00 bash
 6818 ?        00:02:44 pcmanfm
 6820 ?        00:00:01 gam_server
12975 ?        00:01:47 firefox
13240 ?        00:00:00 sh
13241 ?        00:00:00 curl
13480 ?        00:00:00 conky
13521 pts/0    00:00:00 ps
05:13:47 /home/barrie $ >> 

```

I even dl'ed Xubuntu and have considered, but not completed, either to add it as another boot option or just blow away ubuntu.  So far I'm predominately running fluxbox and it's working without errors.

Barrie

---

### Post by CrammitTheFrog on 2010-01-25
I've been thinking about using KDE, and I plan to do a reinstall everything since and get rid of the Windows side of my laptop.  I just haven't done it, yet.

---

