---
title: "Strange behaviour: autostart, volume control, session lock, WLAN"
date: 2010-03-26
forum: Desktop Environments
---

### Post by ybynty on 2010-03-26
Hi everyone,


for no quite some time I am experiencing weird and annoying behaviour of my Ubuntu (with Gnome), all of which occur on every boot.


**1. The autostart applications won't start automatically.**
**2. The volume control is set to mute and 0% volume, although I keep resetting it on 100%.**
**3. I can't lock the screen within a session.**
**4. My WLAN-adapter doesn't look for an available network, like it used to on booting.**


I already made sure that my user has the right to read and write all of the files and directories in his home directory. That didn't help.


I hope this makes sense for someone, since all of the described erratic behaviour seems to have started at the same time, so I figure they should be traced back to some common cause.


Thanks for your help in advance!
Ybynty

---

### Post by ybynty on 2010-03-29
*bump*

---

### Post by MooPi on 2010-03-29
Please list any updates or changes prior to your problem. This may help us diagnose your issue.

---

### Post by ybynty on 2010-03-29
The problems started already at the beginning of March and all of them at once. I can't remember doing any manual change to my system. My machine uses to run several days without rebooting, so I didn't get suspicious at once and so I did not take note of what updates had been done recently. But I do the updates whenever my autoupdater suggests right-away. So any update in the very first days of March would be questionable.

Can I look up which ones have been done at what point of time somewhere?

---

### Post by ybynty on 2010-03-31
It's a bit embarassing, but I have found the problem. It was sitting right in front of the keyboard all along. My gnome logon screen was set to "debug mode". Apparently, this setting won't change from one logon to another, unless you change it. I did not notice that.

Sorry, guys, for the confusion. Thanks anyway!
Ybynty

---

