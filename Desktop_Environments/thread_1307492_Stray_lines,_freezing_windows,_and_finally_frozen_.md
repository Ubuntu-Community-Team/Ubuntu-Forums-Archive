---
title: "Stray lines, freezing windows, and finally frozen desktop"
date: 2009-10-31
forum: Desktop Environments
---

### Post by leprasmurf on 2009-10-31
Hello all,

I got all the way to attaching one last file for this issue, and my desktop froze up completely.  I was able to ssh in, and try to kill things, but nothing associated with Xorg or gnome would die (I'm talking kill -9 <pid>, pkill, top's kill all as root).  

So I have this issue, that I'm having trouble articulating.  Randomly, and semi-regularly (a couple times a week), lines will appear in random spots.  They may be 3 pixes wide (and jagged) or 20 pixels wide.  They may appear on my desktop, or they may appear in an application.  My first thought was they were dead pixels, but they can be covered with another application, and they scroll with firefox if they happen to appear there.  I've also noticed a distortion of fonts, and it's very specific.  Capital A may decide to have some extra pixels, and it happens on every capital A in every application (including xterm).  

Occasionally, when alt tabbing, the desktop will freeze mid-effect.  A few minutes ago, the freezing lasted for 10 seconds.  Then it happened again, and the desktop froze.  I couldn't restart GDM or even kill xorg (as previously mentioned).  Now that I've restarted that computer, the lines that were on the desktop (see attached images) have disappeared.  I've just disabled all compiz effects, in hopes that will solve the problem but...

Syslog isn't telling me much, but my guess is this has something to do with the nvidia drivers due to lines such as:

*note: this was right around the time I started having issues:
```
Oct 31 04:01:00 Poseidon kernel: [144539.505559] NVRM: Xid (0001:00): 8, Channel 00000003
Oct 31 04:01:00 Poseidon kernel: [144539.565379] NVRM: Xid (0001:00): 6, PE0001
Oct 31 04:01:00 Poseidon kernel: [144539.772168] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00001b08 00ba784d 00000001
Oct 31 04:17:14 Poseidon kernel: [145511.153555] NVRM: Xid (0001:00): 8, Channel 00000003
Oct 31 04:32:55 Poseidon kernel: [146450.212068] NVRM: Xid (0001:00): 8, Channel 00000003

```

Unfortunately, I don't really know what this means. Any help would be appreciated.  I haven't upgraded to the 9.10, as I thought that might just exacerbate the problems.  Please find attached, screenshot sections where the random lines appeared, and my syslog right before I restarted (just after the desktop froze).  Thanks in advanced.

Regards,
Tim

P.S. My world is upside-down, my ubuntu machine is unstable and I had to go to a windows machine to post about it...I feel so dirty.

---

### Post by leprasmurf on 2009-11-15
Ok, so I don't know if this has solved my problem entirely, but so far it's looking good.  I upgraded to 9.10, and if anything, the problem got worse.  I had disabled all visual effects, and the problems persisted.  I downgraded the driver from 180 to 173, and the problem got much worse, though different now.  Now random pixels were displaying and disappearing with much greater frequency, and seemed animated.  Anyway, I went to Nvidia, found the latest driver for my card, installed it, ran nvidia-xconfig, and then used nvidia-settings to setup my resolution and dual screens.  Now everything appears stable...lets see how long it lasts.  :popcorn:

---

