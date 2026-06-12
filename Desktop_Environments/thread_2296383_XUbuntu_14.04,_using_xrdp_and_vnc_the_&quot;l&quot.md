---
title: "XUbuntu 14.04, using xrdp and vnc the &quot;l&quot; key is not working, sometimes locks screen"
date: 2015-09-25
forum: Desktop Environments
---

### Post by y-george-b on 2015-09-25
I  have an Xubuntu microserver running XUbuntu 14.04.
When i log in via xrdp or vnc the "l" key does not work, just does not appear on screen.
It sometimes causes the screen to lock and sometimes not.
|The problem is independent of which rdp client I user. I've tried from both Linux and Windows.
This happened to me long time and I never found a solution.
It's a bit so a show stopper.

George

---

### Post by y-george-b on 2015-09-26
To test I created a vm in KVN of ubuntu 14.04, tested xrdpp, same problem no "l" key.
Tried the same with Ubuntu 15.04. "l" key worked.
So I upgraded my system from 14.04 -> 14.10 -> 15.04. Waste of time, the "l" key did not work.
Plus the upgrade trashed Guacamole and Asterisk.
I give up. I'm installing Centos 7.1 and hope for better luck.

---

### Post by y-george-b on 2015-10-03
Ok, I've solved it. The problem was with Cairo Dock,
There is a shortcut configuration option for "<window key> L"
I replaced this with "F4" as an unused key and the problem is gone.

---

