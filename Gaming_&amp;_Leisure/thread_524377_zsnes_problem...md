---
title: "zsnes problem.."
date: 2007-08-13
forum: Gaming &amp; Leisure
---

### Post by Vorde on 2007-08-13
Hello,
I'm having a very weird problem with running zsnes.
I have downloaded all the lib files and stuff it needs. 
Here's a crash dump of the prog to give u the hint of what's going on:
ZSNES v1.42 (c) 1997-2005, ZSNES Team

Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.
Please report crashes to [email]zsnes-devel@lists.sourceforge.net[/email].

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE' thoroughly before doing so.

Use ZSNES -? for command line definitions.

*** glibc detected *** zsnes: munmap_chunk(): invalid pointer: 0xbfeabea8 ***
======= Backtrace: =========
/lib/libc.so.6(cfree+0x1bc)[0xb7bb1a1c]
zsnes[0x80ddad2]
======= Memory map: ========
08048000-082f9000 r-xp 00000000 03:01 2360509    /usr/local/bin/zsnes
082f9000-0834c000 rwxp 002b1000 03:01 2360509    /usr/local/bin/zsnes
0834c000-085d8000 rwxp 0834c000 00:00 0          [heap]
b7002000-b7067000 rwxp b7002000 00:00 0 
b7067000-b706b000 r-xp 00000000 03:01 2180357    /usr/lib/libXdmcp.so.6.0.0
b706b000-b706c000 rwxp 00003000 03:01 2180357    /usr/lib/libXdmcp.so.6.0.0
b706c000-b706e000 r-xp 00000000 03:01 2180346    /usr/lib/libXau.so.6.0.0
b706e000-b706f000 rwxp 00001000 03:01 2180346    /usr/lib/libXau.so.6.0.0
b706f000-b7070000 rwxp b706f000 00:00 0 
b7070000-b715d000 r-xp 00000000 03:01 2180340    /usr/lib/libX11.so.6.2.0
b715d000-b7161000 rwxp 000ed000 03:01 2180340    /usr/lib/libX11.so.6.2.0
b7161000-b716e000 r-xp 00000000 03:01 2180361    /usr/lib/libXext.so.6.4.0
b716e000-b716f000 rwxp 0000d000 03:01 2180361    /usr/lib/libXext.so.6.4.0
b716f000-b7170000 r-xp 00000000 03:01 2719798    /usr/lib/tls/libnvidia-tls.so.1.0.9631
b7170000-b7171000 rwxp 00000000 03:01 2719798    /usr/lib/tls/libnvidia-tls.so.1.0.9631
b7171000-b79be000 r-xp 00000000 03:01 2181650    /usr/lib/libGLcore.so.1.0.9631
b79be000-b79f3000 rwxp 0084d000 03:01 2181650    /usr/lib/libGLcore.so.1.0.9631
b79f3000-b79f7000 rwxp b79f3000 00:00 0 
b79f7000-b7a0a000 r-xp 00000000 03:01 4472927    /lib/libpthread-2.6.1.so
b7a0a000-b7a0c000 rwxp 00012000 03:01 4472927    /lib/libpthread-2.6.1.so
b7a0c000-b7a0f000 rwxp b7a0c000 00:00 0 
b7a0f000-b7a1d000 r-xp 00000000 03:01 2180496    /usr/lib/libdirect-0.9.so.25.0.0
b7a1d000-b7a1e000 rwxp 0000e000 03:01 2180496    /usr/lib/libdirect-0.9.so.25.0.0
b7a1e000-b7a23000 r-xp 00000000 03:01 2180564    /usr/lib/libfusion-0.9.so.25.0.0
b7a23000-b7a24000 rwxp 00004000 03:01 2180564    /usr/lib/libfusion-0.9.so.25.0.0
b7a24000-b7a79000 r-xp 00000000 03:01 2180498    /usr/lib/libdirectfb-0.9.so.25.0.0
b7a79000-b7a7b000 rwxp 00055000 03:01 2180498    /usr/lib/libdirectfb-0.9.so.25.0.0
b7a7b000-b7a7d000 r-xp 00000000 03:01 4472877    /lib/libdl-2.6.1.so
b7a7d000-b7a7f000 rwxp 00001000 03:01 4472877    /lib/libdl-2.6.1.so
b7a7f000-b7b3f000 r-xp 00000000 03:01 2180411    /usr/lib/libasound.so.2.0.0
b7b3f000-b7b44000 rwxp 000bf000 03:01 2180411    /usr/lib/libasound.so.2.0.0
b7b44000-b7c86000 r-xp 00000000 03:01 4472857    /lib/libc-2.6.1.so
b7c86000-b7c87000 r-xp 00142000 03:01 4472857    /lib/libc-2.6.1.so
b7c87000-b7c89000 rwxp 00143000 03:01 4472857    /lib/libc-2.6.1.so
b7c89000-b7c8d000 rwxp b7c89000 00:00 0 
b7c8d000-b7c97000 r-xp 00000000 03:01 4472861    /lib/libgcc_s.so.1
b7c97000-b7c98000 rwxp 00009000 03:01 4472861    /lib/libgcc_s.so.1
b7c98000-b7cbc000 r-xp 00000000 03:01 4472883    /lib/libm-2.6.1.so
b7cbc000-b7cbe000 rwxp 00023000 03:01 4472883    /lib/libm-2.6.1.so
b7cbe000-b7d9e000 r-xp 00000000 03:01 2180400    /usr/lib/libstdc++.so.6.0.9
b7d9e000-b7da1000 r-xp 000e0000 03:01 2180400    /usr/lib/libstdc++.so.6.0.9
b7da1000-b7da3000 rwxp 000e3000 03:01 2180400    /usr/lib/libstdc++.so.6.0.9
b7da3000-b7da9000 rwxp b7da3000 00:00 0 
b7da9000-b7e1a000 r-xp 00000000 03:01 2181649    /usr/lib/libGL.so.1.0.9631
b7e1a000-b7e34000 rwxp 00070000 03:01 2181649    /usr/lib/libGL.so.1.0.9631
b7e34000-b7e35000 rwxp b7e34000 00:00 0 
b7e35000-b7e9a000 r-xp 00000000 03:01 2180334    /usr/lib/libSDL-1.2.so.0.11.0
b7e9a000-b7e9c000 rwxp 00065000 03:01 2180334    /usr/lib/libSDL-1.2.so.0.11.0
b7e9c000-b7ec4000 rwxp b7e9c000 00:00 0 
b7ec4000-b7ed7000 r-xp 00000000 03:01 2181101    /usr/lib/libz.so.1.2.3
b7ed7000-b7ed8000 rwxp 00012000 03:01 2181101    /usr/lib/libz.so.1.2.3
b7ed8000-b7ed9000 rwxp b7ed8000 00:00 0 
b7ee5000-b7ee6000 rwxp b7ee5000 00:00 0 
b7ee6000-b7ee8000 rwxp 00000000 00:0d 2586       /dev/zero
b7ee8000-b7ee9000 rwxp b7ee8000 00:00 0 
b7ee9000-b7f05000 r-xp 00000000 03:01 4472838    /lib/ld-2.6.1.so
b7f05000-b7f07000 rwxp 0001b000 03:01 4472838    /lib/ld-2.6.1.so
bfe97000-bfead000 rwxp bfe97000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

