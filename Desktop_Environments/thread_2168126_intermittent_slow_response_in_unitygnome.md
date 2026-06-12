---
title: "intermittent slow response in unity/gnome"
date: 2013-08-16
forum: Desktop Environments
---

### Post by alexandre-grojsgold on 2013-08-16
I am running Ubuntu amd64 13.04, and  everything  seems to work fine, except for what appears to be an intermittent drop in the graphic desktop environment. What I mean is that from time to time (every minute or more) I have to wait for a longer than reasonable  time ( 1 sec or more) to get response to a mouse click or to a typed character, or even to a mouse wheel scroll.  It is really annoying, after some time using the computer it is really frustrating and irritating. I've been using Ubuntu for more than 3 years and was always happy to have a fast and “fluid” interface. Now it feels “sluggish”. The problem happens both in Unity as in gnome fall-back mode. The memory is lightly used (4G RAM, 1,7 used, 2,1 cache, right now). It did nor happened before, this behavior started about a week ago, and I cannot associate with any other event or software installation or update. Tried to google the symptom, didn't find anything similar. Could not correlate the performance “drop” with anything else. I have some experience with unix like systems, but could not figure out where to start looking at. Any hints, please ??

---

### Post by BBQdave on 2013-08-16
You may want to adjust [Zeitgeist]("http://zeitgeist-project.com/") and it's scope within Dash.

I'm running Ubuntu Unity 12.04LTS - 64bit, I noticed sluggish response in Firefox and Dash searches. System Settings > Privacy > Applications tab, I added Firefox - do not log activity. This sped up Firefox and Dash searches, system overall felt more responsive. Logging Firefox through Zeitgeist seemed redundant since there is a history funtion within the Firefox application.

From Ubuntu Unity 12.10 on, Zeitgeist logging is expanded beyond local and includes web information. Perhaps adjusting Zeitgeist to local logging only, and no logging of web browsers, would help with your system performance.

---

