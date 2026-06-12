---
title: "Installing Street Legal"
date: 2007-06-05
forum: Gaming &amp; Leisure
---

### Post by davkasayres on 2007-06-05
Hi all,

I have recently converted from gentoo and installed ubuntu 7.04 and upgraded to kubuntu.

I have been getting along quite well with my new distro and finding it alot easyer than gentoo.
Recently i found a copy of an old classic " Streel Legal ", a need for speed type game.

I have installed steam and got that working fine with wine.

Now the problem....

Here is what i get when i try and execute the setup.exe using this command:

raven@raven-desktop:~/games/streetlegal/SETUP$ wine SETUP.EXE 
wine: Unhandled page fault on read access to 0x00000000 at address 0x4138eb (thread 0009), sta                                                                                       rting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x004138eb).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:004138eb ESP:0033e96c EBP:00010024 EFLAGS:00210216(   - 00      -RIAP1)
 EAX:00000000 EBX:00000000 ECX:7ec2cec0 EDX:7ec2cec4
 ESI:000003d8 EDI:0000030c
Stack dump:
0x0033e96c:  7ec2cec0 7bc29ec1 7b88c9db 7ec251a4
0x0033e97c:  0000030c 0000ffff 0033e9b4 7ebda2ff
0x0033e98c:  7ec2cec0 0000ffff 7ec2cec0 7ec251a4
0x0033e99c:  00000001 0016f920 0033e9d4 7ebda174
0x0033e9ac:  7ec2cec0 0016f920 0033e9d4 7ebb22aa
0x0033e9bc:  0000030c 0000ffff 7e5623cb 7ec251a4
Backtrace:
=>1 0x004138eb in setup (+0x138eb) (0x00010024)
  2 0x00000000 (0x00000000)
0x004138eb: movb        0x0(%eax),%cl
Modules:
Module  Address                 Debug info      Name (74 modules)
PE        400000-  455000       Export          setup
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bc98000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc98000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d27a000-7d28f000       Deferred        midimap<elf>
  \-PE  7d280000-7d28f000       \               midimap
ELF     7d28f000-7d2b5000       Deferred        msacm32<elf>
  \-PE  7d2a0000-7d2b5000       \               msacm32
ELF     7d2b5000-7d2f1000       Deferred        wineoss<elf>
  \-PE  7d2c0000-7d2f1000       \               wineoss
ELF     7d2f1000-7d323000       Deferred        uxtheme<elf>
  \-PE  7d300000-7d323000       \               uxtheme
ELF     7d58b000-7d5a3000       Deferred        msacm32<elf>
  \-PE  7d590000-7d5a3000       \               msacm32
ELF     7d5a5000-7d5aa000       Deferred        libxfixes.so.3
ELF     7d5aa000-7d5b3000       Deferred        libxcursor.so.1
ELF     7d5b3000-7d5d0000       Deferred        imm32<elf>
  \-PE  7d5c0000-7d5d0000       \               imm32
ELF     7d5d0000-7d5d6000       Deferred        libxrandr.so.2
ELF     7d5d6000-7d5de000       Deferred        libxrender.so.1
ELF     7db07000-7e38d000       Deferred        libglcore.so.1
ELF     7e38d000-7e419000       Deferred        libgl.so.1
ELF     7e419000-7e41e000       Deferred        libxdmcp.so.6
ELF     7e41e000-7e50f000       Deferred        libx11.so.6
ELF     7e50f000-7e51d000       Deferred        libxext.so.6
ELF     7e51d000-7e522000       Deferred        libxxf86vm.so.1
ELF     7e522000-7e53a000       Deferred        libice.so.6
ELF     7e53a000-7e543000       Deferred        libsm.so.6
ELF     7e543000-7e5d2000       Deferred        winex11<elf>
  \-PE  7e550000-7e5d2000       \               winex11
