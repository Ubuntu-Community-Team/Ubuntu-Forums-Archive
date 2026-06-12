---
title: "Steam &amp; WIne"
date: 2006-08-20
forum: Gaming &amp; Leisure
---

### Post by Mutch on 2006-08-20
Hi GUys, im having a slight problem

I just installed steam via this guide "http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games"
it seems to work fine except when i run steam i don't see any text in the window. So i can't navigate around or anything.

Help?

THanks

---

### Post by Mutch on 2006-08-20
Hmmm i fixed the problem, I should have used the search function. Sorry guys.

This thread helped me:
[http://www.ubuntuforums.org/showthread.php?t=138076](http://www.ubuntuforums.org/showthread.php?t=138076)

---

### Post by Mutch on 2006-08-20
Ok So now i have another problem.

I had everything working fine. But next time i opened steam terminal started spitting this out

```
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
fixme:shdocvw:ViewObject_SetAdvise (0xd67b450)->(1 00000002 0x11217f0)
fixme:shdocvw:PersistStreamInit_InitNew (0xd67b450)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xd67b450)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xd67b450)->(ffffffff)
fixme:shdocvw:WebBrowser_put_Silent (0xd67b450)->(ffffffff)
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0xd67b4ec)->((null) 1 0x33d410 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd67b4ec)->((null) 25 0 0x33d424 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd67b4ec)->((null) 26 0 0x33d424 (nil))
fixme:shdocvw:ClDispatch_Invoke (0xd67b4ec)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d378 0x33d3c4 (nil) 0x33d388)
fixme:shdocvw:ClDispatch_Invoke (0xd67b4ec)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d338 0x33d384 (nil) 0x33d348)
fixme:shdocvw:ClDispatch_Invoke (0xd67b4ec)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d378 0x33d3c4 (nil) 0x33d388)
fixme:shdocvw:ClDispatch_Invoke (0xd67b4ec)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d338 0x33d384 (nil) 0x33d348)
fixme:shdocvw:ClDispatch_Invoke (0xd67b4ec)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d378 0x33d3c4 (nil) 0x33d388)
fixme:shdocvw:ClDispatch_Invoke (0xd67b4ec)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d378 0x33d3c4 (nil) 0x33d388)
fixme:shdocvw:ClDispatch_Invoke (0xd67b4ec)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d378 0x33d3c4 (nil) 0x33d388)
fixme:shdocvw:ClientSite_GetContainer (0xd67b4ec)->(0x33d450)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd67b4ec)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33d554 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0xf9068e0)->(L"" L"" 0 0x33d568)
fixme:shdocvw:BindStatusCallback_GetBindInfo (0xf9068e0)->(0x33d56c 0x33d4b0)
fixme:shdocvw:ClientSite_GetContainer (0xd67b4ec)->(0x33d75c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0xd67b4ec)->(0xb7e2d3d3)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd67b4ec)->((null) 25 0 0x33d698 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd67b4ec)->((null) 26 0 0x33d698 (nil))
fixme:mshtml:HTMLTextContainer_get_scrollWidth (0xf252cc4)->(0xb5249a0)
fixme:mshtml:HTMLTextContainer_get_scrollHeight (0xf252cc4)->(0xb5249a4)
fixme:mshtml:HTMLTextContainer_get_scrollWidth (0xf252cc4)->(0xb5249a0)
fixme:mshtml:HTMLTextContainer_get_scrollHeight (0xf252cc4)->(0xb5249a4)
fixme:mshtml:HTMLTextContainer_get_scrollWidth (0xf252cc4)->(0xb5249a0)
fixme:mshtml:HTMLTextContainer_get_scrollHeight (0xf252cc4)->(0xb5249a4)
err:systray:delete_icon invalid tray icon ID specified: 1d
fixme:process:SetProcessWorkingSetSize (0xffffffff,-1,-1): stub - harmless
fixme:mshtml:HlinkTarget_SetBrowseContext (0xd6e3c98)->((nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0xd67b4ec)->((null) 1 0x33d330 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd67b4ec)->((null) 25 0 0x33d344 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd67b4ec)->((null) 26 0 0x33d344 (nil))
fixme:shdocvw:ClDispatch_Invoke (0xd67b4ec)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d298 0x33d2e4 (nil) 0x33d2a8)
fixme:shdocvw:ClDispatch_Invoke (0xd67b4ec)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d258 0x33d2a4 (nil) 0x33d268)
fixme:shdocvw:ClDispatch_Invoke (0xd67b4ec)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d298 0x33d2e4 (nil) 0x33d2a8)
fixme:shdocvw:ClDispatch_Invoke (0xd67b4ec)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d258 0x33d2a4 (nil) 0x33d268)
fixme:shdocvw:ClDispatch_Invoke (0xd67b4ec)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d298 0x33d2e4 (nil) 0x33d2a8)
fixme:shdocvw:ClDispatch_Invoke (0xd67b4ec)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d298 0x33d2e4 (nil) 0x33d2a8)
fixme:shdocvw:ClDispatch_Invoke (0xd67b4ec)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d298 0x33d2e4 (nil) 0x33d2a8)
fixme:shdocvw:ClientSite_GetContainer (0xd67b4ec)->(0x33d370)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd67b4ec)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33d474 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0xd673768)->(L"" L"" 0 0x33d488)
fixme:shdocvw:BindStatusCallback_GetBindInfo (0xd673768)->(0x33d48c 0x33d3d0)
fixme:shdocvw:ClientSite_GetContainer (0xd67b4ec)->(0x33d75c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0xd67b4ec)->(0xb7e2d3d3)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd67b4ec)->((null) 25 0 0x33d698 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd67b4ec)->((null) 26 0 0x33d698 (nil))
fixme:mshtml:HTMLTextContainer_get_scrollWidth (0xf271b7c)->(0xb5249a0)
fixme:mshtml:HTMLTextContainer_get_scrollHeight (0xf271b7c)->(0xb5249a4)
fixme:mshtml:HTMLTextContainer_get_scrollWidth (0xf271b7c)->(0xb5249a0)
fixme:mshtml:HTMLTextContainer_get_scrollHeight (0xf271b7c)->(0xb5249a4)
fixme:mshtml:HTMLTextContainer_get_scrollWidth (0xf271b7c)->(0xb5249a0)
fixme:mshtml:HTMLTextContainer_get_scrollHeight (0xf271b7c)->(0xb5249a4)
Shutting down. . .
300client callback thread error

```

I have no idea what it means. The steam window won't close and doesn't work. Any ideas? Thanks guys.

Mutch

---

### Post by learnmelinux on 2006-08-20
that stuff is just debugging info, if everything is working fine then you can ignore it, to do so use the CLI to start steam with:

WINEDEBUG=-all wine directory/of/steam/Steam.exe

this should increse your performance a bit, i got an extra 10 fps in CS:source.

---

### Post by Mutch on 2006-08-21
> **learnmelinux said:**
> that stuff is just debugging info, if everything is working fine then you can ignore it,

The problem is its not working fine :(. Steam freezes, and i can't close it and i can't paly any games.

---

### Post by learnmelinux on 2006-08-21
sry, i seem to have misread your post. are you trying to minimize the steam window instead of closing it? its a known problem that minimizing will cause X to crash. what i did if i wanted to launch my games from within steam was to launch the game then quickly click the "x" in the steam window to close it, and the game would load normally.

alternativly, you can bypass steam altogether and launch the game from the command line by adding "-applaunch xxx" where xxx is a number corresponding to the game, so it would look like "WINEDEBUG=-all wine directory/of/steam/Steam.exe -applaunch xxx"

if you wanted to play CS:Source, you would replace xxx with 240. DOD:source would be 230 (i think). i dont know the other numbers but you can find it easily with a search. hope this helps.

---

