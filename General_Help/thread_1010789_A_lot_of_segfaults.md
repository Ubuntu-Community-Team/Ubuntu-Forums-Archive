---
title: "A lot of segfaults"
date: 2008-12-14
forum: General Help
---

### Post by guix on 2008-12-14
I'm getting a lot of segfaults since intrepid on a fresh install. It started with aptitude, then I had segfaults with midnight commander (mc), then mostly on a lot of opengl applications (supertux, chromum, xmoto, ...) but not only (vlc for example). Any hints for me ?

Example of vlc segfault :
```

Dec 14 07:33:12 panther kernel: [ 2087.682528] vlc[5636]: segfault at 4 ip b7ee6f83 sp ae4de1d4 error 4 in libc-2.8.90.so[b7e75000+158000]
Dec 14 08:56:04 panther kernel: [ 7059.096706] vlc[7350]: segfault at 0 ip 00000000 sp adbcdff0 error 4 in vlc[8048000+2000]
Dec 14 09:50:09 panther kernel: [10304.310131] vlc[8636]: segfault at 0 ip 00000000 sp aee31380 error 4 in vlc[8048000+2000]
Dec 14 09:53:36 panther kernel: [10511.553073] vlc[8748]: segfault at 150 ip b04990fa sp ae2f01f0 error 4 in libts_plugin.so[b048e000+13000]
Dec 14 10:03:01 panther kernel: [11076.458848] vlc[8860]: segfault at 10 ip b0e560fa sp ae4411f0 error 4 in libts_plugin.so[b0e4b000+13000]
Dec 14 10:08:52 panther kernel: [11426.864486] vlc[9030]: segfault at 8 ip b7d1a9b8 sp ac492da4 error 6 in libc-2.8.90.so[b7ca9000+158000]
Dec 14 10:13:59 panther kernel: [11734.269876] Eeek! page_mapcount(page) went negative! (-1920103025)

```

I seem to have problems with pulseaudio as well, do you think the segfaults can be related ?
```

Dec 14 10:27:54 panther pulseaudio[5374]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Opération non permise
Dec 14 10:27:54 panther pulseaudio[5374]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Opération non permise
Dec 14 10:27:55 panther pulseaudio[5374]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
Dec 14 10:27:55 panther pulseaudio[5374]: main.c: Module load failed.
Dec 14 10:27:55 panther pulseaudio[5374]: main.c: Failed to initialize daemon.
Dec 14 10:27:55 panther pulseaudio[5372]: main.c: daemon startup failed.

```

I also want to fix this one which could be related to the pulseaudio problem (read somewhere so) :
```

Dec 14 10:26:59 panther kernel: Inspecting /boot/System.map-2.6.27-9-generic
Dec 14 10:26:59 panther kernel: Cannot find map file.

```

---

### Post by iponeverything on 2008-12-14
maybe you need to join the party at:

[http://ubuntuforums.org/showthread.php?t=976287](http://ubuntuforums.org/showthread.php?t=976287)

---

### Post by guix on 2008-12-14
Thanks for the link. I'm still reading, but I have no wireless card. And I just had a Rhythmbox segfault...
```

Dec 14 12:14:52 panther kernel: [ 1040.053286] rhythmbox[5612]: segfault at c ip b7d56024 sp b0ed0534 error 4 in libpthread-2.8.90.so[b7d4d000+15000]

```

---

### Post by iponeverything on 2008-12-14
rhythmbox, vlc and what else?

looks to me like you might have a bad memory stick.

run the memtest from grub.  If you don't see any problems there -- then try each of your memory chips by themselves..

---

### Post by guix on 2008-12-14
...and Rhythmbox again... :)
```

Dec 14 12:31:36 panther kernel: [ 2043.454669] rhythmbox[5834]: segfault at 4 ip b6e2085d sp b5e492d0 error 4 in libglib-2.0.so.0.1800.2[b6dc9000+b5000]

```

You are right, I'm gonna test the memory. Thanks for following ! See you later.

---

### Post by guix on 2008-12-14
The test went with no errors at all. It lasted for approx 1 hour and during that time, I usually get a lot of segfaults. I ran the BIOS memory test, too.

I'm gonna try to reduce the CPU speed in order for the CPU to exchange data slower with the memory, at 100 MHz instead of 133 MHz. Maybe some memory sticks are tired and going slower will work. So now putting my Athlon 1GHz in reduced speed (750 Mhz) and testing...

If it doesn't work I will try to turn off the ACPI, then I still can try the intrepid proposed or backported new kernels (I run 2.6.27-9 now).

But after that... I have no other ideas...

---

### Post by iponeverything on 2008-12-14
the other thing you can try would be to remove run the system with each memory stick individually.

---

### Post by guix on 2008-12-14
Good idea. I'll do that if I get another segfault for non-opengl apps like Rhythmbox. For the moment I just had a crash of xmoto (non reported in /var/log/messages), Rhythmbox keeps playing.

---

