---
title: "AWN Launchers won't show up"
date: 2008-02-03
forum: Desktop Effects &amp; Customization
---

### Post by LoSt180 on 2008-02-03
I had AWN curves installed and working, but decided to uninstall it because the icons were constantly messed up (ie icon split with half near bottom and other half in-line with the curve).

I uninstalled using the instructions in this [HOW TO: thread]("http://ubuntuforums.org/showthread.php?t=572019&highlight=awm"). Restarted, curves was gone, but AWN was still there. I changed some settings like bar angle, etc. Then for what ever reason all my launchers have disappeared. The only thing showing are the applets. In the AWN manager, the launchers were still listed, but again not visible. 

I tried to uninstall it all-together. I used synaptic as well as all the 'rm' commands listed in [the HOW TO: install]("http://ubuntuforums.org/showthread.php?t=385981") thread. Rebooted to make sure there wasn't anything in memory, and installed AWN again. When I opened Awn Manager, all the launchers from before are still listed, even a 'black' theme and Bar appearance were still there. But I STILL can't see any launchers! I've tried removing all launchers and re-adding them.. nothing.

Help.. I used the "Mark for complete removal" in synaptic. Is there any other folders where settings might be store? Or how can I get my launchers to show!?

---

### Post by LoSt180 on 2008-02-07
anybody have any ideas on this?

---

### Post by kbless7 on 2008-02-08
I had that problem when I originally installed AWN. I personally think AWN sucks with launchers, but I just reinstalled it was fine in that respect.

---

### Post by Tenken on 2008-02-08
Check your home folder for a .awn folder, which holds the settings/preferences for AWN, even after you remove the program.

---

### Post by Killerah on 2008-02-21
I have the same exact problem, I hope someone knows what to do, I've uninstalled and reinstalled and still I have no launchers, just applets.

---

### Post by LoSt180 on 2008-02-21
Okay, I got it fixed. First there was no .awn folder in my home directory. 
I noticed the AWN had an update and new repositories. So I used Synaptic and did a "Complete" uninstall of AWN and the dependencies. After it was gone, I update my sources.lst and reinstalled AWN. (The [HOW TO]("http://ubuntuforums.org/showthread.php?t=385981") thread has been updated)
After reinstalling, still no launchers! :mad: 

I went through the Applets in AWN Manager and found one called "Launcher/Taskmanager" when I added it, the Lauchers came back! The [AWN Wiki]("http://wiki.awn-project.org/Main_Page") doesn't have the name of this applet listed, but when your looking at applets, look for the one that has this Icon:
[IMG]http://wiki.awn-project.org/images/9/91/Avant-window-navigator.png[/IMG]

So even if you have no Applets in use, make sure at least this one is listed. It's apparently needed for Taskbar/Launcher functionality.

---

### Post by Killerah on 2008-02-22
HAHA! You're the man! I feel like an idiot, thanks so much that fixed the whole issue. I can't believe how simple that was.

Thanks again.
Nate

---

### Post by Diabolis on 2008-04-20
In my awn installation the applet was already added, so I removed it and added it again. It kind of refreshed awn and now I have my launchers.

---

