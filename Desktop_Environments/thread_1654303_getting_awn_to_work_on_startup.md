---
title: "getting awn to work on startup"
date: 2010-12-28
forum: Desktop Environments
---

### Post by dunnns on 2010-12-28
Hi,

I've recently upgraded to lucid lynx from karmic in which I used AWN with no problems. However, I now can't get it to work on start up, even though it is listed as one of the startup applications and the box for activate on start up is checked in the AWN manager. I have compiz installed and AWN works fine when I run it once the computer is turned on. It may be because compiz isn't properly listed as a startup application as I don't know the correct command, however other compiz actions work on start up!

Another minor point is that before I had the settings so that the dock was always hidden unless the cursor was over the area. I have played around with the preferences but can't find the right setting to make that happen! I've tried setting the behaviour as Intellihide which seems the most likely to me, but it just acts the same as window dodge... So maybe it's just not working properly??

Anyway, I would be very grateful if anyone could give me some help on either of these points!

Thanks

---

### Post by ajgreeny on 2010-12-28
I do not use awn, and have never looked at it, but in general if you need an application to start a little after gnome, or other startup apps, in order for it to run properly, you can easily do it with a sleep option in the command.

As an example, I have conky running on my desktop, but in order for it to display properly, it needs to wait until gnome is running fully.  I ensure this by having an amended command in System ->Preferences ->Startup Applications of ```
bash -c "sleep 10; conky"
```which means it appears 10 seconds after the desktop appears, and all is then OK.

Try the same thing for awn, but using whatever the normal command is for awn instead of conky as it is in mine, ie ```
bash -c "sleep 10; awn"
```

---

### Post by Frogs Hair on 2010-12-28
I have been using the AWN ppa with great results in Lucid and Meerkat . You will need purge the existing installation as indicated by the instructions. [http://www.webupd8.org/2010/08/avant-window-navigator-update-ppa.html](http://www.webupd8.org/2010/08/avant-window-navigator-update-ppa.html)

---

### Post by dunnns on 2010-12-28
So there's a new awn? I have the old one, which is actually now working - I just turned my computer back on and the dock was there at the bottom of my screen! I think it's because I used the command "compiz-autostart" in the startup applications. It still doesn't disappear though! But I can cope with that. 

Is this new version of awn a lot better? What are the helpers? (before you say it, I'm guessing they help...!) Is it a lot better than the one I've got? Because apart from not hiding mine is all I want it to be.
Thanks

---

### Post by Frogs Hair on 2010-12-29
The PPA includes lucido style and more features in settings . I can't do a side by side comparison because I can't have both the PPA and the repository version installed at the same time. The PPA has been very stable for me and intellhide and autohide  work great. The repository version is only slightly behind the PPA.

---

