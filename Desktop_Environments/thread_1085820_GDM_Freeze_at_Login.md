---
title: "GDM Freeze at Login"
date: 2009-03-03
forum: Desktop Environments
---

### Post by jaggardjones on 2009-03-03
I know that this topic has been brought up before, but as none of the solutions worked for me, I am being a pain.

The Prob.

I get the pink screen just before login, and the spinning ball does a half spin.

Recovery mode to root works, if I continue as user, then GDM tries again and same prob.

I have tried:

"/etc/init.d/gdm start"         ...same prob

"startx"                        ... I get the Natualis and 
                                    Panel errors

"sudo apt-get update", "apt-get upgrade", install ubuntu-desktop, install sysvconfig, --reinstall gdm, and some others

I know that this has fixed others login freeze, but I get the "cannot resolve archive.ubuntu.com/x/x/x/x/x"

I am plugged directly into my modem, which I know works, and ifconfig results:

Link encap: Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
UP LOOPBACK RUNNING  MTU:16436  Metric:1
and all the packets are at 0.

So, I do not know how to get this internet running, which I believe will help me fix the other problems.

Also, I was messing with some zlib files before this problem, because my panel was being held up by a gzopen64 symbol problem.

Any suggestions would be helpful, thanks a million in advance

---

### Post by teamcoltra on 2010-03-03
I actually need help with this too... I did an upgrade via terminal and when I rebooted... Wham-o No internet.

Ironically I am having this problem to the day (of last year) of this guy.

---

### Post by bhupen on 2011-07-26
Was this issue resolved. I am having the same issue and I have tried going through the log files but I am unable to determine issue.

---

### Post by ajvok on 2011-07-27
I just had this (or a similar problem). Boot..logon screen..enter user name/password..get 'pinkish' background screen, but nothing else.. entire system hangs (can not CTRL-ALT-F1 or ssh to box).
Have to hard reboot.

After reboot and ssh to the box I can see in the log:
gdm-session-worker[2076]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
That's the only odd thing.

The same thing happens everytime I try to logon and am forced to hard-reboot to recover.
Prior to this the machine was fine for weeks. Nothing new done to config in last session.

Eventually discovered that, at logon screen, CTRL-ALT-F1, then logon as root, 
stop gdm
start gdm
And the logon as regular user fixes it.
 
No idea why. Hope that helps someone.

---

