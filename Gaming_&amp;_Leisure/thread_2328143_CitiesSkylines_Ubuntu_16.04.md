---
title: "Cities:Skylines Ubuntu 16.04"
date: 2016-06-17
forum: Gaming &amp; Leisure
---

### Post by yuklop on 2016-06-17
Hi All,

When I try to run Cities:Skylines on Ubuntu 16.04, it just flashes a black screen and returns to desktop.

I have the ATI open source graphics driver (and I suspect this is an issue) as the the game worked fine in Ubuntu 15.XX with the Catalyst propitiatory driver.

If its a help here is the output of the Player.log

```

Selecting FBConfig
GLX_FBCONFIG_ID=131
GLX_BUFFER_SIZE=32
GLX_DOUBLEBUFFER=1
GLX_RED_SIZE=8
GLX_GREEN_SIZE=8
GLX_BLUE_SIZE=8
GLX_ALPHA_SIZE=8
GLX_DEPTH_SIZE=24
GLX_STENCIL_SIZE=8
GLX_SAMPLES_ARB=0
GLX_SAMPLE_BUFFERS_Aterminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct null not valid
Stacktrace:


Native stacktrace:

    /home/danandlana/.steam/steamapps/common/Cities_Skylines/Cities_Data/Mono/x86_64/libmono.so(+0x915d6) [0x7f8a3480c5d6]
    /lib/x86_64-linux-gnu/libpthread.so.0(+0x113d0) [0x7f8a39e143d0]
    /lib/x86_64-linux-gnu/libc.so.6(gsignal+0x38) [0x7f8a3868c418]
    /lib/x86_64-linux-gnu/libc.so.6(abort+0x16a) [0x7f8a3868e01a]
    /home/danandlana/.steam/ubuntu12_32/steam-runtime/amd64/usr/lib/x86_64-linux-gnu/libstdc++.so.6(_ZN9__gnu_cxx27__verbose_terminate_handlerEv+0x155) [0x7f8a38f9fb05]
    /home/danandlana/.steam/ubuntu12_32/steam-runtime/amd64/usr/lib/x86_64-linux-gnu/libstdc++.so.6(+0x5ec76) [0x7f8a38f9dc76]
    /home/danandlana/.steam/ubuntu12_32/steam-runtime/amd64/usr/lib/x86_64-linux-gnu/libstdc++.so.6(+0x5eca3) [0x7f8a38f9dca3]
    /home/danandlana/.steam/ubuntu12_32/steam-runtime/amd64/usr/lib/x86_64-linux-gnu/libstdc++.so.6(+0x5eece) [0x7f8a38f9dece]
    /home/danandlana/.steam/ubuntu12_32/steam-runtime/amd64/usr/lib/x86_64-linux-gnu/libstdc++.so.6(_ZSt19__throw_logic_errorPKc+0x67) [0x7f8a38fef367]
    /home/danandlana/.steam/steamapps/common/Cities_Skylines/Cities.x64() [0xd9bf43]
    /home/danandlana/.steam/steamapps/common/Cities_Skylines/Cities.x64() [0xd9c468]
    /home/danandlana/.steam/steamapps/common/Cities_Skylines/Cities.x64() [0xd97282]
    /home/danandlana/.steam/steamapps/common/Cities_Skylines/Cities.x64() [0x5d209d]
    /home/danandlana/.steam/steamapps/common/Cities_Skylines/Cities.x64() [0x45edb6]
    /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf0) [0x7f8a38677830]
    /home/danandlana/.steam/steamapps/common/Cities_Skylines/Cities.x64() [0x46819d]

Debug info from gdb:

ERROR: ld.so: object '/home/danandlana/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
/usr/bin/gdb: /home/danandlana/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libncurses.so.5: no version information available (required by /usr/bin/gdb)
/usr/bin/gdb: /home/danandlana/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libncurses.so.5: no version information available (required by /usr/bin/gdb)
/usr/bin/gdb: /home/danandlana/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /usr/bin/gdb)
/usr/bin/gdb: /home/danandlana/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /lib/x86_64-linux-gnu/libreadline.so.6)
Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.
No threads.

=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================


```

If anyone can help it is much appreciated.

Thanks,

Dan

---

### Post by BSDShoes on 2016-06-19
Right click the game in the Steam list and go to Properties, select SET LAUNCH OPTIONS... and enter this following line and click OK and it should fix the black graphics:

[B]UNITY_DISABLE_GRAPHICS_DRIVER_WORKAROUNDS=yes %command%

[/B]I once had issues like your's but don't anymore.  Let me know if that fixes it.

---

### Post by yuklop on 2016-06-22
Hi BSDShoes,

Thanks for the reply.

This didn't work. Exactly the same symptom. Flashes a black screen for a second or so and then back to desktop. 
I've also tried disabling the Unity Overlay, going offline and checking the resolution which is correct.

---

### Post by George Edison on 2016-11-25
Good news. I found a fix.

Open a terminal and run the following command:

```

mv ~/.steam/bin/steam-runtime/amd64/usr/lib/x86_64-linux-gnu/libstdc++.so.6{,.bak}

```

For some reason, Steam is bundling an outdated version of the C++ runtime library.

---

