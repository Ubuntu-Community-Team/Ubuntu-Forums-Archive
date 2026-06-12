---
title: "Yet Another WoW help thread..."
date: 2007-01-09
forum: Gaming &amp; Leisure
---

### Post by steevk on 2007-01-09
Hello everybody-

I'm typing this post from my friend's awesome Dell Inspiron E1505. He got fed up with windows, I got him onto Ubuntu. So that's a win right there.

Only problem is, even though World of Warcraft just works for me, it doesn't for him. I've installed the game the same way as I did with my own computer (patched wine 9.26). That didn't work. Then I tried to follow the instructions on the Wiki, and that hasn't worked either...

Basically, the game crashes on startup. In a bunch of different ways. They're all related to memory errors. I have a feeling it has to do with the graphics card drivers...I've used i810, vesa, and intel, and none of them make WoW work correctly.

example error:

Wow Error #132.

Or....

```
goldenchild@goldenchild-laptop:~/.wine/drive_c/Program Files/World of Warcraft$ wine WoW.exe -opengl
libGL warning: 3D driver claims to not support visual 0x5b
libGL warning: 3D driver claims to not support visual 0x5b
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d160000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d160000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x34eedc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f148,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f650,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f63c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:win:EnumDisplayDevicesW ((null),0,0x34ee58,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
wine: Unhandled page fault on read access to 0x00007548 at address 0x7e25c905 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00007548 in 32-bit code (0x7e25c905).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e25c905 ESP:0034c660 EBP:0034c678 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00001405 EBX:7e29c38c ECX:774ed410 EDX:00000000
 ESI:00007548 EDI:7c168f60
Stack dump:
0x0034c660:  7c640a18 7e29c38c 7c640a18 7e29c38c
0x0034c670:  7c640a18 00007548 0034c6c8 7e233fe7
0x0034c680:  7c640a18 00001405 0000000c 00001403
0x0034c690:  00007548 00001403 00007548 7e33b53c
0x0034c6a0:  7e60bc70 00007548 00001403 0000000c
0x0034c6b0:  000010ca 000010c5 00000004 7e632510
Backtrace:
=>1 0x7e25c905 _ac_import_elements+0xe5() in i915_dri.so (0x0034c678)
  2 0x7e233fe7 _tnl_DrawRangeElements+0xc7() in i915_dri.so (0x0034c6c8)
  3 0x7e60bcbd glDrawRangeElementsEXT+0x4d() in libgl.so.1 (0x0034c6f8)
  4 0x7e76be60 in opengl32 (+0x2be60) (0x0034c738)
  5 0x00583e8b in wow (+0x183e8b) (0x0034c764)
  6 0x00570468 in wow (+0x170468) (0x0034c780)
  7 0x0057047b in wow (+0x17047b) (0x0034c7a8)
  8 0x006eedbc in wow (+0x2eedbc) (0x0034c83c)
  9 0x006ec7ae in wow (+0x2ec7ae) (0x0034fbb8)
  10 0x0073156e in wow (+0x33156e) (0x0034fc90)
  11 0x0046523f in wow (+0x6523f) (0x0034fcb4)
  12 0x0072bb47 in wow (+0x32bb47) (0x0034fcd8)
  13 0x0072a76c in wow (+0x32a76c) (0x0034fce4)
  14 0x0043860e in wow (+0x3860e) (0x0034fdac)
  15 0x00416370 in wow (+0x16370) (0x0034fde0)
  16 0x00412d2f in wow (+0x12d2f) (0x0034fe50)
  17 0x004128b1 in wow (+0x128b1) (0x0034fe68)
  18 0x00403ea0 in wow (+0x3ea0) (0x0034ff08)
  19 0x7b8702ce in kernel32 (+0x502ce) (0x0034ffe8)
  20 0xb7e4f587 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7e25c905 _ac_import_elements+0xe5 in i915_dri.so: movzwl      0x0(%esi,%edx,2),%eax
Modules:
Module  Address                 Debug info      Name (95 modules)
PE      350000-3e0000   Deferred        fmod
PE      400000-c87000   Export          wow
PE      10000000-10069000       Deferred        divxdecoder
ELF     77472000-774b9000       Deferred        dbghelp<elf>
  \-PE  77480000-774b9000       \               dbghelp
ELF     7b800000-7b91b000       Export          kernel32<elf>
  \-PE  7b820000-7b91b000       \               kernel32
ELF     7bc00000-7bc83000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc83000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7cd3d000-7cd86000       Deferred        dsound<elf>
  \-PE  7cd50000-7cd86000       \               dsound
ELF     7cdce000-7cde3000       Deferred        psapi<elf>
  \-PE  7cdd0000-7cde3000       \               psapi
ELF     7cde3000-7cde9000       Deferred        libnss_dns.so.2
ELF     7cdfb000-7ce0f000       Deferred        mswsock<elf>
  \-PE  7ce00000-7ce0f000       \               mswsock
ELF     7d388000-7d39d000       Deferred        midimap<elf>
  \-PE  7d390000-7d39d000       \               midimap
PE      7d3a0000-7d3b5000       --none--        msacm32
ELF     7d3b5000-7d3f1000       Deferred        wineoss<elf>
  \-PE  7d3c0000-7d3f1000       \               wineoss
ELF     7d41e000-7d450000       Deferred        uxtheme<elf>
  \-PE  7d430000-7d450000       \               uxtheme
ELF     7d452000-7d457000       Deferred        libxfixes.so.3
ELF     7d457000-7d460000       Deferred        libxcursor.so.1
ELF     7d460000-7d47e000       Deferred        ximcp.so.2
ELF     7d47e000-7d481000       Deferred        libxrandr.so.2
ELF     7d481000-7d489000       Deferred        libxrender.so.1
ELF     7d489000-7d48c000       Deferred        libxinerama.so.1
ELF     7e08c000-7e2b7000       Export          i915_dri.so
ELF     7e2b7000-7e344000       Deferred        winex11<elf>
  \-PE  7e2d0000-7e344000       \               winex11
ELF     7e344000-7e362000       Deferred        libexpat.so.1
ELF     7e362000-7e391000       Deferred        libfontconfig.so.1
ELF     7e391000-7e3a5000       Deferred        libz.so.1
ELF     7e3a5000-7e40f000       Deferred        libfreetype.so.6
ELF     7e40f000-7e42e000       Deferred        mpr<elf>
  \-PE  7e420000-7e42e000       \               mpr
ELF     7e42e000-7e475000       Deferred        wininet<elf>
  \-PE  7e440000-7e475000       \               wininet
ELF     7e475000-7e49b000       Deferred        msacm32<elf>
ELF     7e49b000-7e529000       Deferred        winmm<elf>
  \-PE  7e4b0000-7e529000       \               winmm
ELF     7e529000-7e545000       Deferred        imm32<elf>
  \-PE  7e530000-7e545000       \               imm32
ELF     7e545000-7e54c000       Deferred        libdrm.so.2
ELF     7e54c000-7e5c6000       Deferred        libglu.so.1
ELF     7e5c6000-7e635000       Export          libgl.so.1
ELF     7e635000-7e6fe000       Deferred        libx11.so.6
ELF     7e6fe000-7e70b000       Deferred        libxext.so.6
ELF     7e70b000-7e723000       Deferred        libice.so.6
ELF     7e723000-7e79c000       Export          opengl32<elf>
  \-PE  7e740000-7e79c000       \               opengl32
ELF     7e79c000-7e7c8000       Deferred        ws2_32<elf>
  \-PE  7e7a0000-7e7c8000       \               ws2_32
ELF     7e7c8000-7e7e2000       Deferred        wsock32<elf>
  \-PE  7e7d0000-7e7e2000       \               wsock32
ELF     7e7e2000-7e7f5000       Deferred        libresolv.so.2
ELF     7e7f5000-7e813000       Deferred        iphlpapi<elf>
  \-PE  7e800000-7e813000       \               iphlpapi
ELF     7e813000-7e867000       Deferred        rpcrt4<elf>
  \-PE  7e820000-7e867000       \               rpcrt4
ELF     7e867000-7e8ff000       Deferred        ole32<elf>
  \-PE  7e880000-7e8ff000       \               ole32
ELF     7e8ff000-7e957000       Deferred        shlwapi<elf>
  \-PE  7e910000-7e957000       \               shlwapi
ELF     7e957000-7ea49000       Deferred        shell32<elf>
  \-PE  7e970000-7ea49000       \               shell32
ELF     7ea49000-7ea8f000       Deferred        advapi32<elf>
  \-PE  7ea50000-7ea8f000       \               advapi32
ELF     7ea8f000-7ea9a000       Deferred        libgcc_s.so.1
ELF     7ea9a000-7ea9c000       Deferred        xlcutf8load.so.2
ELF     7ea9e000-7eaa3000       Deferred        libxdmcp.so.6
ELF     7eaa3000-7eaac000       Deferred        libsm.so.6
ELF     7eb8b000-7ec41000       Deferred        gdi32<elf>
  \-PE  7eba0000-7ec41000       \               gdi32
ELF     7ec41000-7ed79000       Deferred        user32<elf>
  \-PE  7ec60000-7ed79000       \               user32
ELF     7ed79000-7ee39000       Deferred        comctl32<elf>
  \-PE  7ed80000-7ee39000       \               comctl32
ELF     7ee39000-7ee9d000       Deferred        msvcrt<elf>
  \-PE  7ee50000-7ee9d000       \               msvcrt
ELF     7efa7000-7efb2000       Deferred        libnss_files.so.2
ELF     7efb2000-7efc8000       Deferred        libnsl.so.1
ELF     7efc8000-7efee000       Deferred        libm.so.6
ELF     7efee000-7eff1000       Deferred        libxau.so.6
ELF     7eff1000-7eff6000       Deferred        libxxf86vm.so.1
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7ce0000-b7ce9000       Deferred        libnss_compat.so.2
ELF     b7cea000-b7cee000       Deferred        libdl.so.2
ELF     b7cee000-b7e22000       Deferred        libc.so.6
ELF     b7e23000-b7e36000       Deferred        libpthread.so.0
ELF     b7e48000-b7f59000       Export          libwine.so.1
ELF     b7f5b000-b7f76000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\World of Warcraft\WoW.exe
        0000001e    0
        0000001d    0
        0000001c    0
        0000001b    0
        0000001a    0
        00000019    0
        00000018    2
        00000017   15
        00000016   15
        00000014   15
        00000012    0
        00000011    0
        00000010    0
        0000000d    1
        00000009    0 <==

```

