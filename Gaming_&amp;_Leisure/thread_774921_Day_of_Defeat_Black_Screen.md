---
title: "Day of Defeat Black Screen"
date: 2008-04-29
forum: Gaming &amp; Leisure
---

### Post by kulotzy on 2008-04-29
Well i apparently made a thread in the wrong forums so here goes...

I was able to successfully install Steam and then Day of Defeat... However, i would run the game but after it loads to the menu, it goes black. Just a black screen... how can i fix this? Any other info. i need to provide? Thanks

---

### Post by Dark Aspect on 2008-04-29
> **kulotzy said:**
> Well i apparently made a thread in the wrong forums so here goes...

I was able to successfully install Steam and then Day of Defeat... However, i would run the game but after it loads to the menu, it goes black. Just a black screen... how can i fix this? Any other info. i need to provide?

Well since you created another thread,I'll pick up where we left off:

[QUOTE=kulotzy]And how do i use WINE to run the game? Post what output?[/QUOTE]

I meant with the terminal,goto Applications/Accessories/terminal.Then type in:

> wine /home/USERNAME/.wine/drive_c/Program\ Files/link/filename.exe

edit link/filename.exe to where ever the day of defeat executable is installed.This will show you every thing that is loaded when you start the game and in terms will help find the problem.

If you can't see the .wine folder in your home folder thats because its hidden,goto view/show hidden files in nautilus to see hidden directories.

---

### Post by kulotzy on 2008-04-29
THANKS AGAIN! ill try this out now. Thanks for not replying to the other thread, just let that one die.

---

### Post by kulotzy on 2008-04-29
I got this: 

> preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
Shutting down. . .

And an error:
> 
Fatal Error: Could not load module 'bin/vgui2.dll'

Using this:

```
wine /home/bros/.wine/drive_c/Valve/Steam/Steam.exe 
```

---

### Post by Dark Aspect on 2008-04-30
> **kulotzy said:**
> I got this: 



And an error:


Using this:

```
wine /home/bros/.wine/drive_c/Valve/Steam/Steam.exe 
```

I am really at a lost,sorry.I was hoping for maybe a missing dll file.One more idea try to disable ALSA sound since a poster on wine appDB said that helped.Use winecfg for that,you could also try vgui2.dll in the dll over rides.

---

