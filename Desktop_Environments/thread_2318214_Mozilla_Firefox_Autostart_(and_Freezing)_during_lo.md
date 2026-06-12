---
title: "Mozilla Firefox Autostart (and Freezing) during log-in drives me nuts."
date: 2016-03-24
forum: Desktop Environments
---

### Post by jenmuxxl on 2016-03-24
Kubuntu 15.10 64 Bit

I had many problems, so I reinstalled my complete system. (I mention this because I formated the system partition and the problem must be in the config files in the user partition ).

But one problem still persists:

When I log-in Kubuntu, firefox starts immediately and somehow crashes and freezes so that the log-in can't proceed. I open a terminal with CTRL-ALT F1 do a ps -A|grep fire and kill the process. Then the log-in process will proceed successfully
Firefox also starts successfully if I start it.

WTF is the autostart up info for this located?

I don't see anything in /userdir/.kde/Autostart
I don't see anything in /userdir/.config/ 


Any ideas? This is totally annoying.

---

### Post by deadflowr on 2016-03-24
Isn't that controlled by the system management settings?
this is kind of old, but does it still hold relevance:
[https://userbase.kde.org/System_Settings/Startup_and_Shutdown#Session_Management](https://userbase.kde.org/System_Settings/Startup_and_Shutdown#Session_Management)

---

### Post by jenmuxxl on 2016-03-24
Thanks but checked that already. "Start with an empty session" is turned on.

---

