---
title: "how to detect new windows opening"
date: 2015-04-09
forum: Desktop Environments
---

### Post by cedardoc on 2015-04-09
I don't know why, but I often get windows opening up but not raising, e.g. a new window generated from a script or a file opened from synapse launcher.

I'd like to automatically run a wmctrl script to raise any new window whenever a window is opened in the system.  Is there a utility that can detect this type of event, maybe something like inotifywait, but specifically for window events instead of file events?


Thanks, 
Dave

---

### Post by cedardoc on 2015-04-09
Sorry, false alarm.  I figured out what I was doing wrong:

I'm using kpie ([https://github.com/skx/kpie](https://github.com/skx/kpie) a devilspie lua variant) and instead of this rule (which works) 


if ( window_class() == "Google-chrome" ) then
	below()
end

I had been using this

if ( window_class() == "Chrome" ) then
	below()
end

which didn't work.  I guess it was only happening when chrome was open - I must use it alot.


btw, I'd still be interested in the answer to this just for interest's sake if someone knows it off the top of their head.  I was surprised I couldn't find such a thing.

---

