---
title: "Half-Life 2 Demo crashes-Please Help..."
date: 2007-10-24
forum: Gaming &amp; Leisure
---

### Post by Espreon on 2007-10-24
Yeah I am trying to run the Half-Life 2 Demo under Wine and it crashes...
I installed it with Steam, when I try to run it, all it does is bring the screen resolution down to 640x480 and crashes, not even a flicker, but as the screen resolution is being brought down I can briefly see the Half-Life 2 logo in the window list applet.

System Specs:

Dell Inspiron E1705
ATI Radeon x1400
! GB of RAM
Wine 9.47
I am also using the fglrx driver and XGL

Terminal outputs:

```

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: C:\Program Files\Steam\ *.mix
dir: C:\Program Files\Steam\ *.asi
dir: C:\Program Files\Steam\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
fixme:shdocvw:ViewObject_SetAdvise (0x102db4b8)->(1 00000002 0x147c440)
fixme:shdocvw:PersistStreamInit_InitNew (0x102db4b8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x102db4b8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x102db4b8)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x102db908)->(1 00000002 0x147c4a8)
fixme:shdocvw:PersistStreamInit_InitNew (0x102db908)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x102db908)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x102db908)->(ffffffff)
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x34c5cc,0x00000000), stub!
err:systray:delete_icon invalid tray icon ID specified: 1
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0xffb6ed0)->(1 00000002 0x147d3c8)
fixme:shdocvw:PersistStreamInit_InitNew (0xffb6ed0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xffb6ed0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xffb6ed0)->(ffffffff)
fixme:process:IsWow64Process (0xffffffff 0x3e6e88) stub!
fixme:win:SetLayeredWindowAttributes (0x30096,0x00000000,56,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30096,0x00000000,56,2): stub!
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
fixme:win:SetLayeredWindowAttributes (0x30096,0x00000000,202,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30096,0x00000000,0,2): stub!
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0xffb6ed0)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0xffb6ed0)
fixme:shdocvw:OleObject_Close (0xffb6ed0)->(1)
fixme:win:EnumDisplayDevicesW ((null),0,0x34e174,0x00000000), stub!
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x138d90) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x138d90) Event query: Unimplemented, but pretending to be supported
fixme:avifile:AVIFileExit (): stub!

```

Tha

---

### Post by wiltk on 2007-10-26
Sounds like the same error I am getting while trying to launch Portal and Team Fortress 2 (full versions, have not tried HL2 or other games from Orange box yet).  I see the intro movie, then the game tried to go full screen, and quits back to just steam.  Same three errors before crash.  Can't figure it out :(

Also using fglrx (8.42 and AIGLX :))

---

