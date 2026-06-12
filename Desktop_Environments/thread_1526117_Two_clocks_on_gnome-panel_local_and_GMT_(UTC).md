---
title: "Two clocks on gnome-panel: local and GMT (UTC)"
date: 2010-07-07
forum: Desktop Environments
---

### Post by ebin on 2010-07-07
A few distributions back the option to display a clock on the gnome-panel in GMT was removed, however to preserve backwards compatibility the option was left in which you could edit by hand or through gconf-editor. Since I have upgraded to Ubuntu 10.04 I've noticed that the option does not work any longer. 

My method has been:

$ gconf-editor

then under: / -> apps -> panel -> applets -> applet_N -> prefs
set: gmt_time = True

PS In writing this post I realize this is actually a Gnome issue and maybe I should go post on the Gnome forums... 

Jon

---

### Post by Cygnia on 2010-07-07
I may not be understanding your question, but I have four time zones in my drop-down gnome clock locations, including GMT. Have you tried clicking the clock and choosing Locations >> Edit?

---

### Post by ebin on 2010-07-08
I want two clocks on my gnome-panel, one in local time the other in UTC. I have other locations added to my drop-down as well, however I have to press the clock to get the drop down. It can be useful to have both clocks clearly visible at all times.

Jon

---

### Post by livewire98801 on 2010-07-08
I'd really like this working as well. . . I read a lot of logfiles that are coded in UTC, and having the two clocks side by side is far more useful than having to open my timezone list (which is rather long) to see UTC.

Is there a gnome forum that might be more useful to post this in?

---

### Post by ebin on 2010-07-12
I'm not sure, but you're probably right. The Ubuntu forums haven't really helped. 

What I find most strange is that it USED to work and now it seems to do nothing.

---

### Post by livewire98801 on 2010-07-12
I can at least answer that part.  From the description in the gconf-editor entry:

> The use of this key was deprecated in GNOME 2.28 in favour of the use of timezones. The schema is retained for compatibility with older versions. 

I'm guessing that they decided it was not necessary . . . wish they had consulted me first :(

---

### Post by ebin on 2010-07-12
Yes but until the newest version of Ubuntu you could. I think it was the move to GNOME 2.30 that caused the problem. So I guess that means GNOME forums are the place to go.

---

### Post by emarkay on 2010-08-03
WELL??

Can it be done? 

I want 2 time displays in my panel, with 2 different time zones.  Should be  simple, eh?

---

