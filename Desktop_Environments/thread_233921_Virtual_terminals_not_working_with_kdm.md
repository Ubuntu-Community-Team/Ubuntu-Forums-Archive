---
title: "Virtual terminals not working with kdm"
date: 2006-08-10
forum: Desktop Environments
---

### Post by clif2 on 2006-08-10
When I first installed Kubuntu the virtual terminals were available on ctrl-alt-[Fn], but now I no longer have access to them. It must have broken during an update. I'm not sure when it happened, and I don't know what's wrong or how to fix it.

kdmrc contains the line:

 ConsoleTTYs=tty1,tty2,tty3,tty4,tty5,tty6

Any idea what might be going on?

I really miss my virtual terminals. :(

---

### Post by avtolle on 2006-08-10
Do you have a nvidia card, and have you changed drivers there recently? [http://ubuntuforums.org/showthread.php?t=233161](http://ubuntuforums.org/showthread.php?t=233161) is the reason I asked.

---

### Post by clif2 on 2006-08-10
> Do you have a nvidia card, and have you changed drivers there recently?

No. Matrox G400 running on a relatively old box. Xorg with mga driver. Tried disabling dri extension as it's not really needed, but makes no difference.

---

### Post by clif2 on 2006-08-11
VCs were accessible but were off-screen. Changing console resolution in boot options helped. However, VC switching is sluggish, very little response to ctl-alt-[Fn]. Rest of the system is fine just VC switch that is unresponsive.

Any idea what causes this? How can it be fixed?

---

