---
title: "High CPU usage in kaffeine"
date: 2006-07-19
forum: Desktop Environments
---

### Post by nuxed on 2006-07-19
I have recently bought and installed a DVB-C Card (a Terratec Cinergy 1200). It works fine and I'm able to watch TV almost flawlessly - there is one problem though:

When I use kaffeine (package version 0.7.1-1.3ubuntu10) to watch DVB (using the xine engine), the CPU usage is usually 90% or higher. Sometimes, the picture even "stutters" or stops for a second or two and I get a load average of 2.0 or more.

The problem does not occur when using mplayer or xine (using xine-ui) to watch, CPU usage then is between 5% and 20%. Anyone know what could be the cause of this, or how I could solve this problem? If there was a different DVB-capable media player, I'd use that too (mplayer and xine-ui don't cut it here because there's no way to list and switch channels).

---

### Post by colsinc on 2006-10-30
Well, I see you posted this a long time ago, so hopefully you have found the problem, but if not, check you deinterlacign settings (in Kaffeine, Player>Video>Deinterlace Quality)  some of those settings can really chew up the CPU.

---

### Post by joutsa on 2006-11-19
I think this is more a DVB problem.

I have the same Terratec Card and I get 80% cpu usage even when recording the broadcast to disc with playback stopped. Watching the broadcast gets 100% CPU and dropped frames whenever something else happens on the computer. On the other hand, when playing back the recorded show with same interlace settings, I get CPU usages around 20%.

The problem is probably in Kaffeine rather than DVB driver since Xine and MPlayer can play DVB streams without excessive CPU usage.

This Dapper with Kaffeine 0.7.1.

---

### Post by mtron on 2006-11-20
Try the 0.8.2 kaffeine package for dapper i posted in this thread:[http://ubuntuforums.org/showthread.php?t=275365](http://ubuntuforums.org/showthread.php?t=275365)

many user reported that it works good. if you like more "edgy" software, give the [0.8.3svn package]("http://mtron.co.nr/kaffeine_0.8.3svn-ubuntu1_i386.deb") for dapper a try.

hope it helps! 

cheers!

---

