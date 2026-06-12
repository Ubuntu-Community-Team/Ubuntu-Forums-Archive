---
title: "World of Warcraft need help badly please"
date: 2011-08-19
forum: Gaming &amp; Leisure
---

### Post by curt122895 on 2011-08-19
Hey, I keep getting this error 132  
Please help, i would love you if you could even suggest something to help me. currently running ubuntu 10.10 
And my comp is plenty powerful Radeon hd 4200 (not too bad)
8 gb of ram 
2.6 CPU speed

==============================================================================
World of WarCraft: Retail Build (build 14480)

Exe:      H:\Documents\World of Warcraft\Wow.exe
Time:     Aug 19, 2011 11:25:22.774 AM
User:     curt
Computer: curt-NY549AA-AB
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal exception!

Program:    H:\Documents\World of Warcraft\Wow.exe
ProcessID:    27
Exception:    0xC0000005 (ACCESS_VIOLATION) at 0023:7E787766

The instruction at "0x7E787766" referenced memory at "0x00000059".
The memory could not be "read".


WoWBuild: 14480
Version: 4.2.0
Type:  WoW
Platform: X86
Settings: 
SET gxWindow "1"
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET readTOS "-1"
SET readEULA "-1"
SET readScanning "-1"
SET readContest "-1"
SET checkAddonVersion "1"
SET locale "enUS"
SET playIntroMovie "0"
SET showToolsUI "1"
SET accounttype "CL"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=00000001  EBX=7E7C3FF4  ECX=00000000  EDX=00000001  ESI=00000000
EDI=00000000  EBP=0033E8F8  ESP=0033E870  EIP=7E787766  FLG=00210246
CS =0023      DS =002B      ES =002B      SS =002B      FS =0063      GS =006B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 6/6 threads...

--- Thread ID: 35 ---

--- Thread ID: 34 ---

--- Thread ID: 33 ---

--- Thread ID: 32 ---
7BC9AFF4 016BE8A8 0001:00089FF4 C:\windows\system32\ntdll.dll

--- Thread ID: 31 ---
00000000 015BE96C 0000:00000000 H:\Documents\World of Warcraft\Wow.exe

--- Thread ID: 28 [Current Thread] ---
7E787766 0033E8F8 0001:000E6766 C:\windows\system32\wined3d.dll
7E6F8CBB 0033EF98 0001:00057CBB C:\windows\system32\wined3d.dll
7E703C9A 0033EFB8 0001:00062C9A C:\windows\system32\wined3d.dll
7E78C28A 0033EFF8 0001:000EB28A C:\windows\system32\wined3d.dll
7E7D9C6D 0033F028 0001:00008C6D C:\windows\system32\d3d9.dll
0084C6BA 0033F03C 0001:0044B6BA H:\Documents\World of Warcraft\Wow.exe
00834EC1 0033F654 0001:00433EC1 H:\Documents\World of Warcraft\Wow.exe
0082B028 0033F66C 0001:0042A028 H:\Documents\World of Warcraft\Wow.exe
0062BC69 0033FA98 0001:0022AC69 H:\Documents\World of Warcraft\Wow.exe
0062B207 0033FB94 0001:0022A207 H:\Documents\World of Warcraft\Wow.exe
00407BCA 0033FDEC 0001:00006BCA H:\Documents\World of Warcraft\Wow.exe
00407D76 0033FDFC 0001:00006D76 H:\Documents\World of Warcraft\Wow.exe
00407DC7 0033FE90 0001:00006DC7 H:\Documents\World of Warcraft\Wow.exe
7B85406C 0033FEA8 0001:0004306C C:\windows\system32\KERNEL32.dll
7B8567DB 0033FEE8 0001:000457DB C:\windows\system32\KERNEL32.dll
7BC6FCE0 0033FEF8 0001:0005ECE0 C:\windows\system32\ntdll.dll
7BC6FEB0 0033FFC8 0001:0005EEB0 C:\windows\system32\ntdll.dll
7BC4ADEA 0033FFE8 0001:00039DEA C:\windows\system32\ntdll.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 6/6 threads...

--- Thread ID: 35 ---

--- Thread ID: 34 ---

--- Thread ID: 33 ---

--- Thread ID: 32 ---
7BC9AFF4 ntdll.dll    <unknown symbol>+0 (00412C4E,00000000,965E14D4,011C0A80)
016BE8EC <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)
011C0A80 <unknown module> <unknown symbol>+0 (011DE118,FF4E0101,00000018,011A8E00)
011C0A80 <unknown module> <unknown symbol>+0 (011A8E00,FF4E0001,000000A8,5C3A4822)

