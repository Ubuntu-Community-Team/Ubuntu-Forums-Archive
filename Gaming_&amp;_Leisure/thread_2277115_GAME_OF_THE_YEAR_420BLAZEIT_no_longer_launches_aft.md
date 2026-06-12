---
title: "GAME OF THE YEAR: 420BLAZEIT no longer launches after update to 15.04"
date: 2015-05-06
forum: Gaming &amp; Leisure
---

### Post by ricky-flammia on 2015-05-06
Hello. I was able to get this game running in 14.10 x64 with the help of this forum and the solution turned out to be downloading some missing x86 packages. This time it seems as though all of the required packages are downloaded and yet the game refuses to run after updating to 15.04 x64. This is a native Linux application and it is set as an executable. Here is the link to the website of origin [http://www.gameoftheyear420blazeit.com/](http://www.gameoftheyear420blazeit.com/). Here is the terminal output when checking for the fulfilment of library requirements for this application.
```
richard@richard-Aspire-TC-120:~/Downloads$ ldd game.x86
    linux-gate.so.1 =>  (0xf7767000)
    libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf7710000)
    libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf76f0000)
    librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0xf76e0000)
    libGLU.so.1 => /usr/lib/i386-linux-gnu/libGLU.so.1 (0xf7668000)
    libGL.so.1 => /usr/lib32/fglrx/libGL.so.1 (0xf75b8000)
    libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf7468000)
    libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf7450000)
    libXcursor.so.1 => /usr/lib/i386-linux-gnu/libXcursor.so.1 (0xf7440000)
    libXrandr.so.2 => /usr/lib/i386-linux-gnu/libXrandr.so.2 (0xf7430000)
    libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf73e0000)
    libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf73c0000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf7200000)
    /lib/ld-linux.so.2 (0xf7740000)
    libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xf7108000)
    libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf70e0000)
    libXrender.so.1 => /usr/lib/i386-linux-gnu/libXrender.so.1 (0xf70d0000)
    libXfixes.so.3 => /usr/lib/i386-linux-gnu/libXfixes.so.3 (0xf70c8000)
    libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf70c0000)
    libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf70b8000)

```
Does anyone have any ideas as to the cause of this problem and how I can get this application running on 15.04 x64. Thanks.

---

