---
title: "Wine / Counterstrike online game launch issue"
date: 2007-02-20
forum: Gaming &amp; Leisure
---

### Post by CheeseEatingBulldog on 2007-02-20
I used to be able to play Condition Zero in wine, no problems, but now when I want to join a server it simply starts the game (to splash) and then dies back to steam (no error). The weird thing is that I can launch an off line game and have at it at bots, but can't launch a damn online game. Anyone have any ideas? 

The only thing I have is the Terminal output from wine:

> err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got b425c94f while expecting fb5386b8)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got c00f8568 while expecting 944aaa52)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got cfaf839f while expecting 28b76abe)
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file ole32.dbg ("")
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open


After which I am returned to the steam menu from which I started before launching the game.

---

### Post by CheeseEatingBulldog on 2007-02-21
I froced a package downgrade (to wine 22, 24, 25, 25 & 30). Only under 22 do I seen an error after it has actually showed the parsing server info, which gives that it cannot connect to the authentication server....

---

