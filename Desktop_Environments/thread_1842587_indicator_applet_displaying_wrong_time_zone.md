---
title: "indicator applet displaying wrong time zone"
date: 2011-09-11
forum: Desktop Environments
---

### Post by blisterpeanuts on 2011-09-11
I installed Ubuntu 10.04 Natty Narwhal and set local time zone to Arizona/MST.  All was fine.

Moved computer to Boston and tried to set it to EST.  No matter what I do, indicator applet continues to display Arizona/MST (3 hours behind).  I click on the time/date, it shows New York is the selected region, and the correct time next to it.  I go into Time & Date Settings, unlock it, make sure time zone is EST and correct time is set.

I have tried resetting the system's time zone:
# sudo dpkg-reconfigure --frontend noninteractive tzdata

# cat /etc/timezone
America/New_York

# export TZ='America/New_York'
reboot
# printenv TZ
America/New_York

# date
Sun Sep 11 18:39:16 EDT 2011

Yet, the stupid indicator applet continues to display
Sun Sep 11 3:39:16 PM

Is this a bug in the applet?  I came across one or two bug reports that might explain this behavior.  Maybe it's been fixed in 10.10?  I'm a little afraid to upgrade, because I found 10.10 to be a mixed bag on my laptop, very different user interface that took a lot of work to put back the way I like it.

I have googled all over the place and have found no solutions :(

Thanks for any assistance 

-Bp

---

### Post by blisterpeanuts on 2011-09-12
More interesting behavior:

running xclock directly from windowing system (alt-F2 xclock) displays the wrong time.

running xclock from a console displays the correct time.

It's as though the parent process (Gnome?  X?) of the run command is passing along some kind of incorrect environment information, whereas a shell command doesn't.

---

### Post by 741Baus on 2011-09-12
Hi blisterpeanuts I don't know if this will help your situation its for resetting clock to local time when dual booting with windows and the time has been reset in the windows partition 

```
sudo hwclock --localtime 
``` 

perhaps this with work ?

---

### Post by blisterpeanuts on 2011-09-12
Thanks for the suggestion.  That doesn't seem to do anything.  Actually, hwclock gives me the correct time, so I think the system clock is OK.

I've killed the indicator applet and I'm just running an oclock in the corner of the screen.  At least I don't have to look at the wrong time.  The heck with it!

---

