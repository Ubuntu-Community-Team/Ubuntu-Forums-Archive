---
title: "Auzentech X-Plosion Sound Cards - No sound"
date: 2009-04-05
forum: General Help
---

### Post by frenchcr on 2009-04-05
I have no sound from my Auzentech X-Plosion (CMI-8770 chipset)

How do I get the sound card to work under 9.04?

is there a driver i need?

Thanks,

Chris

ADDED:
[http://ubuntuforums.org/showthread.php?t=236826]("http://ubuntuforums.org/showthread.php?t=236826")
just found the above..no solution so far !!

---

### Post by WatchingThePain on 2009-04-05
Hi , did it work before and stop working because you upgraded to jaunty?.
If you have just installed a new sound card you might need to disable integrated sound in your bios if applicable.
What have you done so far?.
Did your card come with a driver disc.
Did you run lspci in the terminal?.

---

### Post by frenchcr on 2009-04-05
SOLVED

changed sound config to...

System > Preferences > C-Media CMI8770 ... (OSS)


...which works :guitar:

---

