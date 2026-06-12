---
title: "Please help - endless loop starts with clock applet"
date: 2009-04-01
forum: General Help
---

### Post by kellywmay on 2009-04-01
Gnome Panels load then start disappearing/flashing

This is is not a simple "panels have disappeared" problem. I've read all the posts and tried that. This problem is intermittent and aften starts happening about 10 seconds after Ubuntu Intrepid has loaded and the panels have appeared fine. I can even click them and use them (if I am quick). Then suddenly the top and bottom panel slide out of sight and start appearing and disappearing every half second. It's impossible to click the menu in time. ALt+F1 brings up a menu for a split second then disappears. After 1-2 minutes of this flicking back and forth, the panels don't re-appear and Alt+F1 doesn't work, but the mouse continues to change to a "wait" icon every half-second. In the end I use a keyboard shortcut to open a terminal and use the following to temporarily fix: 

```

gconftool –recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
sudo startx

```

...Then restart.

After two weeks I think have narrowed it down. It seems to happen again when I try to set (re-set) the Location for weather updates in the Clock Preferences appelet in the top panel. I am in Hua Hin, Thailand - Weather code VTPH. Based on other threads and issues and eventually found (on NOAA.gov) that there are periods of "NO DATA" showing over the past 12 hours. Maybe this is causing the appelet to "crash and restart" over and over????

Lately I have had success with manually removing the XML entry for Location in ~/.gconf/apps/panel/applets/clock_screen0/prefs/%gconf.xml 

My xsession-errors file is attached.

Please help...

Kelly

---

