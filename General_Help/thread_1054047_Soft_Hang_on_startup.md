---
title: "Soft Hang on startup"
date: 2009-01-29
forum: General Help
---

### Post by HorryMorry on 2009-01-29
Hey all,
I am having an issue with my system "soft hanging" soon after startup.  By soft hang I mean that all video stops but the mouse still moves...other than that its totally locked.  It seems to only do this with the accelerated graphics enabled and the restricted NVIDIA drivers enabled.

Some system info:
Alienware area 51M 7700
NVIDIA GeForce Go 7900 GTX  W/256 Mem
Restricted drivers enabled
Ubuntu 8.04

Things I have tried:
upgrade NVIDIA drivers to 180.22 (screwed everything up even worse)
upgrade to Ibex (problem seemed to get worse)
Lurk the forums and try just about everything to no avail

System Log:
I have noticed that the hang is usually just a few seconds long but sometimes extends to 20+ seconds.  These hangs seem to correlate to the following logs copied out of the system log in "syslog"
```

Jan 29 06:13:01 TheDude kernel: [ 1810.010809] NVRM: Xid (0001:00): 13, 0000 01019700 00004097 00001900 000206b2 00400000
Jan 29 06:13:05 TheDude kernel: [ 1814.021608] NVRM: Xid (0001:00): 36,  L0 -> L0
Jan 29 06:13:05 TheDude kernel: [ 1814.022819] NVRM: Xid (0001:00): 9, Channel 00000020 Instance 00000000 Intr 00100000
Jan 29 06:13:46 TheDude kernel: [ 1855.126940] NVRM: Xid (0001:00): 6, PE0002 0420 ffdca282 00138c68 f00086d3 00000000
Jan 29 06:13:46 TheDude kernel: [ 1855.137946] NVRM: Xid (0001:00): 36,  L0 -> L0
Jan 29 06:14:16 TheDude kernel: [ 1885.065766] NVRM: Xid (0001:00): 13, 0002 beef3097 00004097 00000370 ff00fff0 00000002
Jan 29 06:14:20 TheDude kernel: [ 1889.078213] NVRM: Xid (0001:00): 36,  L0 -> L0
Jan 29 06:14:41 TheDude kernel: [ 1910.037343] NVRM: Xid (0001:00): 9, Channel 00000020 Instance 00000000 Intr 00100000
Jan 29 06:14:45 TheDude kernel: [ 1914.052906] NVRM: Xid (0001:00): 36,  L1 -> L0
Jan 29 06:14:45 TheDude kernel: [ 1914.054199] NVRM: Xid (0001:00): 9, Channel 00000020 Instance 00000000 Intr 00100000

```

During the 45 or so secs listed above there were about 3 hangs.  Every time you see a break in the time, ie 06:14:20 - 06:14:41 my system was hung.

I am really new to Linux so please bear with me!

Thanks all!!!

---

### Post by HorryMorry on 2009-01-31
Anybody have any ideas?  I was lurking google for a bit and found some people that were talking about it being a dual channel memory problem or something to that effect...any help would be much appreciated!

---

### Post by HorryMorry on 2009-02-04
So I have found that if I am running the system monitor this problem does not seem to raise its head.  Granted this is just a work around and I would still really appreciate any help.

---

### Post by liquidpele on 2009-02-04
I don't have any specific advice, but if you can get the stacktrace and/or dump file, you should submit it as a bug at launchpad.net:

some debugging advice:
[http://www.av8n.com/computer/htm/kernel-lockup.htm](http://www.av8n.com/computer/htm/kernel-lockup.htm)

---

### Post by aBitLater on 2009-02-05
what shows up in the log just before the nvrm xid errors?  I'm having a similar problem where a cron job always shows up just before the nvrm xid errors - causing the monitor to blink

---

### Post by HorryMorry on 2009-02-05
liquidpele:
How do I get the stacktrace or dump files?

aBitLater:
This is what I am getting just as the errors start:
```
Feb  5 06:01:19 TheDude avahi-daemon[5203]: Joining mDNS multicast group on interface ath0.IPv4 with address 192.168.1.101.
Feb  5 06:01:19 TheDude avahi-daemon[5203]: New relevant interface ath0.IPv4 for mDNS.
Feb  5 06:01:19 TheDude avahi-daemon[5203]: Registering new address record for 192.168.1.101 on ath0.IPv4.
Feb  5 06:01:20 TheDude NetworkManager: <info>  Clearing nscd hosts cache. 
Feb  5 06:01:20 TheDude NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Feb  5 06:01:20 TheDude NetworkManager: <info>  Activation (ath0) successful, device activated. 
Feb  5 06:01:20 TheDude NetworkManager: <info>  Activation (ath0) Finish handler scheduled. 
Feb  5 06:01:20 TheDude NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) complete. 
Feb  5 06:01:22 TheDude ntpdate[6255]: step time server 91.189.94.4 offset -2.003221 sec
Feb  5 06:01:20 TheDude avahi-daemon[5203]: Registering new address record for fe80::20b:6bff:fe4f:e48 on ath0.*.
Feb  5 06:01:29 TheDude kernel: [  457.646548] ath0: no IPv6 routers present
Feb  5 06:01:33 TheDude kernel: [  462.152356] NVRM: Xid (0001:00): 9, Channel 00000020 Instance 00000000 Intr 00100000
Feb  5 06:01:38 TheDude kernel: [  466.159368] NVRM: Xid (0001:00): 36,  L0 -> L0
Feb  5 06:01:38 TheDude kernel: [  466.160566] NVRM: Xid (0001:00): 9, Channel 00000020 Instance 00000000 Intr 00100000
```

It looks like the "registering new address record" and the "no IPv6 routers present" messages come up almost every time...at least lately.

Thanks for the responses!!

---