ELF     7e657000-7e677000       Deferred        libexpat.so.1
ELF     7e677000-7e6a2000       Deferred        libfontconfig.so.1
ELF     7e6a2000-7e6b6000       Deferred        libz.so.1
ELF     7e6b6000-7e721000       Deferred        libfreetype.so.6
ELF     7e721000-7e77a000       Deferred        shlwapi<elf>
  \-PE  7e730000-7e77a000       \               shlwapi
ELF     7e77a000-7e877000       Deferred        shell32<elf>
  \-PE  7e790000-7e877000       \               shell32
ELF     7e877000-7e88b000       Deferred        lz32<elf>
  \-PE  7e880000-7e88b000       \               lz32
ELF     7e88b000-7e8a5000       Deferred        version<elf>
  \-PE  7e890000-7e8a5000       \               version
ELF     7e8a5000-7e934000       Deferred        winmm<elf>
  \-PE  7e8b0000-7e934000       \               winmm
ELF     7e934000-7e9f1000       Deferred        comctl32<elf>
  \-PE  7e940000-7e9f1000       \               comctl32
ELF     7e9f1000-7ea04000       Deferred        libresolv.so.2
ELF     7ea04000-7ea22000       Deferred        iphlpapi<elf>
  \-PE  7ea10000-7ea22000       \               iphlpapi
ELF     7ea22000-7ea77000       Deferred        rpcrt4<elf>
  \-PE  7ea30000-7ea77000       \               rpcrt4
ELF     7ea77000-7ea83000       Deferred        libgcc_s.so.1
ELF     7ea84000-7ea86000       Deferred        libnvidia-tls.so.1
ELF     7eb7e000-7ec3e000       Deferred        gdi32<elf>
  \-PE  7eba0000-7ec3e000       \               gdi32
ELF     7ec3e000-7ed7b000       Deferred        user32<elf>
  \-PE  7ec60000-7ed7b000       \               user32
ELF     7ed7b000-7edc3000       Deferred        advapi32<elf>
  \-PE  7ed90000-7edc3000       \               advapi32
ELF     7edc3000-7ee62000       Deferred        ole32<elf>
  \-PE  7edd0000-7ee62000       \               ole32
ELF     7ef93000-7ef9e000       Deferred        libnss_files.so.2
ELF     7ef9e000-7efa8000       Deferred        libnss_nis.so.2
ELF     7efa8000-7efbf000       Deferred        libnsl.so.1
ELF     7efbf000-7efc8000       Deferred        libnss_compat.so.2
ELF     7efc8000-7efef000       Deferred        libm.so.6
ELF     7efef000-7eff2000       Deferred        libxau.so.6
ELF     b7d24000-b7d28000       Deferred        libdl.so.2
ELF     b7d28000-b7e69000       Deferred        libc.so.6
ELF     b7e69000-b7e80000       Deferred        libpthread.so.0
ELF     b7e91000-b7fa5000       Deferred        libwine.so.1
ELF     b7fa7000-b7fc2000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) Z:\home\raven\games\streetlegal\SETUP\SETUP.EXE
        00000009    0 <==
raven@raven-desktop:~/games/streetlegal/SETUP$ 


As you can see, its not healthy. 

Can someone please help me, i really like this game and im stuck on this.

Thanks in advance.

---

### Post by davkasayres on 2007-06-06
Ive also tryed changing the sound from oss to alsa, but still no luck.

Anyone got any ideas?

---

### Post by hikaricore on 2007-06-06
I couldn't find your game on The Wine Application Database: [http://appdb.winehq.org/](http://appdb.winehq.org/)

So I'm not really sure where to point you for more into.

This is a windows game right?  Not an old dos game?  Because you won't be able to run
an old dos game with wine, you would have to use dosemu.  ^_^

Good luck,

--Aaron

---

### Post by davkasayres on 2007-06-06
Its a windows game yeah, but to be honest i had never heard of it up until last year.

Worth it though i'll keep at it.

Cheers

---

