---
title: "World of Warcraft on WINE (another thread?!)"
date: 2007-01-11
forum: Gaming &amp; Leisure
---

### Post by HolyCause on 2007-01-11
I recently tried installing World of Warcraft on my Linux partition (because I use it the most and enjoy playing WoW a lot) but it fails to work with WINE.

First, some information:

Hardware:
[LIST][*]Processor: AMD Athlon64 3800+[*]RAM: 1GB[*]Video card: NVIDIA GeForce 7900GT
[/LIST]

Software:
[LIST][*]Kubuntu 6.10 Edgy Eft[*]WINE version 0.9.22 (from Ubuntu respositories) (installed in /usr/ )[*]WINE version 0.9.29 (compiled from source - no modifications) (installed in my home folder)[*]nvidia-glx 1.0.8776+2 (from Ubuntu respositories)
[/LIST]

Whenever I try to run WoW from both versions of WINE I get this *exact* same error message:

```
[...bunch of FIXMEs...]
wine: Call from 0x4fe04c9d to unimplemented function GDI32.dll.GdiEntry1, aborting
```

I have looked for Google for hours on end looking for any problems relating to this GDI32 as well as any World of Warcraft problems with WINE but it seems that this problem doesn't exist...

I even tried adding the GDI32.DLL into winecfg's libs but if I change that WINE won't even start  XD

Help is greatly appreciated, as I'm completely stumped.

**edit:** I just installed and attempted to run Valve's Steam, and it segfaulted with the exact same error message...

**edit2:** Well, I'll be damned. I had set several libraries to "native" and they must have been maing calls to this "GDI32", which wasn't implemented (funny how error messages usually report the problems!  ;) ). I removed them and now both WoW and Steam work (albeit WoW flickers horribly, but that is something easily solved).

---

