---
title: "Strange Display Behavior"
date: 2008-11-04
forum: Desktop Environments
---

### Post by Max Roswell on 2008-11-04
I upgraded to Kubuntu 8.10 over the weekend.  It intially looked exactly as advertised, but now when I boot up, about 2/3 of the time, I get something that looks like this:

[IMG]http://farm4.static.flickr.com/3146/3001721549_3c0bf6b631.jpg[/IMG]

[IMG]http://farm4.static.flickr.com/3224/3001721943_2c657cc38c.jpg[/IMG]

[IMG]http://farm4.static.flickr.com/3026/3001722231_7e019a1acf.jpg[/IMG]

Please note: I haven't made any changes to the default desktop wallpaper setup.  Those concentric black circles should NOT be there.  

And for what it's worth, here's a graphic I got at the exact same time using KSnapshot.  For whatever reason, it looks normal - so my eyes are seeing something different than my machine:

[IMG]http://farm4.static.flickr.com/3146/3001731371_c475efb6f5.jpg[/IMG]

Does that make any sense to anyone?  Where should I be looking to try to fix this?  It only happens sometimes, and I'm not sure why or when it will.

---

### Post by Max Roswell on 2008-11-07
Just bumping this to see if anyone has any ideas where to start looking.  I had some success by jumping back to an older kernel, but as of today, the problem happens there, too.

If anyone has any suggestions as to which logs or settings might be the place to start investigating, I'd appreciate it.  Maybe something so I can compare when it works to when it doesn't?

---

### Post by dabl on 2008-11-07
Well, since no one else will venture a guess, I'll toss one out.

I'm thinking it is related to your display (the monitor/LCD/CRT) and not the graphics card or the graphics driver.  I think ksnapshot captures the digital image from the graphic card's output, which SHOULD match what is on the display screen, but apparently is not in your case.

How to investigate further?  Another monitor would be really handy!  Otherwise ... hmmmm -- kind of a challenge.

---

### Post by iponeverything on 2008-11-07
pretty strange.

open a terminal type "xwininfo" hit return on click on the background.

Do it for the normal and the funky one.

Also get a  diff for normal and funky /var/log/Xorg.0.log.

what is the video interface?

For the sake of testing, you just use the VESA driver to see if it is a driver related issue.

---

### Post by Max Roswell on 2008-11-07
It's just a SIS M760GX integrated graphics card on a fairly cheap laptop (I think; will double-check when I get home).  I'd think it was an LCD problem, except (a) it doesn't happen at all when I boot into Windows, (b) it never happened until I upgraded to 4.1, and (c) the Kubuntu loading screen looks fine - once X starts up, you can see the screen flicker a bit, and then the login screen with the f'd up background shows.

I'll check those logs/commands and post the output here once I get back to mi casa.

---

### Post by Max Roswell on 2008-12-27
Sorry for the thread necromancy - I've only just had time to sit down and start trying to fix this.  I'm making no progress, and figure I'm just going to dump Kubuntu.  It's so frustrating...I've been almost exlusively using *buntu for over 3 years, and now my machine's pretty much unusable.

Anyway, here's the output of xwininfo:

> xwininfo: Window id: 0x1e0006c (has no name)

  Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 1280
  Height: 800
  Depth: 32
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x1e00001 (not installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+0  -0+0  -0-0  +0-0
  -geometry 1280x800+0+0

That's under the funky display.  I can't post a differential from the normal display because I can no longer get a normal display.

I've opened up xorg.conf, but there's very little info in there.  My limited understanding is that KDE 4.1 doesn't really use it much anymore.

Anyone have any ideas before I dump Kubuntu?

---

### Post by Max Roswell on 2008-12-27
Never mind.

This thread:
[http://ubuntuforums.org/showthread.php?p=6068699](http://ubuntuforums.org/showthread.php?p=6068699)

seems to have fixed the problem.

---

