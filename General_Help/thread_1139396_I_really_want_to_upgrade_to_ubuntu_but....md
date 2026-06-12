---
title: "I really want to upgrade to ubuntu but..."
date: 2009-04-27
forum: General Help
---

### Post by Ishmael42 on 2009-04-27
but I need to get wow running otherwise I can't I got it installed using wine, and it can get through the opening cinematic but then it fails and gives me this error, please help

==============================================================================
World of WarCraft (build 9806)

Exe:      C:\Program Files\World of Warcraft\Wow.exe
Time:     Apr 26, 2009  9:42:16.904 PM
User:     root
Computer: kevin-laptop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:    C:\Program Files\World of Warcraft\Wow.exe
Exception:    0xC0000005 (ACCESS_VIOLATION) at 0023:0061CC3D

The instruction at "0x0061CC3D" referenced memory at "0xFAB85BF0".
The memory could not be "written".


WoWBuild: 9806
Settings: 
SET readTOS "-1"
SET readEULA "-1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET locale "enUS"
SET movie "0"
SET showToolsUI "1"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "777.000000"
SET specular "1"
SET groundEffectDensity "24"
SET projectedTextures "1"
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=01137528  EBX=09C83F88  ECX=FAB85BF0  EDX=02B83530  ESI=09C83F88
EDI=3F7FFFFF  EBP=003AF8BC  ESP=003AF8B0  EIP=0061CC3D  FLG=00210286
CS =0023      DS =002B      ES =002B      SS =002B      FS =0063      GS =006B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 19/19 threads...

--- Thread ID: 62 ---
7BC726C5 0BD9E624 0001:000616C5 C:\windows\system32\ntdll.dll
7BC729C2 0BD9E654 0001:000619C2 C:\windows\system32\ntdll.dll
7B88FDB2 0BD9E794 0001:0006EDB2 C:\windows\system32\KERNEL32.dll
7E09FBEB 0BD9E7C4 0001:0002EBEB C:\windows\system32\winex11.drv
7ED0F7C5 0BD9E974 0001:0007E7C5 C:\windows\system32\user32.dll
7ED0F82F 0BD9E994 0001:0007E82F C:\windows\system32\user32.dll
004417F9 0BD9E9C4 0001:000407F9 C:\Program Files\World of Warcraft\Wow.exe
004427FA 0BD9E9D8 0001:000417FA C:\Program Files\World of Warcraft\Wow.exe
008D4D1F 0BD9EA10 0001:004D3D1F C:\Program Files\World of Warcraft\Wow.exe
008D4DC4 0BD9EA28 0001:004D3DC4 C:\Program Files\World of Warcraft\Wow.exe
7BC75FA2 0BD9EAC8 0001:00064FA2 C:\windows\system32\ntdll.dll
7BC76170 0BD9F3B8 0001:00065170 C:\windows\system32\ntdll.dll
F7E594FF 0BD9F4B8 0000:00000000 <unknown>

--- Thread ID: 61 ---
7BC726C5 0BC2E848 0001:000616C5 C:\windows\system32\ntdll.dll
7BC729C2 0BC2E878 0001:000619C2 C:\windows\system32\ntdll.dll
7B88FDB2 0BC2E9B8 0001:0006EDB2 C:\windows\system32\KERNEL32.dll
7B88FFAC 0BC2E9D8 0001:0006EFAC C:\windows\system32\KERNEL32.dll
008916A5 0BC2E9F4 0001:004906A5 C:\Program Files\World of Warcraft\Wow.exe
00850ADA 0BC2EA04 0001:0044FADA C:\Program Files\World of Warcraft\Wow.exe
00851130 0BC2EA18 0001:00450130 C:\Program Files\World of Warcraft\Wow.exe
7BC7413E 0BC2EA28 0001:0006313E C:\windows\system32\ntdll.dll
7BC75FA2 0BC2EAC8 0001:00064FA2 C:\windows\system32\ntdll.dll
7BC76170 0BC2F3B8 0001:00065170 C:\windows\system32\ntdll.dll
F7E594FF 0BC2F4B8 0000:00000000 <unknown>

--- Thread ID: 60 ---
7BC726C5 0BABE624 0001:000616C5 C:\windows\system32\ntdll.dll
7BC729C2 0BABE654 0001:000619C2 C:\windows\system32\ntdll.dll
7B88FDB2 0BABE794 0001:0006EDB2 C:\windows\system32\KERNEL32.dll
7E09FBEB 0BABE7C4 0001:0002EBEB C:\windows\system32\winex11.drv
7ED0F7C5 0BABE974 0001:0007E7C5 C:\windows\system32\user32.dll
7ED0F82F 0BABE994 0001:0007E82F C:\windows\system32\user32.dll
004417F9 0BABE9C4 0001:000407F9 C:\Program Files\World of Warcraft\Wow.exe
004427FA 0BABE9D8 0001:000417FA C:\Program Files\World of Warcraft\Wow.exe
008D4D1F 0BABEA10 0001:004D3D1F C:\Program Files\World of Warcraft\Wow.exe
008D4DC4 0BABEA28 0001:004D3DC4 C:\Program Files\World of Warcraft\Wow.exe
7BC75FA2 0BABEAC8 0001:00064FA2 C:\windows\system32\ntdll.dll
7BC76170 0BABF3B8 0001:00065170 C:\windows\system32\ntdll.dll
F7E594FF 0BABF4B8 0000:00000000 <unknown>

--- Thread ID: 59 ---
7BC726C5 0657E848 0001:000616C5 C:\windows\system32\ntdll.dll
7BC729C2 0657E878 0001:000619C2 C:\windows\system32\ntdll.dll
7B88FDB2 0657E9B8 0001:0006EDB2 C:\windows\system32\KERNEL32.dll
7B88FFAC 0657E9D8 0001:0006EFAC C:\windows\system32\KERNEL32.dll
008916A5 0657E9F4 0001:004906A5 C:\Program Files\World of Warcraft\Wow.exe
00850ADA 0657EA04 0001:0044FADA C:\Program Files\World of Warcraft\Wow.exe
00851130 0657EA18 0001:00450130 C:\Program Files\World of Warcraft\Wow.exe
7BC7413E 0657EA28 0001:0006313E C:\windows\system32\ntdll.dll
7BC75FA2 0657EAC8 0001:00064FA2 C:\windows\system32\ntdll.dll
7BC76170 0657F3B8 0001:00065170 C:\windows\system32\ntdll.dll
F7E594FF 0657F4B8 0000:00000000 <unknown>

