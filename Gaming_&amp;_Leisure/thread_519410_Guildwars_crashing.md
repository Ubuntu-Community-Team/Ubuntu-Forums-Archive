---
title: "Guildwars crashing"
date: 2007-08-07
forum: Gaming &amp; Leisure
---

### Post by Lordmarshal on 2007-08-07
ok so i can open up guildwars fine and get into the game ...but i cant see the mouse.  after about a minute it locks up and then i get this code in terminal...could someone please help.

fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout (nil) is not supported
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout (nil) is not supported
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout (nil) is not supported
fixme:dbghelp:SymInitializeW what to do ??
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1a23798 ) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1a23798 ) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1a23798 ) : stub
fixme:dbghelp:SymInitializeW what to do ??
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1a23798 ) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1a23798 ) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1a23798 ) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1a23798 ) : stub
fixme:dbghelp:SymInitializeW what to do ??
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout (nil) is not supported
fixme:dbghelp:SymInitializeW what to do ??
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout (nil) is not supported
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
Killed

---

### Post by buttons on 2007-08-07
The mouse and the lock are different problems.  The first can be solved by right clicking a couple times (wine doesn't support animated cursors yet, and right clicking a few times gets the regular cursor back).

The second requires the too many concurrent lights patch, found in [this thread]("http://ubuntuforums.org/showthread.php?t=283122").

---

### Post by Hewus on 2007-08-07
Also try adding the -nosound flag. This worked for me, but at the cost of the obvious loss of sound.

---

### Post by Ziggyz on 2007-08-07
My guild wars doesnt even start or install properly for that matter.

---

### Post by MonkeyBoy on 2007-08-07
When I first installed Guild Wars with Wine, it wouldn't start so I read a few articles and threads on the subject and added the following to the end of my launch script:  ```
-dsound -noshaders -dx8 flags -repair -image
```

I'm not sure whether all of these are required but it certainly does the trick and even works in places like the Catacombs which have a reputation for crashing Wine.

It has to be worth a try.

---

### Post by buttons on 2007-08-07
At the moment, guildwars starts and runs fine (more than fine, it plays quite well in fact) for me with the -dsound, -dx8, and -noshaders command line arguments.  YMMV.

---

### Post by Lordmarshal on 2007-08-08
ok so i fixed the too many concurent lights issue but now i just keep getting this ...and im running Wine 0.9.4

fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1a60028 ) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1a60028 ) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1a60028 ) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1a60028) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1a60028 ) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1a60028 ) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1a60028) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1a60028 ) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1a60028 ) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1a60028 ) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1a60028 ) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1a60028 ) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1a60028 ) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1a60028 ) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1a60028 ) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1a60028 ) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1a60028 ) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1a60028 ) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1a60028 ) : stub

---

