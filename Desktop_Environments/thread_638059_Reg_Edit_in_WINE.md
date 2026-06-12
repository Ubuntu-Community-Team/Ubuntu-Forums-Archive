---
title: "Reg Edit in WINE?"
date: 2007-12-11
forum: Desktop Environments
---

### Post by johnbl on 2007-12-11
IN attempting to get a Win program to install in Wine I found the program rufused to install in the absence of IE. Attempted an install of IE 7 - bad move. That didn't and attempts to install IE6 SP1 stops on a " newer version present " message. There are references in the Wine system reg to Explorer but no idea which I could simply delete.

" uninstall " lists IE 6 as available for uninstall, however only offers in the end a repair and that fails with the suggestion to do a full reinstall... PERFECT Catch 22! <sigh>

Is there a way to edit out any references to the failed IE install bar a full uninstall of Wine?

Any ideas  .... please!

Johnbl

---

### Post by rax_m on 2007-12-12
If you type "regedit" in a terminal window you get the wine registry editor :D 

Not sure if it will help your problem tho'.

---

### Post by johnbl on 2007-12-12
Thank you for that. Didn't think of regedit <dugh> <g>
Nothing to loose so I'll try regedit to delete every thing I can find with Explorer mentioned. Presumably that won't stop a full wine removal if all else fails..

Johnbl

---

### Post by carlos1992 on 2007-12-12
Have you try with the actual IE that comes with Wine (is an .exe) cuz i just double click on that and done

---

### Post by johnbl on 2007-12-13
Well, learning more about Wine... Thanks for that pointer I had no idea wine came ' bundled ' as it were with IE. I just ' assumed ' I'd have to go get it and install from scratch.

It would appear that now I've done the full techie bit, - first break it, then read the manual - an uninstall of wine and a full reinstall would appear the smartest move.

Must go now, need to write out 500 times RTFM <VBG>

Johnbl

---

### Post by topolab on 2008-04-26
> **rax_m said:**
> If you type "regedit" in a terminal window you get the wine registry editor :D 

Not sure if it will help your problem tho'.

damn thanks!! i successfully installed autocad 2004 in my 8.04 tls

---

