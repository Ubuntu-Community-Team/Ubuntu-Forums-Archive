---
title: "cut &amp; paste"
date: 2005-08-12
forum: Desktop Environments
---

### Post by dr1445 on 2005-08-12
greetings forum

i have tried to do a copy and paste while in terminal. it can only copy and paste within the terminal. if i try to place the paste outside the terminal, web forum/desktop/home file etc. nothing happens, it only will paste within the terminal. is this normal behavior for kubuntu.
regards
dave

---

### Post by GeneralZod on 2005-08-12
It should be fine.  What terminal are you using?  I use konsole, and copying is done by selecting the text to copy, right-clicking, and selecting "copy" (note that the usual CTRL+C will *not* work in a terminal, since CTRL+C is the "STOP" signal! :)).  Pasting can be done via the pop-up menu (I think) or by SHIFT+INS (I think, again!).

Hope this helps!

---

### Post by dr1445 on 2005-08-12
yep, highlight>right click>select copy. i tried both the K>system>terminal and > root terminal. both have the same result. the machine is a intel slot 1cpu, 400mhz, 256ram.

---

### Post by kinus on 2005-08-12
or use one of the greatest linux features if you have a 3 button mouse or a mouse with a scroller. Select the text and then just middle click where you want it.

---

### Post by cwaldbieser on 2005-08-12
[QUOTE=dr1445]yep, highlight>right click>select copy. i tried both the K>system>terminal and > root terminal. both have the same result. the machine is a intel slot 1cpu, 400mhz, 256ram.[/QUOTE]
Do you have klipper running?  If you look in it's history, do you see the text you copied?

I wrote a little script that I put in my PATH so I can pipe output from konsole directly to the clipboard without having to highlight at all:

```
#!/bin/bash
##################################################
# A simple shell script that works in conjunction with
# the KDE DCOP server to let you pipe text to the
# klipboard.
#
# example:
# 
# $cat file | klipin
#
##################################################

a=$(cat)
dcop klipper klipper setClipboardContents "$a"
``` 

I wrote a companion called klipout, but it requires python + pydcop.

---

