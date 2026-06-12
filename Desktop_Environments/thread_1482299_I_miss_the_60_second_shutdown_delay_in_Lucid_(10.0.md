---
title: "I miss the 60 second shutdown delay in Lucid (10.04)"
date: 2010-05-13
forum: Desktop Environments
---

### Post by jlanawalt on 2010-05-13
I recently upgraded my desktop system from Ubuntu 9.10 (Karmic Koala) to Ubuntu 10.04 LTS (Lucid Lynx) and am missing the feature where I would get prompted with a shutdown confirmation dialog that would auto-activate after 60 seconds. Now if I click the power button in the top right corner, and select shutdown I get the "are you sure" dialog without the 60 second count-down.

I like the "are you sure" because sometimes I click the wrong option, so I don't want to *suppress_logout_restart_shutdown* in */ > apps > indicator-session* of *gconf-editor*. I also like being able to walk away from the system and have it shut down without clicking again if I was confident I did click the right one.

I can click twice, no big deal. I am just wondering if there is a user option to bring back, and possibly set, the timeout. I didn't see mention of it one way or the other in */usr/share/doc/indicator-session/changelog.Debian.gz* nor did I have any luck finding the feature in the 0.1.7 or 0.2.8 source.


I just came across bug 548415 which seems related to my question and points to the change which appears to not be configurable by some user option.

[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/548415](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/548415)

I also came across the ctrl+alt+del shutdown shortcut that pulls up a gnome-session shutdown/restart/suspend/hibernate dialog with a 60 second timeout and found that on my now-upgraded laptop the power button maps to this dialog.

While I am less likely to accidentally press ctrl+alt+delete than click the wrong thing in the shutdown menu, my toddler does occasionally go on power button rampages on the laptop so I'm glad the confirmation dialog is there. I believe it is *gconf-editor > / > apps > gnome-session > options > logout_prompt* but I haven't tested it yet. Maybe it should also have an option to configure or disable the auto-action timeout.

---

### Post by ghelbig on 2011-06-11
I agree with those that say it is a useful feature that got removed.

I agree with those that say that the USER should be the one deciding how his user interface works.

Telling me what my user interface should like like is why I switched from windows.

Please don't start doing that in Gnome or ubuntu!

---

