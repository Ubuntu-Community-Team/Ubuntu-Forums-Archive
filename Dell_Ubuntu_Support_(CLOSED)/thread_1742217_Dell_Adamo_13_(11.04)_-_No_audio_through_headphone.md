---
title: "Dell Adamo 13 (11.04) - No audio through headphones"
date: 2011-04-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Jackslaps on 2011-04-28
Just installed Natty Narwhal today and the headphones don't work. I've already checked Alsa Mixer, nothing is muted. I messed around with all the options and settings available in System>Preferences>Sound and still nothing (currently set to default settings). I edited /etc/modprobe.d/alsa-base.conf with the line "options snd-hda-intel model=dell-m6" and I still get nothing. Does anyone have an idea of what I can do to solve this problem?

EDIT: This is the configuration on my laptop:
[http://www.alsa-project.org/db/?f=e61b6e35c2a061e65559ee323a96fde5e004b2f7](http://www.alsa-project.org/db/?f=e61b6e35c2a061e65559ee323a96fde5e004b2f7)

---

### Post by auroraskyes on 2011-04-28
I too have this issue.

---

### Post by Jackslaps on 2011-04-30
I solved my issue!

My solution: When editing the modprobe options file, rather than inputting:

```
snd-hda-intel: model=dell-m6
```

use:
```
snd-hda-intel: model=dell-eq
```

I found the solution to this through one of the threads posted here in the forums. I'll try and find it in a bit and edit the OP as so to include the link.

---

### Post by auroraskyes on 2011-05-12
This does fix the headphones, but this leaves my internal mic not working.

The line **options snd-hda-intel model=dell-m6** in 10.10 64 bit worked for both the headphones and mic.

The line **options snd-hda-intel model=dell-eq **in 11.04 only seems to bring back just the headphones.

I will just have to keep digging for a solution.

---

### Post by auroraskyes on 2011-05-12
Just a heads up Jackslaps this will bring the internal mic back as well:

options snd-hda-intel model=dell-m6[B]-dmic

I found that out here:
[/B]
[http://ubuntuforums.org/showthread.php?t=1503312&highlight=dell+adamo+mic](http://ubuntuforums.org/showthread.php?t=1503312&highlight=dell+adamo+mic)

---

