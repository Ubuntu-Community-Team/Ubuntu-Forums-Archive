---
title: "Crystalspace &amp; Ubuntu."
date: 2009-01-10
forum: Gaming &amp; Leisure
---

### Post by Kallewoof on 2009-01-10
Hello,

I've apt-get installed the crystalspace packages in Ubuntu (Intrepid) and tried to run the various demos available. Whenever I start e.g. "startme", I get the following message:

crystalspace.pluginmgr.loadplugin:
  could not load plugin 'crystalspace.graphics3d.shader.glcg'
  could not load plugin 'crystalspace.graphics3d.shader.glcg'

The thing starts up okay, but without any shades.

When I click walktest (the top left one in the startme list of icons), it starts loading up, then segfaults. 

WARNING: could not load plugin 'crystalspace.sndsys.software.driver.alsa'
WARNING: could not load plugin 'crystalspace.sndsys.software.driver.crystalspace.sndsys.software.driver.alsa'
ERROR: Failed to load driver as [crystalspace.sndsys.software.driver.alsa] or [crystalspace.sndsys.software.driver.crystalspace.sndsys.software.driver.alsa].
WARNING: failed to initialize plugin 'crystalspace.sndsys.renderer.software'
ATTENTION: default value of option force_s3tc_enable overridden by environment.
ALERT: crystalspace.vfscachemgr.createfile:  Could not create file 'lm_precalc_info' in VFS dir '/lev/castle/cache'


