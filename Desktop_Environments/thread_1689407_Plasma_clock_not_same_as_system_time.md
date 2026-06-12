---
title: "Plasma clock not same as system time"
date: 2011-02-16
forum: Desktop Environments
---

### Post by neanderslob on 2011-02-16
Hi all,

I restored my .kde directory after changing some stuff unrelated to my clock and now all plasma clocks are exactly 5 hours faster than my system time (the correct time).  I've set the time zone for Date&Time in System Settings properly and that's working well and I've ALSO gone into the time zone settings for the plasma widgets and switched between UTC and Local manually but that doesn't do anything.  Any ideas?  ](*,)

---

### Post by neanderslob on 2011-02-18
Heh, uh-oh, any at all?

---

### Post by ankspo71 on 2011-02-18
Hi,
Copy and paste this command in the terminal and see if your system time is correct (including the time zone):
```
date "+%r %Z %F"
```
If it isn't you will need to modify the system's time again.

If the system time is correct...then I can't think of a reason why your clock plasmoids are not reading the system time correctly, but have you already tried the following:

Right click on your plasma clock,
Choose "Analog Clock Settings" (or digital clock settings),
Click on "Time Zones",
Add a checkmark next to your time zone,
Then where it says "Clock Defaults To:", choose the time zone you added from the dropdown list.
Click OK.
(screenshot included)

Hope this helps.

PS. You might also want to see if you can find a solution for this at [http://www.kubuntuforums.net/](http://www.kubuntuforums.net/) too.

---

### Post by neanderslob on 2011-02-19
Hey thanks for the reply.  My system time is indeed correct, however I noticed that my plasma time zones don't look like the list you have all I have is one that says UTC and an option to set local.  According to the help menu local goes into the system time and fetches whatever number that is.  How do you get the different time zones in the plasma settings?  (See screen shot for reference).  If that doesn't seem to make sense, I'll take your suggestion and hit up kubuntuforums.  Thanks again! :guitar:

---

### Post by ankspo71 on 2011-02-19
Hmm, that's odd. 

Can you check to see if a file called 'ktimezonedrc' exists in your KDE settings folder?

The path to it is:
/home/yourname/.kde/share/config/ktimezonedrc

If it exists in that location, does it look like this when you open the file?
> 
[TimeZones]
LocalZone=America/Detroit
ZoneinfoDir=/usr/share/zoneinfo
Zonetab=/usr/share/zoneinfo/zone.tab
ZonetabCache=


note: you might also have a backup of this file located at /home/yourname/.kde/.kdebackup/share/config/ktimezonedrc too. (but maybe not if you reset/deleted your kde settings)

I could be wrong, but I believe this is the file responsible for the time zones that appear in your clock plasmoids.

Also make sure the system folder /usr/share/zoneinfo is not empty and make sure the system file /usr/share/zoneinfo/zone.tab exists.

I'm sure these files and folders can be copied from your Kubuntu live cd if any of them don't exist on your system.
Hope this helps.

---

### Post by ankspo71 on 2011-02-19
Hi again,
Here's a related post:
[http://forum.kde.org/viewtopic.php?f=67&t=79391](http://forum.kde.org/viewtopic.php?f=67&t=79391)

Check the permissions of ktimezonedrc (KDE might not be able to read it if it is owned by root)

---

### Post by neanderslob on 2011-02-19
Wow, thanks for doing my research for me!  That worked like a charm!  In case anyone else looks here first, my configuration at the location .kde/share/config/ktimezonedrc was set to root permissions so that it couldn't be accessed by plasma.  This directory I believe could also be found under the .kde4 directory depending on how your system is configured.  All I did was sudo chmod 777 .kde/share/config/ktimezonedrc, restarted then went into the clock menu and told it I wanted New York time.  Thanks so much!.

---

### Post by ankspo71 on 2011-02-19
You're welcome. :)

---

