---
title: "video no longer mapped properly in beryl"
date: 2007-07-21
forum: Desktop Environments
---

### Post by roboknight on 2007-07-21
Hello,
This is my first post to an Ubuntu forum.  Used to use FC6, but found Feisty a much cleaner, better install.  Things just work here.  Or at least most of them did.  I have a curious problem that I cannot find an answer to.  When I first installed feisty, it detected my ATI radeon 9200 and installed the proper drivers just fine.  At least I thought so.  I went on from there to install Beryl and everything seemed fine.  In fact, everything went so well I moved on to install the drivers for DVD playback.  Eventually I had everything up and running and I even took a desktop snapshot of Robert Redford in "The Natural" running on the side of the Beryl desktop cube.  It was a neat shot.  Then I started fiddling with GNU chess and found out I was missing stuff for the 3d to work properly.  So I installed it.  In that process, I somehow got off on the wrong track and started fooling with the fglrx drivers for the radeon.  Found out they don't work for the 9200 anymore unless you go to edgy and use an older driver.  That is fine, because I don't really want to use them.  So I eventually got myself back to the open source ATI driver.  However, NOW, anytime I play a video, it doesn't "move with the window" and it no longer plays nicely on the side of the cube.  If I move mplayer or any other player for that matter, while the video plays, the video stays in one spot until the window is dropped.  Plus the video is "jumpy" meaning it doesn't play smoothly.  That may be due to my slow machine (1.5 GHz Celeron combined with the ATI 9200, so beryl might not run all that well, although the "spinning desktop" spins fast enough if I don't use the skydome)

So my question is:  Has anyone else seen this?:?:  Is there a fix?  I had it working at one time, so I figure it works, but I don't know what I broke, so I decided to turn to the ubuntu forums to find out if there is something I need to check.  Thanks for reading my post.

roboknight.

---

### Post by roboknight on 2007-07-22
Quick note:  I fixed the DVD speed playback issue.  That appears to have been some settings for the ATI driver to speed things up (I think particularly triple buffering, but not sure.).  I also wanted to attach the screen shot so that you can get a better idea of what I mean.  There's Robert Redford, there on the side, the picture visible.  However, now, anytime either the window or desktop move, the video doesn't follow the display area.  Instead it looks like it remains "behind" its window and as the window moves, it gets clipped.  I don't know how it worked before.  Maybe it is the 3d stuff I added for GNU chess?  I wouldn't think so, but maybe it affects 2d displays in some way as well as 3d displays.  Some kind of clipping feature?  Anyway, I just wanted find out because if that is it, then I can get rid of it as GNU chess 3d doesn't really work.  The 3d display "vanishes" behind an empty 2d display.  That is one of the reasons I thought it might be related.  But before I get rid of it, I thought I would see if anyone else had an idea as to the cause.

---

