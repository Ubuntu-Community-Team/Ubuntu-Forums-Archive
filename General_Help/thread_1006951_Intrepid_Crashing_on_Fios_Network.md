---
title: "Intrepid Crashing on Fios Network"
date: 2008-12-09
forum: General Help
---

### Post by Bill Day on 2008-12-09
I seem to be having a networking problem that includes my Intrepid box but also causes problems for the Windows box on the same home network, so I apologize if this is not the right forum, but I am hoping the community can offer me some guidance.

The main problem is that my X server freezes at random times when the system is idle.  I am not able to ssh into the box, restart gdm, or pull up a terminal.  I am *usually* but not always able to restart the box with Alt+SysReq S, U, B.  I have scrutinized the logs and there is no culprit that is obvious to me, but I would be happy to post a portion of whatever log might be relevant.

My box has a static IP of 192.168.1.25.  The DHCP range on my FIOS router is limited to 192.168.1.100-255.  My box is currently configured with /etc/hosts, although I have tried running my own nameserver, with no apparent effect.

For a while I thought BOINC might be a problem because of system load, but uninstalling it had no effect.

For a while I thought temperature might be a problem, but I am carefully monitoring the temperature and it seems to be within a normal range. Besides, the computer normally fails when it is idle, whether I am logged in or not (which makes me suspect that it is not a screensaver issue.)

I have tried compiz on, compiz off, and compiz uninstalled.

I have tried both Hardy and Intrepid -- same problem.  

I have tried gnome-screensaver and x-screensaver.

I have tried resetting the fios router.

At this point, I am flailing more than troubleshooting. If anyone has any advice, I would appreciate it.  I am a basically non-technical person, however, a little better than a newbie.  I will run any test, but if you want me to run a test, please follow Denzel Washington's advice in Philadelphia and explain it to me as though I were a two-year-old.  I am good at following directions, but I usually need directions.

Thanks to anyone who has ideas.

Sincerely,

Bill Day

---

