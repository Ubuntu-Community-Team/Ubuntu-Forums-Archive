---
title: "KDE System Setting deactivates second monitor"
date: 2006-11-29
forum: Desktop Environments
---

### Post by jimmybondo on 2006-11-29
So I was toying around with the system settings monitor section in KDE trying to get tv-out to work. I changed the resolution using the slider and hit apply. Then all of a sudden my second monitor (working with nvidia twinview) goes blank and KDE only recognizes the one monitor. I know this is not a problem with my xorg.conf because I have a backup that I restored and still have same problem. Gnome still works with 2 monitors, as does Xfce, just not KDE. Even the login page has 2 monitors enabled, but as soon as I log into KDE, it switches to 1.

Any ideas on how to fix this?
Jim

---

### Post by tkman on 2006-12-12
I have the same problem.  It's like KDE shuts my second monitor off.  Please someone help us.

---

### Post by tkman on 2006-12-12
After having a little time to experiment I have narrowed things down to one line in my xorg.conf file

Option "Metamodes" "1280x1024,1280x1024"

As long as I keep this option to just one choice I'm ok. I used to have:

Option "Metamodes" "1280x1024,1280x1024; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL"

When it was like this it would shut the second monitor down right after I logged in. This all started right after I installed the 3D game trigger.
Any suggestions?

---

