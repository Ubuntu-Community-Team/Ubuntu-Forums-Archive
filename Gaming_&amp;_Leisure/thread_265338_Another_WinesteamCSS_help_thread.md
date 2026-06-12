---
title: "Another Wine/steam/CSS help thread"
date: 2006-09-25
forum: Gaming &amp; Leisure
---

### Post by CAUSTICROUTER on 2006-09-25
Appartenly, Steam doesn't think there is enough Wine help threads, so it doesn't work right.
Ok, so steam runs fine, 100% awesome.  But, when I try and start CSS, it goes to the splash screen then crashes to desktop.
This is what the terminal outputs. I didn't know where I should cut it off, so I copied all of it.
Wine version-.0.9.21
I didn't use wine tools btw, and if i need to reinstall wine/steam, is there a way to backup CSS so i don't have to DL it again?
```
matt@matt-desktop:~$ cd .wine/drive_c/program_files/Valve/Steam
matt@matt-desktop:~/.wine/drive_c/program_files/Valve/Steam$ wine steam.exe
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:process:IsWow64Process (0xffffffff 0xb5741c) stub!
fixme:shdocvw:ViewObject_SetAdvise (0xd806bb0)->(1 00000002 0x1291810)
fixme:shdocvw:PersistStreamInit_InitNew (0xd806bb0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xd806bb0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xd806bb0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_Silent (0xd806bb0)->(ffffffff)
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0xd806c4c)->((null) 1 0x33d624 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd806c4c)->((null) 25 2 0x33d638 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd806c4c)->((null) 26 2 0x33d638 (nil))
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d58c 0x33d5d8 (nil) 0x33d59c)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d54c 0x33d598 (nil) 0x33d55c)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d58c 0x33d5d8 (nil) 0x33d59c)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d54c 0x33d598 (nil) 0x33d55c)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d58c 0x33d5d8 (nil) 0x33d59c)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d58c 0x33d5d8 (nil) 0x33d59c)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d58c 0x33d5d8 (nil) 0x33d59c)
fixme:shdocvw:ClientSite_GetContainer (0xd806c4c)->(0x33d664)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd806c4c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33d768 (nil))
fixme:mshtml:PersistMoniker_Load not supported pibc
err:systray:delete_icon invalid tray icon ID specified: 1d
fixme:process:SetProcessWorkingSetSize (0xffffffff,-1,-1): stub - harmless
fixme:mshtml:HlinkTarget_SetBrowseContext (0xd874298)->((nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0xd806c4c)->((null) 1 0x33d624 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd806c4c)->((null) 25 2 0x33d638 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd806c4c)->((null) 26 2 0x33d638 (nil))
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d58c 0x33d5d8 (nil) 0x33d59c)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d54c 0x33d598 (nil) 0x33d55c)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d58c 0x33d5d8 (nil) 0x33d59c)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d54c 0x33d598 (nil) 0x33d55c)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d58c 0x33d5d8 (nil) 0x33d59c)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d58c 0x33d5d8 (nil) 0x33d59c)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d58c 0x33d5d8 (nil) 0x33d59c)
fixme:shdocvw:ClientSite_GetContainer (0xd806c4c)->(0x33d664)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd806c4c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33d768 (nil))
fixme:mshtml:PersistMoniker_Load not supported pibc
fixme:mshtml:HlinkTarget_SetBrowseContext (0xd874298)->((nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0xd806c4c)->((null) 1 0x33d530 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd806c4c)->((null) 25 2 0x33d544 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd806c4c)->((null) 26 2 0x33d544 (nil))
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d458 0x33d4a4 (nil) 0x33d468)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d458 0x33d4a4 (nil) 0x33d468)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClientSite_GetContainer (0xd806c4c)->(0x33d570)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd806c4c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33d674 (nil))
fixme:mshtml:PersistMoniker_Load not supported pibc
fixme:mshtml:HlinkTarget_SetBrowseContext (0xd874458)->((nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0xd806c4c)->((null) 1 0x33d530 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd806c4c)->((null) 25 2 0x33d544 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd806c4c)->((null) 26 2 0x33d544 (nil))
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d458 0x33d4a4 (nil) 0x33d468)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d458 0x33d4a4 (nil) 0x33d468)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClientSite_GetContainer (0xd806c4c)->(0x33d570)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd806c4c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33d674 (nil))
fixme:mshtml:PersistMoniker_Load not supported pibc
fixme:mshtml:HlinkTarget_SetBrowseContext (0xd874458)->((nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0xd806c4c)->((null) 1 0x33d530 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd806c4c)->((null) 25 2 0x33d544 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd806c4c)->((null) 26 2 0x33d544 (nil))
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d458 0x33d4a4 (nil) 0x33d468)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d458 0x33d4a4 (nil) 0x33d468)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClientSite_GetContainer (0xd806c4c)->(0x33d570)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd806c4c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33d674 (nil))
fixme:mshtml:PersistMoniker_Load not supported pibc
fixme:mshtml:HlinkTarget_SetBrowseContext (0xd874458)->((nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0xd806c4c)->((null) 1 0x33d530 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd806c4c)->((null) 25 2 0x33d544 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd806c4c)->((null) 26 2 0x33d544 (nil))
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d458 0x33d4a4 (nil) 0x33d468)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d458 0x33d4a4 (nil) 0x33d468)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClientSite_GetContainer (0xd806c4c)->(0x33d570)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd806c4c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33d674 (nil))
fixme:mshtml:PersistMoniker_Load not supported pibc
fixme:mshtml:HlinkTarget_SetBrowseContext (0xd874458)->((nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0xd806c4c)->((null) 1 0x33d530 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd806c4c)->((null) 25 2 0x33d544 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd806c4c)->((null) 26 2 0x33d544 (nil))
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d458 0x33d4a4 (nil) 0x33d468)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d458 0x33d4a4 (nil) 0x33d468)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClientSite_GetContainer (0xd806c4c)->(0x33d570)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd806c4c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33d674 (nil))
fixme:mshtml:PersistMoniker_Load not supported pibc
fixme:mshtml:HlinkTarget_SetBrowseContext (0xd874280)->((nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0xd806c4c)->((null) 1 0x33d530 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd806c4c)->((null) 25 2 0x33d544 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd806c4c)->((null) 26 2 0x33d544 (nil))
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d458 0x33d4a4 (nil) 0x33d468)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d458 0x33d4a4 (nil) 0x33d468)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClDispatch_Invoke (0xd806c4c)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d498 0x33d4e4 (nil) 0x33d4a8)
fixme:shdocvw:ClientSite_GetContainer (0xd806c4c)->(0x33d570)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd806c4c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33d674 (nil))
fixme:mshtml:PersistMoniker_Load not supported pibc
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:shdocvw:ViewObject_SetAdvise (0xd8413d0)->(1 00000002 0x1294c48)
fixme:shdocvw:PersistStreamInit_InitNew (0xd8413d0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xd8413d0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xd8413d0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_Silent (0xd8413d0)->(ffffffff)
fixme:process:SetProcessWorkingSetSize (0xffffffff,-1,-1): stub - harmless
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0xd8413d0)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0xd8413d0)
fixme:shdocvw:OleObject_Close (0xd8413d0)->(1)
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
fixme:avifile:AVIFileExit (): stub!

```
Thank all of you for your patience and help.