Does anyone have any ideas? This is the difference between Windows going back on this laptop or, as he just told me, becoming a Linux user for life. Gimme some ideas, people!

Thanks,
steev

---

### Post by pay on 2007-01-09
With the latest wine you don't need to patch it (0.9.28). To test if the graphics are set up correctly type this into the terminal ```
glxinfo | grep direct
```If that comes up with "Direct Rendering: No" Then try this```
sudo aptitude install alien
wget -c http://downloadmirror.intel.com/df-support/8211/eng/dri-I915-v1.1-20041217.i386.rpm
sudo alien -i dri-I915-v1.1-20041217.i386.rpm
```

---

### Post by steevk on 2007-01-09
Thanks for the quick reply! 

goldenchild@goldenchild-laptop:~$ glxinfo | grep direct
libGL warning: 3D driver claims to not support visual 0x5b
direct rendering: Yes


That's what I get. So I ran your other option anyway...and now it segfaults.

Is that libGL warning bad?


EDIT: Now I've got it not segfaulting. Wine 0.9.28. Still doesn't work.

---

### Post by Sammi on 2007-01-10
I'm also convinced you haven't gotten your graphics driver to work properly, but have you explored all the options all troubleshoting tips in this howto: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Try the dll tip in the troubleshooting section.

You can also just copy a working WoW installation from anywhere else, even installing in Win and then copying the Win installation over to your Ubuntu partition.

---

### Post by steevk on 2007-01-10
> **Sammi said:**
> I'm also convinced you haven't gotten your graphics driver to work properly, but have you explored all the options all troubleshoting tips in this howto: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Try the dll tip in the troubleshooting section.

Dlls: Did.
Wow won't run in d3d mode either.

The other options are related to sounds and such...


> You can also just copy a working WoW installation from anywhere else, even installing in Win and then copying the Win installation over to your Ubuntu partition.

WoW installed correctly, it's running the game that's all messed up.


EDIT: Here's what it's looking like...

---

### Post by Josh1 on 2007-01-10
I get that when i installed the openbeta client and had the wrong driver installed when i was in windows in 2004.
So make sure the correct drivers are installed or try the -opengl flag at the end of wine wow.exe

---

### Post by Sammi on 2007-01-10
Ok I agree. It's most definatively a driver issue or you are running in d3d mode not opengl.

The howto explains how to enable opengl mode.

Did the graphics driver, which pay suggested, install correctly?

To test this you can run these commands and post the output here:
     [LEFT]```
