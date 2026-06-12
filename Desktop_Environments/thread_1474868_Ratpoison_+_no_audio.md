---
title: "Ratpoison + no audio"
date: 2010-05-06
forum: Desktop Environments
---

### Post by Elegia on 2010-05-06
Hi all.

I've decided to give ratpoison a try, but I'm having trouble getting audio to work. I'm not sure what the problem is. Audio works perfect in gnome.

I've tried changing the volume with alsamixer, but I get the following error:

```
Cannot open mixer. No such file or directory.
```

I think the audio device itself is set up correctly based on the following output:

```
#:ls /dev/snd/control*
/dev/snd/controlC0
#:ls /dev | grep mixer
mixer
```

Any idea what could be the problem?

---

