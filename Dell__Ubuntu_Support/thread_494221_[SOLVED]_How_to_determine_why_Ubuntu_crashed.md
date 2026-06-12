---
title: "[SOLVED] How to determine why Ubuntu crashed?"
date: 2007-07-06
forum: Dell  Ubuntu Support
---

### Post by xluryan on 2007-07-06
Hey, I have a question...

When I leave my Dell laptop alone for 2 days or so, I usually come back to find it sitting at a black screen, fan spinning, and unresponsive to ANY type of peripheral activity.

Moving the mouse does nothing, pressing any key or key combination does nothing.

I hold the power button down to shut it off, reboot, and it's fine.

Where would I start looking to find the root of this problem?

---

### Post by neptho on 2007-07-06
Try turning off all DPMS (screen savers, blanking, etc), and look at your last system log and dmesg:

```
%zless /var/log/syslog.1.gz /var/log/dmesg.1.gz
```

---

### Post by punkybouy on 2007-07-07
Sounds like its going into standby mode.  I believe there are settings for that under the System\Administration menu.  I have Dapper running on an Inspiron 8200 and it goes into and comes out of standby mode just fine.  Could it also be your CPU is over heating and the bios is shutting it down?  If you have a screen saver that requires a lot of processing it could be overheating the cpu.

---

### Post by xluryan on 2007-07-07
It's definitely not a standby issue. I press the power button and nothing comes back.

I'm using the Matrix screensaver that comes with Gnome. Average CPU usage for that is around 1-5%. CPU core is still running at normal temperature.

BIOS is up to date, and when my Intel chip overheats the computer just turns off. But it's not turning off, it just sits on a black screen, still turned on.

After examining the system and dmesg logs I think I've found the problem. For some reason my External NTFS HDD was being remounted in RW mode, instead of RO. The write-protect was turned off. I don't have any type of NTFS writing libraries installed, so there would be major problems if my Ubuntu was trying to write to that HDD. I've unmounted it, so I'll let my computer go for a few more days and see if that does it.

Thanks for your interest in this post!

---

### Post by LostInTheSnow on 2007-07-08
So, did that do it? Just curious whether it was indeed a remounting issue.

---

### Post by xluryan on 2007-07-08
Well I had to restart it several times last night as I was working on some bluetooth stuff. It usually takes a couple of days without touching it to determine if it's gonna freeze or not. So as soon as I can determine that I'll definitely post back :)

---

### Post by xluryan on 2007-07-16
Well, I just went back to my place the other night to find my laptop sitting at a black screen. The external HDD has been turned off, so that's obviously not the cause. The next thing I'm going to look at is the power manager.

---

### Post by motin on 2007-07-16
> **xluryan said:**
> Hey, I have a question...

When I leave my Dell laptop alone for 2 days or so, I usually come back to find it sitting at a black screen, fan spinning, and unresponsive to ANY type of peripheral activity.

Moving the mouse does nothing, pressing any key or key combination does nothing.

I hold the power button down to shut it off, reboot, and it's fine.

Where would I start looking to find the root of this problem?

Check this thread out: [How do I look under the hood?]("http://ubuntuforums.org/showthread.php?t=409734") to answer your general question.

---

### Post by xluryan on 2007-07-17
Ok well, I've made progress and started a new thread. Please check it out at the following address:

[http://ubuntuforums.org/showthread.php?p=3036485]("http://ubuntuforums.org/showthread.php?p=3036485")

---