glxinfo | grep vendor
glxinfo | grep 'OpenGL version'
```[/LEFT]
 
And let this command run for a while, say 30 seconds, then post the output:
     [LEFT]```
glxgears -printfps
```[/LEFT]

---

### Post by pay on 2007-01-10
It also doesn't seem to be displaying fonts. Try ```
sudo aptitude install msttcorefonts
```

---

### Post by crd16 on 2007-01-10
I am also helping out with this problem.  The guy who is trying to get wow to work on his computer is a mutual friend of steevk and I.  I'm actually on the computer in question now.  I ran the necessary commands to print out the specs.

$ glxinfo | grep vendor
    libGL warning: 3D driver claims to not support visual 0x5b
    server glx vendor string: SGI
    client glx vendor string: SGI
    OpenGL vendor string: Tungsten Graphics, Inc

$ glxinfo | grep 'OpenGL version'
     libGL warning: 3D driver claims to not support visual 0x5b
     OpenGL version string: 1.3 Mesa 6.5.1

$ glxgears -printfps
     libGL warning: 3D driver claims to not support visual 0x5b
     3941 frames in 5.0 seconds = 788.102 FPS
     4970 frames in 5.0 seconds = 993.974 FPS
     5674 frames in 5.0 seconds = 1134.672 FPS
     5709 frames in 5.0 seconds = 1141.606 FPS
     5676 frames in 5.0 seconds = 1135.172 FPS
     5507 frames in 5.0 seconds = 1101.275 FPS
     5595 frames in 5.0 seconds = 1118.820 FPS

There it is folks.  We appreciate everyone's help.  Also, I am brand new to this forum so go easy on me about forum conventions.

Also, in reply to the possible solution of downloading new drivers... the problem with that is that the graphics processor is an intel integrated chipset 950 of the 945gma chipset family.  We looked for a few hours on forums and on the dell website and the intel website and all over the web and couldn't find drivers for ubuntu or even red hat that worked at all.  Any thoughts on that would help as well.

---

### Post by chadk on 2007-01-10
> **pay said:**
> With the latest wine you don't need to patch it (0.9.28). To test if the graphics are set up correctly type this into the terminal ```
glxinfo | grep direct
```If that comes up with "Direct Rendering: No" Then try this```
sudo aptitude install alien
wget -c http://downloadmirror.intel.com/df-support/8211/eng/dri-I915-v1.1-20041217.i386.rpm
sudo alien -i dri-I915-v1.1-20041217.i386.rpm
```

When I typed glxinfo | grep direct it restarted X.
I came here because I can't run WoW all of the sudden.  I think there was just an xorg update?  Well whatever it is, I can no longer open wow.  When I try it restarts X, I see the nvidia logo and then login prompt.  If I try to log in, type in my password, it will just go to a blank screen like it's loading but never does anything.

If I switch (at the login screen) from gnome to enlightenment, it lets me log in, but even in enlightenment if I type glxinfo in a term it just restarts X.  but then I can log into gnome again.

---

### Post by Sammi on 2007-01-10
> **chadk said:**
> When I typed glxinfo | grep direct it restarted X.
I came here because I can't run WoW all of the sudden.  I think there was just an xorg update?  Well whatever it is, I can no longer open wow.  When I try it restarts X, I see the nvidia logo and then login prompt.  If I try to log in, type in my password, it will just go to a blank screen like it's loading but never does anything.

If I switch (at the login screen) from gnome to enlightenment, it lets me log in, but even in enlightenment if I type glxinfo in a term it just restarts X.  but then I can log into gnome again.
Had the same prob here. Solved it by uninstalling and reinstalling my Nvidia drivers.

---

### Post by chadk on 2007-01-10
> **Sammi said:**
> Had the same prob here. Solved it by uninstalling and reinstalling my Nvidia drivers.

Yep. That fixed it for me as well..  Automatix failed to reinstall nvidia so I used the good old Envy script.  Love that script.

---

### Post by crd16 on 2007-01-10
Does anyone know what that Vendor: SGI stuff is? I thought this was an Intel chipset...

---

### Post by steevk on 2007-01-10
So we have it running now.

I went into Config.wtf and turned off the "Pixel Shaders" option that WoW automatically put in there. The game loaded up, and now it's downloading the updates. We'll see in a while if the game works once the patches download.

---

### Post by steevk on 2007-01-11
Okay guys, it runs. I can log in. Can't play the game however...the graphics are a bit off. See attached screenshot. Thanks for the help....we're making progress!

---

### Post by Sammi on 2007-01-11
Try to run the game in d3d mode. Disable some options in video settings, like shaders for example, and run it in opengl again.

Also try the newly released version of Wine 0.9.29. It's supposed to have better d3d support.

---

### Post by steevk on 2007-01-12
Yep. No idea why, but it runs great in D3D.

Thanks for everyone that helped...we have a successful Linux convert!

---

### Post by Sammi on 2007-01-12
Great! :D

I find it to be nothing short of fantastic that DirectX support is finally picking up in Wine :cool:

But it's still strange that OpenGL won't work. I'm still suspecting a driver issue.

---

### Post by steevk on 2007-01-12
Yeah, the extra support is great...

There was a site that indicated that the laptop in question has a Radeon in it instead of an Intel Integrated. It said to use those drivers...but that didn't work for us. So I don't know. Important thing is that it works.

---

### Post by apakun on 2007-01-17
In short, is there anyone can tell  me how to solve the problem:
libGL warning: 3D driver claims to not support visual 0x5b

I get this error and unable to run "wine control"

Thanks

---

