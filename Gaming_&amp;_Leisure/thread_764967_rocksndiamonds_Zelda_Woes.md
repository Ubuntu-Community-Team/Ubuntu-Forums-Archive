---
title: "rocksndiamonds Zelda Woes"
date: 2008-04-24
forum: Gaming &amp; Leisure
---

### Post by mikedep333 on 2008-04-24
Although it seems like regular rocksndiamonds works fine (I have to start it from the command line with 'rocksndiamonds', I'm having trouble with both the the original zelda level set, and the zelda II level set.

With the original zelda level set, as synaptic downloaded, it freezes at the main menu every time.

With [Zelda II, downloaded from the artsoft website]("http://www.artsoft.org/rocksndiamonds/levels.html"), it either freezes at the main menu or it crashes with the output below shortly in game.

Does anyone know how to make these level sets work?

```
mike@appropriatetouching:~$ rocksndiamonds
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
write /dev/sequencer or /dev/snd/seq: Bad file descriptor
Segmentation fault

```

---

### Post by Sockerdrickan on 2008-04-24
Close all apps that uses audio before you start it.

---

