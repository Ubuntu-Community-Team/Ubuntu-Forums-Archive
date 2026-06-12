---
title: "World of Goo bought through Software center error"
date: 2011-12-02
forum: Gaming &amp; Leisure
---

### Post by su-37 on 2011-12-02
Hey, i just bought the world of Goo game through the center and when i click on the icon to run nothing happens. No error messages, no black screens, just nothing happens. Im running 11.10 updated this morning.

Any help would be appreciated,
James

---

### Post by thatguruguy on 2011-12-02
Open a terminal and type the following:
```
WorldOfGoo
```
Copy and paste everything from the terminal into this thread. For the sake of readability, please make sure to put code tags around the output.

---

### Post by su-37 on 2011-12-04
Thanks for helping me out. Heres what came up when i ran what you said.


"james@james-Aspire-5745G:~$ WorldOfGoo
Aborted

It looks like World of Goo crashed! If you need support, please include the
contents of the log file in your problem report.
The log file is stored at: /home/james/.WorldOfGoo/WorldOfGoo.log
"

---

### Post by thatguruguy on 2011-12-04
Perhaps you'd like to post the contents of the log here. It might also be a good idea to give us an idea of your system set up.  E.g., the type of computer you're running, the version of Ubuntu you're running, and the graphics hardware you have.

---

### Post by su-37 on 2011-12-05
Tried looking for that file path, but it wasn't there. I'll try installing again.

---

### Post by MasterMIKE on 2012-02-02
I have the same problem. The terminal says:
~$ WorldOfGoo
Segmentation fault (core dumped)

It looks like World of Goo crashed! If you need support, please include the
contents of the log file in your problem report.
The log file is stored at: /home/****/.WorldOfGoo/WorldOfGoo.log

This is what the log file said:

Libraries used:
    linux-vdso.so.1 =>  (0x00007fff7b7ff000)
    librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007fd3c2e0d000)
    libGL.so.1 => /usr/lib/libGL.so.1 (0x00007fd3c2c04000)
    libGLU.so.1 => /usr/lib/x86_64-linux-gnu/libGLU.so.1 (0x00007fd3c2996000)
    libSDL-1.2.so.0 => ./libs64/libSDL-1.2.so.0 (0x00007fd3c26d0000)
    libSDL_mixer-1.2.so.0 => ./libs64/libSDL_mixer-1.2.so.0 (0x00007fd3c2448000)
    libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007fd3c2147000)
    libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fd3c1ec3000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fd3c1b21000)
    /lib64/ld-linux-x86-64.so.2 (0x00007fd3c3033000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007fd3c1903000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007fd3c16ff000)
    libXext.so.6 => /usr/lib/x86_64-linux-gnu/libXext.so.6 (0x00007fd3c14ec000)
    libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007fd3c12d5000)
    libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007fd3c0fa1000)
    libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007fd3c0d84000)
    libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007fd3c0b81000)
    libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007fd3c097b000)

glxinfo not found!

---

