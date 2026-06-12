---
title: "6400 fan and i8kmon don't seem to work well in Lucid"
date: 2010-08-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cnbiz850 on 2010-08-07
I used to use Gkrellm and its i8k plugin to control fan operation in Karmic and other previous versions of Ubuntu, but now upgraded to Lucid and the i8k plugin is no longer in the repository.  So I followed guidelines in [here]("http://wwww.ubuntuforums.org/showpost.php?p=3389584&postcount=4") to setup i8kmon.  The fan runs after that, but it acts strangely in the sense that it goes on high for a couple seconds and then low for a couple seconds (when actually it should be always on high as set by the temperature levels).  Seems something is in conflict with it and fights for control.  I suspect it is the BIOS - I also upgraded the BIOS to the most recent (A17) after I upgraded to Lucid.  I checked in the BIOS and there is no place for me to set about the fans there.  

Well, does i8kmon work at all?  Obviously it does.  Without it, the fan is on on low seemingly always.  I tried to run some intensive applications to heat up the machine to over 80C and the fan was kept at low speed.  I guess that was due to the BIOS schedule.

What can I do to remove the strange behavior when using i8kmon?  Anyone please help.

---

### Post by cnbiz850 on 2010-08-08
Well, it seems alright now.  Don't know what was happenning.  I will see.

---

### Post by cnbiz850 on 2010-08-10
My last post is not always true.  The strange fan behavior still exists.  I can't really say exactly under what circumstances.  One situation under which I see it seems basically when I play a movie with vlc to bring the temperature to somewhere near 70C.  Literally then the fan is on high for 3 seconds and on low for 3 seconds.  I can repeatedly check with i8kfan and it gives results corresponding to the noise levels (low/high) of the fan.

The setting of my /etc/i8kmon is:
```
$ more /etc/i8kmon
set config(0) {{- 0} -1 45 -1 50}
set config(1) {{- 1} 35 55 40 60}
set config(2) {{- 2} 45 128 50 128}

```

Any thoughts on what is going on?

---

### Post by cnbiz850 on 2010-08-16
Still not working right.  Any thougts on what to check?

---

### Post by cnbiz850 on 2010-09-10
Still suffering from this problem.  The computer can easily go above 90C with some intensive apps running.

What I notice is this: it heats above 50C, fan turns to 2.  At 70C, the fan turns to 1 fully.  As it cools down to 62C, the fan goes between 1 and 2.

As the battery is dead on the laptop, I wonder it the temperature settings for the CPU and battery might cause the trouble.  So I lowed the temperature settings for the battery way down.  But still no help.

Anyone has any clue please?

---

### Post by cnbiz850 on 2010-09-10
Another notice.  I kill the i8kmon and then try to use i8kctl to check the fan info.  Up to 85C, the fan is al on 1 as much as I can by the noise level.  But an interesting thing is that i8kctl indicate that fan is at 2 when above ~75C, but I can't hear the high level of noise.  If I do "i8kfan - 2", then I definitely can hear the high level of noise.  But even with this command, the fan stays at 2 for a couple second, even during the time when i8kctl indicates 2.

Could it be that something is wrong with the HW?

---

