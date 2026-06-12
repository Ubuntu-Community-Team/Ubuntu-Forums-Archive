---
title: "How do I set the screen resolution for KDM?"
date: 2006-06-29
forum: Desktop Environments
---

### Post by lastexyle on 2006-06-29
Here's the deal: I have my xorg configuration set up how I want it, but I don't want KDM to use my monitor's maximum resolution. Is there any way I can manually set the resolution KDM uses? I'd like to avoid simply removing any resolution entries above what I want for KDM from xorg.conf since I do use higher resolutions elsewhere.

---

### Post by asimon on 2006-06-29
Never done such a thing, but in /etc/kde3/kdm/kdmrc you'll find a line starting with "ServerCmd=", which defines how kdm starts the X server.
So for example you could replace the default command with "/usr/bin/X -br -config /etc/X11/xorg-kdm.conf" and create xorg-kdm.conf as a copy of your normal xorg.conf but with the undesired resolutions for kdm removed. Maybe X also has some command line options for start it with a specific resolution.

---

### Post by lastexyle on 2006-06-30
Thanks, I'll give that a try.

---

