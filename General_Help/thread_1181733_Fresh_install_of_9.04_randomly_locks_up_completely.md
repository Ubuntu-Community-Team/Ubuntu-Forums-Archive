---
title: "Fresh install of 9.04 randomly locks up completely"
date: 2009-06-08
forum: General Help
---

### Post by diablo75 on 2009-06-08
So I just finished re-installing 9.04 on a fresh ext4 root partition (and I'm re-using a separate ext3 partition for my /home).  I did this because ever since upgrading from 8.10, my computer will randomly lock up; I was hoping a fresh start would solve the problem.  

When it happens, the mouse won't move and everything on the screen (like the system monitor or clock on the upper panel) is frozen.  I have to hit the reset button or power the system completely off and then restart.

Can anything be done to trace the cause of the problem?  Perhaps I'm using a piece of hardware that is known to have issues?  Might I need to update my BIOS?

Edit:  I wanted to add a picture to my post.  This is a message I see on my monitor just a split second before the Ubuntu splash screen appears and I don't know if it means something bad or not.  I only have one hard drive (sata) in my computer and one DVD burner (IDE).

---

### Post by Jive Turkey on 2009-06-08
Can you ctrl+alt+f1 when this lockup happens?  In any case make note of the time on your frozen screen before resetting then after restarting, check your logs for any helpful message with close to the time of the lockup.  That might give you some hints.  There is a log viewer application under System > admin > log viewer.  Most of your logs are going to be in /var/log

---

### Post by diablo75 on 2009-06-24
Well another lockup happened so here's what I'm seeing.  I set the system to not shut the monitor off for any reason so if this happened while I was away from my PC, I could see the clock in the corner and know exactly what time it crashed.  In this case, it happened at 2:30 in the morning.  I'm just now turning the computer back on again at 3:45 in the afternoon.

Here's what that looks like in the "messages" log:

```
Jun 24 01:47:33 ubuntu kernel: [11801.154225] ath5k phy0: unsupported jumbo
Jun 24 02:04:21 ubuntu kernel: [12808.825501] ath5k phy0: unsupported jumbo
Jun 24 02:06:19 ubuntu kernel: [12927.198284] ath5k phy0: unsupported jumbo
Jun 24 15:45:03 ubuntu syslogd 1.5.0#5ubuntu3: restart.
Jun 24 15:45:03 ubuntu kernel: Inspecting /boot/System.map-2.6.28-13-generic
Jun 24 15:45:03 ubuntu kernel: Cannot find map file.
Jun 24 15:45:03 ubuntu kernel: Loaded 76870 symbols from 60 modules.
```

In this case, there seems to be something happening with an "ath5k phy0" whatever that is, just before 2:30, but not very close to 2:30.

In the "syslog" log file:

```
Jun 24 02:04:21 ubuntu kernel: [12808.825501] ath5k phy0: unsupported jumbo
Jun 24 02:06:19 ubuntu kernel: [12927.198284] ath5k phy0: unsupported jumbo
Jun 24 02:10:01 ubuntu /USR/SBIN/CRON[7221]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun 24 02:17:01 ubuntu /USR/SBIN/CRON[7352]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 24 02:20:01 ubuntu /USR/SBIN/CRON[7423]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun 24 02:30:02 ubuntu /USR/SBIN/CRON[7554]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
```

And in the auth.log file:

```
Jun 24 02:20:01 ubuntu CRON[7416]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun 24 02:20:01 ubuntu dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.31" (uid=1000 pid=3406 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.68" (uid=0 pid=7416 comm="/USR/SBIN/CRON "))
Jun 24 02:20:01 ubuntu CRON[7416]: pam_unix(cron:session): session closed for user root
Jun 24 02:30:01 ubuntu CRON[7547]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun 24 02:30:01 ubuntu dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.31" (uid=1000 pid=3406 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.69" (uid=0 pid=7547 comm="/USR/SBIN/CRON "))
Jun 24 02:30:02 ubuntu CRON[7547]: pam_unix(cron:session): session closed for user root
```

That's about all I can find as far as long files that contain events within a half hour or so before the crash.  And I'm not an expert about any of this so I don't know how to read it.

---

### Post by izzy84075 on 2009-06-24
I'm also having this problem. No useful messages in any of the logs, just a random lockup. It's happened..4 times, I think, in the last two days.

As far as I can tell, it only happens when it's not actively being used. When you're using the computer as a server, though, that tends to be quite a bit... Let me know if there's anything else you need to help diagnose.

Also, it didn't start until the last batch of updates I did... I know it included a new version of the X server, so that might have something to do with it.

Edit: Just realized I didn't really include anything about my system... Jaunty, with / on an Ext4 partition. Older ATi video card, 512MBs RAM, 1.4GHZ AMD processor.

---

### Post by diablo75 on 2009-06-28
Out of curiosity, I was wondering exactly what kind of RAM everyone who is experiencing this problem have in their PCs.  I happen to have two sticks of memory that are not rated to function at the same speed and the motherboard is actually under-clocking one while over-clocking another.  So I was thinking it's possible that one stick is having a glitch or something and causing the whole system to freeze...

---

### Post by Steelmourne on 2009-06-28
It could be the RAM, try slotting in a new set of 2x1GB or a similar RAM set. However, the pic you attached says ata1: softreset so your hard drive may not be configured properly. There may also be something related to your atheros wireless card and its update schedule.

---

### Post by diablo75 on 2009-06-30
Well I pulled the slower of the two sticks of RAM out of my PC and I'm going to leave it running for a week strait to see if it ever locks up.  I'll keep ya guys posted...

---

### Post by lech@ibcl.at on 2009-07-01
My Thinkpad T61p has crashed twice while idle since the last apt-get upgrade (with proposed).
I suspect some Xorg/Nvidia/Screensaver problem.
I have now configured the screen saver to just blank the screen instead of any GL based gimmicks.
Hope that helps, because' I'd hate if it'd be a hardware problem.
Regards Christoph

---

### Post by psycovic23 on 2009-07-01
It's probably because of ath5k, which has been causing me issues in 8.10 as well. It freezes at random, and I can't figure it out.

Some links:
[http://bugzilla.kernel.org/show_bug.cgi?id=12647](http://bugzilla.kernel.org/show_bug.cgi?id=12647)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/341952](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/341952)

They claim it's fixed, but I installed the ath5k from linuxwireless and it's still crashing, though I'm not entirely sure I did it right.  

One thing you can try and do is install linux-backports-modules-jaunty and see if that helps - it includes a new ath5k, but you might be better off getting the freshest version from linuxwireless and trying that.

I *really* need a solution to this - it's unacceptable to have my computer lock up once a day at random.

---

### Post by diablo75 on 2009-07-03
Well the experiment with pulling the one of two sticks of RAM didn't help.  System just locked up about 10 minutes ago shortly after logging in.  I'm leaning more towards the ath5k issue mentioned above.  I've not looked at the bug reports yet...

---

### Post by diablo75 on 2009-07-03
I've noticed in my Hardware Drivers Manager that there is an "alternative madwifi driver" available for my wireless adapter but I've never installed it before.  Is it possible that using this driver instead would bypass the ath5k problems I'm having?  Has anyone installed these drivers before with success?

---

### Post by psycovic23 on 2009-07-03
Actually I think I've fixed it by using kernel 2.6.29.

---

### Post by diablo75 on 2009-07-04
> **psycovic23 said:**
> Actually I think I've fixed it by using kernel 2.6.29.
Does that have to be installed manually?  I've done some recent updates, but I don't think the kernel version issued out with the latest batch is quite that up-to-date.  I'm not at my PC right now but I was thinking it's using 2.6.28

---

### Post by yavez on 2009-07-04
> **diablo75 said:**
> Does that have to be installed manually?  I've done some recent updates, but I don't think the kernel version issued out with the latest batch is quite that up-to-date.  I'm not at my PC right now but I was thinking it's using 2.6.28

Same here. on 2.6.28.  My system has frozen on 6 different occasions in the last couple of days and all I could find out was that it might have something to do with EXT4 which I'm running on.  Seems completely random to me, but it is a show stopper.  Anybody confirm kernel 2.6.29 fixes this problem?

---

### Post by psycovic23 on 2009-07-05
> **diablo75 said:**
> Does that have to be installed manually?  I've done some recent updates, but I don't think the kernel version issued out with the latest batch is quite that up-to-date.  I'm not at my PC right now but I was thinking it's using 2.6.28

I downloaded 3 debs to install the kernel, but can't remember from where :-\

Stability is reaching  4 days now on wireless. Looking good.

---

### Post by diablo75 on 2009-07-05
> **psycovic23 said:**
> I downloaded 3 debs to install the kernel, but can't remember from where :-\

[http://ubuntuforums.org/showpost.php?p=7564237&postcount=2](http://ubuntuforums.org/showpost.php?p=7564237&postcount=2)

I think I found where you might have got the downloads from.  I'd try it on my system right now if I were at home at the damn thing hadn't locked up while I was away AGAIN ha ha ha.  Looking forward to trying this out; I'll check back in later.

---

### Post by psycovic23 on 2009-07-05
> **diablo75 said:**
> [http://ubuntuforums.org/showpost.php?p=7564237&postcount=2](http://ubuntuforums.org/showpost.php?p=7564237&postcount=2)

I think I found where you might have got the downloads from.  I'd try it on my system right now if I were at home at the damn thing hadn't locked up while I was away AGAIN ha ha ha.  Looking forward to trying this out; I'll check back in later.

Yea that was it.

I ought to point out that I picked the 2.6.29 kernel after reading the ath5k bug reports and one dude saying he pushed a bunch of patches into that kernel. So I don't think this'll do anything for the EXT4 problem.

---

### Post by diablo75 on 2009-07-06
Well I applied 2.6.29 and things haven't locked up yet.  It hasn't yet been a full 24 hours, but my wireless networking in general does seem to be working more smoothly.  I remember several times recently where I'd try to check my email or get on a website and it'd just sit there, probably spitting out those "unsupported jumbo" errors into a log file and the connection would be briefly disrupted (if it didn't flat out lock the whole system up).  I'd also notice, while VNC'ed into the system, the video stream would freeze and I'd say, "Damn it, it's locked up again." but then it would suddenly recover about 10 or 15 seconds later.  So I have a good feeling about this!
:guitar:

---