I really hope someone can figure this damn **** out. Thanx! :)

---

### Post by ddrichardson on 2007-08-13
Did you install it through apt-get/synaptics from the repositories?

---

### Post by Vorde on 2007-08-14
yes, I downloaded most of the packages through the synaptic pkg manager, but I downloaded one or two from deb files I found online. I was thinking I might need to link some files to the program or something. 
Anyone else, can u help? :):confused:

EDIT: I noticed now that all the files listed here are all library files, and all the ones listed here aren't linked like the rest of them. How do I link these, as it gives me the option, but it's all grey'd out :(
I'm going to look up linking files...

---

### Post by BoyOfDestiny on 2007-08-14
> **Vorde said:**
> yes, I downloaded most of the packages through the synaptic pkg manager, but I downloaded one or two from deb files I found online. I was thinking I might need to link some files to the program or something. 
Anyone else, can u help? :):confused:

EDIT: I noticed now that all the files listed here are all library files, and all the ones listed here aren't linked like the rest of them. How do I link these, as it gives me the option, but it's all grey'd out :(
I'm going to look up linking files...

Hmm... You should just have to grab one package (zsnes) in synaptic. What version of Ubuntu are you using. What architecture (x86, amd64, ppc?)

Anyway, you can try this package:

[http://www.getdeb.net/search.php?keywords=zsnes](http://www.getdeb.net/search.php?keywords=zsnes)

---

### Post by Vorde on 2007-08-14
I'm running Ubuntu 7.04 (Feisty) for x86. I've grabbed those deb files before, they just give me the same damn errors :confused:
I think the guy before u was talking about dependencies...
I have them all, but it just gives me this crap:(

---

### Post by BigSilly on 2007-08-14
I can't for the life of me understand why you're having this problem. It's crap when stuff like this happens, so you have my sympathy. :(

I must have been lucky I suppose. I just downloaded the .deb file from GetDeb, double-clicked it, and it installed just fine into my Games folder. I think I had an issue with crackly sound, but that was solved by installing the OSS sound drivers.

Hope you sort it dude.

---

### Post by ddrichardson on 2007-08-14
This seems to be related to installing debs from two different sources. ZSNES worked for me through synaptics on 7.04 x86.

It might be worth uninstalling what you've got then doing it again through apt-get. You wont fix an invalid pointer error by linking to other files.

---

### Post by KingHanco on 2007-08-15
ZSNES v1.42 is old. Try ZSNES v1.51.

---

