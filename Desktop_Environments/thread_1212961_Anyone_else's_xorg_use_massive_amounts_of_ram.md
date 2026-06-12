---
title: "Anyone else's xorg use massive amounts of ram?"
date: 2009-07-14
forum: Desktop Environments
---

### Post by corwinspyre on 2009-07-14
I found this thread, but the last post is over a year old, and no solutions are offered: [http://ubuntuforums.org/showthread.php?t=440038&page=6&highlight=xorg+memory](http://ubuntuforums.org/showthread.php?t=440038&page=6&highlight=xorg+memory)

My xorg, as reported by top, reaches 400mb of ram (res, not virtual) probably within an hour of use and always climbs to 700-900mb within a few days of use, at which point I restart because it causes my laptop to heat up and the fan runs loudly as a result.

Here you can see after three or four hours of use (and 15 hours since the last restart) it's already up over 500mb: [img]http://i28.tinypic.com/286y1kp.jpg[/img]

I've really only noticed it in the past few months.  Is this isolated to me?  And is there anything to be done?  Thanks!

---

### Post by PmDematagoda on 2009-07-14
When exactly did this issue start popping up? Did it start as a result of upgrading to a new release, updating packages or suddenly for no reason?

---

### Post by yota on 2009-07-14
Have you got an Intel video card?

I have a (as lspci says) "VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)" and i'm affected by a leakage with EXA rendering as described here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/360319](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/360319)

Switching to UXA helps me a lot, since the system runs fine, but exposes me to [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/356850](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/356850) (which happens quite rarely, but consistently).

Hope this helps!

---

### Post by corwinspyre on 2009-07-14
> **PmDematagoda said:**
> When exactly did this issue start popping up? Did it start as a result of upgrading to a new release, updating packages or suddenly for no reason?

I wish I could be exact, but I'm not entirely sure.  Like I said, it's been a few months anyway, at least since May.  I know it was after 9.04 (which I did a full-install of, not an upgrade).  And I've reinstalled two or three times since (for other reasons) with the same problem.  I figured this was a common problem so didn't post about it until now, but it hit 1.1gb recently, making me suitably annoyed to do some googling.

I should've posted this right away, but I'll mention it now anyway: I'm using an HP tx2500, which uses an ATI HD 3200 card, and I'm using the proprietary ATI driver.  The laptop also has a touchscreen, so I use wacom drivers, too.  And currently I have installed both Ubuntu and Ubuntu Mint 9.04 x86_64 (both have the issue, perhaps unsurprisingly).


edit:
> **yota said:**
> Have you got an Intel video card?

I have a (as lspci says) "VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)" and i'm affected by a leakage with EXA rendering as described here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/360319](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/360319)

Switching to UXA helps me a lot, since the system runs fine, but exposes me to [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/356850](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/356850) (which happens quite rarely, but consistently).

Hope this helps!
Nope, ATI here :(

---

### Post by GeneralZod on 2009-07-14
Installing and running xrestop might help to find the worst pixmap-gobblers :)

---

### Post by raymondh on 2009-07-14
Here's mine (top) for comparison. Running an updated 9.04 on a desktop using an ATI HD2600XT card.

---

### Post by ianmillington on 2009-07-20
I am using Kubuntu 9.04

I have a very similar issue, although not exactly the same, and I think it probably happened when I did the latest kernel update or to KDE 4.3 RC2. Not sure which although using the 28.13 and 28.11 kernels doesn't fix the problem.

Anyway, By about 20/25 seconds I'm at the KDE splash screen. 30 seconds later, I get a black screen with a cursor. Hard drive bangs away for about 20 secs, then I get just the gkrell monitor, interestingly showing the system is using just under 700MB ram at that stage, which is where it stays.

About 20/25 seconds after that, my desktop appears. So the system takes 25 seconds to boot, and about an extra minute to get to the desktop.

Once up and running, it seems Okay. However, running Top shows that xorg is taking up about 25% of my computers memory, about 500Mb in total. Plasma is thrashing the CPU.  Hitting the off button then requires a 30 second wait before anything happens, with python using 100% CPU.  When running gnome - no problems, definitely a KDE issue.

Anyone any clues on how to fix it?

Thanks

Ian

---

