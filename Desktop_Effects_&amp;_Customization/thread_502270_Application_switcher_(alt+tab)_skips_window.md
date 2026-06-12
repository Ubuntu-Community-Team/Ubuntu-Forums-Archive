---
title: "Application switcher (alt+tab) skips window"
date: 2007-07-16
forum: Desktop Effects &amp; Customization
---

### Post by curiousben on 2007-07-16
I have an odd problem. I'm running Ubuntu Feisty and installed compiz as prescribed on the sticky thread [here]("http://ubuntuforums.org/showthread.php?t=481314"). Everything is working great except for the application switcher.

It seems that when I use alt+tab to invoke the app switcher, it skips a window. So if I have two windows visible, the switcher will cycle through only one of them, consistently skipping the next one. This problem is made more apparent when I have three windows. I can tell by the app switcher previews that the windows are cycled in a 1, 3, 2, 1, 3, 2 manner. This is driving me nuts.

Please advise on how I can diagnose and fix the problem. 
Note: the Ring switcher is working fine, and the window order is as expected.

Additional info:

```
$ compiz --version
compiz 0.5.1

$ ps ax | grep compiz
 8886 ?        S      0:00 /bin/bash /usr/bin/compiz --replace -c emerald &
 8887 ?        SL     0:30 /usr/bin/compiz.real --ignore-desktop-hints --replace --sm-disable ccp
10237 pts/0    R+     0:00 grep compiz

```

---

### Post by daveaphillips on 2007-07-16
Weirdly, I am having exactly the same problem.  Any help would be appreciated!!

Cheers,

Dave

---

### Post by Soybean on 2007-07-16
Ah, I had the same problem on *one* of the computers I installed Fusion on. So it's not happening everywhere for some reason. Anyway, what I did was:
-Go into the "Application Switcher" settings in the CompizConfig Settings Manager
-On the "Actions" tab, expand the "General" category (the only one there)
-Note that there are 3 different types of "Next window" and "Prev window", and that two of them are assigned to "Alt+Tab"
-Change one of them to something else.

I think the idea is that you could assign more than one key combination to switching windows... but on some systems, I think it's triggering both events -- 'next window' twice for one keypress. Changing the key binding fixed it for me, anyway.

---

### Post by daveaphillips on 2007-07-16
Thanks for the good advice, but I checked and under my actions tab only one 'next window' had alt+tab next to it, and even if I change it to something random I still get the same problem...

---

### Post by curiousben on 2007-07-16
Thanks for the advice. This worked for me. I actually had three  entries for "Next Window" and three entries for "Prev Window". I disabled all but one of each. 

Best of luck to you, daveaphillips.  Not sure what's different about your environment. Let me know if you have any questions about mine.

---

### Post by crazyhunk on 2007-07-17
have a look here.... they do have a workaround...

[http://forums.opencompositing.org/viewtopic.php?f=49&t=1017&p=8356&](http://forums.opencompositing.org/viewtopic.php?f=49&t=1017&p=8356&)

---

