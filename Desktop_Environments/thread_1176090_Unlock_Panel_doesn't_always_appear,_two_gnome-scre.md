---
title: "Unlock Panel doesn't always appear, two gnome-screensaver processes running = bad?"
date: 2009-06-01
forum: Desktop Environments
---

### Post by ipsi on 2009-06-01
Ok, I've got a few (possibly related) problems here:

1) I don't normally turn my work laptop off. Much easier just leaving it on all the time. So I normally just lock the computer by going CTRL+ALT+L. Nice and simple.

However, when I came in on Saturday (office == warmer than outside while waiting for the bus), the unlock dialog box that normally comes up didn't appear.

2) When I went in to a terminal (CTRL+ALT+F1) to see what was going on, I noticed there were two gnome-screensaver processes running. One was using ~95% of the CPU, and one was pretty much idle, according to top. Both processes were owned by me, and when I killed the one using all the CPU, nothing actually happened. Still didn't see the unlock panel. When I went back into the terminal, the second process had started up again, using the majority of the CPU.

3) When I killed both processes, I discovered that I couldn't actually do an awful lot, because large chunks of the file system (which I had been using) were locked. Damned if I know why. Shutdown all my active programs and rebooted.

4) When it tried to start up again, it told me that the drive hadn't been safely shut down, and that it would do a check. The check failed, and I had to run fsck manually. I did so (just fsck, no options or anything), and got a whole bunch of messages like the following:

```
Jun  2 08:04:16 andrew-laptop kernel: [138230.438793] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jun  2 08:04:16 andrew-laptop kernel: [138230.438802] ata1.00: BMDMA stat 0x65
Jun  2 08:04:16 andrew-laptop kernel: [138230.438816] ata1.00: cmd c8/00:08:e7:6e:5e/00:00:00:00:00/e3 tag 0 dma 4096 in
Jun  2 08:04:16 andrew-laptop kernel: [138230.438819]          res 51/40:08:e7:6e:5e/00:00:00:00:00/e3 Emask 0x9 (media error)
Jun  2 08:04:16 andrew-laptop kernel: [138230.438826] ata1.00: status: { DRDY ERR }
Jun  2 08:04:16 andrew-laptop kernel: [138230.438831] ata1.00: error: { UNC }
Jun  2 08:04:16 andrew-laptop kernel: [138230.460903] ata1.00: configured for UDMA/100
Jun  2 08:04:16 andrew-laptop kernel: [138230.476607] ata1.01: configured for MWDMA2
Jun  2 08:04:16 andrew-laptop kernel: [138230.476632] ata1: EH complete
```

The dates aren't accurate, but the messages themselves are. These are what I found in the log, and they happened roughly 6 hours before I arrived in the office.

So it looks like my drive might be dying, but why am I not able to unlock the screen? It's only started recently (some time after upgrading to 9.04), and it doesn't happen straight away. I need to leave it for some time (not sure how long) before it does it. So I can lock the screen, wait a few seconds, and have no problems unlocking it. Leaving it overnight, though, would probably be a bad idea.

Anyone got any suggestions? I've turned the screensaver off, and told it not to turn off the screen when the laptop is on AC power, see if that helps.

---

