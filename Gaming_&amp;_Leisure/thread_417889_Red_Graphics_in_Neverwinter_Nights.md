---
title: "Red Graphics in Neverwinter Nights"
date: 2007-04-22
forum: Gaming &amp; Leisure
---

### Post by JNowka on 2007-04-22
I have just installed Feisty, and I installed Neverwinter Nights.  When running NWN everything is fine until I load up a module.  From there all the graphics in game are red in color unless I zoom in a bit.  Anyone have a clue?

---

### Post by leech on 2007-04-23
I'm going to hazard a guess here and say you have ATI hardware?  I've played it on my Feisty installation and it has never turned red on me.  But I always stick with nVidia, since their drivers aren't crap.  With ATI's drivers, it's always a hit and miss with many things.

Leech

---

### Post by JNowka on 2007-04-23
Actually I have the Intel 945GM graphics set.  I went for open source all the way.  I had perfect colors on this game under Edgy on this laptop, but now I don't.  I have the memory set to 128mb.  I just can't figure it out.  I have already tried changing all the video settings to see if that would help to no avail.  Any toughts?

---

### Post by jackliddlephysics on 2007-04-24
I have the same graphics set up as you (Intel 945) and have also installed Feisty from fresh copied my nwn install from my external hd.

Except my graphics have gone green unless I zoom in a little bit.

All we need is someone with slightly blue graphics and were laughing!

---

### Post by JNowka on 2007-04-24
LOL, Yep that is the truth man.  I just hope this crap can be fixed

---

### Post by JNowka on 2007-04-26
I have tried to install several xserver-xorg-video-i810 graphics drivers.  They all produce the same error.  Graphics drivers tried:

Edgy
Feisty
Current Debian Stable

I have also tried the xserver-xorg-video-Intel graphics driver.  It also produces the same error.

If I didn't know better I would say it is the video card.  Problem is that I played the same game on Edgy with no problems.  I could also assume that it is the xserver or that it is the game itself.  But only Intel cards are being affected.  Current list of problems either reported by others or experienced myself.

Graphics are red.
Graphics are green.
Graphics are as if a very bright light is being shined on them.

As I discover more I will post here.

---

### Post by steve0921 on 2007-04-28
I too am having this trouble (the lighting is extremely exaggerated). It was fine before upgrading to feisty.

According to [this bug]("http://bugs.freedesktop.org/show_bug.cgi?id=10529") it appears as though it might be a mesa problem. I'm not sure if there's anything to do but wait for an update/fix.

---

### Post by the8thstar on 2007-04-28
I'm having the same problem with my Intel 945M here and my graphics are orange. About the link provided by Steve0921, if anyone can make sense of what it says, let me know. :confused:

---

### Post by the8thstar on 2007-04-28
What about wine nwn.exe -opengl ?

---

### Post by JNowka on 2007-04-28
I have tried nwn using wine, and because wine uses the opengl mesa drivers to display the game, the problem is not fixed.  

As for the link, basically what it is saying is
1)There was a fix from the previous version of the mesa driver to this one, concerning the fog generator.  This fix has some way effected NWN.

2)The intel video drivers fog code is deprecated, and needs to be updated.

3)If a fix is not found soon, then the new mesa driver will come out without a fix.

4)Because the new xserver requires the newer mesa driver, it is impossible to install the previous mesa driver as a workaround/fix without installing an older xserver, and gods know what else.

Basically, if a fix isn't found soon, we are screwed for a few months.

---

### Post by JNowka on 2007-04-28
Actually, it might be possible to just install and older mesa driver.  You would just have to live with a bunch of upgradable files.

---

### Post by the8thstar on 2007-04-29
Thank you for your  excellent diagnosis, **JNowka**. We'll see how the issue is resolved.

I was wondering, do players have this issue with NWN when playing in native mode?

---

### Post by JNowka on 2007-04-29
Yes these issues are affecting both the native and wine installed nwn.

---

### Post by JNowka on 2007-04-29
For a fix to this issue please follow this link.
[http://ubuntuforums.org/showthread.php?t=427500](http://ubuntuforums.org/showthread.php?t=427500)

---

