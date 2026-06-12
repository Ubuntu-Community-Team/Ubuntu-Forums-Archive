---
title: "Theme not applied on battery startup"
date: 2010-01-18
forum: Desktop Environments
---

### Post by HarrisonFan on 2010-01-18
Hi,

I am running into an issue where the configured theme is not being applied when my laptop is started when on battery power.  After it starts up If I navigate to Preferences->Appearance the configured theme will be enabled. This only happens when starting on battery.  When plugged into AC it starts up fine and the configured theme is loaded.

Any thoughts?

Thanks,
Zac

---

### Post by HarrisonFan on 2010-01-19
Should I submit a bug report for this?

---

### Post by HarrisonFan on 2010-01-20
Anyone?

---

### Post by cousinDave on 2010-04-24
Hi

This happens to me too, but it's doing it with the power supply plugged. Have not tried it on battery. Very annoying. As the OP says, as soon as you bring up the Preferences>Appearance window, the theme is applied without clicking anything else. Running Karmic.

---

### Post by HarrisonFan on 2010-04-27
Hi cousinDave,

I am glad to hear that I am not the only one who has seen this. Unfortunately, I still do not have any solution.  It has become one of those quirks that I have just learned to live with.  I hope that maybe someone will run into this thread and be able to give us an answer. 

Thanks,
Zac

---

### Post by Zeppe on 2010-05-22
I have the same problem. I never noticed the correlation with the battery, I'll pay more attention in the future though. It may be worth opening a bug anyway. I'll keep searching for other reports now, I'll let you know if I come to understand more. 

UPDATE: I've found a report on launchpad: [https://bugs.launchpad.net/ubuntu/+bug/521766](https://bugs.launchpad.net/ubuntu/+bug/521766)

I've enable apport and I'll reopen the bug as soon as I discover if the settings-daemon crashes at startup. I'd suggest you to subscribe to the bug and do the same. 

Zeppe

---

### Post by kolinab on 2010-06-03
Strange. Just noticed this behaviour for the first time tonigh on my t60. I don't really want to troubleshoot this problem . . . !

---

### Post by dtzortzis on 2010-06-05
I have the same problem although I'm not using a laptop so I'm never on battery :) Sometimes the system starts normally while others (almost half the times) it doesn't.
While searching in the forums I found another thread about it. It appears that "gnome-settings-daemon" crashes on startup. 
My quick "fix": I created a text file with the lines:
> gnome-settings-daemon
killall nautilusThen I made it executable by running in terminal
> chmod +x nameof_the_fileThen I moved it to my /usr/local/bin folder and execute it everytime the bug appears.
It's not a solution though. It's very annoying and I don't understand what's causing it. 
Check out this thread too: [http://ubuntuforums.org/showthread.php?t=1449832&highlight=theme+startup](http://ubuntuforums.org/showthread.php?t=1449832&highlight=theme+startup)

---

### Post by kolinab on 2010-07-27
Although I rarely boot my laptop from cold startup on battery, I can report that for me, this quirk seems now to be happily resolved. Must have been in one of the updates . . .

---

### Post by iwhar on 2011-02-16
Hi

I have exactly the same problem, theme is not applied when I start my laptop on the battery, it's really annoying and didn't fix with any ap-get update  apt-get dist-upgrade

anyone have an Idea?

---

