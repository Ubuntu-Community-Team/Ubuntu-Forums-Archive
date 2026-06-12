---
title: "Sid Meier's Colonization under Wine [feisty]"
date: 2007-06-05
forum: Gaming &amp; Leisure
---

### Post by lazerous on 2007-06-05
I'm trying to get Colonization running on Feisty.  I realize that someone has been nice enough to create "freecol" however the original still holds a place in my heart :) .

Anyhow...I tried to install the game using: wine install.exe however the output was crazy...

//OUTPUT
lazerous@lazerous-desktop:~/Desktop/Colonization$ wine INSTALL.EXE
Warning: unprotecting memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.
wine: Unhandled page fault on read access to 0xffffffff at address 0x7bc6818f (thread 0023), starting debugger...
//OUTPUT

Everything started to go banana sandwich after that point and I didn't understand a lick of it...

Any ideas?

[Laz]

---

### Post by lazerous on 2007-06-07
If anyone was wondering, I checked around and decided to use Dosbox for emulation instead.  I don't know if the issue was that I was trying to install the dos version of Colonization using wine or what.

I got everything working fairly easily.

[Laz]

---

