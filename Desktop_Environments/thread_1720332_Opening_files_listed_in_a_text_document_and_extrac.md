---
title: "Opening files listed in a text document and extracting strings"
date: 2011-04-03
forum: Desktop Environments
---

### Post by 71GA on 2011-04-03
Hello!

I have a text document and within i have files listed. It looks like this.
```
ea3131_startup_entry.c
pad.c
ea3131_board.c
lpc313x_cgu_default.c
lpc313x_cgu_driver.c
lpc313x_dma_driver.c
```
I need bash comand to individually open each one of these files and read what files do they include. For example if i open ea3131_board.c i can find 2 lines at the top:
```
#include LPC_header.h
#include dma_driver.h
```
I need to extract strings LPC_header.h, dma_driver.h to a variable DEP or to another text file.

---

