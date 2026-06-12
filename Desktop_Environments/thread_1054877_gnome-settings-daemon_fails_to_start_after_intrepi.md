---
title: "gnome-settings-daemon fails to start after intrepid upgrade"
date: 2009-01-30
forum: Desktop Environments
---

### Post by ouch67 on 2009-01-30
my theme is missing and whenever I try to change a system setting like my screen resolution nothing happens.

For instance when I go to system->preferances->screen resolution I get this message:

Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

then the dialog pops up but nothing happens when I change the res and click apply.

I've re-installed dbus, bonobo, and the gnome-settings-daemon itself and it still occurs.

I can run:

sudo gnome-settings-daemon

And my theme comes back, but when I go to change my resolution the same problem occurs.

I ran it in debug mode and all it said was "**MATCH" something with xrandr

---

### Post by Xamiga on 2009-01-30
Same thing happened to me.  In System->Preferences->Sessions, gnome-settings-daemon became unchecked.

---

### Post by ouch67 on 2009-01-30
Mine is checked. But strangely, if I uncheck it, and log out and log back in I get a larger screen resolution...

but after manually starting the daemon it still gives me that error every time I try to go to the change resolution dialog.

---

### Post by ouch67 on 2009-02-02
Well can anyone tell me which files effects this program so I can figure it out myself then? (gnome-settings-daemon)

---

### Post by [z]er0 HP on 2009-02-06
Currently having the same problem except can't run gnome-settings-daemon from terminal or run. Settings are not saved after logout/restart. Same error as OP.

NEED HELP PLEASE! This is driving me insane

---

### Post by skunkbad on 2009-02-19
I installed a dual boot of WinXP and Ubuntu 8.10 on a machine today, and when I tried to install Adobe's Flash Player on the Ubuntu side, I was getting this gnome settings manager error. All I did was reinstall the Flash player a second time, and everything was fine after that. I am by no means a Linux guru, but since what I did was simple, I'm guessing that your problem is also simple.

---

### Post by [z]er0 HP on 2009-02-22
I fixed this problem by removing the settings stored in /home/username/.gconf/
I removed them, rebooted and then re-added the ones I needed and reconfigured a few different things.

---

### Post by PaulWhipp on 2009-03-19
This has happened to me too following the latest 8.10 updates. Changing or even removing .gconf makes no difference.

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6383169](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6383169) mentions removing a libvisual file which makes no difference.

Currently I'm stuck with nasty blue windows title bars and no ability to change the appearance on my system.

---

### Post by ouch67 on 2009-04-05
Yes I can confirm doing the things above DO NOT work. As a result were left with a crippled system.

I thought this would be fixed by now. Can't anyone fix this thing?

---

### Post by PaulWhipp on 2009-04-05
I'm in the same boat. gnome-settings-daemon and sound are broken following the updates.

I have a very strong suspicion that the gstreamer update was responsible for the problem but I've not been able to re-install anything there that fixes the problem so I'm still stumped.

Anyone know of a way to re-install all the sound stuff i/c drivers?

---

