---
title: "Can't move mouse between screens--3 monitors w/bezel compensation"
date: 2012-04-13
forum: Desktop Environments
---

### Post by zbuffered on 2012-04-13
Hi folks, I have a bit of a unique setup.  I have three 1080p monitors mounted side-by-side in portrait mode attached to an ATI 5870 eyefinity 6 video card.  I've had some success setting this up (and I'll post details for others), but I need help in a few areas as well.

I've got a new install using Ubuntu 12.04 Desktop, Beta 2.  I had the first issue in 11.1 and now with Precise, the second issue below as well.

With the [_fglrx driver installed_]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"), I've had all three screens working in 11.10 with the following [_xorg.conf_]("http://paste.ubuntu.com/928594/").  Note that the width is 3596 and not 3240 (1080 * 3).  The monitors are separated by 178 pixels on the virtual screen. This compensates for the bezels on the monitors.

With the above configured, I could fullscreen a video in 11.10 and it would stretch across three screens, with some of the video "hidden behind" the bezels which maintains continuity in the displayed video.  In Windows this technique is called "Eyefinity" or "single large surface".  [_Here is a page_]("https://sites.google.com/site/brandtwesting/test/untitledpost") which provides insight into this if you're confused by the concept.

**[SIZE="2"]Problem[/SIZE]**
With the bezels turned on, I can't move the mouse off of the first monitor.  However, if I connect the Ubuntu machine to another one using synergy, I can move the mouse across monitors using the external machine.  If I use an alternate [xorg.conf setup with no bezels]("http://paste.ubuntu.com/928488/") built in, moving the mouse between monitors works fine, but then of course the gaps between monitors are not compensated for.

**[SIZE="2"]Problem 2[/SIZE]**
In 11.10, I was able to get applications to maximize across three screens by [_using these instructions_]("http://askubuntu.com/questions/73573/how-to-maximise-a-window-across-two-monitors"); going into CompizConfig Settings Manager, under General Options -> Display Settings, disable "Detect Outputs" and edit "outputs" to: 3596x1920+0+0.  If "Detect Outputs" is left on, an application will full-screen to just one monitor.  Now in 12.04 this doesn't seem to have an effect (applications will maximize/fullscreen to only one screen, won't span all three).  This still persists when I use the xorg.conf with no bezels.

Advice is greatly appreciated.  I am resolved to get my virtual window up and running!

---

### Post by zbuffered on 2012-04-17
Since I haven't gotten any responses, what about this option:

Instead of having space between each monitor, what about configuring "dummy" monitors to fill the space?  A 173x1920 "screen" using the "dummy" driver (xserver-xorg-video-dummy)?  It seems like that should work.

[http://blog.mediafederation.com/andy-hawkins/ubuntu-headless-vnc-vesa-800x600-fix/]("http://blog.mediafederation.com/andy-hawkins/ubuntu-headless-vnc-vesa-800x600-fix/")

I'll try it and let you know ):P

---

### Post by zbuffered on 2012-04-25
So, I've given up on the ATI card.  The drivers just aren't "there" for what I'm looking to do.  

Using the fglrx driver, I was able to get things to work almost 100% but the video playback was not smooth.  Whether I was playing a large or small file, I wouldn't get every frame and it was problematic for me.  I'm sure I could have tried more things but I instead went for the radeon driver.

With the radeon driver I was able to get it to work as well using a different xorg.conf setup, ultimately however the video performance was much worse with high-resolution Apple ProRes 4:4:4 video, and so I abandoned that one.  Video tearing was prevalent as well and with reports of others on #radeon having this problem, I had to give it up.

I switched to using two nvidia cards and xinerama, and although I'm not able to maximize across all three screens yet, the video playback is flawless.  I've definitely traded one problem for another now, but having a new and different problem is at least some kind of progress.

---

