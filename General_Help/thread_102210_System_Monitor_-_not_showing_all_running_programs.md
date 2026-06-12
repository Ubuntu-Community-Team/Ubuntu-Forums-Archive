---
title: "System Monitor - not showing all running programs"
date: 2005-12-11
forum: General Help
---

### Post by Granduke on 2005-12-11
I 'think' I launched Apache and Gnump3d but I don't see any recognizable processes under System Monitor.  Is this because as servers they run at a different 'level' or something and aren't reported?
Or, much more likely  I'm doing something wrong again.

---

### Post by Zelut on 2005-12-11
If you're using the Gnome System Monitor you'll want to make sure you're listing ALL Processes (View > All Processes).  I think by default it shows user-run processes, or the options are 'Active', 'All' or 'My Processes'.  Make sure you've got them all listed and see if that helps.  Otherwise I'd suggest restarting both programs (sudo /etc/init.d/gnump3d restart & sudo /etc/init.d/apache2 restart)

You can also use 'top' from the terminal to see running processes.  See if you can see them listed in there.

---

### Post by Granduke on 2005-12-11
Yes. you're right again kuyaedz.
That's two questions of mine you answered in the same amount of minutes.
Thank's again.

---

