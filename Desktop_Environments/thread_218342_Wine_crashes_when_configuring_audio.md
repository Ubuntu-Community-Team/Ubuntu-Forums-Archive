---
title: "Wine crashes when configuring audio"
date: 2006-07-18
forum: Desktop Environments
---

### Post by HelloImHowie on 2006-07-18
I'm having a problem running winecfg. When I click on the Audio tab, it simply closes. The terminal outputs this:

```

ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/howie/.kde/socket-Lappy486.
can't create mcop directory
```

Currently, Wine has no audio whatsoever. My sound card is Intel HD Audio. If it helps, this is the contents of /dev/snd
```

controlC0  pcmC0D0c  pcmC0D0p  pcmC0D1c  timer
```
Help would be much appreciated :-)

---

### Post by galileon on 2006-07-28
sudo gedit /etc/modules


add this:

snd-seq


save, reboot....

or sudo modprobe snd-seq

---

