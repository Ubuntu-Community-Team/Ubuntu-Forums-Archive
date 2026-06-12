---
title: "Age of Empires 3 : Asian Dynasties not working"
date: 2010-06-21
forum: Gaming &amp; Leisure
---

### Post by boaty on 2010-06-21
Hey everyone,

today I successfully installed both Age of Empires 3 and the Asian Dynasties expansion following the instructions in the Wine AppDB.

In addition, I've also patched AoE to version 1.14 and Asian Dynasties to 1.03.

However, whenever I attempt to play either game, I get this:
"Initialization Failed"

Wine Version:  1.1.42

The terminal output for Asian Dynasties:
```

zach@Zach-Desktop:~/.wine/drive_c/Program Files/Microsoft Games/Age of Empires III$ wine age3y.exe
fixme:msctf:LangBarMgr_GetShowFloatingStatus STUB:(0x1657b0)
fixme:msctf:LangBarMgr_ShowFloating STUB:(0x1657b0)
fixme:imm:ImmDisableTextFrameService Stub
fixme:imm:ImmReleaseContext (0x10058, 0x132310): stub
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:ole:CoCreateInstance no instance created for interface {3e90ade3-7594-4cb0-bb58-69628f5f458c} of class {529a9e6b-6587-4f23-ab9e-9c7d683e3c50}, hres is 0x80004002
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000001 not handled
fixme:win:EnumDisplayDevicesW ((null),0,0x32f048,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e9ac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e240,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e300,0x00000000), stub!
fixme:mixer:ALSA_MixerInit No master control found on HD-Audio Generic, disabling mixer
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:win:EnumDisplayDevicesW ((null),0,0x32eafc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e390,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e450,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:win:EnumDisplayDevicesW ((null),0,0x32e428,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32dcbc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32dd7c,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:win:EnumDisplayDevicesW ((null),0,0x32e930,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e1c4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e284,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
zach@Zach-Desktop:~/.wine/drive_c/Program Files/Microsoft Games/Age of Empires III$ wine age3y.exe
fixme:msctf:LangBarMgr_GetShowFloatingStatus STUB:(0x1657b0)
fixme:msctf:LangBarMgr_ShowFloating STUB:(0x1657b0)
fixme:imm:ImmDisableTextFrameService Stub
fixme:imm:ImmReleaseContext (0x10058, 0x132310): stub
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:ole:CoCreateInstance no instance created for interface {3e90ade3-7594-4cb0-bb58-69628f5f458c} of class {529a9e6b-6587-4f23-ab9e-9c7d683e3c50}, hres is 0x80004002
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000001 not handled
fixme:win:EnumDisplayDevicesW ((null),0,0x32f048,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e9ac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e240,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e300,0x00000000), stub!
fixme:mixer:ALSA_MixerInit No master control found on HD-Audio Generic, disabling mixer
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:win:EnumDisplayDevicesW ((null),0,0x32eafc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e390,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e450,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:win:EnumDisplayDevicesW ((null),0,0x32e428,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32dcbc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32dd7c,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:win:EnumDisplayDevicesW ((null),0,0x32e930,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e1c4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e284,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:msctf:LangBarMgr_GetShowFloatingStatus STUB:(0x131c18)
fixme:msctf:LangBarMgr_ShowFloating STUB:(0x131c18)

```

Thank for in advance for any help.  Let me know if there is anything else that would be useful in helping figure this out.

---

### Post by skaarr on 2010-06-21
Afraid I can't offer any expert advice, but have you tried running the command with sudo. I find that can sometimes solve wine problems. Good luck.

---

