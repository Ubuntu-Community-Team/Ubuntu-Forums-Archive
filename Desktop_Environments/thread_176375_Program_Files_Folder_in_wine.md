---
title: "Program Files Folder in wine"
date: 2006-05-14
forum: Desktop Environments
---

### Post by tamarku on 2006-05-14
Ok, I've been trying for awhile to get this thing to work.  I have followed instructions to a 'T'.  Now I am 100% I have it installed correctly but when I attempt to launch Internet Explorer I type in  "wine /home/kaos/.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE". When I hit enter I get an error saying that the folder Program does not exist??  Now I thought that Linux had problems with Folders and files that have spaces in them so how do I get around this?  I can cd too to get all the way through to /c/ but can't go any further.  Any help would be greatly appreciated.

---

### Post by louis_nichols on 2006-05-14
try this: wine /home/kaos/.wine/c/Program\ Files/Internet\ Explorer/IEXPLORE.EXE

notice how, toescape a space, you place a backslash in front of it

Or just use TAB to autocomplete, after pressing the first couple of letters of your target.

EDIT: another way is this:

wine "C:\Program Files\Internet Explorer\IEXPLORE.EXE"

just like in windows.

---

### Post by tamarku on 2006-05-14
Alright, I think I may have figured it out but not sure.  I didn't have the quotes " around /home/kaos/.wine/Program Files/Internet Explorer/IEXPLORE.EXE.  Once I put the quotes arount the path it opened up a blank window.  So it looks like it will work but the window stays blank.  Here are the terminal errors that popped up: 

[email]kaos@wintergreenubuntu:~/.wine[/email]/c$ wine "/home/kaos/.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE
> "
wine: cannot find '/home/kaos/.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE
'
[email]kaos@wintergreenubuntu:~/.wine[/email]/c$ wine "/home/kaos/.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE"
fixme:shdocvw:IEWinMain "" 1
fixme:rpc:I_RpcServerStartListening (0x10024): stub
fixme:rpc:I_RpcWindowProc (0x10024,0000001c,00000001,00000000): stub
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x7fdd95ec)->((null) 1 0x7faffb0c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x7fdd95ec)->((null) 25 0 0x7faffaf8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x7fdd95ec)->((null) 26 0 0x7faffaf8 (nil))
fixme:shdocvw:ClDispatch_Invoke (0x7fdd95ec)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7faffa84 0x7faffab0 (nil) 0x7faffa94)
fixme:shdocvw:ClDispatch_Invoke (0x7fdd95ec)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7faffa64 0x7faffa90 (nil) 0x7faffa74)
fixme:shdocvw:ClDispatch_Invoke (0x7fdd95ec)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7faffa84 0x7faffab0 (nil) 0x7faffa94)
fixme:shdocvw:ClDispatch_Invoke (0x7fdd95ec)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7faffa64 0x7faffa90 (nil) 0x7faffa74)
fixme:shdocvw:ClDispatch_Invoke (0x7fdd95ec)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7faffa84 0x7faffab0 (nil) 0x7faffa94)
fixme:shdocvw:ClDispatch_Invoke (0x7fdd95ec)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7faffa84 0x7faffab0 (nil) 0x7faffa94)
fixme:shdocvw:ClDispatch_Invoke (0x7fdd95ec)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7faffa84 0x7faffab0 (nil) 0x7faffa94)
fixme:shdocvw:ClientSite_GetContainer (0x7fdd95ec)->(0x7faffb2c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x7fdd95ec)->({000214d1-0000-0000-c000-000000000046} 37 0 0x7faffc18 (nil))
fixme:rpc:I_RpcWindowProc (0x10024,0000001c,00000000,00000000): stub
fixme:rpc:I_RpcServerStopListening (): stub
fixme:rpc:I_RpcWindowProc (0x10024,00000002,00000000,00000000): stub
fixme:rpc:I_RpcWindowProc (0x10024,00000082,00000000,00000000): stub
fixme:rpc:RpcServerUnregisterIf (IfSpec == (RPC_IF_HANDLE)^0x65f0cf10, MgrTypeUuid == (null), WaitForCallsToComplete == 1): stub
fixme:rpc:RpcServerUnregisterIf (IfSpec == (RPC_IF_HANDLE)^0x65f0cec8, MgrTypeUuid == (null), WaitForCallsToComplete == 1): stub
fixme:rpc:RpcServerUnregisterIf (IfSpec == (RPC_IF_HANDLE)^0x7fdd9270, MgrTypeUuid == (null), WaitForCallsToComplete == 1): stub
fixme:rpc:RpcServerUnregisterIf (IfSpec == (RPC_IF_HANDLE)^0x7fdc7df0, MgrTypeUuid == (null), WaitForCallsToComplete == 1): stub
[email]kaos@wintergreenubuntu:~/.wine[/email]/c$


Thanks for the help Louis!! Now if you could figure this one out I'd be in Hog Heaven, or should I say Breezy Badger Heaven.

---

### Post by louis_nichols on 2006-05-14
Sorry, man, but my knowledge doesn't go that far. Try searching the forums and google, because there are certainly lots of ppl that have experienced what you're going through.

I only installed IE once, and that was through winetools. Worked like a charm. Now thay say winetools isn't recommended anymore, cause it messes up the initial wine configuration... I don't know. But if you REALLY need IE (and only IE, in case winetools really makes installing other stuff difficult) then it's definitely the way to go.

---