--- Thread ID: 57 ---
7BC726C5 0B94E968 0001:000616C5 C:\windows\system32\ntdll.dll
7BC729C2 0B94E998 0001:000619C2 C:\windows\system32\ntdll.dll
7BC72A1C 0B94E9B8 0001:00061A1C C:\windows\system32\ntdll.dll
7BC781C5 0B94EA18 0001:000671C5 C:\windows\system32\ntdll.dll
7BC7413E 0B94EA28 0001:0006313E C:\windows\system32\ntdll.dll
7BC75FA2 0B94EAC8 0001:00064FA2 C:\windows\system32\ntdll.dll
7BC76170 0B94F3B8 0001:00065170 C:\windows\system32\ntdll.dll
F7E594FF 0B94F4B8 0000:00000000 <unknown>

--- Thread ID: 56 ---
7BC726C5 0830E624 0001:000616C5 C:\windows\system32\ntdll.dll
7BC729C2 0830E654 0001:000619C2 C:\windows\system32\ntdll.dll
7B88FDB2 0830E794 0001:0006EDB2 C:\windows\system32\KERNEL32.dll
7E09FBEB 0830E7C4 0001:0002EBEB C:\windows\system32\winex11.drv
7ED0F7C5 0830E974 0001:0007E7C5 C:\windows\system32\user32.dll
7ED0F82F 0830E994 0001:0007E82F C:\windows\system32\user32.dll
004417F9 0830E9C4 0001:000407F9 C:\Program Files\World of Warcraft\Wow.exe
004427FA 0830E9D8 0001:000417FA C:\Program Files\World of Warcraft\Wow.exe
008D4D1F 0830EA10 0001:004D3D1F C:\Program Files\World of Warcraft\Wow.exe
008D4DC4 0830EA28 0001:004D3DC4 C:\Program Files\World of Warcraft\Wow.exe
7BC75FA2 0830EAC8 0001:00064FA2 C:\windows\system32\ntdll.dll
7BC76170 0830F3B8 0001:00065170 C:\windows\system32\ntdll.dll
F7E594FF 0830F4B8 0000:00000000 <unknown>

--- Thread ID: 55 ---
7BC726C5 0819E608 0001:000616C5 C:\windows\system32\ntdll.dll
7BC729C2 0819E638 0001:000619C2 C:\windows\system32\ntdll.dll
7B88FDB2 0819E778 0001:0006EDB2 C:\windows\system32\KERNEL32.dll
7B88FF0A 0819E798 0001:0006EF0A C:\windows\system32\KERNEL32.dll
00462CFB 0819E9F0 0001:00061CFB C:\Program Files\World of Warcraft\Wow.exe
0046243E 0819E9FC 0001:0006143E C:\Program Files\World of Warcraft\Wow.exe
0053AF87 0819EA18 0001:00139F87 C:\Program Files\World of Warcraft\Wow.exe
7BC7413E 0819EA28 0001:0006313E C:\windows\system32\ntdll.dll
7BC75FA2 0819EAC8 0001:00064FA2 C:\windows\system32\ntdll.dll
7BC76170 0819F3B8 0001:00065170 C:\windows\system32\ntdll.dll
F7E594FF 0819F4B8 0000:00000000 <unknown>

--- Thread ID: 54 ---
7BC726C5 0802E838 0001:000616C5 C:\windows\system32\ntdll.dll
7BC729C2 0802E868 0001:000619C2 C:\windows\system32\ntdll.dll
7B88FDB2 0802E9A8 0001:0006EDB2 C:\windows\system32\KERNEL32.dll
7B88FFAC 0802E9C8 0001:0006EFAC C:\windows\system32\KERNEL32.dll
0053F4F0 0802E9D8 0001:0013E4F0 C:\Program Files\World of Warcraft\Wow.exe
00462495 0802E9F0 0001:00061495 C:\Program Files\World of Warcraft\Wow.exe
00462601 0802E9FC 0001:00061601 C:\Program Files\World of Warcraft\Wow.exe
0053AF87 0802EA18 0001:00139F87 C:\Program Files\World of Warcraft\Wow.exe
7BC7413E 0802EA28 0001:0006313E C:\windows\system32\ntdll.dll
7BC75FA2 0802EAC8 0001:00064FA2 C:\windows\system32\ntdll.dll
7BC76170 0802F3B8 0001:00065170 C:\windows\system32\ntdll.dll
F7E594FF 0802F4B8 0000:00000000 <unknown>

--- Thread ID: 53 ---
7BC726C5 07EBE850 0001:000616C5 C:\windows\system32\ntdll.dll
7BC729C2 07EBE880 0001:000619C2 C:\windows\system32\ntdll.dll
7B88FDB2 07EBE9C0 0001:0006EDB2 C:\windows\system32\KERNEL32.dll
7B88FFAC 07EBE9E0 0001:0006EFAC C:\windows\system32\KERNEL32.dll
0053F4F0 07EBE9F0 0001:0013E4F0 C:\Program Files\World of Warcraft\Wow.exe
007A8D0B 07EBEA18 0001:003A7D0B C:\Program Files\World of Warcraft\Wow.exe
7BC7413E 07EBEA28 0001:0006313E C:\windows\system32\ntdll.dll
7BC75FA2 07EBEAC8 0001:00064FA2 C:\windows\system32\ntdll.dll
7BC76170 07EBF3B8 0001:00065170 C:\windows\system32\ntdll.dll
F7E594FF 07EBF4B8 0000:00000000 <unknown>

--- Thread ID: 52 ---
7B8900C2 07D4E9D8 0001:0006F0C2 C:\windows\system32\KERNEL32.dll
7B890105 07D4E9F8 0001:0006F105 C:\windows\system32\KERNEL32.dll
0085093D 07D4EA04 0001:0044F93D C:\Program Files\World of Warcraft\Wow.exe
0085116C 07D4EA18 0001:0045016C C:\Program Files\World of Warcraft\Wow.exe
7BC7413E 07D4EA28 0001:0006313E C:\windows\system32\ntdll.dll
7BC75FA2 07D4EAC8 0001:00064FA2 C:\windows\system32\ntdll.dll
7BC76170 07D4F3B8 0001:00065170 C:\windows\system32\ntdll.dll
F7E594FF 07D4F4B8 0000:00000000 <unknown>

