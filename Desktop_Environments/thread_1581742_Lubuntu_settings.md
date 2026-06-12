---
title: "Lubuntu settings"
date: 2010-09-25
forum: Desktop Environments
---

### Post by w00ly on 2010-09-25
There's a mouse setting in the preferences menu of Lubuntu but after I increase mouse speed and click close it resets back to the default of 20 and doesn't increase the sensitivity. 

Also I can't find sound settings anywhere so I always have the click noise which is especially annoying in chrome every time I open/close a tab or click save. How do I disable sound themes in Lubuntu?

---

### Post by w00ly on 2010-09-26
bump

---

### Post by Gaygerbil on 2010-10-12
I'm not sure about the mouse speed (I haven't messed with that yet) but for the sound themes, you can turn em' off in LxApperance (Look and Feel or something) it's the last tab, Other you will find a menu of two checkboxes for Sound Effects, uncheck both.

---

### Post by Black_Parrot on 2011-06-02
I have the same problem with mouse settings... but settings window close by itself when i try to change value(speed or sensetivity)

Asus eee 1005ha.
I have final lubuntu version and last updates...

How i can change mouse speed?

---

Here is about this bug: [http://ubuntuforums.org/showthread.php?t=1744829](http://ubuntuforums.org/showthread.php?t=1744829)

---

### Post by jadonchristensen on 2011-07-16
Same problem here. Toshiba X505-Q860 laptop. Cannot change mouse speed.

Is there a config file that I can edit this manually until it's fixed?

Related post:
[http://ubuntuforums.org/showthread.php?t=1744829](http://ubuntuforums.org/showthread.php?t=1744829)

---

### Post by SteveDee on 2011-07-16
> **jadonchristensen said:**
> ...is there a config file that I can edit this manually until it's fixed?
[/url]

For Lubuntu edit:-
/etc/xdg/lxsession/Lubuntu/desktop.conf

...or for Netbook:-
/etc/xdg/lxsession/Lubuntu-Netbook/desktop.conf

Changes will not be reflected in the gui (lxinput) as this is not working.

---

### Post by robcul on 2011-09-29
When I try to edit the desktop.conf file, I am given this error message after trying to overwrite the file: "can't open file to write." Any suggestions? Thanks.

---

### Post by SteveDee on 2011-09-30
> **robcul said:**
> When I try to edit the desktop.conf file, I am given this error message after trying to overwrite the file: "can't open file to write." Any suggestions? Thanks.

Yes, you need to be root to change this file.

So navigate to /etc/xdg/lxsession/Lubuntu using file manager (PCManFM), then select menu Tools > Open Current Folder as Root.

Now you can open desktop.conf from the new (root) window, edit and save the file.

---

### Post by robcul on 2011-09-30
Thanks for your help. That worked perfectly (of course).

---

### Post by amjjawad on 2011-10-01
> **SteveDee said:**
> 

[QUOTE]+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
Don't ask me, I use [COLOR=Red]Lubuntu[/COLOR].
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+

The best ever :D

---

