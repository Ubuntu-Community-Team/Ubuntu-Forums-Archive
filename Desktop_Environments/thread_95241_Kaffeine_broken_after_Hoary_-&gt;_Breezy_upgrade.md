---
title: "Kaffeine broken after Hoary -&gt; Breezy upgrade"
date: 2005-11-26
forum: Desktop Environments
---

### Post by pestie on 2005-11-26
Every time I try playing any type of video in Kaffeine, I get an error message saying "There were no decoders found to handle the stream, you might need to install the corresponding plugins." I noticed that Kaffeine is now using something called the Gstreamer engine, which I'm not familiar with, so I installed Kaffeine-xine, and switched to the Xine engine. That made things a little better, but not much. Now I get video, but no audio, and every time I click the "Open" button, Kaffeine dies with a segfault.

Is this perhaps because I had, under Hoary, installed another Kaffeine .deb? Kaffeine was horribly broken under Hoary and didn't get fixed, so someone here created a .deb with a fixed version (details [here](http://ubuntuforums.org/showthread.php?t=27670)) which worked great. But now everything's gone completely to hell since I upgraded and I can't figure out what's going on. Anyone have any suggestions? A simple reinstall didn't help.

---

### Post by daller on 2005-11-26
[QUOTE=pestie]Every time I try playing any type of video in Kaffeine, I get an error message saying "There were no decoders found to handle the stream, you might need to install the corresponding plugins." I noticed that Kaffeine is now using something called the Gstreamer engine, which I'm not familiar with, so I installed Kaffeine-xine, and switched to the Xine engine. That made things a little better, but not much. Now I get video, but no audio, and every time I click the "Open" button, Kaffeine dies with a segfault.

Is this perhaps because I had, under Hoary, installed another Kaffeine .deb? Kaffeine was horribly broken under Hoary and didn't get fixed, so someone here created a .deb with a fixed version (details [here](http://ubuntuforums.org/showthread.php?t=27670)) which worked great. But now everything's gone completely to hell since I upgraded and I can't figure out what's going on. Anyone have any suggestions? A simple reinstall didn't help.[/QUOTE]

What audio and video-driver have you chosen?

---

### Post by pestie on 2005-11-26
I'm not sure it matters at this point. After some more digging, I found [this thread](http://ubuntuforums.org/showthread.php?t=78785), which leads me to believe that installing Kaffeine from the repositories is a total waste of time. I've just given up and switched my preferences to VLC, which is a slick piece of software, but a little ugly due to the lack of anti-aliased fonts (at least under KDE - I haven't tried it in Gnome). I might just uninstall the Kaffeine package and compile from sources at some point, but for now, at least I can play video files and DVD's with VLC.

---

### Post by palsyboy on 2005-11-27
I've been having the same problem for weeks now and for the same reasons.  I even found the same semi-solution of using MPlayer for .wmv files and VLC for everything else.

daller: How would I check to see which drivers I've chosen?  Thanks.

---

