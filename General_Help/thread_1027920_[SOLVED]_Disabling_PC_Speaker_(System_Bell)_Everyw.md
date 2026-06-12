---
title: "[SOLVED] Disabling PC Speaker (System Bell) Everywhere?"
date: 2009-01-01
forum: General Help
---

### Post by vonsperb on 2009-01-01
How can I get completely rid of the annoying PC Speaker 'beep' in all applications? For example, when you type backspace and there's no character left to delete in the Hardware Testing report tool... Back in '96 when I ran Slackware on my PC I'd just disconnect the PC Speaker, but I'd rather have a software solution on my current laptop. Thanks!

---

### Post by Dr Small on 2009-01-01
Try:
```
xset b off
```

---

### Post by cariboo on 2009-01-01
If it isn't all ready you can blacklist the pc speaker. You can add it to /etc/modprobe.d/blacklist this way, press Alt-F2 and type:

```
gksu gedit /etc/modprobe.d/blacklist
```

then add:

```
blacklist snd_pcsp
```

to the bottom of the file.

Jim

---

### Post by vonsperb on 2009-01-03
Well, it is blacklisted already, with interesting comments:

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

Any other ideas? Thanks!

---

### Post by cta16 on 2009-01-03
> **cariboo907 said:**
> If it isn't all ready you can blacklist the pc speaker. You can add it to /etc/modprobe.d/blacklist this way, press Alt-F2 and type:

```
gksu gedit /etc/modprobe.d/blacklist
```

then add:

```
blacklist snd_pcsp
```

to the bottom of the file.

Jim

I did the same as above except I blacklisted pcspkr

```
blacklist pcspkr
```

---

### Post by vonsperb on 2009-01-04
It works! Thanks a lot!

---