--- Thread ID: 51 ---
7B8900C2 069CE9D8 0001:0006F0C2 C:\windows\system32\KERNEL32.dll
7B890105 069CE9F8 0001:0006F105 C:\windows\system32\KERNEL32.dll
0085093D 069CEA04 0001:0044F93D C:\Program Files\World of Warcraft\Wow.exe
0085116C 069CEA18 0001:0045016C C:\Program Files\World of Warcraft\Wow.exe
7BC7413E 069CEA28 0001:0006313E C:\windows\system32\ntdll.dll
7BC75FA2 069CEAC8 0001:00064FA2 C:\windows\system32\ntdll.dll
7BC76170 069CF3B8 0001:00065170 C:\windows\system32\ntdll.dll
F7E594FF 069CF4B8 0000:00000000 <unknown>

--- Thread ID: 50 ---
7DFF830B 0609E9C8 0001:0000730B C:\windows\system32\winealsa.drv
7E00B4EC 0609EA18 0001:0001A4EC C:\windows\system32\winealsa.drv
7BC7413E 0609EA28 0001:0006313E C:\windows\system32\ntdll.dll
7BC75FA2 0609EAC8 0001:00064FA2 C:\windows\system32\ntdll.dll
7BC76170 0609F3B8 0001:00065170 C:\windows\system32\ntdll.dll
F7E594FF 0609F4B8 0000:00000000 <unknown>

--- Thread ID: 49 ---
7B8900C2 0685E9D8 0001:0006F0C2 C:\windows\system32\KERNEL32.dll
7B890105 0685E9F8 0001:0006F105 C:\windows\system32\KERNEL32.dll
0085093D 0685EA04 0001:0044F93D C:\Program Files\World of Warcraft\Wow.exe
0085116C 0685EA18 0001:0045016C C:\Program Files\World of Warcraft\Wow.exe
7BC7413E 0685EA28 0001:0006313E C:\windows\system32\ntdll.dll
7BC75FA2 0685EAC8 0001:00064FA2 C:\windows\system32\ntdll.dll
7BC76170 0685F3B8 0001:00065170 C:\windows\system32\ntdll.dll
F7E594FF 0685F4B8 0000:00000000 <unknown>

--- Thread ID: 48 ---
7B8900C2 066EE9D8 0001:0006F0C2 C:\windows\system32\KERNEL32.dll
7B890105 066EE9F8 0001:0006F105 C:\windows\system32\KERNEL32.dll
0085093D 066EEA04 0001:0044F93D C:\Program Files\World of Warcraft\Wow.exe
0085116C 066EEA18 0001:0045016C C:\Program Files\World of Warcraft\Wow.exe
7BC7413E 066EEA28 0001:0006313E C:\windows\system32\ntdll.dll
7BC75FA2 066EEAC8 0001:00064FA2 C:\windows\system32\ntdll.dll
7BC76170 066EF3B8 0001:00065170 C:\windows\system32\ntdll.dll
F7E594FF 066EF4B8 0000:00000000 <unknown>

--- Thread ID: 46 ---
7EDFE1D7 0640EA18 0001:0002D1D7 C:\windows\system32\winmm.dll
7BC7413E 0640EA28 0001:0006313E C:\windows\system32\ntdll.dll
7BC75FA2 0640EAC8 0001:00064FA2 C:\windows\system32\ntdll.dll
7BC76170 0640F3B8 0001:00065170 C:\windows\system32\ntdll.dll
F7E594FF 0640F4B8 0000:00000000 <unknown>

--- Thread ID: 44 ---
7BC726C5 040DE844 0001:000616C5 C:\windows\system32\ntdll.dll
7BC729C2 040DE874 0001:000619C2 C:\windows\system32\ntdll.dll
7B88FDB2 040DE9B4 0001:0006EDB2 C:\windows\system32\KERNEL32.dll
7B88FFAC 040DE9D4 0001:0006EFAC C:\windows\system32\KERNEL32.dll
0053F4F0 040DE9E4 0001:0013E4F0 C:\Program Files\World of Warcraft\Wow.exe
00478102 040DE9FC 0001:00077102 C:\Program Files\World of Warcraft\Wow.exe
0053AF87 040DEA18 0001:00139F87 C:\Program Files\World of Warcraft\Wow.exe
7BC7413E 040DEA28 0001:0006313E C:\windows\system32\ntdll.dll
7BC75FA2 040DEAC8 0001:00064FA2 C:\windows\system32\ntdll.dll
7BC76170 040DF3B8 0001:00065170 C:\windows\system32\ntdll.dll
F7E594FF 040DF4B8 0000:00000000 <unknown>

--- Thread ID: 43 ---
7B8900C2 03A0E5B0 0001:0006F0C2 C:\windows\system32\KERNEL32.dll
7B890105 03A0E5D0 0001:0006F105 C:\windows\system32\KERNEL32.dll
0046EC9D 03A0E5DC 0001:0006DC9D C:\Program Files\World of Warcraft\Wow.exe
007D5E45 03A0E9FC 0001:003D4E45 C:\Program Files\World of Warcraft\Wow.exe
0053AF87 03A0EA18 0001:00139F87 C:\Program Files\World of Warcraft\Wow.exe
7BC7413E 03A0EA28 0001:0006313E C:\windows\system32\ntdll.dll
7BC75FA2 03A0EAC8 0001:00064FA2 C:\windows\system32\ntdll.dll
7BC76170 03A0F3B8 0001:00065170 C:\windows\system32\ntdll.dll
F7E594FF 03A0F4B8 0000:00000000 <unknown>

