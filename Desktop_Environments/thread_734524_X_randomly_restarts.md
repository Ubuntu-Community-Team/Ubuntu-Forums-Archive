---
title: "X randomly restarts"
date: 2008-03-24
forum: Desktop Environments
---

### Post by zukakog on 2008-03-24
For the record, I tried to search for similar problems, but the search feature won't let me search for 'x server' because X is too short. Stupid VBulletin.

For some unknown reason, X server randomly restarts, just like if I were to hit Ctrl+Alt+Backspace. Sometimes it does it when I'm just staring at the screen, but other times it does it when I move the mouse.

The only thing I can find is in /var/log/daemon.log
```

Mar 24 17:56:41 mymachine kdm[5212]: X server for display :0 terminated unexpectedly

```

Any suggestions would be appreciated.:)

BTW, I'm running 7.10 (Gusty) on a Core 2 Duo with an older nVidia GeForce FX 5200. I'm using the 'restricted' nVidia driver offered upon first boot.

---

### Post by kellemes on 2008-03-25
> **zukakog said:**
> For the record, I tried to search for similar problems, but the search feature won't let me search for 'x server' because X is too short. Stupid VBulletin.

For some unknown reason, X server randomly restarts, just like if I were to hit Ctrl+Alt+Backspace. Sometimes it does it when I'm just staring at the screen, but other times it does it when I move the mouse.

The only thing I can find is in /var/log/daemon.log
```

Mar 24 17:56:41 mymachine kdm[5212]: X server for display :0 terminated unexpectedly

```

Any suggestions would be appreciated.:)

BTW, I'm running 7.10 (Gusty) on a Core 2 Duo with an older nVidia GeForce FX 5200. I'm using the 'restricted' nVidia driver offered upon first boot.

Use google.. much much better search engine. ;-)

Are there any hints of trouble in /var/log/Xorg.0.log maybe? Watch out for (WW) and especially (EE).
And is /var/log/messages showing anything relevant?

---

### Post by zukakog on 2008-03-25
True...google is much more OSS friendly than vBulletin.

I didn't see anything exciting in /var/log/Xorg.0.log or /var/log/messages last time I checked. I'll dump them here next time it happens. Thanks for the quick response!

---

### Post by zukakog on 2008-03-27
Nope. The only EE's or WW's were the examples, and:
```
(WW) NVIDIA(0): No valid modes for "1792x1344@75"; removing.
```

Any other suggestions?

---

### Post by kellemes on 2008-03-28
> **zukakog said:**
> Nope. The only EE's or WW's were the examples, and:
```
(WW) NVIDIA(0): No valid modes for "1792x1344@75"; removing.
```

Any other suggestions?

Well, only to keep on searching, maybe /var/log/syslog shows anything?

Often this has to do with the videodriver I think.. I just don't use NVidia myself so can't help you there..
You could try to replace your current driver for a while and see if this problem persists, this way you can at least find out if that's the problem.

---

### Post by zukakog on 2008-04-08
Sorry, somehow I missed your reply.

I'll go ahead and use the nv driver for a while and see how that does. Thanks.

---

### Post by Crafty Kisses on 2008-04-08
You may want to post some of you're logs, sounds like a video card issue.

---

