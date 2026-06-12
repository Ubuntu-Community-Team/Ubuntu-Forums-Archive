---
title: "Generic Gnome panel applet to display script output?"
date: 2006-03-29
forum: Desktop Environments
---

### Post by nmuntz on 2006-03-29
I've spent a significant amount of time looking for a panel applet that will simply run a script every X seconds (or minutes) and display the text output on the panel.    Does such a thing exist?  I couldn't even find anything on gnomefiles.org.

---

### Post by 5-HT on 2006-03-29
Haven't heard of any panel applet that allows that, but there would be an easy way to do this using a terminal and cron.

You could set up a cronjob to run the script whenever you want and pipe whatever output to want to your terminal using the 'write' command.

HTH

---

