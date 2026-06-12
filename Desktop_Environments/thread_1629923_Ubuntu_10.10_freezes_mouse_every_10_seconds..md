---
title: "Ubuntu 10.10 freezes mouse every 10 seconds."
date: 2010-11-24
forum: Desktop Environments
---

### Post by Eraknelo on 2010-11-24
Hi there,

I am running a a fresh Ubuntu Live (X64) off of a 8GB flash drive with an 4GB Casper file.
Everything works perfectly except for the mouse freezing EXACTLY every 10 seconds.
I have tried another mouse, and it also does exactly this.

Both mice are USB devices, as I am running on a laptop with no PS/2 connection.
The CPU and RAM usage is low.
Does anybody know how I could fix this, or what the problem is?

Thanks in advance,

-René

UPDATE: Apparently, the whole screen freezes... So even videos, etc. freeze every 10 seconds. The duration is approx. 5 milliseconds.

UPDATE 2: I am now running the exact same specifications outside of now running X32 on a different same size flash drive, and I no longer have the problems. Also am using a touchpad, might make the difference.

---

### Post by azertyh on 2010-11-24
hello,
check your log files. sometimes, there are error messages. in this case, google these messages to get more info.

---

### Post by Eraknelo on 2010-11-24
> **azertyh said:**
> hello,
check your log files. sometimes, there are error messages. in this case, google these messages to get more info.
Alright, which ones of the logs should I be looking at? dmesg, messages, syslog, or what?

---

### Post by azertyh on 2010-11-25
hello,
yes. syslog
```
tail -f /var/log/syslog
```
and
```
dmesg
```

---

### Post by bburtin on 2011-03-11
I'm seeing this too.  Every 10 seconds, I see this in /var/log/syslog:
```

Mar 11 17:17:26 cosmonaut kernel: [28444.122221] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
Mar 11 17:17:26 cosmonaut kernel: [28444.122226] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
Mar 11 17:17:26 cosmonaut kernel: [28444.122228] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
Mar 11 17:17:26 cosmonaut kernel: [28444.122229] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................

...

Mar 11 17:17:27 cosmonaut kernel: [28444.437707] 
Mar 11 17:17:27 cosmonaut kernel: [28444.437712] nouveau 0000:01:00.0: VGA-1: EDID block 0 invalid.
Mar 11 17:17:27 cosmonaut kernel: [28444.437719] [drm] nouveau 0000:01:00.0: DDC responded, but no EDID for VGA-1

```

---

### Post by docmojo on 2011-05-09
Hi guys, I am a novice in these technical issues...

But faced this mouse freeze prob for a few days... Just struck me that, I had installed ClamAV prior to this glitch... So removed it from the system, and the problem seems to have disappeared... 

Do you'll have it installed too?

---

### Post by psypher on 2012-03-02
This issue is still occuring in ubuntu precise and is highly annoying. Only reason I use the nouveau driver is that the nvidia multi monitor management is terrible and cumbersome. The ubuntu precise display manager is waay better. 

BTW I do NOT have clamav installed.

I logged a bug about this:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/926714](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/926714)

please feel free to click "this affects me" on the bug so more attention is given to it. It seems to be a general nouveau issue:

[http://forums.opensuse.org/english/get-technical-help-here/applications/455885-opensuse-11-4-freezes-every-10-seconds-so.html](http://forums.opensuse.org/english/get-technical-help-here/applications/455885-opensuse-11-4-freezes-every-10-seconds-so.html)
[http://lists.opensuse.org/opensuse-bugs/2011-03/msg03309.html](http://lists.opensuse.org/opensuse-bugs/2011-03/msg03309.html)
[https://bbs.archlinux.org/viewtopic.php?id=134946](https://bbs.archlinux.org/viewtopic.php?id=134946)

---

