---
title: "cs1.6 randomly freezes"
date: 2007-04-22
forum: Gaming &amp; Leisure
---

### Post by boast on 2007-04-22
After this great feisty update, cs1.6 randomly freezes while I play.

[img]http://img160.imageshack.us/img160/2011/img1205cf1.jpg[/img]

---

### Post by boast on 2007-04-22
well, now it looks beautiful. 

[img]http://img57.imageshack.us/img57/7493/screenshotzy3.png[/img]

heres what the terminal shows

```
~$ steam
fixme:process:IsWow64Process (0xffffffff 0xc17e4c) stub!
fixme:shdocvw:ViewObject_SetAdvise (0xd8e1cc8)->(1 00000002 0x1262ca0)
fixme:shdocvw:PersistStreamInit_InitNew (0xd8e1cc8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xd8e1cc8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xd8e1cc8)->(ffffffff)
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0xd8e1d5c)->((null) 1 0x33bf4c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd8e1d5c)->((null) 25 2 0x33bf60 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd8e1d5c)->((null) 26 2 0x33bf60 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:shdocvw:ClientSite_GetContainer (0xd8e1d5c)->(0x33bf9c)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd8e1d5c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33c0c0 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0xfea69d8)->(L"" L"" 0 0x33c0d4)
fixme:shdocvw:BindStatusCallback_GetBindInfo (0xfea69d8)->(0x33c0d8 0x33bffc)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd8e1d5c)->((null) 29 2 0x33d708 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0xd8e1d5c)
fixme:shdocvw:ClientSite_GetContainer (0xd8e1d5c)->(0x33d718)
fixme:shdocvw:InPlaceFrame_SetStatusText (0xd8e1d5c)->(0xb7e0fc49)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd8e1d5c)->((null) 25 2 0x33d654 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd8e1d5c)->((null) 26 2 0x33d654 (nil))
fixme:mshtml:HTMLBodyElement_put_scroll (0x10736190)->(L"no")
fixme:mshtml:HTMLTextContainer_get_scrollWidth (0x10736194)->(0xb663e9c)
fixme:mshtml:HTMLTextContainer_get_scrollHeight (0x10736194)->(0xb663ea0)
fixme:mshtml:HTMLBodyElement_put_scroll (0x10736190)->(L"no")
fixme:mshtml:HTMLTextContainer_get_scrollWidth (0x10736194)->(0xb663e9c)
fixme:mshtml:HTMLTextContainer_get_scrollHeight (0x10736194)->(0xb663ea0)
fixme:mshtml:HTMLBodyElement_put_scroll (0x10736190)->(L"no")
fixme:mshtml:HTMLTextContainer_get_scrollWidth (0x10736194)->(0xb663e9c)
fixme:mshtml:HTMLTextContainer_get_scrollHeight (0x10736194)->(0xb663ea0)
err:systray:delete_icon invalid tray icon ID specified: 1d
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0xfe67238)->(1 00000002 0x1263530)
fixme:shdocvw:PersistStreamInit_InitNew (0xfe67238)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xfe67238)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xfe67238)->(ffffffff)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0xfe67238)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0xfe67238)
fixme:shdocvw:OleObject_Close (0xfe67238)->(1)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1a4188) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1a31f8)->((nil),00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1a31f8)->((nil),00000013)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1a31f8)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:mshtml:hidden_proc (0x200a0 49225 0 1)
fixme:shdocvw:ViewObject_SetAdvise (0x1ebc30)->(1 00000002 0x7ca038)
fixme:shdocvw:PersistStreamInit_InitNew (0x1ebc30)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1ebc30)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1ebc30)->(ffffffff)
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1ebc30)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1ebc30)
fixme:shdocvw:OleObject_Close (0x1ebc30)->(1)
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0xfe67238)->(1 00000002 0x1263548)
fixme:shdocvw:PersistStreamInit_InitNew (0xfe67238)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xfe67238)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xfe67238)->(ffffffff)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0xfe67238)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0xfe67238)
fixme:shdocvw:OleObject_Close (0xfe67238)->(1)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1a4188) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1a31f8)->((nil),00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1a31f8)->((nil),00000013)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1a31f8)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:shdocvw:ViewObject_SetAdvise (0x1ebc28)->(1 00000002 0x7ca038)
fixme:shdocvw:PersistStreamInit_InitNew (0x1ebc28)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1ebc28)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1ebc28)->(ffffffff)
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
fixme:mshtml:hidden_proc (0x200a0 49225 0 1)
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1ebc28)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1ebc28)
fixme:shdocvw:OleObject_Close (0x1ebc28)->(1)

```

---

