---
title: "Screenlets and AWN when turned off computer"
date: 2008-04-05
forum: Desktop Effects &amp; Customization
---

### Post by Elliot76 on 2008-04-05
When I turn off my computer and turn it back on, I have to start the AWN program manually and start screenlets and put 'em back where I want them.

Is there anyway I can save the settings so the screenlets and AWN Always load?

---

### Post by stek79 on 2008-04-05
Hi,
 with the 'awn-manager' tool you can choose to run AWN at your logon.

BTW I have noticed that this options seem absent with the AWN version provided into the Ubuntu repositories.

However, to edit the startup programs it is easy: just go to System->Preferences->Sessions. Here you can insert an entry to start AWN, with that command:

avant-window-navigator

Good luck!

---

### Post by DagMan on 2008-04-06
The screenlets you should be able to run one by one on startup in the same fashion described above, but better would be to put them all in a script, and just have the script run at startup.

You'de need to put the & at the end of each screenlet command if it's in a script, so the script backgrounds it and goes on to the next one.  Mine looks like this, it's not ubuntu so the location of the screenlet may be differnat but you get the idea

```
#!/bin/bash

/usr/share/screenlets/Clock/ClockScreenlet.py  &

/usr/share/screenlets/ClearWeather/ClearWeatherScreenlet.py  &

/usr/share/screenlets/ClearCalendar/ClearCalendarScreenlet.py &

```

---