crystalspace.vfscachemgr.createfile:  Could not create file 'lm_precalc_info' in VFS dir '/lev/castle/cache'
crystalspace.vfscachemgr.createfile:  
WARNING! Object 'Mesh.002' is not closed!
WARNING! Object 'Cylinder.231' is not closed!
WARNING! Object 'Cylinder.025' is not closed!
WARNING! Object 'Cube.581' is not closed!
WARNING! Object 'Cube.579' is not closed!
WARNING! Object 'Cube.577' is not closed!
...
*** buffer overflow detected ***: /usr/bin/walktest terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7eeb558]
/lib/tls/i686/cmov/libc.so.6[0xb7ee9680]
/lib/tls/i686/cmov/libc.so.6(__strcpy_chk+0x44)[0xb7ee8944]
/usr/lib/crystalspace-1.2/thing.so[0xaea8d94d]
======= Memory map: ========
08048000-0816d000 r-xp 00000000 08:01 686712     /usr/bin/walktest-1.2
0816d000-0818a000 r--p 00125000 08:01 686712     /usr/bin/walktest-1.2
0818a000-0818b000 rw-p 00142000 08:01 686712     /usr/bin/walktest-1.2
087d8000-09b60000 rw-p 087d8000 00:00 0          [heap]
ae478000-ae488000 rw-p ae478000 00:00 0 
ae488000-ae4f5000 r-xp 00000000 08:01 99622      /usr/lib/crystalspace-1.2/spr3d.so
ae4f5000-ae4ff000 r--p 0006d000 08:01 99622      /usr/lib/crystalspace-1.2/spr3d.so
ae4ff000-ae500000 rw-p 00077000 08:01 99622      /usr/lib/crystalspace-1.2/spr3d.so
ae500000-ae529000 rw-p ae500000 00:00 0 
ae529000-ae600000 ---p ae529000 00:00 0 
ae60b000-ae6ac000 rw-p ae60b000 00:00 0 
ae6ac000-ae6e4000 r-xp 00000000 08:01 99645      /usr/lib/crystalspace-1.2/sequence.so
ae6e4000-ae6ea000 r--p 00038000 08:01 99645      /usr/lib/crystalspace-1.2/sequence.so
ae6ea000-ae6eb000 rw-p 0003e000 08:01 99645      /usr/lib/crystalspace-1.2/sequence.so
ae6eb000-ae745000 r-xp 00000000 08:01 99562      /usr/lib/crystalspace-1.2/engseq.so
ae745000-ae754000 r--p 00059000 08:01 99562      /usr/lib/crystalspace-1.2/engseq.so
ae754000-ae755000 rw-p 00068000 08:01 99562      /usr/lib/crystalspace-1.2/engseq.so
ae755000-ae825000 rw-p ae755000 00:00 0 
ae825000-ae8bd000 r-xp 00000000 08:01 99053      /usr/lib/crystalspace-1.2/dynavis.so
ae8bd000-ae8c6000 r--p 00097000 08:01 99053      /usr/lib/crystalspace-1.2/dynavis.so
ae8c6000-ae8c7000 rw-p 000a0000 08:01 99053      /usr/lib/crystalspace-1.2/dynavis.so
ae8c7000-ae8e7000 rw-p ae8c7000 00:00 0 
ae8f6000-ae966000 rw-p ae8f6000 00:00 0 
ae966000-ae9d9000 r-xp 00000000 08:01 99618      /usr/lib/crystalspace-1.2/particles.so
ae9d9000-ae9e8000 r--p 00072000 08:01 99618      /usr/lib/crystalspace-1.2/particles.so
ae9e8000-ae9e9000 rw-p 00081000 08:01 99618      /usr/lib/crystalspace-1.2/particles.so
ae9e9000-ae9f9000 rw-p ae9e9000 00:00 0 
ae9ff000-aea1f000 rw-p ae9ff000 00:00 0 
aea1f000-aea48000 r-xp 00000000 08:01 99619      /usr/lib/crystalspace-1.2/particlesldr.so
aea48000-aea4b000 r--p 00028000 08:01 99619      /usr/lib/crystalspace-1.2/particlesldr.so
aea4b000-aea4c000 rw-p 0002b000 08:01 99619      /usr/lib/crystalspace-1.2/particlesldr.so
aea4c000-aeb12000 r-xp 00000000 08:01 99632      /usr/lib/crystalspace-1.2/thing.so
aeb12000-aeb22000 r--p 000c5000 08:01 99632      /usr/lib/crystalspace-1.2/thing.so
aeb22000-aeb23000 rw-p 000d5000 08:01 99632      /usr/lib/crystalspace-1.2/thing.so
aeb23000-aeb53000 rw-p aeb23000 00:00 0 
aeb56000-aec56000 rw-p aeb56000 00:00 0 
aec5e000-aec7e000 rw-p aec5e000 00:00 0 
aec7f000-aecbf000 rw-p aec7f000 00:00 0 
aecbf000-aecf0000 r-xp 00000000 08:01 99633      /usr/lib/crystalspace-1.2/thingldr.so
aecf0000-aecf3000 r--p 00030000 08:01 99633      /usr/lib/crystalspace-1.2/thingldr.so
aecf3000-aecf4000 rw-p 00033000 08:01 99633      /usr/lib/crystalspace-1.2/thingldr.so
aecf7000-aed15000 r-xp 00000000 08:01 99558      /usr/lib/crystalspace-1.2/rendloop_loader.so
aed15000-aed16000 r--p 0001e000 08:01 99558      /usr/lib/crystalspace-1.2/rendloop_loader.so
aed16000-aed17000 rw-p 0001f000 08:01 99558      /usr/lib/crystalspace-1.2/rendloop_loader.so
aed17000-aee37000 rw-p aed17000 00:00 0 
aee3f000-aee51000 r-xp 00000000 08:01 99624      /usr/lib/crystalspace-1.2/spr3dldr.so
aee51000-aee54000 r--p 00011000 08:01 99624      /usr/lib/crystalspace-1.2/spr3dldr.so
aee54000-aee55000 rw-p 00014000 08:01 99624      /usr/lib/crystalspace-1.2/spr3dldr.so
aee55000-aee75000 rw-p aee55000 00:00 0 
aee7a000-aeeda000 rw-p aee7a000 00:00 0 
aeedd000-aefcd000 rw-p aeedd000 00:00 0 
aefcd000-af05e000 r-xp 00000000 08:01 99604      /usr/lib/crystalspace-1.2/genmesh.so
af05e000-af06c000 r--p 00090000 08Aborted

Any ideas what might be up with that?

---