--- Thread ID: 31 ---
015BE9D0 <unknown module> <unknown symbol>+0 (00000000,F7669AA0,F7544610,F7693170)

--- Thread ID: 28 [Current Thread] ---
7E787766 wined3d.dll  <unknown symbol>+0 (0013354C,000080E1,0033ECE0,000080E1)
7E6F8CBB wined3d.dll  <unknown symbol>+0 (00110060,7BC47D8B,7E7C3FF4,0033EFF8)
7E703C9A wined3d.dll  <unknown symbol>+0 (00133528,00133510,00133510,0033EFF8)
7E78C28A wined3d.dll  WineDirect3DCreate+90 (00000009,00000010,0010000F,7E7D9C10)
7E7D9C6D d3d9.dll     Direct3DCreate9+93 (00000020,00000000,00834EC1,0033F650)
0084C6BA Wow.exe      <unknown symbol>+0 (0033F64C,00DE7AD4,00000000,00000040)
00834EC1 Wow.exe      <unknown symbol>+0 (00DE7AD4,00DE7AD8,0033FA98,00DE7AD4)
0082B028 Wow.exe      <unknown symbol>+0 (00DE7AD4,00DE7AD8,000000F2,00000000)
0062BC69 Wow.exe      <unknown symbol>+0 (00DE7AD4,00B87BE0,00000001,00000000)
0062B207 Wow.exe      <unknown symbol>+0 (0033FBBC,00000001,00000023,00000000)
00407BCA Wow.exe      <unknown symbol>+0 (00000001,0033FE90,0040D975,00000000)
00407D76 Wow.exe      <unknown symbol>+0 (0040D975,00000000,0000000A,004011B0)
00407DC7 Wow.exe      <unknown symbol>+0 (7FFDF000,7B882FF4,0033FEE8,7FFDF000)
7B85406C KERNEL32.dll call_process_entry+12 (7FFDF000,00000000,00000000,00000000)
7B8567DB KERNEL32.dll <unknown symbol>+0 (7FFDF000,0033FFC8,7B856780,00000000)
7BC6FCE0 ntdll.dll    call_thread_func+12 (7B856780,00000000,FFFFFFFF,7B835930)
7BC6FEB0 ntdll.dll    call_thread_entry_point+112 (7B856780,00000000,00000000,00000000)
7BC4ADEA ntdll.dll    <unknown symbol>+0 (7B856780,00000000,00000000,00000000)



----------------------------------------
    Loaded Modules
----------------------------------------

DBG-MODULE<00400000 00C98000 "Wow.exe" "Wow.pdb" 0 {69998df6-47b1-49a4-a94fe352d257e808} 1 1312424395>
DBG-MODULE<7B810000 0016C000 "KERNEL32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7BC10000 000A7000 "ntdll.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7D710000 00093000 "winex11.drv" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DA70000 00023000 "uxtheme.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DF50000 00022000 "msacm32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DF80000 00087000 "winmm.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E010000 0000C000 "hid.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E020000 00010000 "lz32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E040000 00009000 "version.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E050000 00030000 "winspool.drv" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E090000 0004E000 "setupapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E0F0000 00061000 "rpcrt4.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E170000 000DF000 "ole32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E260000 00028000 "dinput.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E290000 00025000 "ws2_32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E2C0000 000DF000 "comctl32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E3B0000 001C8000 "shell32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E590000 00049000 "shlwapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E5E0000 0001D000 "mpr.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E620000 0004D000 "wininet.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E670000 0001E000 "imm32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E6A0000 00126000 "wined3d.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7E7D0000 0002A000 "d3d9.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7EB00000 00085000 "opengl32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7EB90000 0004F000 "advapi32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7EBF0000 0007A000 "gdi32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7EC80000 0011A000 "user32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7EFF0000 00010000 "dinput8.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<F6EF0000 0004F000 "dbghelp.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<F74E0000 00007000 "psapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>

----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 7E787766)

7E787766: F6 41 59 02  75 51 6B C8  68 8B 45 08  03 88 FC 07  .AY.uQk.h.E.....


Stack: 1024 bytes starting at (ESP = 0033E870)

