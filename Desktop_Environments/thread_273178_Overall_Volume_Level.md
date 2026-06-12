---
title: "Overall Volume Level"
date: 2006-10-07
forum: Desktop Environments
---

### Post by barrack on 2006-10-07
On my machine I dual boot Windows and Ubuntu. I have noticed a big difference in overall volume levels. On Ubuntu all OS volume levels are maxed out and my physical speaker dials are as well. Yet, the sound output is only about 1/4 that of what it would be in Windows.

On XP, I usually have the speakers set to about 1/4 of max.. and when I have a party or something, crank it up to like 3/4.

Any ideas?

Thanks!

---

### Post by BitTorrentBuddha on 2006-10-07
I have a similar problem. Have you made sure to look at all the levels with ```
alsamixer
```

---

### Post by GuiGuy on 2006-10-07
> **barrack said:**
> 

Any ideas?

Check the master control in GMIX to see that it is set to maximum (?).

regards

---

### Post by barrack on 2006-10-07
> **BitTorrentBuddha said:**
> I have a similar problem. Have you made sure to look at all the levels with ```
alsamixer
```

The master was set to 100 already. There was a bunch of other options, but I dunno what to change.

---

### Post by campbeln on 2006-10-08
I'm having the same issue under Kubuntu/KMix! I've got an eMachines m6804 with a VIA 8235 chipset (I believe) that under 5.10 worked just fine, but now after having upgraded to 6.06 everything is VERY low volume (25%-ish).

It worked just fine under 5.10, so it's something to do with 6.06. I've maxed out all of the KMix settings, and there's no volume knob to adjust, so it's 6.06.

Anyone got a fix for us? :-k

---

### Post by campbeln on 2006-10-09
I found this post in another forum:


[from [https://launchpad.net/distros/ubuntu...ls/+bug/45246]](https://launchpad.net/distros/ubuntu...ls/+bug/45246])
Arthur Penn at 2006-05-31 22:25:09 UTC

I had the same problem after upgrading Breezy to Dapper RC, but not on a ThinkPad--instead on a frankenbuild Athlon XP 2200+ desktop. In my case, in alsamixer there were four identical entries labeled VIA DXS all the way to the right of the mixer console. These were all turned down to zero. I turned them up to 81 and then I got sound from speaker-test, KDE, etc.


So I fired up a shell, ran 'alsamixer' then arrowed to the right all the way, and there they were... 3 levels for 'VIA DXS'. I turned these babies up to '100<>100' and my sound is back to normal. Best of luck!!

---

### Post by barrack on 2006-10-09
> **campbeln said:**
> I found this post in another forum:
So I fired up a shell, ran 'alsamixer' then arrowed to the right all the way, and there they were... 3 levels for 'VIA DXS'. I turned these babies up to '100<>100' and my sound is back to normal. Best of luck!!

I ran alsamixer and turned up the PCM which was set pretty low. However, when i rebooted, it was at the original level again!

Any ideas on making this more permanent?

---

