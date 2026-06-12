---
title: "Pcsx2 crashing immediately"
date: 2016-04-18
forum: Emulators
---

### Post by oniondip420 on 2016-04-18
So my ps2 died and i figured why not try and work out an emulator. I am fairly new to Ubuntu, Linux in general. This is officially my first question post. Here goes. I downloaded pcsx2. Seems to work fine. Downloaded an .iso ps2 game. I go to load the iso in the settings, the whole emulator crashes. I don't run from the terminal but when i run the debug button at the top i get this message.

 
/build/pcsx2-MSPTJA/pcsx2-1.4.0/common/src/Utilities/Linux/LnxHostSys.cpp(64) : assertion failed:
    Function:  void SysPageFaultSignalFilter(int, siginfo_t*, void*)
    Thread:    EE Core
    Condition: false
    Message:   Unhandled page fault @ 0x00000030
                                   
Stacktrace:
[00] wxSpinCtrlBase::~wxSpinCtrlBase()           
[01] 0x0xb76f8c98                                
[02] wxString wxString::Format<char const*>(wxFormatString const&, char const*)
[03] wxString wxString::Format<char const*>(wxFormatString const&, char const*)
[04] wxString wxString::Format<char const*>(wxFormatString const&, char const*)
[05] wxString wxString::Format<char const*>(wxFormatString const&, char const*)
[06] wxString wxString::Format<char const*>(wxFormatString const&, char const*)
[07] wxSpinCtrlBase::~wxSpinCtrlBase()           
[08] wxSpinCtrlBase::~wxSpinCtrlBase()           
[09] wxSpinCtrlBase::~wxSpinCtrlBase()           
[10] wxSpinCtrlBase::~wxSpinCtrlBase()           
[11] wxSpinCtrlBase::~wxSpinCtrlBase()           
[12] wxSpinCtrlBase::~wxSpinCtrlBase()           
[13] 0x0xb673af70                                
[14] clone                                       


 No idea what that means. Been at this all day trying to figure it out i hope some one can help me.

---

### Post by deadflowr on 2016-04-18
Moved to **Emulators**

---

### Post by oniondip420 on 2016-04-18
Thanks! Sorry....

---

### Post by oniondip420 on 2016-04-21
[
PCSX2 1.4.0-0- compiled on Jan  6 2016
Savestate version: 0x9a0b0000

Host Machine Init:
    Operating System =  Linux 3.19.0-58-generic i686
    Physical RAM     =  3978 MB
    CPU name         =  Intel(R) Core(TM) i7 CPU       Q 720  @ 1.60GHz
    Vendor/Model     =  GenuineIntel (stepping 05)
    CPU speed        =  1.593 ghz (8 logical threads)
    x86PType         =  Standard OEM
    x86Flags         =  bfebfbff 0098e3fd
    x86EFlags        =  28100000

x86 Features Detected:
    SSE2.. SSE3.. SSSE3.. SSE4.1.. SSE4.2

Installing POSIX SIGSEGV handler...
Reserving memory for recompilers...

Loading plugins...
    Binding   GS: /usr/lib/games/PCSX2/libGSdx-1.0.0.so 
(GameDB) 9693 games on record (loaded in 339ms)
    Binding  PAD: /usr/lib/games/PCSX2/libonepad-1.1.0.so 
    Binding SPU2: /usr/lib/games/PCSX2/libspu2x-2.0.0.so 
    Binding CDVD: /usr/lib/games/PCSX2/libCDVDnull.so 
    Binding  USB: /usr/lib/games/PCSX2/libUSBnull-0.7.0.so 
    Binding   FW: /usr/lib/games/PCSX2/libFWnull-0.7.0.so 
    Binding DEV9: /usr/lib/games/PCSX2/libdev9null-0.5.0.so 
Plugins loaded successfully.

]

So theoretically it should work from everything i have read. Yet if fails every time. I wish i knew more, because at this point i cannot game on Linux( Steam account has ten games not supported, emulators not working, blizzard through wine is a nightmare, anything through wine is glitchy and more trouble then buying windows yet I do not want to support Microsoft on principal so i will fore go gaming until i receive help.)

---

### Post by oniondip420 on 2016-04-23
So i figured out how to open pcsx2 from my terminal. "Trace/breakpoint trap (core dumped)"  is what it says when it crashes when i select the .iso

---

### Post by oniondip420 on 2016-04-27
[http://forums.pcsx2.net/Thread-Need-help-Pcsx-crashing?pid=516927#pid516927](http://forums.pcsx2.net/Thread-Need-help-Pcsx-crashing?pid=516927#pid516927)

---

