---
title: "Date &amp; Time settings missing &quot;Clock&quot; tab"
date: 2012-07-16
forum: Desktop Environments
---

### Post by faustobp on 2012-07-16
On my system (ubuntu 12.04 running the classic gnome fallback) the "clock" tab is missing on the "Date & Time" settings dialog.

Here is how it should be:
[http://ubuntuforums.org/attachment.php?attachmentid=217245&d=1336095670]("http://ubuntuforums.org/attachment.php?attachmentid=217245&d=1336095670")

And how I see it:
[http://ubuntuforums.org/attachment.php?attachmentid=217250&d=1336101867]("http://ubuntuforums.org/attachment.php?attachmentid=217250&d=1336101867")

Without this tab I can't change how my clock is displayed and, more importantly, I can't add other locations and timezones to it.

Anyone have any idea what could be causing it?

---

### Post by Frogs Hair on 2012-07-16
The settings appear the same way in the Gnome Shell. The Time / location set _was _below the calendar when the panel indicator was selected.

---

### Post by elkr on 2012-08-05
I'm experiencing the same problem (gnome classic), and would appreciate a solution. For now I found this workaround:

to set preferences for the clock:
gsettings set com.canonical.indicator.datetime show-clock true
gsettings set com.canonical.indicator.datetime show-calendar true
gsettings set com.canonical.indicator.datetime show-date true
gsettings set com.canonical.indicator.datetime show-day true
gsettings set com.canonical.indicator.datetime show-events false
gsettings set com.canonical.indicator.datetime show-locations true
 gsettings set com.canonical.indicator.datetime show-seconds false

to set locations:
gsettings set com.canonical.indicator.datetime locations "['Europe/Amsterdam', 'Europe/Warsaw', 'UCT' ]"

---

### Post by heyup on 2012-08-11
> **faustobp said:**
> On my system (ubuntu 12.04 running the classic gnome fallback) the "clock" tab is missing on the "Date & Time" settings dialog.

I'm testing a fresh install of Precise 12.04 and have the same problem.

---

### Post by heyup on 2012-08-11
Found a workaround that worked for me:

[http://ubuntuforums.org/showthread.php?t=1980379](http://ubuntuforums.org/showthread.php?t=1980379)

Bug report:
 
[https://bugs.launchpad.net/bugs/964492](https://bugs.launchpad.net/bugs/964492)

---