---

### Post by hotspoons on 2006-09-26
I'm getting the same problem on wine 0.9.21 on Edgy. I spent a couple of hours googling this, and came up with nothing that helped much. This seems to be related to the latest version of Wine. I don't feel like compiling an older version from source, so I'll probably just wait it out, or maybe a fix will come along. My box is running the newest Nvidia drivers (9.something), and it has a 6600GT card on 32 bit Edgy.  Here's what the console tells me when I run "wine C:/Program\ Files/Steam/Steam.exe -windowed  -width 1024 height 768 -applaunch 240 -dxlevel 7 -novideo -heapsize 512000" (just the end part):

```

fixme:shdocvw:OleObject_Close (0xf3d6240)->(1)
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:avifile:AVIFileExit (): stub!
```

Anybody have a clue, or should I just wait?

---

### Post by Ferrat on 2006-09-26
It's a know problem with 0.9.21 and they ain't really sure why hehe but the wine guys are working on it, but afaik 0.9.21 will crash hl2/css ect for a pretty big chunk of ppl, but using 0.9.18-20 should work, but for ppl like me that plays WoW that finaly runs great, well Im not really wanna do that trade off.

There is however two "versions" of this bug, one that affects all 3D games and one that only affects Steam games, there is a fix for the one that crashes all games [http://bugs.winehq.org/show_bug.cgi?id=6205](http://bugs.winehq.org/show_bug.cgi?id=6205)

Edit:
you can try the patch with either problem, might help otherwise just reinstall wine

---

### Post by CAUSTICROUTER on 2006-09-26
Would you guys mind pointing me in the direction of how to install an older version of wine? I'm kind of a n00b as I just recently installed ubuntu, anyway's thanks for your help.I fixed it nvm, thanks.

---

### Post by CAUSTICROUTER on 2006-09-26
Ok, I had CSS working, I tried to join a server, works, then, it froze on Sending Client info... I Ctrl-alt-bckspc out of it, and it gave me a text screen asking for my login, which was abnormal.  Tyhen, it logged off, i logged back on, and it says the game is currently unavailable.
```
fixme:shdocvw:ViewObject_SetAdvise (0xd8d96f0)->(1 00000002 0x1294c80)
fixme:shdocvw:PersistStreamInit_InitNew (0xd8d96f0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xd8d96f0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xd8d96f0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_Silent (0xd8d96f0)->(ffffffff)
Cannot delete file c:\program_files\valve\steam\steamapps\mattcorreia\counter-strike source\bin\datacache.dll error 32
Cannot delete file c:\program_files\valve\steam\steamapps\mattcorreia\counter-strike source\bin\datacache.dll error 32
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0xd8d96f0)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0xd8d96f0)
fixme:shdocvw:OleObject_Close (0xd8d96f0)->(1)

```
I think it might be because there is a problem with the bin folder.

---

### Post by byoon on 2006-09-26
> **CAUSTICROUTER said:**
> Would you guys mind pointing me in the direction of how to install an older version of wine? I'm kind of a n00b as I just recently installed ubuntu, anyway's thanks for your help.I fixed it nvm, thanks.

I couldn't get CSS or HL2 to work with Wine 0.9.21 or 0.9.20, but was able to get it to work with 0.9.19.  The only problem is that the tray icon doesn't work in 0,9.19 so you have to manually kill Wine after you exit the game (or use File->Exit from Steam).

You can go to:

[http://wine.budgetdedicated.com/archive/index.html]("http://wine.budgetdedicated.com/archive/index.html")

Download Wine 0.9.19 (wine_0.9.19~winehq0~ubuntu~6.06-2_i386.deb)

Open up a console and cd to the directory you put it in (cd Desktop).

Run the following command:

dpkg -i wine_0.9.19~winehq0~ubuntu~6.06-2_i386.deb

Make sure you run winecfg and Allow Pixel Shader under the Graphics tab.

I get about 15-20 fps in HL2 (10 in open areas) with my 6600 GT 128 MB card.  Most things are set to high, but I set the shader and shadow setting to low in HL2.

---

### Post by CAUSTICROUTER on 2006-09-26
Thank you, but I resolved my problem that exact way, but with 0.9.20. I think something might of been corropted in the bin folder, but, I just rebooted and it works fine. Thank you all for your help.

---

### Post by terryfunk4life on 2006-09-28
i feel like a complete noob but how do "CD" ?

---

### Post by CAUSTICROUTER on 2006-09-28
What do you mean? Change directory's? simply type 
```
cd "enter/directory/here"
``` 
Remember that it is cap sensitive and if the folder has spaces in it, you need the quotes.

---

