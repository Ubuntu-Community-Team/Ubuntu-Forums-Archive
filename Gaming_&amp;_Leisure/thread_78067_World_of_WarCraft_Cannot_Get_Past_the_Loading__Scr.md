---
title: "World of WarCraft Cannot Get Past the Loading  Screen (Debug Info Included)"
date: 2005-10-17
forum: Gaming &amp; Leisure
---

### Post by Anchovie on 2005-10-17
My problem is when starting World of WarCraft using Cedega 4.4.3, I was able to log in and play fine when starting a new character. However when I try to log in to an existing character who sits inside Orgrimmar, the game freezes on loading screen, it's the screen after you selected your character and clicked on Enter World, the one with the blue progress bar. There's music and the mouse moves, but no other response, the only way out is Ctrl + Alt + Backspace.

I tried to run it in OpenGL with all the fixes suggested in the documentation, same problem except the mouse freezes as well, only way out is Ctrl + Alt + Backspace.

At first I  thought it's because too much stuff has to be rendered inside Orgrimmar so I had a friend moved my character to the Tauren newbie camp, but still can't log in.

Here's the exact error that's 'causing  the problem...

```
err:ntdll:display_wait_error Timeout. Retry with 60 secs: crit=0x417930f4 name="X11DRV_CritSection" ec=531 cc=531
err:ntdll:display_wait_error backtrace="0x4006373a,0x4006331f,0x40062d0f,0x40062cb2,0x400ca7b4,0x417429d9,0x41742ef1,0x4"...
err:ntdll:display_wait_error   crit (0x417930f4): lc 2 rc 2 ot 2 sem 8708 spin 0
```

Your help is greatly appreciated.

---