--- Thread ID: 42 ---
7B8900C2 01CCE990 0001:0006F0C2 C:\windows\system32\KERNEL32.dll
7B890105 01CCE9B0 0001:0006F105 C:\windows\system32\KERNEL32.dll
00424754 01CCE9D8 0001:00023754 C:\Program Files\World of Warcraft\Wow.exe
008D4D1F 01CCEA10 0001:004D3D1F C:\Program Files\World of Warcraft\Wow.exe
008D4DC4 01CCEA28 0001:004D3DC4 C:\Program Files\World of Warcraft\Wow.exe
7BC75FA2 01CCEAC8 0001:00064FA2 C:\windows\system32\ntdll.dll
7BC76170 01CCF3B8 0001:00065170 C:\windows\system32\ntdll.dll
F7E594FF 01CCF4B8 0000:00000000 <unknown>

--- Thread ID: 41 [Current Thread] ---
0061CC3D 003AF8BC 0001:0021BC3D C:\Program Files\World of Warcraft\Wow.exe
0061A34A 003AF8DC 0001:0021934A C:\Program Files\World of Warcraft\Wow.exe
00479387 003AF90C 0001:00078387 C:\Program Files\World of Warcraft\Wow.exe
00483E5D 003AF934 0001:00082E5D C:\Program Files\World of Warcraft\Wow.exe
00486E88 003AFA08 0001:00085E88 C:\Program Files\World of Warcraft\Wow.exe
00487105 003AFAD8 0001:00086105 C:\Program Files\World of Warcraft\Wow.exe
007FA141 003AFBB0 0001:003F9141 C:\Program Files\World of Warcraft\Wow.exe
007B74D0 003AFBDC 0001:003B64D0 C:\Program Files\World of Warcraft\Wow.exe
007F4E6A 003AFC9C 0001:003F3E6A C:\Program Files\World of Warcraft\Wow.exe
00810E67 003AFCB8 0001:0040FE67 C:\Program Files\World of Warcraft\Wow.exe
0081135B 003AFCD4 0001:0041035B C:\Program Files\World of Warcraft\Wow.exe
007E4A6C 003AFDA0 0001:003E3A6C C:\Program Files\World of Warcraft\Wow.exe
00830C39 003AFDD0 0001:0042FC39 C:\Program Files\World of Warcraft\Wow.exe
0082F3AF 003AFE54 0001:0042E3AF C:\Program Files\World of Warcraft\Wow.exe
0082F491 003AFE6C 0001:0042E491 C:\Program Files\World of Warcraft\Wow.exe
00406C4D 003AFF08 0001:00005C4D C:\Program Files\World of Warcraft\Wow.exe
7B878550 003AFFE8 0001:00057550 C:\windows\system32\KERNEL32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 19/19 threads...

