---
title: "Unity loads, but does not display properly"
date: 2011-04-21
forum: Desktop Environments
---

### Post by Funnyguts on 2011-04-21
A few nights ago I upgraded from 10.10 to 11.04, and discovered that Unity will load but will not display correctly. The panel and launcher are not visible, but are still loaded. Everything looks to be completely transparent. I can click on the panel and see the menus from the appindicators, but I can't actually see the indicators. I can click on the upper left part of where the launcher should be and bring up my home folder, but again, I can't actually see the launcher. I have no idea whether the dash is working or not.

I tried using 'unity --replace' and turning Unity off and on in CCSM, but neither helped. I made sure that the panel is on full opacity in CCSM too. I did not see this problem here or on Launchpad, so I'm hoping this new thread will help. (Everything else works really well, including Classic Ubuntu, Unity is the only problem I'm having with Natty.)

---

### Post by kamembe on 2011-04-23
Sounds like I'm having the same problem.

I also upgraded (online) from Maverick to Natty beta 2.

Running on i386 Pentium 4, with NVidia fx5200 proprietary drivers. Again, wallpaper loads, but no panels or anything else..

However, I have something else slightly strange. It seems to go into a loop  trying to display icons. They pop up, then they jump slightly left, then slight up then disappear again. Clicking makes no difference. I have to go to another terminal and restart to get out (as even Ctrl-alt-del doesn't do anything for me)

Classic desktop works fine (am posting from that)

Thanks

Rob

---

### Post by iz0ndg on 2011-04-23
> **kamembe said:**
> Sounds like I'm having the same problem.

I also upgraded (online) from Maverick to Natty beta 2.

Running on i386 Pentium 4, with NVidia fx5200 proprietary drivers. Again, wallpaper loads, but no panels or anything else..

However, I have something else slightly strange. It seems to go into a loop  trying to display icons. They pop up, then they jump slightly left, then slight up then disappear again. Clicking makes no difference. I have to go to another terminal and restart to get out (as even Ctrl-alt-del doesn't do anything for me)

Classic desktop works fine (am posting from that)

Thanks

Rob

Hi, I have the same problem, same graphic card and same cpu.

the Xorg.log reports:
Warning: Xalloc: requesting unpleasantly large amount of memory: 0 butes.

Compiz is load, seems to be a Unity Bug.

Help!

Thanks.

Fabio

---

### Post by kamembe on 2011-04-23
Have taken a video of it happening on my desktop - it's a bit of a strange effect to describe, so I thought a picture might say a thousand words. If it's helpful, good. Sorry about the video quality.

It's here:

[http://www.mediafire.com/?xa6d7f2rnfd2qgh](http://www.mediafire.com/?xa6d7f2rnfd2qgh)

Also, as shown in the video, I noticed that if I'm really quick, and I manage to double-click one of the icons, it opens, but the window that is opened also starts flickering in and out of view.

Cheers

Rob

p.s. Thanks for all the effort in making Ubuntu truly great - I'm convinced  these are short-term teething problems, and I'm happy as larry with  Ubuntu in general :)

---

### Post by KegHead on 2011-04-23
Hi!

Just a thought;

1. Do you have a top panel..if so system..admin..login

2. You can select a default. (classic, etc)

3. Can you post "top"?

KegHead

---

### Post by iz0ndg on 2011-04-24
My  problem is exactly equal to that of Kamembe (thanks for the video !), everything works fine with  the Classic, I also loaded unity2d and also works well with this. It looks like a problem between unity/compiz  and the Nvidia driver (173.14.30).

Any ideas?

---

### Post by kamembe on 2011-04-24
Is this is what you were looking for. It's the menu I get in the System > Admin > Login screen dialog for classic.

(The top item for me is 'user defined')

Thanks

Rob

---

### Post by KegHead on 2011-04-24
Hi!

Yes, you can select classic from your screen if you wish.

"top" is a terminal command.

KegHead

---

### Post by iz0ndg on 2011-04-24
'Ubuntu' (unity) state:

top.txt -> top command in terminal
ps_fax -> ps fax command in terminal

---

### Post by r1chard on 2011-05-02
I've pretty much the same issue as the original poster, so bumping this topic.

As with video from original poster, kamembe, X loads, wall paper loads, some flashing of desktop icons and items in my start-up session every few seconds, but no unity interface.

X.org.Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.

And this in my kernel log:

compiz[27387]: segfault at 34 ip 00bf5d75 sp bfdb9fd0 error 4 in libnux-graphics-0.9.so.0.942.4[b5c000+cd000]


Again in common with kamembe, Graphics card NVIDIA GPU GeForce FX 5200.

I suspect the ancient NVidia 5200 card with the NVidia 173 driver may cause this issue, there's a bit about this error with Compiz on the net.


-Richard

---