### Post by buttons on 2007-04-22
From what I can gather with google and such, the unknown nb_ctl request appears to be a speech bug, and direct sound is giving you fits there in the second terminal, which is at least a semi-confirmation in my book.

> err:wave: DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave: DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".

Have you done this?

Are you sure you're using OSS?  You haven't done something silly like change your config to enable both MMap and Full duplex, have you?

---

### Post by boast on 2007-04-22
yeah, I did it. I don't know how to make sure im using OSS, but I would believe so.

cs1.6 is still freezing tho. (not the whole system now tho)

```
client callback thread error
client callback thread error
pipes.cpp (534) : Assertion Failed: bRet
interfacemap.h (74) : Assertion Failed: bufRet.GetUint8() == k_EClientCommandInterface
pipes.cpp (534) : Assertion Failed: bRet
interfacemap.h (405) : Assertion Failed: bufRet.GetUint8() == k_EClientCommandInterface
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x6827470)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x6827470)
fixme:shdocvw:OleObject_Close (0x6827470)->(1)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x6827f28)->((nil))
pipes.cpp (534) : Assertion Failed: bRet
interfacemap.h (31) : Assertion Failed: bufRet.GetUint8() == k_EClientCommandInterface
pipes.cpp (534) : Assertion Failed: bRet
interfacemap.h (31) : Assertion Failed: bufRet.GetUint8() == k_EClientCommandInterface
pipes.cpp (534) : Assertion Failed: bRet
interfacemap.h (405) : Assertion Failed: bufRet.GetUint8() == k_EClientCommandInterface
pipes.cpp (534) : Assertion Failed: bRet
steamclient.cpp (428) : Assertion Failed: pClientPipe->BWriteAndReadResult( buf, bufRet )
steamclient.cpp (439) : Assertion Failed: bufRet.TellPut() == sizeof(uint8)
steamclient.cpp (440) : Assertion Failed: bufRet.GetUint8() == k_EClientCommandDisconnectUser
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1ebb40)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1ebb40)
fixme:shdocvw:OleObject_Close (0x1ebb40)->(1)
pipes.cpp (534) : Assertion Failed: bRet
steamclient.cpp (428) : Assertion Failed: pClientPipe->BWriteAndReadResult( buf, bufRet )
steamclient.cpp (439) : Assertion Failed: bufRet.TellPut() == sizeof(uint8)
steamclient.cpp (440) : Assertion Failed: bufRet.GetUint8() == k_EClientCommandDisconnectUser

```

---

### Post by buttons on 2007-04-22
Whoa.

The only mention of this I found on google has to do with HLDS [problems with plugins]("http://bugs.alliedmods.net/?do=details&task_id=71").  In fact, searches for all of those errors are turning up HLDS-related things.

---

### Post by boast on 2007-04-22
hmmm, :(

---

### Post by x2x180 on 2007-04-23
do u have the tahoma font installed so u can read everything? lol i dont kno much about linux
but it looks like in ur screen of 1.6 u  dont have the font installed

---

### Post by buttons on 2007-04-23
It's just a thought, but have you tried using an earlier version of wine?

Older debs are available [here]("http://wine.budgetdedicated.com/archive/index.html").  I checked 1.6 today and it seems I'm getting the nb_ctl errors as well.  CS isn't freezing on me yet; though to be fair I didn't test too much.

---

### Post by buttons on 2007-04-25
Curiouser and curiouser!

I've gotten rid of the nb_ctl errors and my framerates are back to normal.  This may or may not work for you or anyone else.

Some google research into the nb_ctl errors reveals that it seems to stem from the speex codec.  I noticed that, thanks to having the pkg-voip.buildserver.net repo in my sources.list, my libspeex1 package was at version 1.1.12-4.feisty with some numbers after it, while the official version sits at 1.1.12-3.  Figuring that the upgrade to feisty had something to do with the problem, I removed the pkg-voip repo and downgraded the package.  I also downgraded wine to 0.9.32 because, well, I like it better.  Note that downgrading wine alone did NOT clear the errors for me.

Lo and behold, no more nb_ctl crap, and I played for an hour or two without issue.

hope that helps

---

### Post by boast on 2007-04-26
tried what you did, I stil get the errors :(

---

### Post by boast on 2007-04-28
the new wine update doesnt help

[img]http://img403.imageshack.us/img403/9427/screenshotfatalerrorgl9.png[/img]

err:ntdll:RtlpWaitForCriticalSection section 0x7dd76abc "audio.c: OSS_MSG_RING.msg_crst" wait timed out in thread 0044, blocked by 0043, retrying (60 sec)
Killed
client callback thread error
client callback thread error
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open

---

