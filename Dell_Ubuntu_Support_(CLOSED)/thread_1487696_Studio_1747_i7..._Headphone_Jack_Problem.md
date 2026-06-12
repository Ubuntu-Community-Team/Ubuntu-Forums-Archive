---
title: "Studio 1747 i7... Headphone Jack Problem"
date: 2010-05-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by AshRice on 2010-05-19
All, I've searched for this and other people seem to be having a different problem.

My problem is like the Studio 15 where the speakers mute but no sound comes out of the headphones. The addition of the line to "....m6" line to alsa-base.conf causes the speakers to fail completely.

```
$ lspci | grep -a Audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
02:00.1 Audio device: ATI Technologies Inc RV710/730

```

---

### Post by AshRice on 2010-05-20
Really? no dice... nothing?

---

### Post by merry_meerkat on 2010-07-29
Hello,
same machine here, however "...m6" did work for me. I.e. adding the following line to **/etc/modprobe.d/alsa-base.conf** solved the headphone problem:
```
options snd-hda-intel model=dell-m6
```

---

### Post by ptn107 on 2010-07-30
I just installed linux-backports-modules-alsa-lucid-generic.

---

