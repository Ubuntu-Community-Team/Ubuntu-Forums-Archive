---
title: "Ongoing, unresolved, common probems with Beryl"
date: 2007-01-20
forum: Desktop Environments
---

### Post by medley on 2007-01-20
Despite what seems like 50 different ways all over the web to get Beryl working, I have as yet been unable to do so. I'm starting YAT (Yet Another Thread) about this because they seem to get old and lose interest/contributions really quickly.

As have many other people experiencing these problems, I  have tried just about every method anybody has mentioned that I can find on the web about what to do. I've been working on this for more than 2 weeks without success (apart from one isolated incident).

My setup:
Kubuntu Edgy (6.10)
Nvidia FX5200 with 97.46 driver
AMD 2400+
780M ram

I have gl acceleration enabled, confirmed by glxinfo. I can also tell by GL-type screen savers and games. I have tried nv's 97.46 driver, as well as one before that (didn't notice the rev). I have also tried at least three revs of Beryl. I have "AddARGBVisuals" set to true and "Composite" set to enable in xorg.conf per the thousands of blogs/posts/wikis I slaveishly followed.

When the 1.99 update came out a couple of days ago, I upgraded and beryl worked. In fact it worked fabulously for several hours. However, when I logged out of the session and restarted, I went back to having the same problem(s) I have been having from day one; ie, the windows have no borders or controls, and Beryl doesn't seem to be working. If I kill off the beryl-manager process and try restarting it from the konsole, beryl crashes with the message "composite manager has crashed twice in one minute and will be disabled for this session". 

I have installed Emerald and Aquamarine. I can run beryl-settings. I also (as in one of the thousands of suggestions) have the option to start beryl as a session type. The behavior seems to be the same whether I start it this way or start it from within a session via konsole (typing 'beryl-manager').

Please help. I know thousands are happily using Beryl, and from what I've seen, it's incredible. I would really like to feel the love as well.

---

### Post by dabl on 2007-01-22
I doubt I can provide anything more than moral support, but I'll share what is and isn't working on my Kubuntu 6.10 system:

Intel x6800 on Intel motherboard, lots of RAM
Edgy 6.10 generic (so it uses the dual CPUs)
Nvidia 7900 GS card
Samsung SyncMaster 1100 CRT

I used Envy to install the Nvidia driver
I used the Nvidia Xserver utility to set the CRT screen resolution and refresh
I installed Beryl last week and it would NOT work reliably
I updated Beryl on the weekend -- I think it is ver. 0.2.0 (I'm away from my system)
I updated Aquamarine over the weekend.

As of last night, Beryl seems to be working great, but Aquamarine still crashes pretty much every time I try to use it.  The Emerald windows decorator seems to be fine, so that's what I'm using.  So it looks to me like the KDE+Beryl+Emerald is kinda stable at this point, but Aquamarine is still the bad actor on my system.

Hope this provides encouragement, at least.  :D

---

