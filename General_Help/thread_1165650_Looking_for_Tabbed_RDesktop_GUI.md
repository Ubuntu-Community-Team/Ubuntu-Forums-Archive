---
title: "Looking for Tabbed RDesktop GUI"
date: 2009-05-20
forum: General Help
---

### Post by DemonBob on 2009-05-20
Hey guys, 


Was wondering if anyone knew of a Tabbed Rdesktop GUI for ubuntu? I'm a windows server administrator, and use RDP multiple times during the day, sometimes i have upwards of 10 RDP sessions open at a time. I use MRemote and Terminals on windows to give me this functionality, but was wondering if anyone know a application for Linux that does this?..

It is not an option to switch to VNC for the servers at this time.

---

### Post by albinootje on 2009-05-20
> **DemonBob said:**
> Was wondering if anyone knew of a Tabbed Rdesktop GUI for ubuntu? 

I'm not aware of software that runs on Ubuntu that can do that.

You could however try to find a Rdesktop client which has java support, to use tabs in your web browser with it :
[http://en.wikipedia.org/wiki/Comparison_of_remote_desktop_software](http://en.wikipedia.org/wiki/Comparison_of_remote_desktop_software)

And, since I was curious, I downloaded the portable version of mRemote, and tried running it with Wine in Ubuntu, which showed this :
```

$ wine ./mRemote.exe 
fixme:actctx:parse_manifest_buffer root element is L"asmv1:assembly", not <assembly>
install the Windows version of Mono to run .NET executables

```
After installing Mono...
```

fixme:actctx:parse_manifest_buffer root element is L"asmv1:assembly", not <assembly>
wine: Call from 0x7b844b20 to unimplemented function gdiplus.dll.GdipCreateFontFamilyFromName, aborting
err:seh:raise_exception Unhandled exception code c00000fd flags 0 addr 0x7b844bca

```

---

### Post by directhex on 2009-05-21
Can't find one in the archive. Vinagre is exactly what you want - but is VNC-only (no RDP)

---

### Post by DemonBob on 2009-05-21
Well, looks like I'll have to figure out something then. Honestly switching to VNC is not an option for me, we use VNC for our desktops support, but for servers we like to have auditing on at a per user basis, so we can see what was done when and where. Since VNC does not offer user authentication then it's out of the loop.

---

