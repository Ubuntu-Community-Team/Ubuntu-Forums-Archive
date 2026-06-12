---
title: "How to play sound file from command line?"
date: 2005-12-14
forum: Desktop Environments
---

### Post by Mguel on 2005-12-14
Hi, I'm new to ubuntu, and I haven't been able to play an audio file from the terminal.

I installed splay using synaptic, but I can't get it to play anything.

I can play them via GUI players (totem, rythmbox)

Thanks in advance,
Mguel

---

### Post by Mguel on 2005-12-14
Finally found aplay with which it works...

```
aplay -q sound.wav
```

---

### Post by poptones on 2005-12-14
mplayer will play just about anything from the command line.

---

### Post by 23meg on 2005-12-14
aplay works with ALSA only; check out the play command as well. ```
man play
```

---

### Post by Mguel on 2005-12-15
OK... I'll try them also, after [repairing or reinstalling]("http://ubuntuforums.org/showthread.php?p=576189") ubuntu :(

Thanks,
Mguel

---

