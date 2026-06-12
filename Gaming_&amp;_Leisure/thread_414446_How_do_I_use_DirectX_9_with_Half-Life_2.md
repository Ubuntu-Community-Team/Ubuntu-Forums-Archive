---
title: "How do I use DirectX 9 with Half-Life 2?"
date: 2007-04-19
forum: Gaming &amp; Leisure
---

### Post by FoolsGold on 2007-04-19
Is it as simple as setting the -dxlevel 90 option in the HL2 properties?

When I used to run HL2 in Windows, the game would automatically detect the highest level your hardware could do and set it there (in my case, DX9). When I tried HL2 in Wine (without the -dxlevel switch), it would only detect 8.1.

Does Wine support DX9 functionality? If it does, why do you have to force -dxlevel 90? Shouldn't HL2 just detect it on the first run anyway, or do you have to do something else to enable it?

---

### Post by GameGod on 2007-04-20
Yes, just adding -dxlevel 90 to the HL2 properties in Steam will cause it to use DirectX 9 with WINE.

WINE's support for DirectX 9 is fairly recent (although it's over a year old), and it's possible you may get better performance with -dxlevel 80 (or 81), which is the only reason I can think of why they'd have it default to that. (WINE's DirectX 9 support is pretty darn good though these days.)

---

### Post by FoolsGold on 2007-04-20
Ah, OK. Performance does seem as the most likely reason for it defaulting to 80 or 81. Thanks anyway.

---

