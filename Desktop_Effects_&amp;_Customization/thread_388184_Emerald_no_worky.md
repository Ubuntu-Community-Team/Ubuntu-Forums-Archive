---
title: "Emerald no worky"
date: 2007-03-19
forum: Desktop Effects &amp; Customization
---

### Post by jonny_boy27 on 2007-03-19
a bit of background: running edgy with beryl on my main desktop pc with a radeon 9800pro

initially installed beryl and emerald from the beryl project repos, and using the open-source ati (or was it radeon) driver and AIGLX everything was nice and pretty, wobbly and spinny!

I found the performance of the Free driver in games was a bit substandard so I grabbed the fglrx driver (yes I know it's evil...) and found that it doesnt do compositing, so AIGLX was out of the window and I switched to XGL (and set up a new log-in session for XGL).

Unfortunately at this point my graphics card went foobar so it all got put on hold for a while and i was back with the standard metacity setup for a while.

Only now have I started playing again and I find everything is a bit dodgy!

The actual 3d effects work fine but I find that the icons and shadows etc. are all really ugly and I can't change them via either system-prefs-theme or via emerald. the window decoration is the one I used to use back with radeon/aiglx and I can't seem to change this at all with emerald-manager

In short, I'm having trouble theming my desktop with either sys->prefs->theme or emerald-manger.

Any help gratefully appreciated!

---

### Post by adam.tropics on 2007-03-19
Emerald manager has a problem these days in that it doesn't self apply changes. You have to hit 'reload window decorator' from the Beryl Manager menu in your notification area on your panel. Also if you wish to use Gnome themes with GTK, you can, just install Heliodor. It will show up as a window decorator under Emerald on the Beryl Manager list.

---

### Post by jonny_boy27 on 2007-03-19
cool, thanks! the reload window decorator  did the trick re: the window decorations, but every thing else is still a bit ugly. I think it's an XGL issue since when i'm logged into a non-xgl session everything is nice and smooth like a standard ubuntu install. Dialogue boxes, context menus and the panel all look like windows 95! See attachments.

thanks for the help so far! :)

---

### Post by adam.tropics on 2007-03-19
Add gnome-settings-daemon to your startup programs. and restart your session, that should do the trick.

edit. System-->Preferences-->Sessions

---

### Post by jonny_boy27 on 2007-03-19
I tried running "gnome-settings-daemon &" as recommended in the beryl wiki for de-uglyfying xgl and, aside from breaking my keyboard layout, it didnt seem to do much!

---

### Post by adam.tropics on 2007-03-19
what theme are you trying to use anyway?

---

### Post by jonny_boy27 on 2007-03-19
just human!

right, I added gnome-settings-daemon to my startup list and then did a restart and magically it all works now!

thanks very much for help! :)

---

### Post by adam.tropics on 2007-03-19
You're welcome. I had terrible times with that too a while back! I don't know what was worse, the fact that I couldn't get it to work, or that as a punishment I had to stare at win95 while I figured it out!!

---

