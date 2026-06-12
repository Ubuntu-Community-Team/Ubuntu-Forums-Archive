---
title: "King's Arthur Gold - Sound problem"
date: 2011-09-07
forum: Gaming &amp; Leisure
---

### Post by cerda on 2011-09-07
Hello there. I've just found this real nice sandbox/team fortress oriented 2D game.

[http://kag2d.com/](http://kag2d.com/)

It has a linux client !! just download it and go play for free. The problem is I can't get sound in ubuntu 11.04 64bit. The error I get is

```
irrKlang sound library version 1.3.0
Could not load libasound.so

```

I've posted on the game forums and I'm trying here as well. Anyone knows how to fix it?? Thank you very much !!

---

### Post by donkyhotay on 2011-09-07
Looks like a conflict with the sound libraries. It probably uses either ALSA or OSS (probably ALSA) which doesn't always work pulseaudio. Kind of a shot in the dark but you might try
```

pasuspender ./name/of/file

```
that will temporarily suspend pulseaudio and sometimes fixes these types of issues.

---

