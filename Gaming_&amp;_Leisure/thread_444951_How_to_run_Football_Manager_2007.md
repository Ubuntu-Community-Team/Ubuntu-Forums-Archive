---
title: "How to run Football Manager 2007?"
date: 2007-05-15
forum: Gaming &amp; Leisure
---

### Post by danny71 on 2007-05-15
Is it possible to run Football Manager 2007 with wine?

After installation, I get a message "Unload the debugger and try again".

---

### Post by danny71 on 2007-05-15
I've changed to Windows XP at winecfg, and after runnibg the program, I get this:

home@home-desktop:~$ wine /home/home/.wine/drive_c/ProgramFiles/SportsInteractive/FootballManager2007/fm.exe
Unknown device ID 5B62, please report. Assuming plain R300.
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135
Unknown device ID 5B62, please report. Assuming plain R300.
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
Unknown device ID 5B62, please report. Assuming plain R300.
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
home@home-desktop:~$ Unknown device ID 5B62, please report. Assuming plain R300.*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!

home@home-desktop:~$ winecfg
Unknown device ID 5B62, please report. Assuming plain R300.
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
Unknown device ID 5B62, please report. Assuming plain R300.
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
home@home-desktop:~$

Can you please help me?

---

### Post by Dev'olution on 2007-05-15
I have a similar problem except mine spews out:

```
kristian@kristian-laptop:/media/mydisk$ wine Setup\ FM2007\ PC.exe 
fixme:win:EnumDisplayDevicesW ((null),0,0x7c840e2c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x7c840e2c,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x2a8e9c0) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x2756828)->((nil),00001008)
fixme:system:SystemParametersInfoW Unimplemented action: 8202 (SPI_GETFONTSMOOTHINGTYPE)
fixme:system:SystemParametersInfoW Unimplemented action: 8204 (SPI_GETFONTSMOOTHINGCONTRAST)
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:imm:ImmGetDefaultIMEWnd (0x10032 - (nil) 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10022 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x20030 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10032 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10022 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x20030 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10032 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10022 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x20030 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10032 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10022 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x20030 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10032 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10022 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x20030 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10032 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10022 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x20030 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10032 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10022 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x20030 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10032 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10022 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x20030 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10032 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10022 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x20030 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10032 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10022 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10036 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x20030 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10032 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - 0x20030 0x166170 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10022 - 0x20030 0x166170 ): semi-stub
fixme:msvcrt:MSVCRT__sopen : pmode 0x01b6 ignored
fixme:msvcrt:MSVCRT__sopen : pmode 0x01b6 ignored
err:ole:CoUninitialize Mismatched CoUninitialize

```

But thats when i'm installing...

---

### Post by scotty2hott2k on 2007-05-15
you need a nocd crack/patch, that is why you are getting the debugger message. (you will need to set windows version to win98 iirc otherwise the cursor doesn't show up)

---

### Post by Dev'olution on 2007-05-15
mate, mine's currently telling me to run the installer in console mode :S

What do i do?

---

### Post by scotty2hott2k on 2007-05-15
[http://appdb.winehq.org/appview.php?iVersionId=7729](http://appdb.winehq.org/appview.php?iVersionId=7729) <-- read that, its a howto install and play the game via wine

---

### Post by michux on 2007-05-18
I know it's not what you were asking but: have you tried [BygFoot -- the free football manager](http://polishlinux.org/apps/football-managers/bygfoot-free-football-manager/) for Linux?
It may be not as sophisticated and flashy but it's surely playable.

---

