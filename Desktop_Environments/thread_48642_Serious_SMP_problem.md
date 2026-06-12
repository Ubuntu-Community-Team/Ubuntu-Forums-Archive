---
title: "Serious SMP problem"
date: 2005-07-13
forum: Desktop Environments
---

### Post by Sheep Me on 2005-07-13
After installing the SMP kernel (linux-686-smp) to make use of my P4 hyperthreading processor, I get the following error at startup, and my PS/2 keyboard isn't working:
> i8042.c: Can't read CTR while initializing i8042.

Searching Google, I found these ideas:
[list]
[*]I've tried adding 'i8042.noacpi=1' to my kernel parameters.
[*]I've looked for an option in my BIOS to disable USB emulation - no such thing - and I've looked for something with 'legacy support' in its name - no such thing either.
[/list] 

What can I do?

If I fail to sort this out, do you think it would give a better performance, if I disable hyperthreading support in the BIOS (and just use the default kernel)? And should I install Ubuntu all over, if I go from enabled hyperthreading to disabled hyperthreading, or will Linux automatically adjust to that change?

I'd really much appreciate any ideas you might have, even if you think they probably wouldn't help, that they are stupid or whatever. I'm a total n00b, so don't assume anything about me or what I've tried. :)

---

### Post by alastair on 2005-07-13
Try disabling hyperthreading. You probably won't notice a thing - Linux will cope fine.

---