--- Thread ID: 62 ---
7BC726C5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000003,0x0BD9E67C,0x00000004,0x00000000)
7BC729C2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000003,0x0BD9E67C,0x00000000,0x00000000)
7B88FDB2 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000003,0x0BD9E7F4,0x00000000,0xFFFFFFFF)
7E09FBEB winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+187 (0x00000003,0x0BD9E7F4,0xFFFFFFFF,0x00000000)
7ED0F7C5 user32.dll   MsgWaitForMultipleObjectsEx+229 (0x00000002,0x0BD9E9BC,0xFFFFFFFF,0x00000000)
7ED0F82F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x0BD9E9BC,0x00000000,0xFFFFFFFF)
004417F9 Wow.exe      <unknown symbol>+0 (0x01063278,0x008D4D45,0x09C7F970,0x0BD9EA10)
004427FA Wow.exe      <unknown symbol>+0 (0x09DCB620,0x8A354C51,0x008D4D45,0x09C7F970)
008D4D1F Wow.exe      <unknown symbol>+0 (0x09C7F970,0x7BC7413E,0x09C7F970,0x008D4D45)
008D4DC4 Wow.exe      <unknown symbol>+0 (0x008D4D45,0x09C7F970,0x7BCB0880,0xF7E5E5B1)
7BC75FA2 ntdll.dll    <unknown symbol>+0 (0x0BD9EAFC,0x00000000,0x00000000,0x00000000)
7BC76170 ntdll.dll    <unknown symbol>+0 (0x7FF8CFB8,0x0BD9FB90,0x0BD9FB90,0x0BD9FB90)
F7E594FF              start_thread+191 (0x0BD9FB90,0x00000000,0x00000000,0x00000000)
F7DD5B9E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 61 ---
7BC726C5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x0BC2E8A0,0x00000004,0x00000000)
7BC729C2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x0BC2E8A0,0x00000000,0x00000000)
7B88FDB2 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x0BC2E9E0,0x00000000,0xFFFFFFFF)
7B88FFAC KERNEL32.dll WaitForSingleObject+60 (0x0000220C,0xFFFFFFFF,0x008510F0,0x09C60C44)
008916A5 Wow.exe      <unknown symbol>+0 (0x09C60DD8,0xFFFFFFFF,0x0BC2EA18,0x00851130)
00850ADA Wow.exe      <unknown symbol>+0 (0x09C60DD8,0x09C60C44,0x0000003D,0x0BC2EA28)
00851130 Wow.exe      <unknown symbol>+0 (0x09C60C44,0x008510F0,0x0BC2EAC8,0x7BC75FA2)
7BC7413E ntdll.dll    call_thread_entry_point+14 (0x008510F0,0x09C60C44,0x7BCB0880,0xF7E5E5B1)
7BC75FA2 ntdll.dll    <unknown symbol>+0 (0x0BC2EAFC,0x00000000,0x00000000,0x00000000)
7BC76170 ntdll.dll    <unknown symbol>+0 (0x7FF90FB8,0x0BC2FB90,0x0BC2FB90,0x0BC2FB90)
F7E594FF              start_thread+191 (0x0BC2FB90,0x00000000,0x00000000,0x00000000)
F7DD5B9E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 60 ---
7BC726C5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000003,0x0BABE67C,0x00000004,0x00000000)
7BC729C2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000003,0x0BABE67C,0x00000000,0x00000000)
7B88FDB2 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000003,0x0BABE7F4,0x00000000,0xFFFFFFFF)
7E09FBEB winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+187 (0x00000003,0x0BABE7F4,0xFFFFFFFF,0x00000000)
7ED0F7C5 user32.dll   MsgWaitForMultipleObjectsEx+229 (0x00000002,0x0BABE9BC,0xFFFFFFFF,0x00000000)
7ED0F82F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x0BABE9BC,0x00000000,0xFFFFFFFF)
004417F9 Wow.exe      <unknown symbol>+0 (0x01063218,0x008D4D45,0x09552D48,0x0BABEA10)
004427FA Wow.exe      <unknown symbol>+0 (0x09561018,0x8A474C51,0x008D4D45,0x09552D48)
008D4D1F Wow.exe      <unknown symbol>+0 (0x09552D48,0x7BC7413E,0x09552D48,0x008D4D45)
008D4DC4 Wow.exe      <unknown symbol>+0 (0x008D4D45,0x09552D48,0x7BCB0880,0xF7E5E5B1)
7BC75FA2 ntdll.dll    <unknown symbol>+0 (0x0BABEAFC,0x00000000,0x00000000,0x00000000)
7BC76170 ntdll.dll    <unknown symbol>+0 (0x7FF94FB8,0x0BABFB90,0x0BABFB90,0x0BABFB90)
F7E594FF              start_thread+191 (0x0BABFB90,0x00000000,0x00000000,0x00000000)
F7DD5B9E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 59 ---
7BC726C5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x0657E8A0,0x00000004,0x00000000)
7BC729C2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x0657E8A0,0x00000000,0x00000000)
7B88FDB2 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x0657E9E0,0x00000000,0xFFFFFFFF)
7B88FFAC KERNEL32.dll WaitForSingleObject+60 (0x000021DC,0xFFFFFFFF,0x008510F0,0x099EE74C)
008916A5 Wow.exe      <unknown symbol>+0 (0x0954C198,0xFFFFFFFF,0x0657EA18,0x00851130)
00850ADA Wow.exe      <unknown symbol>+0 (0x0954C198,0x099EE74C,0x0000003B,0x0657EA28)
00851130 Wow.exe      <unknown symbol>+0 (0x099EE74C,0x008510F0,0x0657EAC8,0x7BC75FA2)
7BC7413E ntdll.dll    call_thread_entry_point+14 (0x008510F0,0x099EE74C,0x7BCB0880,0xF7E5E5B1)
7BC75FA2 ntdll.dll    <unknown symbol>+0 (0x0657EAFC,0x00000000,0x00000000,0x00000000)
7BC76170 ntdll.dll    <unknown symbol>+0 (0x7FFC0FB8,0x0657FB90,0x0657FB90,0x0657FB90)
F7E594FF              start_thread+191 (0x0657FB90,0x00000000,0x00000000,0x00000000)
F7DD5B9E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 57 ---
7BC726C5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x0B94E9C0,0x00000004,0x0B94EA00)
7BC729C2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x0B94E9C0,0x00000000,0x00000000)
7BC72A1C ntdll.dll    NtWaitForSingleObject+60 (0x000021D8,0x00000000,0x0B94EA00,0x7BC90BC4)
7BC781C5 ntdll.dll    <unknown symbol>+0 (0x00000000,0x7BC78080,0x0B94EAC8,0x7BC75FA2)
7BC7413E ntdll.dll    call_thread_entry_point+14 (0x7BC78080,0x00000000,0x7BCB0880,0xF7E5E5B1)
7BC75FA2 ntdll.dll    <unknown symbol>+0 (0x0B94EAFC,0x00000000,0x00000000,0x00000000)
7BC76170 ntdll.dll    <unknown symbol>+0 (0x7FF9CFB8,0x0B94FB90,0x0B94FB90,0x0B94FB90)
F7E594FF              start_thread+191 (0x0B94FB90,0x00000000,0x00000000,0x00000000)
F7DD5B9E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 56 ---
7BC726C5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000003,0x0830E67C,0x00000004,0x00000000)
7BC729C2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000003,0x0830E67C,0x00000000,0x00000000)
7B88FDB2 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000003,0x0830E7F4,0x00000000,0xFFFFFFFF)
7E09FBEB winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+187 (0x00000003,0x0830E7F4,0xFFFFFFFF,0x00000000)
7ED0F7C5 user32.dll   MsgWaitForMultipleObjectsEx+229 (0x00000002,0x0830E9BC,0xFFFFFFFF,0x00000000)
7ED0F82F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x0830E9BC,0x00000000,0xFFFFFFFF)
004417F9 Wow.exe      <unknown symbol>+0 (0x010631D0,0x008D4D45,0x07BA8050,0x0830EA10)
004427FA Wow.exe      <unknown symbol>+0 (0x07BA7FF0,0x89DC4C51,0x008D4D45,0x07BA8050)
008D4D1F Wow.exe      <unknown symbol>+0 (0x07BA8050,0x7BC7413E,0x07BA8050,0x008D4D45)
008D4DC4 Wow.exe      <unknown symbol>+0 (0x008D4D45,0x07BA8050,0x7BCB0880,0xF7E5E5B1)
7BC75FA2 ntdll.dll    <unknown symbol>+0 (0x0830EAFC,0x00000000,0x00000000,0x00000000)
7BC76170 ntdll.dll    <unknown symbol>+0 (0x7FFA0FB8,0x0830FB90,0x0830FB90,0x0830FB90)
F7E594FF              start_thread+191 (0x0830FB90,0x00000000,0x00000000,0x00000000)
F7DD5B9E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 55 ---
7BC726C5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x0819E660,0x00000004,0x0819E760)
7BC729C2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x0819E660,0x00000000,0x00000000)
7B88FDB2 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x0819E8BC,0x00000000,0x000001F4)
7B88FF0A KERNEL32.dll WaitForMultipleObjects+58 (0x00000001,0x0819E8BC,0x00000000,0x000001F4)
00462CFB Wow.exe      <unknown symbol>+0 (0x00462430,0x0819EA18,0x0053AF87,0x0780E5A0)
0046243E Wow.exe      <unknown symbol>+0 (0x0780E5A0,0x0053AF30,0x07691D78,0x7BC94FF4)
0053AF87 Wow.exe      <unknown symbol>+0 (0x000021B4,0x0053AF30,0x0819EAC8,0x7BC75FA2)
7BC7413E ntdll.dll    call_thread_entry_point+14 (0x0053AF30,0x07691D78,0x7BCB0880,0xF7E5E5B1)
7BC75FA2 ntdll.dll    <unknown symbol>+0 (0x0819EAFC,0x00000000,0x00000000,0x00000000)
7BC76170 ntdll.dll    <unknown symbol>+0 (0x7FFA4FB8,0x0819FB90,0x0819FB90,0x0819FB90)
F7E594FF              start_thread+191 (0x0819FB90,0x00000000,0x00000000,0x00000000)
F7DD5B9E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 54 ---
7BC726C5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x0802E890,0x00000004,0x0802E990)
7BC729C2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x0802E890,0x00000000,0x00000000)
7B88FDB2 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x0802E9D0,0x00000000,0x000003E8)
7B88FFAC KERNEL32.dll WaitForSingleObject+60 (0x00002124,0x000003E8,0x0802E9F0,0x00462495)
0053F4F0 Wow.exe      <unknown symbol>+0 (0x000003E8,0x00000036,0x004625F0,0x0780E5B0)
00462495 Wow.exe      <unknown symbol>+0 (0x00000000,0x0802EA18,0x0053AF87,0x0780E5B0)
00462601 Wow.exe      <unknown symbol>+0 (0x0780E5B0,0x0053AF30,0x07691D60,0x7BC94FF4)
0053AF87 Wow.exe      <unknown symbol>+0 (0x000021B0,0x0053AF30,0x0802EAC8,0x7BC75FA2)
7BC7413E ntdll.dll    call_thread_entry_point+14 (0x0053AF30,0x07691D60,0x7BCB0880,0xF7E5E5B1)
7BC75FA2 ntdll.dll    <unknown symbol>+0 (0x0802EAFC,0x00000000,0x00000000,0x00000000)
7BC76170 ntdll.dll    <unknown symbol>+0 (0x7FFA8FB8,0x0802FB90,0x0802FB90,0x0802FB90)
F7E594FF              start_thread+191 (0x0802FB90,0x00000000,0x00000000,0x00000000)
F7DD5B9E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 53 ---
7BC726C5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x07EBE8A8,0x00000004,0x00000000)
7BC729C2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x07EBE8A8,0x00000000,0x00000000)
7B88FDB2 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x07EBE9E8,0x00000000,0xFFFFFFFF)
7B88FFAC KERNEL32.dll WaitForSingleObject+60 (0x00002078,0xFFFFFFFF,0x07EBEA18,0x007A8D0B)
0053F4F0 Wow.exe      <unknown symbol>+0 (0xFFFFFFFF,0x00000000,0x0053AF87,0x00000000)
007A8D0B Wow.exe      <unknown symbol>+0 (0x0000211C,0x0053AF30,0x07EBEAC8,0x7BC75FA2)
7BC7413E ntdll.dll    call_thread_entry_point+14 (0x0053AF30,0x07755C10,0x7BCB0880,0xF7E5E5B1)
7BC75FA2 ntdll.dll    <unknown symbol>+0 (0x07EBEAFC,0x00000000,0x00000000,0x00000000)
7BC76170 ntdll.dll    <unknown symbol>+0 (0x7FFACFB8,0x07EBFB90,0x07EBFB90,0x07EBFB90)
F7E594FF              start_thread+191 (0x07EBFB90,0x00000000,0x00000000,0x00000000)
F7DD5B9E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 52 ---
7B8900C2 KERNEL32.dll SleepEx+50 (0x0000000A,0x00000000,0x07D4EA04,0x0083E3CA)
7B890105 KERNEL32.dll Sleep+37 (0x0000000A,0x07D4EA18,0x0085116C,0x0000000A)
0085093D Wow.exe      <unknown symbol>+0 (0x0000000A,0x04DA6EC8,0x00000034,0x07D4EA28)
0085116C Wow.exe      <unknown symbol>+0 (0x04DA6EC8,0x008510F0,0x07D4EAC8,0x7BC75FA2)
7BC7413E ntdll.dll    call_thread_entry_point+14 (0x008510F0,0x04DA6EC8,0x7BCB0880,0xF7E5E5B1)
7BC75FA2 ntdll.dll    <unknown symbol>+0 (0x07D4EAFC,0x00000000,0x00000000,0x00000000)
7BC76170 ntdll.dll    <unknown symbol>+0 (0x7FFB0FB8,0x07D4FB90,0x07D4FB90,0x07D4FB90)
F7E594FF              start_thread+191 (0x07D4FB90,0x00000000,0x00000000,0x00000000)
F7DD5B9E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 51 ---
7B8900C2 KERNEL32.dll SleepEx+50 (0x0000000A,0x00000000,0x00000000,0x00000013)
7B890105 KERNEL32.dll Sleep+37 (0x0000000A,0x069CEA18,0x0085116C,0x0000000A)
0085093D Wow.exe      <unknown symbol>+0 (0x0000000A,0x04C86020,0x00000033,0x069CEA28)
0085116C Wow.exe      <unknown symbol>+0 (0x04C86020,0x008510F0,0x069CEAC8,0x7BC75FA2)
7BC7413E ntdll.dll    call_thread_entry_point+14 (0x008510F0,0x04C86020,0x7BCB0880,0xF7E5E5B1)
7BC75FA2 ntdll.dll    <unknown symbol>+0 (0x069CEAFC,0x00000000,0x00000000,0x00000000)
7BC76170 ntdll.dll    <unknown symbol>+0 (0x7FFB4FB8,0x069CFB90,0x069CFB90,0x069CFB90)
F7E594FF              start_thread+191 (0x069CFB90,0x00000000,0x00000000,0x00000000)
F7DD5B9E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 50 ---
7DFF830B winealsa.drv ALSA_WaitRingMessage+59 (0x00129BA0,0x0000000B,0x00000000,0x00000000)
7E00B4EC winealsa.drv <unknown symbol>+0 (0x00000000,0x7E00B450,0x0609EAC8,0x7BC75FA2)
7BC7413E ntdll.dll    call_thread_entry_point+14 (0x7E00B450,0x00000000,0x7BCB0880,0xF7E5E5B1)
7BC75FA2 ntdll.dll    <unknown symbol>+0 (0x0609EAFC,0x00000000,0x00000000,0x00000000)
7BC76170 ntdll.dll    <unknown symbol>+0 (0x7FFC8FB8,0x0609FB90,0x0609FB90,0x0609FB90)
F7E594FF              start_thread+191 (0x0609FB90,0x00000000,0x00000000,0x00000000)
F7DD5B9E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 49 ---
7B8900C2 KERNEL32.dll SleepEx+50 (0x0000000A,0x00000000,0x0685EA04,0x0083E3CA)
7B890105 KERNEL32.dll Sleep+37 (0x0000000A,0x0685EA18,0x0085116C,0x0000000A)
0085093D Wow.exe      <unknown symbol>+0 (0x0000000A,0x04DAF548,0x00000031,0x0685EA28)
0085116C Wow.exe      <unknown symbol>+0 (0x04DAF548,0x008510F0,0x0685EAC8,0x7BC75FA2)
7BC7413E ntdll.dll    call_thread_entry_point+14 (0x008510F0,0x04DAF548,0x7BCB0880,0xF7E5E5B1)
7BC75FA2 ntdll.dll    <unknown symbol>+0 (0x0685EAFC,0x00000000,0x00000000,0x00000000)
7BC76170 ntdll.dll    <unknown symbol>+0 (0x7FFB8FB8,0x0685FB90,0x0685FB90,0x0685FB90)
F7E594FF              start_thread+191 (0x0685FB90,0x00000000,0x00000000,0x00000000)
F7DD5B9E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 48 ---
7B8900C2 KERNEL32.dll SleepEx+50 (0x0000000A,0x00000000,0x00000000,0x00000007)
7B890105 KERNEL32.dll Sleep+37 (0x0000000A,0x066EEA18,0x0085116C,0x0000000A)
0085093D Wow.exe      <unknown symbol>+0 (0x0000000A,0x04B06E90,0x00000030,0x066EEA28)
0085116C Wow.exe      <unknown symbol>+0 (0x04B06E90,0x008510F0,0x066EEAC8,0x7BC75FA2)
7BC7413E ntdll.dll    call_thread_entry_point+14 (0x008510F0,0x04B06E90,0x7BCB0880,0xF7E5E5B1)
7BC75FA2 ntdll.dll    <unknown symbol>+0 (0x066EEAFC,0x00000000,0x00000000,0x00000000)
7BC76170 ntdll.dll    <unknown symbol>+0 (0x7FFBCFB8,0x066EFB90,0x066EFB90,0x066EFB90)
F7E594FF              start_thread+191 (0x066EFB90,0x00000000,0x00000000,0x00000000)
F7DD5B9E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 46 ---
7EDFE1D7 winmm.dll    <unknown symbol>+0 (0x00000000,0x7EDFDFA0,0x0640EAC8,0x7BC75FA2)
7BC7413E ntdll.dll    call_thread_entry_point+14 (0x7EDFDFA0,0x00000000,0x7BCB0880,0xF7E5E5B1)
7BC75FA2 ntdll.dll    <unknown symbol>+0 (0x0640EAFC,0x00000000,0x00000000,0x00000000)
7BC76170 ntdll.dll    <unknown symbol>+0 (0x7FFC4FB8,0x0640FB90,0x0640FB90,0x0640FB90)
F7E594FF              start_thread+191 (0x0640FB90,0x00000000,0x00000000,0x00000000)
F7DD5B9E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 44 ---
7BC726C5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x040DE89C,0x00000004,0x00000000)
7BC729C2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x040DE89C,0x00000000,0x00000000)
7B88FDB2 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x040DE9DC,0x00000000,0xFFFFFFFF)
7B88FFAC KERNEL32.dll WaitForSingleObject+60 (0x00002068,0xFFFFFFFF,0x040DE9FC,0x00478102)
0053F4F0 Wow.exe      <unknown symbol>+0 (0xFFFFFFFF,0x0106B010,0x0000002C,0x004780A0)
00478102 Wow.exe      <unknown symbol>+0 (0x0106B010,0x0053AF30,0x02BE86A0,0x7BC94FF4)
0053AF87 Wow.exe      <unknown symbol>+0 (0x000020DC,0x0053AF30,0x040DEAC8,0x7BC75FA2)
7BC7413E ntdll.dll    call_thread_entry_point+14 (0x0053AF30,0x02BE86A0,0x7BCB0880,0xF7E5E5B1)
7BC75FA2 ntdll.dll    <unknown symbol>+0 (0x040DEAFC,0x00000000,0x00000000,0x00000000)
7BC76170 ntdll.dll    <unknown symbol>+0 (0x7FFCCFB8,0x040DFB90,0x040DFB90,0x040DFB90)
F7E594FF              start_thread+191 (0x040DFB90,0x00000000,0x00000000,0x00000000)
F7DD5B9E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 43 ---
7B890105 KERNEL32.dll Sleep+37 (0x00000001,0x03A0E9FC,0x007D5E45,0x00000001)
0046EC9D Wow.exe      <unknown symbol>+0 (0x00000001,0x007D5C70,0x02B8DFA8,0x0000002B)
007D5E45 Wow.exe      <unknown symbol>+0 (0x02B8DFA8,0x0053AF30,0x02B8DFC8,0x7BC94FF4)
0053AF87 Wow.exe      <unknown symbol>+0 (0x000020D8,0x0053AF30,0x03A0EAC8,0x7BC75FA2)
7BC7413E ntdll.dll    call_thread_entry_point+14 (0x0053AF30,0x02B8DFC8,0x7BCB0880,0xF7E5E5B1)
7BC75FA2 ntdll.dll    <unknown symbol>+0 (0x03A0EAFC,0x00000000,0x00000000,0x00000000)
7BC76170 ntdll.dll    <unknown symbol>+0 (0x7FFD0FB8,0x03A0FB90,0x03A0FB90,0x03A0FB90)
F7E594FF              start_thread+191 (0x03A0FB90,0x00000000,0x00000000,0x00000000)
F7DD5B9E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 42 ---
7B8900C2 KERNEL32.dll SleepEx+50 (0x00000064,0x00000000,0x01CCE9B0,0x7B854B27)
7B890105 KERNEL32.dll Sleep+37 (0x00000064,0x008D4D45,0x7BC94FF4,0x01AEC1A0)
00424754 Wow.exe      <unknown symbol>+0 (0x01AEC1A0,0x80204C51,0x008D4D45,0x01AEC200)
008D4D1F Wow.exe      <unknown symbol>+0 (0x01AEC200,0x7BC7413E,0x01AEC200,0x01AEC200)
008D4DC4 Wow.exe      <unknown symbol>+0 (0x008D4D45,0x01AEC200,0x7BCB0880,0xF7E5E5B1)
7BC75FA2 ntdll.dll    <unknown symbol>+0 (0x01CCEAFC,0x00000000,0x00000000,0x00000000)
7BC76170 ntdll.dll    <unknown symbol>+0 (0x7FFD4FB8,0x01CCFB90,0x01CCFB90,0x01CCFB90)
F7E594FF              start_thread+191 (0x01CCFB90,0x00000000,0x00000000,0x00000000)
F7DD5B9E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 41 [Current Thread] ---
0061CC3D Wow.exe      <unknown symbol>+0 (0x00000006,0x01137528,0x00000006,0x04560B10)
0061A34A Wow.exe      <unknown symbol>+0 (0x09C83F88,0x0000000C,0x00000000,0x00000001)
00479387 Wow.exe      <unknown symbol>+0 (0x00000000,0x003AFA28,0x09C83DA8,0x003AFA28)
00483E5D Wow.exe      <unknown symbol>+0 (0x00000000,0x00000000,0x0962B938,0x3F77FE41)
00486E88 Wow.exe      <unknown symbol>+0 (0x00000000,0x09E5C960,0x09C83DA8,0x00000002)
00487105 Wow.exe      <unknown symbol>+0 (0x00000000,0x0968AFCC,0x3F800000,0x00000000)
007FA141 Wow.exe      <unknown symbol>+0 (0xFF000000,0x00000003,0xFF000000,0x0954F7C4)
007B74D0 Wow.exe      <unknown symbol>+0 (0xFF000000,0x00000001,0x0954F748,0x0954F7C4)
007F4E6A Wow.exe      <unknown symbol>+0 (0x0954F7C4,0x094E3280,0x00000006,0x094E2590)
00810E67 Wow.exe      <unknown symbol>+0 (0x02BE74D0,0x07BA21E0,0x07BA21C8,0x00000000)
0081135B Wow.exe      <unknown symbol>+0 (0x00000000,0x07BA21D0,0x07BA21E0,0x3B83126F)
007E4A6C Wow.exe      <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x02B8D8F0)
00830C39 Wow.exe      <unknown symbol>+0 (0x02B8D8F0,0x00000017,0x00000000,0x00000A28)
0082F3AF Wow.exe      <unknown symbol>+0 (0x00000000,0x00406BD2,0x00000001,0x00000001)
0082F491 Wow.exe      <unknown symbol>+0 (0x0040AFA9,0x00400000,0x00000000,0x00114EB4)
00406C4D Wow.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7B878550 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
F7E8EDE7              wine_switch_to_stack+23 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00400000 - 0x01751000  C:\Program Files\World of Warcraft\Wow.exe
0x10000000 - 0x10069000  C:\Program Files\World of Warcraft\DivxDecoder.dll
0x7B820000 - 0x7B948000  C:\windows\system32\KERNEL32.dll
0x7BC10000 - 0x7BCB1000  C:\windows\system32\ntdll.dll
0x7BF20000 - 0x7BF6A000  C:\windows\system32\dbghelp.dll
0x7C040000 - 0x7C07B000  C:\windows\system32\dsound.dll
0x7C4D0000 - 0x7C4DC000  C:\windows\system32\psapi.dll
0x7C5A0000 - 0x7C5D0000  C:\windows\system32\uxtheme.dll
0x7DE60000 - 0x7DE6F000  C:\windows\system32\midimap.dll
0x7DFD0000 - 0x7DFE0000  C:\windows\system32\msacm32.drv
0x7DFF0000 - 0x7E017000  C:\windows\system32\winealsa.drv
0x7E070000 - 0x7E0FB000  C:\windows\system32\winex11.drv
0x7E260000 - 0x7E26B000  C:\windows\system32\lz32.dll
0x7E270000 - 0x7E286000  C:\windows\system32\version.dll
0x7E290000 - 0x7E2F3000  C:\windows\system32\rpcrt4.dll
0x7E310000 - 0x7E3EC000  C:\windows\system32\ole32.dll
0x7E3F0000 - 0x7E424000  C:\windows\system32\dinput.dll
0x7E430000 - 0x7E451000  C:\windows\system32\ws2_32.dll
0x7E460000 - 0x7E477000  C:\windows\system32\msacm32.dll
0x7E480000 - 0x7E540000  C:\windows\system32\comctl32.dll
0x7E550000 - 0x7E6CA000  C:\windows\system32\shell32.dll
0x7E6E0000 - 0x7E728000  C:\windows\system32\shlwapi.dll
0x7E730000 - 0x7E74B000  C:\windows\system32\mpr.dll
0x7E750000 - 0x7E79D000  C:\windows\system32\wininet.dll
0x7E7A0000 - 0x7E7BE000  C:\windows\system32\imm32.dll
0x7E7D0000 - 0x7E8E3000  C:\windows\system32\wined3d.dll
0x7E8F0000 - 0x7E914000  C:\windows\system32\d3d9.dll
0x7EB00000 - 0x7EB84000  C:\windows\system32\opengl32.dll
0x7EB90000 - 0x7EBDA000  C:\windows\system32\advapi32.dll
0x7EBF0000 - 0x7EC7B000  C:\windows\system32\gdi32.dll
0x7EC90000 - 0x7EDC7000  C:\windows\system32\user32.dll
0x7EDD0000 - 0x7EE5A000  C:\windows\system32\winmm.dll
0x7EE80000 - 0x7EE95000  C:\windows\system32\dinput8.dll

-

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7ffeffff
Processor Mask:         0x3
Number of Processors:   2
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        6
Processor Revision:     5894
Os Version:             5.1
Os Service Pack:        4.0

Percent memory used:    22
Total physical memory:  3127496704
Free Memory:            2424967168
Page file:              3700482048
Total virtual memory:   2147352575

---

### Post by Hellstudios on 2009-04-27
do you have the correct drivers installed?



system >> administration >> hardware drivers


active them all.


and maybe you could put some ```
 
``` tags around that giant wall of text? :P

---

### Post by Ishmael42 on 2009-04-27
> **Hellstudios said:**
> do you have the correct drivers installed?



system >> administration >> hardware drivers


active them all.


and maybe you could put some  tags around that giant wall of text? :P
I have all the drivers, the graphics driver is the nvidia 180

and sorry about the wall of text

---

