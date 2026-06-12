---
title: "wine not showing up on panel"
date: 2005-08-09
forum: Desktop Environments
---

### Post by aloysius on 2005-08-09
I run a few mapping/ geocaching based programs under wine that i have not been able to live without under ubuntu...mainly GSAK and OziExplorer. They both run beautifully under wine..but...they dont appear on my gnome panel....all other running programs are there but not any wine programs. 

Is this possible in gnome? i have asked friends who run kde and they have this working in k....i have tried running from console and also from a shortcut and neither show on panel. Anyone else experienceing this? wine installed from repo's via apt-get...

---

### Post by svasie on 2005-08-09
This is a known problem.

[http://www.codeweavers.com/support/tickets/browse/?ticket_id=57969;list=6;ticket_level=2](http://www.codeweavers.com/support/tickets/browse/?ticket_id=57969;list=6;ticket_level=2)

I'm using CrossOver Office with Lotus Notes and i found a way to put Notes Minder in the notification area. The trick is to launch a KDE app which docks in the panel (smb4k in my case), launch the wine application and then quit the KDE app. This way Notes Minder keeps docked at notification area.

If you want to do it automatically, you can modify the launcher, doing something like this:

launch KDE app -> launch wine app -> sleep 10 secs -> kill KDE app

Wish it helps.

---

