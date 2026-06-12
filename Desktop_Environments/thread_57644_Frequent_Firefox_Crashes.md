---
title: "Frequent Firefox Crashes"
date: 2005-08-17
forum: Desktop Environments
---

### Post by Oddball_Inc. on 2005-08-17
Hi all,

I am having an issue where firefox is crashing frequently. Occasionally after a crash I'll have to kill the pid to even re-lauch the app. Most of the time however; I can relaunch the brower (after a try or two).

Has anyone experienced this issue, or could you point me to a log where I can understand better what is happening during the crash.

I don't know if this is helpful; however, Epiphany (mozilla based) exhibits the same behavior as firefox.

Let me know if you I need to provide additional information.

Thanks in advance,
OB

---

### Post by tofu1 on 2005-08-17
I have the same problem. Firefox freezes and I'm forced to kill it when I visit certain sites.

[www.honda.ca](www.honda.ca)
[www.mapleglobal.com](www.mapleglobal.com)

are two..

---

### Post by Oddball_Inc. on 2005-08-17
[QUOTE=tofu1]I have the same problem. Firefox freezes and I'm forced to kill it when I visit certain sites.

[www.honda.ca](www.honda.ca)
[www.mapleglobal.com](www.mapleglobal.com)

are two..[/QUOTE]

I have yet to experience a "freeze". My browser actually closes. And my success in re-opening firefox varies....

---

### Post by auburn on 2005-08-17
same here, Oddball. But it's the same for me with Thunderbird too. Both firefox and thunderbird will suddenly close, for no apparent reason, and then sometimes they will not come back up. (When I click to start it again I can see the outline of the window appear but then it disappears.) I've tried killing and restarting X, and I've tried calling ps aux|grep firefox but it simply wasn't running.

I'm suspicious I have either a bad install of ubuntu or some obscure hardware problem that I haven't discovered yet.

Here is a similar thread:
[http://www.ubuntuforums.org/showthread.php?t=41031](http://www.ubuntuforums.org/showthread.php?t=41031)

---

### Post by Oddball_Inc. on 2005-08-17
[QUOTE=auburn]same here, Oddball. But it's the same for me with Thunderbird too. Both firefox and thunderbird will suddenly close, for no apparent reason, and then sometimes they will not come back up. (When I click to start it again I can see the outline of the window appear but then it disappears.) I've tried killing and restarting X, and I've tried calling ps aux|grep firefox but it simply wasn't running.

I'm suspicious I have either a bad install of ubuntu or some obscure hardware problem that I haven't discovered yet.

Here is a similar thread:
[http://www.ubuntuforums.org/showthread.php?t=41031](http://www.ubuntuforums.org/showthread.php?t=41031)[/QUOTE]

I haven't *totally* ruled out hardware yet either. My install has been remarkably stable expept for this issue; however, in the last 2 weeks I have had some other annoying crashes with of all things the terminal app and sign-on mgr...

Thanks for the thread..
ob

---

### Post by Oddball_Inc. on 2005-08-17
I don't know if this is of any help; however, I was running firefox from a terminal and when it crashed, it did report that it was a:
Segmentation Fault

Any ideas?
OB

---

### Post by bob k on 2005-08-17
There was a thred about this a while back, and the conclusion
was the last security fix broke some of the API's that the firefox extensions an plugin's use. The latest release in synaptic 1.0.6 and fixes alot of the seg faults, but I still get a few, mostly from mplayerplug-in and spellbound. I'm currently running mplayerplug-in 2.85, but this plug-in is real buggy and doesn't work smooth, the latest is 3.05. I have downloaded and complied it and expetct to install it this weekend when I have a day to get it working.

---

### Post by Oddball_Inc. on 2005-08-17
[QUOTE=bob k]There was a thred about this a while back, and the conclusion
was the last security fix broke some of the API's that the firefox extensions an plugin's use. The latest release in synaptic 1.0.6 and fixes alot of the seg faults, but I still get a few, mostly from mplayerplug-in and spellbound. I'm currently running mplayerplug-in 2.85, but this plug-in is real buggy and doesn't work smooth, the latest is 3.05. I have downloaded and complied it and expetct to install it this weekend when I have a day to get it working.[/QUOTE]

BK,

Thanks for the suggestion. I'll upgrade to 1.0.6 to see if that improves things..
OB

---

