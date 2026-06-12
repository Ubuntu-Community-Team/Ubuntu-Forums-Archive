---
title: "wine binaries from 2005?"
date: 2006-05-26
forum: Desktop Environments
---

### Post by fat elvis on 2006-05-26
Hello Everyone-

I'm new to linux, and am trying to locate an old version of wine.  I checked sourceforge, and the winehq site...but no luck.  If anyone could point me in the right direction I'd appreciate it.  

Specifically I'm looking for the release from 20050211.  I need this version because I'm trying to get some old software running on my system.  It's the Remedy AR User Client 5.1...which I'm afraid I'm stuck with.

Thanks!

---

### Post by mostwanted on 2006-05-26
Wouldn't a newer version (e.g. repository version) support it just as well or maybe better?

---

### Post by fat elvis on 2006-05-26
[QUOTE=mostwanted]Wouldn't a newer version (e.g. repository version) support it just as well or maybe better?[/QUOTE]

One would think...I did some research and the folks that got it working were running older versions.  This is my first attempt to run any applications via wine...so it's quite possible I'm doing something wrong.

I installed wine, and then pointed it to the .exe that I'm trying to use.  It launches, begins to install and then freezes with the following error:

```

 wine user.exe
err:ole:get_unmarshaler_from_stream Failed to read common OBJREF header, 0x00000001
fixme:ole:NdrClearOutParameters (0x7d80e5a0,0x603a410a,0x7d80e6d4): stub
fixme:win:SetWindowTextA setting text "Remedy User Setup" of other process window (nil) should not use SendMessage
fixme:x11drv:X11DRV_SetWindowRgn not supported on other thread window 0x2002c
err:heap:HEAP_ValidateInUseArena Heap 0x7fd70000: prev arena 0x7dbd4f68 invalid for in-use 0x7dbd5018
err:ntdll:RtlpWaitForCriticalSection section 0x7fd70020 "heap.c: main process heap section" wait timed out in thread 000f, blocked by 000b, retrying (60 sec)
```

I did some searching online for ole erros and from what I could gather it was a problem with missing DLLs.  I got the necessary (or what I think are the necessary) DLLs from a functional Windows system...and copied them into ~/.wine/drive_c/windows/system/.  That did not resolve the problem.

At that point I searched some more and it ended up logging into the wine Applications Database.  It was there I found the information about the old versions of wine working with the Remedy AR User application.

If there's anything you can to do get me going in the right direction I'd appreciate it.

---

