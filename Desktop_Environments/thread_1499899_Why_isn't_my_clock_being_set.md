---
title: "Why isn't my clock being set?"
date: 2010-06-02
forum: Desktop Environments
---

### Post by Jedster on 2010-06-02
Hi, I'm running UNR 9.10 on a joggler which has no internal battery so as soon as we have a power blip it reboots and the date / time is wrong.
How do I get it to automatically get the correct time once I have a network?

I have 
ntpdate
ntp-doc
ntp
all installed

The clock I'm using appears to be gnome Clock 2.28.0 so I can right click, adjust date time, Set system time, (password) which just closes the window again.
If I right click, preferences, time settings, Set system time - again that just closes that window and takes me back to the preferences.

I have my location set (London).

If I go to Time and Date settings, they are set to London and Keep Sync with internet servers with a couple of UK servers selected.

Thanks,
Jedster

---

### Post by Isaacgallegos on 2010-06-02
You might need to add a command in the "startup applications" menu, to tell Ubuntu to sync its clock.

---

### Post by Jedster on 2010-06-03
As best I can work out, I either need to start ntp as
ntp -g
(being new to this game I'm not sure where the ntp is issued from so don't know how to update that)  
or update /etc/ntp.conf with 
tinker panic 0

although I've yet to check either of those work.
Jedster

---

### Post by smithshn on 2010-06-03
It may be possible that the clock is disable from your computer. Once check it out and enable it. Second thing is that you might need to add a command in the "startup applications" menu, to tell Ubuntu to sync its clock.

---

