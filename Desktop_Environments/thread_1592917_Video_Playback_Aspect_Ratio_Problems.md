---
title: "Video Playback Aspect Ratio Problems"
date: 2010-10-11
forum: Desktop Environments
---

### Post by Shibblet on 2010-10-11
I have noticed when I go to play any video in SMPlayer, and Gnome Mplayer with Ubuntu 10.10, the aspect ratio is off.

Is this bug known?

---

### Post by Shibblet on 2010-10-11
Well, I have looked further into the problem, and it seems that videos that have an aspect ratio that doesn't fit the pixel count is what is playing back wrong.

I learned this a long time ago with DVD's.  DVD resolution is 720x480.  Correct pixel resolution for 16:9 would be 854x480.  Correct pixel resolution for 4:3 would be 640x480.  That means by design, DVD's were not set up at the proper aspect ratio.  

Fortunately Blu-Ray's are, at 1920x1080, and 1280x720.  Both of these aspect ratios are perfect for 16:9.

So, back to the original problem.  My video files that are 720x480 are playing back over stretched wide if they are 16:9, and tall and skinny if they are 4:3.

I did not have this problem with 10.04.

---

### Post by snowy16 on 2010-10-18
I'm having the same problem after upgrading to 10.10.  Anybody have any ideas.

---

### Post by Shibblet on 2010-10-19
> **snowy16 said:**
> I'm having the same problem after upgrading to 10.10.  Anybody have any ideas.

It's Mplayer.  I switched to VLC Player.

---

### Post by snowy16 on 2010-10-20
I'm having the same problems with VLC.

---

### Post by GribbleMR2 on 2010-11-26
I am having this problem as well.  It is occurring in VLC, Totem, and Banshee.  I have been using Ubuntu since 8.10, but did not encounter this problem until I got 10.10.  I also upgraded my graphics card when I upgraded to 10.10 (Radeon HD 5670) and installed the proprietary drivers.

---

### Post by Pitje99 on 2010-12-04
I am having this problem as well. It is occurring in all players. Evera slideshow I have burned hat the wrong aspect ratio. No ideas?

---

### Post by Shibblet on 2011-03-22
4 Month - Bump

---

### Post by Shibblet on 2011-04-04
Well, it seems as if it is just SMplayer or Mplayer in general.

Can anyone please shed light on this situation.  The only way I can get away from screen tearing is to use VDPAU, and VLC doesn't do it.

Here is a screenshot of what I mean.
[ATTACH]188079[/ATTACH]

---

### Post by Shibblet on 2011-05-02
Same issue with Natty.

---

### Post by Shibblet on 2011-05-10
Well, just for defication and giggle, I decided to try an MKV file instead of an MP4...

Lo and behold Mplayer's aspect ratio was spot on.  So then I decided to encode my own MKV with an odd Pixel count, but correct aspect, and it works just FINE!

So, seems as if the problem is the way Mplayer uses MP4.  Or maybe the way MP4 reports the aspect... I don't know...  All I know is that I should have been using MKV from the beginning.  :P

---

