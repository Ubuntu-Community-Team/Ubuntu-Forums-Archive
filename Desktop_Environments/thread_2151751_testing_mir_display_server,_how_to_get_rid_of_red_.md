---
title: "testing mir display server, how to get rid of red arrow following cursor?"
date: 2013-06-05
forum: Desktop Environments
---

### Post by pawloch on 2013-06-05
Hi, I've followed that instruction to install mir server:

[http://unity.ubuntu.com/mir/using_mir_on_pc.html](http://unity.ubuntu.com/mir/using_mir_on_pc.html)

and everything works great, except there is a big red arrow following my mouse. Anyone knows how to disable it?
When I move my mouse slowly its right where cursor is, but when I move my mouse faster it get desynchronized and it's really annoying

Thanks in advance.

---

### Post by sanderj on 2013-06-05
I can't answer your question. I do have a question for you: that page says "lsmod | grep drm", but not what the output should be. Should it contains the letters "mesa", or ... ?

On my Intel GPU system, I get

```
sander@hapee:~$ lsmod | grep drm
drm_kms_helper         49394  1 i915
drm                   286313  5 i915,drm_kms_helper
sander@hapee:~$
```

Is that good for MIR, or ... ?

---

### Post by pawloch on 2013-06-05
Hi,

I'm using laptop with dual graphic (intel hd3000 + nvidia 520m) and my output is:

```

drm_kms_helper         49082  2 i915,nouveau
drm                   295908  5 ttm,i915,drm_kms_helper,nouveau

```

so I think your output is quite ok. hope that helps.

---

### Post by grahammechanical on 2013-06-05
That sounds like something that was called mouse trails on another OS. Have you installed any tweaking utilities?

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]pawloch; Big red arrow: 
Mouse mark desktop effect (??)
key combo ctl+shift+meta for the start of that mouse
key combo again to mark the end ...

and I hope that key combo once more to remove that red arrow ....

seen this on another post
[/COLOR][INDENT=2][COLOR=#000000]
hope this helps

[/COLOR][/INDENT]

---