* = addr  **                                                  *               
0033E870: E8 B7 91 7D  30 7F 27 7D  39 2B 66 F7  F4 EF DB 7D  ...}0.'}9+f....}
0033E880: 01 00 00 00  E8 B7 91 7D  39 2B 66 F7  00 00 00 00  .......}9+f.....
0033E890: 30 06 7D 7D  02 00 00 00  4C 0A 00 00  F4 EF DB 7D  0.}}....L......}
0033E8A0: 10 00 00 00  E8 B7 91 7D  F8 E8 33 00  AE 8E B3 7D  .......}..3....}
0033E8B0: 70 32 9A 7D  DC E8 33 00  3E DE C7 7B  11 9C 70 7E  p2.}..3.>..{..p~
0033E8C0: 20 96 00 00  F4 ED 33 00  E0 10 7C 7E  80 8D 7B 7E   .....3...|~..{~
0033E8D0: E0 EC 33 00  F4 9F 79 7D  F8 E8 33 00  60 D2 76 7D  ..3...y}..3.`.v}
0033E8E0: 40 DA 79 7D  07 00 00 00  7B 76 78 7E  F4 3F 7C 7E  @.y}....{vx~.?|~
0033E8F0: 31 00 00 00  02 10 00 00  98 EF 33 00  BB 8C 6F 7E  1.........3...o~
0033E900: 4C 35 13 00  02 10 00 00  E1 80 00 00  67 83 00 00  L5..........g...
0033E910: E0 EC 33 00  04 00 00 00  E1 80 00 00  67 83 00 00  ..3.........g...
0033E920: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E930: 00 00 00 00  20 22 DD 01  6F 00 75 00  6E 00 64 00  .... "..o.u.n.d.
0033E940: DD E4 79 7D  57 33 7A 7E  BC EF 79 7E  5C EE 33 00  ..y}W3z~..y~\.3.
0033E950: 0F 3D 7A 7E  E8 4F 7C 7E  CD 3D 7A 7E  70 EE 33 00  .=z~.O|~.=z~p.3.
0033E960: 68 EE 33 00  64 EE 33 00  20 EE 33 00  C0 3E 7A 7E  h.3.d.3. .3..>z~
0033E970: 09 2A 7A 7E  02 10 00 00  00 00 06 00  E0 EC 33 00  .*z~..........3.
0033E980: 4C 35 13 00  3C 35 13 00  20 96 00 00  28 35 13 00  L5..<5.. ...(5..
0033E990: A4 E9 33 00  06 71 C4 7B  F4 AF C9 7B  00 00 11 00  ..3..q.{...{....
0033E9A0: F4 AF C9 7B  6F CF FD 00  00 00 00 00  98 06 00 00  ...{o...........
0033E9B0: 00 00 00 00  E5 45 00 00  00 00 33 33  65 63 63 30  .....E....33ecc0
0033E9C0: 00 00 00 00  00 00 00 00  00 00 00 00  81 43 96 AE  .............C..
0033E9D0: 0E FD 68 95  25 02 2E A6  0D EE 8F 31  01 00 00 00  ..h.%......1....
0033E9E0: E9 28 84 8E  6B 52 04 1B  54 EE 33 00  48 EE 33 00  .(..kR..T.3.H.3.
0033E9F0: E8 95 B3 00  FF FF FF FF  54 EE 33 00  34 1B 7E 00  ........T.3.4.~.
0033EA00: C4 61 58 02  00 00 00 00  28 BF 22 02  4C EE 33 00  .aX.....(.".L.3.
0033EA10: 54 6C B5 00  4C EE 33 00  74 77 56 F7  70 4E E7 00  Tl..L.3.twV.pN..
0033EA20: 00 00 00 00  F4 3F 65 F7  78 EA 33 00  E0 EB 33 00  .....?e.x.3...3.
0033EA30: B2 8A 56 F7  00 00 00 00  74 77 56 F7  F4 3F 65 F7  ..V.....twV..?e.
0033EA40: 18 EB 33 00  F4 3F 65 F7  98 EA 33 00  6C EC 33 00  ..3..?e...3.l.3.
0033EA50: B2 8A 56 F7  98 EA 33 00  7C EA 33 00  F4 3F 65 F7  ..V...3.|.3..?e.
0033EA60: 38 EB 33 00  46 5F CB 7B  84 EB 33 00  00 E3 55 F7  8.3.F_.{..3...U.
0033EA70: 46 5F CB 7B  84 EB 33 00  00 E3 55 F7  98 EA 33 00  F_.{..3...U...3.
0033EA80: DA 67 D2 7E  6C EC 33 00  46 5F CB 7B  00 00 00 00  .g.~l.3.F_.{....
0033EA90: 98 EA 33 00  E1 03 00 00  01 80 AD FB  46 5F CB 7B  ..3.........F_.{
0033EAA0: 46 5F CB 7B  46 5F CB 7B  46 5F CB 7B  6C 5F CB 7B  F_.{F_.{F_.{l_.{
0033EAB0: 27 63 CB 7B  46 5F CB 7B  27 63 CB 7B  00 00 00 00  'c.{F_.{'c.{....
0033EAC0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033EAD0: 1F 00 00 00  00 00 00 00  24 00 00 00  00 00 00 F7  ........$.......
0033EAE0: 00 00 00 00  7F 98 7D 00  70 4E E7 00  00 00 00 00  ......}.pN......
0033EAF0: 78 1E 13 02  00 00 00 00  71 32 69 F7  4C 4C 00 54  x.......q2i.LL.T
0033EB00: FF FF FF FF  61 63 65 20  69 73 20 66  E0 36 65 F7  ....ace is f.6e.
0033EB10: 00 00 00 00  00 00 00 00  20 73 6F 6D  75 6C 6C 2E  ........ somull.
0033EB20: 68 65 20 64  65 20 73 70  61 73 65 20  E0 36 65 F7  he de spase .6e.
0033EB30: 00 00 00 00  58 EB 33 00  C5 97 79 00  31 77 52 F7  ....X.3...y.1wR.
0033EB40: B0 61 58 02  02 00 00 00  F4 AF C9 7B  CC EC 33 00  .aX........{..3.
0033EB50: 00 00 00 00  34 EC 33 00  94 93 69 F7  00 00 00 00  ....4.3...i.....
0033EB60: 20 5B CB 7B  B4 EB 33 00  D1 50 C3 7B  28 5F CB 7B   [.{..3..P.{(_.{
0033EB70: 00 04 00 00  26 00 00 00  20 5B CB 7B  D4 EB 33 00  ....&... [.{..3.
0033EB80: 54 68 66 F7  20 5B CB 7B  92 51 C3 7B  28 5F CB 7B  Thf. [.{.Q.{(_.{
0033EB90: 6C 5F CB 7B  00 00 00 00  6C EC 33 00  CA 3A 54 7F  l_.{....l.3..:T.
0033EBA0: 00 00 00 00  00 00 00 00  26 00 00 00  00 00 00 00  ........&.......
0033EBB0: 00 00 00 00  28 5F CB 7B  46 5F CB 7B  C3 C4 C8 7B  ....(_.{F_.{...{
0033EBC0: E0 EB 33 00  18 A6 54 02  F4 AF C9 7B  1E 00 00 00  ..3...T....{....
0033EBD0: DA 67 D2 7E  14 EC 33 00  43 52 C3 7B  DA 67 D2 7E  .g.~..3.CR.{.g.~
0033EBE0: 6C EC 33 00  C1 09 D7 7E  0C 6B D2 7E  00 4A 70 F7  l.3....~.k.~.Jp.
0033EBF0: 16 00 00 00  4C F5 33 00  80 92 84 7B  01 00 00 00  ....L.3....{....
0033EC00: 60 AE 6A F7  00 00 00 00  60 9D 6A F7  00 00 00 00  `.j.....`.j.....
0033EC10: C0 09 D7 7E  54 EC 33 00  87 3D 69 F7  00 00 00 00  ...~T.3..=i.....
0033EC20: C0 09 D7 7E  0C 6B D2 7E  F4 2F 88 7B  14 EF 33 00  ...~.k.~./.{..3.
0033EC30: 80 00 00 00  94 EC 33 00  F0 95 84 7B  A0 A6 7B F7  ......3....{..{.
0033EC40: 00 00 00 00  14 EF 33 00  01 00 00 00  CC F5 33 00  ......3.......3.
0033EC50: 80 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033EC60: 01 00 00 00  A0 A6 7B F7  DA 67 D2 7E  92 72 69 F7  ......{..g.~.ri.


------------------------------------------------------------------------------
Percent memory used:    16
Total physical memory:  3823771648
Free physical memory:   3175477248
Page file:              6131683328
Total virtual memory:   4294836223
Free virtual memory:    4294770687
------------------------------------------------------------------------------

List of running WoW processes:

Process: H:\Documents\World of Warcraft\Wow.exe; pid: 27

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0xfffeffff
Processor Mask:         0xf
Number of Processors:   4
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        16
Processor Revision:     1026
Os Version:             5.1
Os Service Pack:        3.0

---

