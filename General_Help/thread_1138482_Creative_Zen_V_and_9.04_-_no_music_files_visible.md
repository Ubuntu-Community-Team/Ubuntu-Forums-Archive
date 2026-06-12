---
title: "Creative Zen V and 9.04 - no music files visible"
date: 2009-04-26
forum: General Help
---

### Post by tarniak on 2009-04-26
I'm glad that they thought of MTP support for mp3 players in 9.04, but apparently something is really messed up. Up to now, I have used gnomad2 to transfer audio to my Creative Zen V player. 

The problem is that even though the player mounts perfectly, and is browsable via nautilus, files are not detected by the ZEN firmware. Gnomad, however, doesn't detect the player any more. Has anyone encountered such a problem?

Best regards and thx in advance.

---

### Post by moon82 on 2009-04-27
I'm having the exact same problem. I tried all tagging programs available in the repos, but the files still don't show in the player. When I re-tag them in foobar (windows) it works... :confused:

---

### Post by mect on 2009-04-27
I think the problem is related to interference between mtp and ums mode.  While I didn't fully understand it, there's more information about the problem here.
[https://bugs.launchpad.net/ubuntu/+source/libmtp/+bug/139649]("https://bugs.launchpad.net/ubuntu/+source/libmtp/+bug/139649")
It did help me figure out a way to get around the problem.  Plug in the device, and then when the icon shows up on the desktop, unmount it.  Then open gnomad, and it should detect it (did for me).  Hopefully this helps.

---

### Post by tarniak on 2009-04-28
Workaround works great. Thank you. Seems like we'll just have to wait a little longer for proper MTP support.

---

### Post by TusharG on 2009-05-05
This issue is due to 2 application trying to take hold on one interface. You just need to unmount it incase if you wish to access it from GNomad2, or you can now directly browse the entire device file system. 

Here is the link of my blog where I have explained how I'm managing my Zen with Banshee and other apps really well.

[http://tusharg.blogspot.com](http://tusharg.blogspot.com)

---

### Post by ivago on 2009-05-11
thanks for this awesome tip, 've been (re)compiling libmtp and gnomad2 for a week before I noticed this post and was almost planning to downgrade back to my 8.04 system.

Anyway hope they fix this problem sson because this is a specific ubuntu bug

---

### Post by Elep.Repu on 2009-08-06
Workaround *doesn't* work great. Transfers over, but doesn't show,
also I think we shouldn't be limited to using banshee to transfer over.
Especially if I have all the right mtp stuff installed...

---

