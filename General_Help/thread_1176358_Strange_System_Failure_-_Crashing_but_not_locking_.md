---
title: "Strange System Failure - Crashing but not locking up"
date: 2009-06-02
forum: General Help
---

### Post by RobOrr on 2009-06-02
Hi all,
My system keeps failing with no apparent cause. I almost always have rhythmbox playing and firefox open on my PC (they're its main uses), audio will continue to play, most applications will continue to open, but firefox will not let me do anything other than browse currently opened tabs (changed website or opening new tabs won't work, and closing it crashes firefox).

 System monitor won't open and so I restart X with log out or Ctrl-Alt-BkSp.  X kicks me out to the login screen, all well and good.  On logging in after resetting X my usual startup programs switch on (Sunbird and Screenlets) but my panels do not appear. I cannot bring up a command line (Alt-F2 also doesn't work) and restarting X and logging in again returns the same result, so I have to hard reset to get my computer functional again.

 I've had this problem very occasionally for a while now, although over the past week it has become an endemic problem for my computer (has happened 4 times in the last hour) and is making me pull my hair out. Has anyone heard / experienced this before? and does anyone have any inkling on whether this is a hardware or a software fault?   The System Logs (from the System>Administration menu) that I have checked report nothing abnormal around the time that the error occurs, if there are other logs I can check please let me know.  Thanks for your consideration.

---

### Post by pedro_orange on 2009-06-02
I presume you're using 9.04 (Jaunty) ? 

I had this problem using Jaunty, with xserver crashing for random reasons. I think it did not like my nvidia driver. After pulling alot of hair, I decided to roll back to my Hardy install & all is well.

However, if you want to fix your install you'd need to check your xorg.conf, xorg.0.log and dmesg logs to see if you can identify if it's hardware or software, and also what's causing it to crash.

---

### Post by RobOrr on 2009-06-05
I'm running Intrepid. Jaunty doesn't support my card (Radeon X700) on the proprietary drivers.

xorg.conf hasn't changed in about 3 months, checked against my last couple of backups of it. 
xorg.0.log has nothing out of the ordinary when this happens as well.

I haven't checked the dmesg log before, will have to wait until it goes mental again. I've had the entire day without any problems today. typical random failures...

---

### Post by RobOrr on 2009-06-19
dmesg.log has nothing out of the ordinary. This bug in all likelihood has something to do with compiz, as my computer has been running perfectly for 2 weeks now with compiz disabled.

---

