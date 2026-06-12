---
title: "Goonzu problem with Server select"
date: 2007-07-27
forum: Gaming &amp; Leisure
---

### Post by joojle on 2007-07-27
Now Goonzu can run on my kubuntu 7.04 but I also have a problem with login. I click login button it show message "Now have Loged in to front server" but it does not show server select dialog. What should i do next.
I am also look in the terminal it show the connection is OK (I am using proxychains) but nothing show after i click OK.
:)
This is my wine output
```

joojle@joojle-desktop:~/.wine/drive_c/Program Files/NDOORS/GoonzuEng$ proxychains wine Goonzu
ProxyChains-3.1 (http://proxychains.sf.net)
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x17bb28) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x17b6d0)->(0x10024,00000011)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:shdocvw:PersistStorage_InitNew (0x1e21e8)->(0x7743b8)
fixme:shdocvw:WebBrowser_QueryInterface (0x1e21e8)->({0000011e-0000-0000-c000-000000000046} 0x34c59c) interface not supported
fixme:shdocvw:OleObject_SetHostNames (0x1e21e8)->(L"My Host Name", (null))
|S-chain|-<>-**ip**-<><>-**ip**-<--denied
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1e227c)->((null) 1 0x34cc50 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1e227c)->((null) 25 2 0x34cc64 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1e227c)->((null) 26 2 0x34cc64 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1e227c)->(0x34cca0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1e227c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x34cd4c (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x1e3800)->(L"" L"" 0 0x34cd80)
fixme:shdocvw:BindStatusCallback_GetBindInfo (0x1e3800)->(0x34cd84 0x34cd94)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x534f3f8)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x534ce98)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1e227c)->((null) 29 2 0x34cf44 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1e227c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1e227c)->((null) 26 2 0x34cf24 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1e227c)->((null) 29 2 0x34cf34 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1e227c)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1e227c)->((null) 35 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1e227c)->((null) 28 2 0x34ce9c (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1e227c)->(0x34ce30)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1e227c)->(0xb6ecb229)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1e227c)->((null) 25 2 0x34cd64 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1e227c)->((null) 26 2 0x34cd64 (nil))
fixme:shdocvw:DocHostUIHandler_UpdateUI (0x1e227c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1e227c)->((null) 21 2 (nil) (nil))
|S-chain|-<>-**ip**-<><>-**ip**-<><>-OK

```

---

