---
title: "Guest sessions missing in 10.04 on netbook"
date: 2010-06-05
forum: Desktop Environments
---

### Post by jonthysell on 2010-06-05
Ever since upgrading to 10.04 from 9.10, my netbook is missing the guest session and switch user options from the upper right menu.

It's there on my desktop install. Is there a flag somewhere so I can turn it back on?

---

### Post by TheMusicGuy on 2010-07-12
I'm not using Netbook Remix, but I know that Desktop edition's panel applets have been split, combined, and renamed. There are, for example, three *distinct* panel applets with similar purpose and name. They are called "Indicator Applet", "Indicator Applet Session", and "Notification Area." I'm still trying to figure out exactly which ones do what, but if you have one of each in your panel, you should see everything you want.

---

### Post by jw12321 on 2010-07-20
I have all of them in my panel, but there still is no Guest session option under the power button. When I log in to GNOME, however, it appears.

Any way to have Guest session appear in UNR? (If it helps, I'm running Easy Peasy)

---

### Post by magnadoodle on 2010-07-25
What I did to get it to work was to add "gdm-guest-session" through synaptic package manager.  I can then run the guest session by typing /usr/share/gdm/guest-session/guest-session-launch in the terminal.  It also works if you add the "Indicator Applet Session" to the panel and there will be a guest session option now.

---