### Post by boaty on 2010-06-21
Okay, that actually helped a little.  It got to the point where I had to input the serial.  I thought I already did it, but who knows.  Once I typed it in though, the window closed.  Here's the output.
```

zach@Zach-Desktop:~/.wine/drive_c/Program Files/Microsoft Games/Age of Empires III$ sudo wine age3y.exe
wine: /home/zach/.wine is not owned by you
zach@Zach-Desktop:~/.wine/drive_c/Program Files/Microsoft Games/Age of Empires III$ sudo su
root@Zach-Desktop:/home/zach/.wine/drive_c/Program Files/Microsoft Games/Age of Empires III# wine age3y.exe
wine: created the configuration directory '/root/.wine'
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33cfd4
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\xpti.dat" 1 536870916 (nil) (nil) 0x1924dc (nil)
fixme:iphlpapi:NotifyAddrChange (Handle 0xa71e8d8, overlapped 0xa71e8e0): stub
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\compreg.dat" 1 536870916 (nil) (nil) 0x1e5c7b4 (nil)
wine: configuration in '/root/.wine' has been updated.
fixme:msctf:LangBarMgr_GetShowFloatingStatus STUB:(0x12cc30)
fixme:msctf:LangBarMgr_ShowFloating STUB:(0x12cc30)
fixme:msctf:LangBarMgr_GetShowFloatingStatus STUB:(0x16a718)
fixme:msctf:LangBarMgr_ShowFloating STUB:(0x16a718)
fixme:msctf:LangBarMgr_GetShowFloatingStatus STUB:(0x167170)
fixme:msctf:LangBarMgr_ShowFloating STUB:(0x167170)
fixme:msctf:LangBarMgr_GetShowFloatingStatus STUB:(0x167170)
fixme:msctf:LangBarMgr_ShowFloating STUB:(0x167170)
err:richedit:ReadStyleSheet missing style number
fixme:imm:ImmDisableTextFrameService Stub
fixme:imm:ImmReleaseContext (0x2005c, 0x131b00): stub
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:ole:CoCreateInstance no instance created for interface {3e90ade3-7594-4cb0-bb58-69628f5f458c} of class {529a9e6b-6587-4f23-ab9e-9c7d683e3c50}, hres is 0x80004002
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000001 not handled
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  159 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  4339
  Current serial number in output stream:  4339
root@Zach-Desktop:/home/zach/.wine/drive_c/Program Files/Microsoft Games/Age of Empires III# 

```

Edit:
After re-running the command, the screen just popped up and then disappeared.  The output was the same as above.  So...it needed the serial, but by the error it seems it may have been an incorrect one...?

More investigation is needed.

Edit 2:
So I decided to run AoE (without expansion) and this is what happened.  Same serial popping up, but then I got a peculiar error message instead of just closing.  I have a feeling that if I ran Asian Dynasties with the correct serial (my theory is that I mistyped it) the same thing would happen.

Error Popup states:
"Error loading the PID Generator DLL.  The DLL could not be found!
Please make sure the file is available in the installation directory."

```

root@Zach-Desktop:/home/zach/.wine/drive_c/Program Files/Microsoft Games/Age of Empires III# wine age3.exe
fixme:msctf:LangBarMgr_GetShowFloatingStatus STUB:(0x12ccb8)
fixme:msctf:LangBarMgr_ShowFloating STUB:(0x12ccb8)
fixme:msctf:LangBarMgr_GetShowFloatingStatus STUB:(0x16b080)
fixme:msctf:LangBarMgr_ShowFloating STUB:(0x16b080)
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\zach\\.wine\\drive_c\\Program Files\\Microsoft Games\\Age of Empires III\\PIDGen.dll") not found
fixme:msctf:LangBarMgr_GetShowFloatingStatus STUB:(0x16d530)
fixme:msctf:LangBarMgr_ShowFloating STUB:(0x16d530)
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\zach\\.wine\\drive_c\\Program Files\\Microsoft Games\\Age of Empires III\\PIDGen.dll") not found
fixme:msctf:LangBarMgr_GetShowFloatingStatus STUB:(0x16a590)
fixme:msctf:LangBarMgr_ShowFloating STUB:(0x16a590)
root@Zach-Desktop:/home/zach/.wine/drive_c/Program Files/Microsoft Games/Age of Empires III# 

```

---