### Post by FrozenFox on 2009-01-11
[http://forums.fedoraforum.org/showthread.php?t=193564](http://forums.fedoraforum.org/showthread.php?t=193564)

This thread isn't for ubuntu, but if you know what you are doing with ubuntu and cg, libcg, perhaps compiling, etc, it may help you fix your problem.

---

### Post by Kallewoof on 2009-01-11
Thanks for the link, FrozenFox.

Unfortunately I didn't get very far into that before it crashed where the author said it should "work fine except for the shader problem".

> $ sudo walktest-1.2 -relight
DEBUG: Sound System Software Renderer Initializing...
WARNING: could not load plugin 'crystalspace.sndsys.software.driver.alsa'
WARNING: could not load plugin 'crystalspace.sndsys.software.driver.crystalspace.sndsys.software.driver.alsa'
ERROR: Failed to load driver as [crystalspace.sndsys.software.driver.alsa] or [crystalspace.sndsys.software.driver.crystalspace.sndsys.software.driver.alsa].
WARNING: failed to initialize plugin 'crystalspace.sndsys.renderer.software'
ATTENTION: default value of option force_s3tc_enable overridden by environment.
WARNING! Object 'Cube.582' is not closed!
WARNING! Object 'Cylinder.232' is not closed!
WARNING! Object 'Cylinder.230' is not closed!
WARNING! Object 'Cylinder.012' is not closed!
WARNING! Object 'Cube.580' is not closed!
WARNING! Object 'Cube.578' is not closed!
...
*** buffer overflow detected ***: walktest-1.2 terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7dcc558]
/lib/tls/i686/cmov/libc.so.6[0xb7dca680]
/lib/tls/i686/cmov/libc.so.6(__strcpy_chk+0x44)[0xb7dc9944]
/usr/lib/crystalspace-1.2/thing.so[0xaeb0094d]
======= Memory map: ========
08048000-0816d000 r-xp 00000000 08:01 686712     /usr/bin/walktest-1.2
0816d000-0818a000 r--p 00125000 08:01 686712     /usr/bin/walktest-1.2
0818a000-0818b000 rw-p 00142000 08:01 686712     /usr/bin/walktest-1.2
08f1b000-0a3d6000 rw-p 08f1b000 00:00 0          [heap]
ae5d3000-ae623000 rw-p ae5d3000 00:00 0 
ae623000-ae690000 r-xp 00000000 08:01 99622      /usr/lib/crystalspace-1.2/spr3d.so
ae690000-ae69a000 r--p 0006d000 08:01 99622      /usr/lib/crystalspace-1.2/spr3d.so
ae69a000-ae69b000 rw-p 00077000 08:01 99622      /usr/lib/crystalspace-1.2/spr3d.so
ae69b000-ae6ad000 r-xp 00000000 08:01 99624      /usr/lib/crystalspace-1.2/spr3dldr.so
ae6ad000-ae6b0000 r--p 00011000 08:01 99624      /usr/lib/crystalspace-1.2/spr3dldr.so
ae6b0000-ae6b1000 rw-p 00014000 08:01 99624      /usr/lib/crystalspace-1.2/spr3dldr.so
ae6b1000-ae752000 rw-p ae6b1000 00:00 0 
ae752000-ae78a000 r-xp 00000000 08:01 99645      /usr/lib/crystalspace-1.2/sequence.so
ae78a000-ae790000 r--p 00038000 08:01 99645      /usr/lib/crystalspace-1.2/sequence.so
ae790000-ae791000 rw-p 0003e000 08:01 99645      /usr/lib/crystalspace-1.2/sequence.so
ae791000-ae7eb000 r-xp 00000000 08:01 99562      /usr/lib/crystalspace-1.2/engseq.so
ae7eb000-ae7fa000 r--p 00059000 08:01 99562      /usr/lib/crystalspace-1.2/engseq.so
ae7fa000-ae7fb000 rw-p 00068000 08:01 99562      /usr/lib/crystalspace-1.2/engseq.so
ae7fb000-ae8ab000 rw-p ae7fb000 00:00 0 
ae8ab000-ae943000 r-xp 00000000 08:01 99053      /usr/lib/crystalspace-1.2/dynavis.so
ae943000-ae94c000 r--p 00097000 08:01 99053      /usr/lib/crystalspace-1.2/dynavis.so
ae94c000-ae94d000 rw-p 000a0000 08:01 99053      /usr/lib/crystalspace-1.2/dynavis.so
ae94d000-ae9c0000 r-xp 00000000 08:01 99618      /usr/lib/crystalspace-1.2/particles.so
ae9c0000-ae9cf000 r--p 00072000 08:01 99618      /usr/lib/crystalspace-1.2/particles.so
ae9cf000-ae9d0000 rw-p 00081000 08:01 99618      /usr/lib/crystalspace-1.2/particles.so
ae9d0000-ae9e0000 rw-p ae9d0000 00:00 0 
ae9e2000-aea42000 rw-p ae9e2000 00:00 0 
aea42000-aea6b000 r-xp 00000000 08:01 99619      /usr/lib/crystalspace-1.2/particlesldr.so
aea6b000-aea6e000 r--p 00028000 08:01 99619      /usr/lib/crystalspace-1.2/particlesldr.so
aea6e000-aea6f000 rw-p 0002b000 08:01 99619      /usr/lib/crystalspace-1.2/particlesldr.so
aea6f000-aea8d000 r-xp 00000000 08:01 99558      /usr/lib/crystalspace-1.2/rendloop_loader.so
aea8d000-aea8e000 r--p 0001e000 08:01 99558      /usr/lib/crystalspace-1.2/rendloop_loader.so
aea8e000-aea8f000 rw-p 0001f000 08:01 99558      /usr/lib/crystalspace-1.2/rendloop_loader.so
aea8f000-aeabf000 rw-p aea8f000 00:00 0 
aeabf000-aeb85000 r-xp 00000000 08:01 99632      /usr/lib/crystalspace-1.2/thing.so
aeb85000-aeb95000 r--p 000c5000 08:01 99632      /usr/lib/crystalspace-1.2/thing.so
aeb95000-aeb96000 rw-p 000d5000 08:01 99632      /usr/lib/crystalspace-1.2/thing.so
aeb96000-aee08000 rw-p aeb96000 00:00 0 
aee09000-aee29000 rw-p aee09000 00:00 0 
aee29000-aee5a000 r-xp 00000000 08:01 99633      /usr/lib/crystalspace-1.2/thingldr.so
aee5a000-aee5d000 r--p 00030000 08:01 99633      /usr/lib/crystalspace-1.2/thingldr.so
aee5d000-aee5e000 rw-p 00033000 08:01 99633      /usr/lib/crystalspace-1.2/thingldr.so
aee5e000-af1af000 rw-p aee5e000 00:00 0 
af1b9000-af1d9000 rw-p af1b9000 00:00 0 
af1df000-af401000 rw-p af1df000 00:00 0 
af402000-af422000 rw-p af402000 00:00 0 
af428000-af7dc000 rw-p af428000 00:00 0 
af7e1000-b010d000 rw-p af7e1000 00:00 0 
b0110000-b0302000 rw-p b0110000 00:00 0 
b0302000-b0393000 r-xp 00000000 08:01 99604      /usr/lib/crystalspace-1.2/genmesh.so
b0393000-b03a1000 r--p 00090000 08:01 99604      /usr/lib/crystalspace-1.2/genmesh.so
b03a1000-b03a2000 rw-p 0009e000 08:01 99604      /usr/lib/crystalspace-1.2/genmesh.so
b03a2000-b03d1000 r-xp 00000000 08:01 99605      /usr/lib/crystalspace-1.2/gmeshldr.so
b03d1000-b03d4000 r--p 0002e000 08:01 99605      /usr/lib/crystalspace-1.2/gmeshldr.so
b03d4000-b03d5000 rw-p 00031000 08:01 99605      /usr/lib/crystalspace-1.2/gmeshldr.so
b03d5000-b0435000 rw-p b03d5000 00:00 0 
b0438000-b06cb000 rw-p b0438000 00:00 0 
b06d4000-b06e4000 rw-p b06d4000 00:00 0 
b06e7000-b0b3c000 rw-p b06e7000 00:00 0 
b0b3f000-b0d31000 rw-p b0b3f000 00:00 0 
b0d31000-b0d70000 r-xp 00000000 08:01 99689      /usr/lib/crystalspace-1.2/cspngimg.so
b0d70000-b0d77000 r--p 0003f000 08:01 99689      /usr/lib/crystalspace-1.2/cspngimg.so
b0d77000-b0d78000 rw-p 00046000 08:01 99689      /usr/lib/crystalspace-1.2/cspngimg.so
b0d78000-b0f9b000 rw-p b0d78000 00:00 0 
b0fa8000-b1089000 rw-p b0fa8000 00:00 0 
b1090000-b10b4000 r-xp 00000000 08:01 83338      /usr/lib/libpng12.so.0.27.0
b10b4000-b10b6000 rw-p 00023000 08:01 83338      /usr/lib/libpng12.so.0.27.0
b10b6000-b1177000 rw-p b10b6000 00:00 0 
b1177000-b1178000 ---p b1177000 00:00 0 
b1178000-b1978000 rw-p b1178000 00:00 0 
b1978000-b19b8000 r-xp 00000000 08:01 99684      /usr/lib/crystalspace-1.2/csjpgimg.so
b19b8000-b19bf000 r--p 0003f000 08:01 99684      /usr/lib/crystalspace-1.2/csjpgimg.so
b19bf000-b19c0000 rw-p 00046000 08:01 99684      /usr/lib/crystalspace-1.2/csjpgimg.so
b19c0000-b1a23000 rw-p b19c0000 00:00 0 
b1a23000-b1a33000 rw-p b1a23000 00:00 0 
b1a33000-b1a62000 r-xp 00000000 08:01 82408      /usr/lib/liblcms.so.1.0.16
b1a62000-b1a63000 r--p 0002e000 08:01 82408      /usr/lib/liblcms.so.1.0.16
b1a63000-b1a64000 rw-p 0002f000 08:01 82408      /usr/lib/liblcms.so.1.0.16
b1a64000-b1a67000 rw-p b1a64000 00:00 0 
b1a67000-b1a86000 r-xp 00000000 08:01 82346      /usr/lib/libjpeg.so.62.0.0
b1a86000-b1a87000 rw-p 0001e000 08:01 82346      /usr/lib/libjpeg.so.62.0.0
b1a87000-b1af2000 r-xp 00000000 08:01 82390      /usr/lib/libmng.so.1.1.0.9
b1af2000-b1af5000 rw-p 0006a000 08:01 82390      /usr/lib/libmng.so.1.1.0.9
b1af5000-b1b34000 r-xp 00000000 08:01 99682      /usr/lib/crystalspace-1.2/csjngimg.so
b1b34000-b1b3a000 r--p 0003e000 08:01 99682      /usr/lib/crystalspace-1.2/csjngimg.so
b1b3a000-b1b3b000 rw-p 00044000 08:01 99682      /usr/lib/crystalspace-1.2/csjngimg.so
b1b3b000-b1b8e000 r-xp 00000000 08:01 99675      /usr/lib/crystalspace-1.2/csddsimg.so
b1b8e000-b1b94000 r--p 00052000 08:01 99675      /usr/lib/crystalspace-1.2/csddsimg.so
b1b94000-b1b95000 rw-p 00058000 08:01 99675      /usr/lib/crystalspace-1.2/csddsimg.so
b1b95000-b1ef0000 rw-p b1b95000 00:00 0 
b1ef8000-b1f18000 r-xp 00000000 08:01 99676      /usr/lib/crystalspace-1.2/csgifimg.so
b1f18000-b1f1c000 r--p 0001f000 08:01 99676      /usr/lib/crystalspace-1.2/csgifimg.so
b1f1c000-b1f1d000 rw-p 00023000 08:01 99676      /usr/lib/crystalspace-1.2/csgifimg.so
b1f1d000-b1f3e000 r-xp 00000000 08:01 99674      /usr/lib/crystalspace-1.2/csbmpimg.so
b1f3e000-b1f42000 r--p 00021000 08:01 99674      /usr/lib/crystalspace-1.2/csbmpimg.so
b1f42000-b1f43000 rw-p 00025000 08:01 99674      /usr/lib/crystalspace-1.2/csbmpimg.so
b1f43000-b2009000 rw-p b1f43000 00:00 0 
b200a000-b2103000 rw-p b200a000 00:00 0 
b2112000-b2122000 rw-p b2112000 00:00 0 
b2123000-b2176000 rw-p b2123000 00:00 0 
b2178000-b22a1000 rw-p b2178000 00:00 0 
b22a2000-b2368000 rw-p b22a2000 00:00 0 
b236c000-b2916000 rw-p b236c000 00:00 0 
b2917000-b29bd000 rw-p b2917000 00:00 0 
b29be000-b2a11000 rw-p b29be000 00:00 0 
b2a11000-b3411000 rwxp b2a11000 00:00 0 
b3411000-b3491000 r-xp 00000000 08:01 97962      /usr/lib/crystalspace-1.2/csopcode.so
b3491000-b3495000 r--p 00080000 08:01 97962      /usr/lib/crystalspace-1.2/csopcode.so
b3495000-b3496000 rw-p 00084000 08:01 97962      /usr/lib/crystalspace-1.2/csopcode.so
b3496000-b350f000 rw-p b3496000 00:00 0 
b350f000-b358c000 r-xp 00000000 08:01 99559      /usr/lib/crystalspace-1.2/rendstep_std.so
b358c000-b359e000 r--p 0007c000 08:01 99559      /usr/lib/crystalspace-1.2/rendstep_std.so
b359e000-b359f000 rw-p 0008e000 08:01 99559      /usr/lib/crystalspace-1.2/rendstep_std.so
b359f000-b3ae9000 rw-p b359f000 00:00 0 
b3aea000-b3b90000 rw-p b3aea000 00:00 0 
b3b91000-b3be4000 rw-p b3b91000 00:00 0 
b3be5000-b3c48000 rw-p b3be5000 00:00 0 
b3c49000-b3c8a000 rw-p b3c49000 00:00 0 
b3c8a000-b3d28000 r-xp 00000000 08:01 99711      /usr/lib/crystalspace-1.2/xmlshader.so
b3Aborted



---

