---
title: "EEE Box on Ubuntu 8.10 Locking Up"
date: 2009-03-01
forum: General Help
---

### Post by campbecf on 2009-03-01
I have a EEE Box running Ubuntu 8.10. It has been locking up to a 'tan'-ish screen. By using ctrl alt and the number keys or whatever I can get out to a console and use that just fine.

Attached should be the Xorg log, it has a lot of these lines:
(EE) intel(0): underrun on pipe A!

Anyone help? If you need more information I will gladly post it.

This seems to be a similar problem:
[http://bbs.archlinux.org/viewtopic.php?id=60705](http://bbs.archlinux.org/viewtopic.php?id=60705)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/311895](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/311895)

---

### Post by sgosnell on 2009-03-01
I'm far from an expert, but it looks like it's choking on your video card.

---

### Post by campbecf on 2009-03-02
How do I fix "choking on your video card" errors?

Ive updated the main post with this link, but I will put it here too. This seems to be a similar problem: [http://bbs.archlinux.org/viewtopic.php?id=60705](http://bbs.archlinux.org/viewtopic.php?id=60705)

---

### Post by sgosnell on 2009-03-02
Sorry, no idea.  This seems to be a rather deep problem, and the link mentioned problems with several distros.  Perhaps deeper Googling will turn something up.

---

### Post by campbecf on 2009-03-03
This didn't seem to be happening for us until Jan/Feb area, maybe something was pushed into the updates that is causing it?

---

### Post by campbecf on 2009-03-04
Can anyone give me some direction on this issue? Would downgrading help? Should I switch to a different distribution?

---

### Post by campbecf on 2009-03-07
This is still a problem, the computer has been virtually unusable for the past few weeks. My research online suggests that this may be a more widespread Linux problem so switching distributions probably won't help.

If the problem persists and I can't find a solution we are going to have to buy a copy of Windows XP and try our luck with that, which I would rather not do. It is a lot easier to manage the security of the computer if it is not a windows environment.

---

### Post by raghu1111 on 2009-03-09
Could you try the workaround of disabling "FramebufferCompression" as suggested at [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/311895/comments/14](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/311895/comments/14) . I am currently  using this workaround with my Eee Box.

I am not familiar with internals of X drivers. I am not exactly sure if this is same as spontaneous black screen described in the above bug. Because the the "black screen" problem always existed with 8.10 (possibly earlier versions too).

---

### Post by campbecf on 2009-03-09
I have disabled all desktop effects, we haven't had the problem occur for the last 1~2 days. I will post back in a few days if it seems like that has fixed it.

---

### Post by campbecf on 2009-03-16
It has not had this problem reoccur since disabling desktop effects. It's still odd that this problem only started to occur recently - the hardware should be able to handle the effects.

---

