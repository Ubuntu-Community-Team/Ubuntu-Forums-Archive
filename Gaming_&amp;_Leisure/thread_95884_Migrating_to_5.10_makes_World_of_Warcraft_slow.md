---
title: "Migrating to 5.10 makes World of Warcraft slow"
date: 2005-11-27
forum: Gaming &amp; Leisure
---

### Post by Lacraia on 2005-11-27
I've stumbled upon this really wierd problem. With Ubuntu 5.04 I'm able to play World of Warcraft using Cedega, but if I install Ubuntu 5.10 the performance is so bad that I don't even consider trying. I've would like to put 5.10 on my thinkpad, because of the other upgrades, but with such bad performance it's not an option.

Does anyone have a clue about what the reason for this can be. I have a IBM ThinkPad R40 with these specs: (Maybe one software package can't handle the hardware properly.)
Intel Mobile Pentium M at 1.3GHz
512MB RAM
32MB RADEON ATI Mobility chipset
AC97 combatible sound

---

### Post by disler on 2005-11-27
Run glxinfo, does Direct Rendering (bout 3 or 4 lines from the top of the output) report as Yes or No? If you run fglrxinfo, what does it report?

What sort of fps does glxgears -printfps produce?

In WoW, while running around in a fairly low pop area, use ctrl-R to enable fps output, and check whether or not enabling/disabling the UI (using ctrl-Z) makes a significant difference.

---

### Post by Lacraia on 2005-12-23
Oh, thanks for the reply. I havn't had time looking into this for a while. 'Cause of the christmas holidays I found time for another try on 5.10. I still haven't installed WoW, instead I've been struggleing with fglrx (thinking that may solve the problem), but gotten nowhere.

glxinfo reports:
direct rendering: Yes

I haven't got fglrx functioning, so that doesn't report anything.

glxgears -printfps gives me just above 560 fps. I'm gonna install WoW tomorrow. I'll be back with more info then.

---

