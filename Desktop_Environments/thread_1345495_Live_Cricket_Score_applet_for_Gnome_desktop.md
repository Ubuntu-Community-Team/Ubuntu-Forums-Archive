---
title: "Live Cricket Score applet for Gnome desktop"
date: 2009-12-04
forum: Desktop Environments
---

### Post by sachin6870 on 2009-12-04
I have written a nice applet which will show live cricket match score at gnome panel, the same way, we see date/time. It is written in python. It will also score updates through libnotify module. You can select matches from matches in progress. 
 Sceen Shot:
[IMG]http://cricscoreapplet.sourceforge.net/screenshot1.jpg[/IMG]

 1) Match selection preference if there are multiple matches in progress.
 2) Wicket, four, sixes update through libnotify pop ups.
 3) see score of multiple matches at same time.

 Download link and more screen shot available at [CricScore]("http://cricscoreapplet.sourceforge.net/")

Enjoy,

Thanks,
-- Sachin

[My Blog]("http://www.sachystechnoworld.co.cc/")

---

### Post by The Thug on 2009-12-04
That's great, will test it out during the forthcoming series between SA & England !

---

### Post by sachin6870 on 2009-12-04
Feel free to report issues if you find any:
[bug tracker]("http://sourceforge.net/tracker/?group_id=290695&atid=1229719").

---

### Post by The Thug on 2009-12-08
Have logged a problem on Sourceforge.

---

### Post by sachin6870 on 2009-12-08
try running in shell,

>cricketscore.py run-in-window

 Also I replied to bug post.

Thanks,

-- Sachin.

---

### Post by sachin6870 on 2009-12-08
Features:

# Show Score Update Preference: With this preference user can enable/disable libnotify score update.

# Score Update Notification TimeOut Preference: Timeout value for notification to disappear.

# Fixed to avoid notifications after match is complete

# Added logging support through Logging Module.

more details,
   [http://tiny.cc/9F5DG](http://tiny.cc/9F5DG)

Fun!!!

-- Sachin.

---

### Post by raovq on 2009-12-27
I get an error while attempting to add it to a panel.

Running it from terminal gives:

      cricketscore.py run-in-window
Traceback (most recent call last):
  File "/usr/local/bin/cricketscore.py", line 24, in <module>
    import cricscore_prefs
  File "/usr/local/bin/cricscore_prefs.py", line 25, in <module>
    import io
ImportError: No module named io


Running Python 2.5.2-3 on Debian Lenny, all other dependencies are matched. Anything I can do to fix this?

---

### Post by sachin6870 on 2009-12-28
Upgrade python to 2.6, IO module is part of python 2.6.

I will update System Requirements. Thanks for reporting.

-- Sachin

---

### Post by The Thug on 2010-01-15
I've just downloaded and installed the latest version and its working perfectly.

---

### Post by Steeperton on 2010-01-15
Works nicely, Thanks!

One suggestion - how about a link to cricinfo, or whatever when clicking on the score? Just noticed a wicket had gone, and wanted to read up on the details...

Also, I'd like to be able to have notifications (notify-osd) on wickets, but not for boundaries, etc - could this be another user-set preference?

Cheers!

---

### Post by sachin6870 on 2010-01-21
you are welcome!!!

@Steeperton, will work on above features whenever I get free time.

Thanks,
-- Sachin.

---

### Post by namdung on 2010-10-03
Very useful. Haven't found any other applet like this so far.
It could do with more features, with user control to view more details of the match in preferences.
Well done!!!

---

### Post by RAJASD on 2012-09-21
is this applet still working?? i cant install it

---

