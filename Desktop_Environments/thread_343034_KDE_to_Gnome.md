---
title: "KDE to Gnome"
date: 2007-01-20
forum: Desktop Environments
---

### Post by Ted D. on 2007-01-20
I have been using the KDE Desktop for about 2 weeks - comparing its difference from gnome.
I am now trying to log into Gnome, but I am running into difficulties.
The Log in works OK. Ubuntu loads up until the point where the desktop itself is trying to load. The top and bottom panels appear (with no icons and/or launchers). The panels themselves disappear after a several seconds and then reappear again. Gnome recycles through this sequence every several seconds - as if in a loop.
Any suggestions on a fix.
Thanks in advance.
Ted D.

---

### Post by wireddad on 2007-01-20
I would think that if KDE worked fine Gnome should too.  KDE is more system intensive.  What are you running?  Have you tried updating?

---

### Post by aysiu on 2007-01-20
Create a test user and log in with that test user. Run into the same problem?

---

### Post by Ted D. on 2007-01-21
> **aysiu said:**
> Create a test user and log in with that test user. Run into the same problem?

I have been able to log into Gnome with an new test user. Of course there are none of my original settings. 
I did manage to get a little farther once under the regular user. Was getting an applet loading error, which asked me if I wanted to delete the applets. (I did delete them.) I Found that some some launcher icons would not launch their application. I haven't been able to get the regular desktop loaded completely again - it went back to it's earlier behavior.
Perhaps this has some to do with the themes I have in Ubuntu. Can I revert to the default themes in Ubuntu via Kubuntu.
Suggests or solutions?

---

### Post by Ted D. on 2007-01-21
> **Ted D. said:**
> I have been able to log into Gnome with an new test user. Of course there are none of my original settings. 
I did manage to get a little farther once under the regular user. Was getting an applet loading error, which asked me if I wanted to delete the applets. (I did delete them.) I Found that some some launcher icons would not launch their application. I haven't been able to get the regular desktop loaded completely again - it went back to it's earlier behavior.
Perhaps this has some to do with the themes I have in Ubuntu. Can I revert to the default themes in Ubuntu via Kubuntu.
Suggests or solutions?

PS, I am running Ubuntu dapper with the KDE destktop at present.

---

### Post by aysiu on 2007-01-21
Sure.

In Kubuntu, press Alt-F2 and type ```
gnome-theme-manager
```

You may also want to go to /home/ted/.themes and /home/ted/.icons and delete any problematic themes.

---

### Post by Ted D. on 2007-01-21
I have deleted some themes but no there is no change in the Gnome destop behavior. (There didn't seem to be anything in the icons that hadn't worked in the Gnome desktop before.)
I did manage, again, to get farther into the destop load. There were icons in the panels but they didn't launch their applications.
The error mesage I got was:" The panel encountered a problem while loading OAFFIID: Gnome_Panel_TrashApplet."and asked if I wanted to delete this applet. I chose Don't Delete.
Then I tried launching from the icons in the panel no luck. I was able to Log out or switch users. But did not give me the option to shutdown or restart. So I am back using the KDE desktop.

---

