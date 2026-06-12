---
title: "regnum question"
date: 2008-02-09
forum: Gaming &amp; Leisure
---

### Post by TechDragon on 2008-02-09
I save the rolauncher to

/home/linux/Games/

I then go to a terminal and type


> linux@laptop:~$ cd Games
linux@laptop:~/Games$ sudo ./rolauncher
[sudo] password for linux:
*** glibc detected *** ./rolauncher: free(): invalid pointer: 0x08645d40 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb788bd65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb788f800]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb779b961]
./rolauncher[0x817613d]
./rolauncher[0x8070b53]
./rolauncher[0x8065a7a]
./rolauncher[0x8067ed1]
./rolauncher[0x810074e]
./rolauncher[0x805c55e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7838050]
./rolauncher(__gxx_personality_v0+0x3d5)[0x805c391]
======= Memory map: ========
08048000-0840e000 r-xp 00000000 08:01 8290633    /home/linux/Games/rolauncher
0840e000-0844b000 rw-p 003c6000 08:01 8290633    /home/linux/Games/rolauncher
0844b000-08663000 rw-p 0844b000 00:00 0          [heap]
b6800000-b6821000 rw-p b6800000 00:00 0 
b6821000-b6900000 ---p b6821000 00:00 0 
b6902000-b698d000 r--p 00000000 08:01 7801822    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b698d000-b698f000 r-xp 00000000 08:01 7701946    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b698f000-b6990000 rw-p 00001000 08:01 7701946    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6990000-b6996000 r--s 00000000 08:01 4145237    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b6996000-b6999000 r--s 00000000 08:01 4145725    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b6999000-b699d000 r--s 00000000 08:01 4145724    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b699d000-b699e000 r--s 00000000 08:01 4145719    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b699e000-b699f000 r--s 00000000 08:01 4145718    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b699f000-b69a2000 r--s 00000000 08:01 4145717    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b69a2000-b69a3000 r--s 00000000 08:01 4145716    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b69a3000-b69a6000 r--s 00000000 08:01 4145715    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b69a6000-b69a8000 r--s 00000000 08:01 4145714    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b69a8000-b69b0000 r--s 00000000 08:01 4145707    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b69b0000-b69b6000 r--s 00000000 08:01 4145706    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b69b6000-b69b7000 r--s 00000000 08:01 4145704    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b69b7000-b69ce000 r--s 00000000 08:01 4146069    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b69ce000-b69d0000 r--s 00000000 08:01 4145702    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b69d0000-b69d6000 r--s 00000000 08:01 4145700    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b69d6000-b69da000 r--s 00000000 08:01 4145222    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b69da000-b69e1000 r--s 00000000 08:01 4146047    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b69e1000-b69e2000 r--s 00000000 08:01 4145771    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b69e2000-b69e3000 r--s 00000000 08:01 4145767    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b69e3000-b69e4000 r--s 00000000 08:01 4148495    /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b69e4000-b69e7000 r--s 00000000 08:01 4148494    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b69e7000-b69ea000 r--s 00000000 08:01 4145764    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b69ea000-b69f1000 r--s 00000000 08:01 4148493    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b69f1000-b69f3000 r--s 00000000 08:01 4145760    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b69f3000-b69f4000 r--s 00000000 08:01 4145758    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b69f4000-b69f5000 r--s 00000000 08:01 4145757    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b69f5000-b69f6000 r--s 00000000 08:01 4145754    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b69f6000-b69fb000 r--s 00000000 08:01 4145752    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b69fb000-b6a00000 r--s 00000000 08:01 4145751    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b6a00000-b6a02000 r--s 00000000 08:01 4145749    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b6a02000-b6a05000 r--s 00000000 08:01 4145747    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b6a05000-b6a06000 r--s 00000000 08:01 4145746    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b6a06000-b6a07000 r--s 00000000 08:01 4148459    /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b6a07000-b6a08000 r--s 00000000 08:01 4145743    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b6a08000-b6a0c000 r--s 00000000 08:01 4148458    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b6a0c000-b6a12000 r--s 00000000 08:01 4145739    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b6a12000-b6a13000 r--s 00000000 08:01 4145738    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b6a13000-b6a17000 r--s 00000000 08:01 4145736    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b6a17000-b6a1b000 r--s 00000000 08:01 4148457    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b6a1b000-b6a2d000 r-xp 00000000 08:01 7635027    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b6a2d000-b6a2e000 rw-p 00011000 08:01 7635027    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b6a2e000-b6a2f000 ---p b6a2e000 00:00 0 
b6a2f000-b722f000 rwxp b6a2f000 00:00 0 
b722f000-b7250000 rw-p b722f000 00:00 0 
b7250000-b7259000 r-xp 00000000 08:01 5570646    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b7259000-b725b000 rw-p 00008000 08:01 5570646    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b725b000-b7263000 r-xp 00000000 08:01 5570650    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b7263000-b7265000 rw-p 00007000 08:01 5570650    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b7265000-b7279000 r-xp 00000000 08:01 5570637    /lib/tls/i686/cmov/libnsl-2.6.1.so
b7279000-b727b000 rw-p 00013000 08:01 5570637    /lib/tls/i686/cmov/libnsl-2.6.1.so
b727b000-b727d000 rw-p b727b000 00:00 0 
b727d000-b7284000 r-xp 00000000 08:01 5570642    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7284000-b7286000 rw-p 00006000 08:01 5570642    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7287000-b728b000 r--s 00000000 08:01 4145732    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b728b000-b7290000 r--s 00000000 08:01 4148455    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b7290000-b7291000 r-xp 00000000 08:01 7575177    /usr/lib/gconv/ISO8859-1.so
b7291000-b7293000 rw-p 00000000 08:01 7575177    /usr/lib/gconv/ISO8859-1.so
b7293000-b7294000 r--p 00000000 08:01 7635864    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7294000-b7295000 r--p 00000000 08:01 7635867    /usr/lib/locale/en_US.utf8/LC_TIME
b7295000-b7375000 r--p 00000000 08:01 7635858    /usr/lib/locale/en_US.utf8/LC_COLLATE
b7375000-b7376000 r--p 00000000 08:01 7635862    /usr/lib/locale/en_US.utf8/LC_MONETARY
b7376000-b7377000 r--p 00000000 08:01 7635868    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7377000-b7378000 r--p 00000000 08:01 7635865    /usr/lib/locale/en_US.utf8/LC_PAPER
b7378000-b7379000 r--p 00000000 08:01 7635863    /usr/lib/locale/en_US.utf8/LC_NAME
b7379000-b737a000 r--p 00000000 08:01 7635857    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b737a000-b737b000 r--p 00000000 08:01 7635866    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b737b000-b73ba000 r--p 00000000 08:01 7635859    /usr/lib/locale/en_US.utf8/LC_CTYPE
b73ba000-b73bc000 rw-p b73ba000 00:00 0 
b73bc000-b73de000 r-xp 00000000 08:01 7570215    /usr/lib/libpng12.so.0.15.0
b73de000-b73df000 rw-p 00021000 08:01 7570215    /usr/lib/libpng12.so.0.15.0
b73df000-b73e0000 rw-p b73df000 00:00 0 
b73e0000-b744c000 r-xp 00000000 08:01 7571233    /usr/lib/libfreetype.so.6.3.16
b744c000-b7450000 rw-p 0006b000 08:01 7571233    /usr/lib/libfreetype.so.6.3.16
b7450000-b747d000 r-xp 00000000 08:01 7569525    /usr/lib/libpangoft2-1.0.so.0.1800.3
b747d000-b747e000 rw-p 0002c000 08:01 7569525    /usr/lib/libpangoft2-1.0.so.0.1800.3
b747e000-b7482000 r-xp 00000000 08:01 7571028    /usr/lib/libXdmcp.so.6.0.0
b7482000-b7483000 rw-p 00003000 08:01 7571028    /usr/lib/libXdmcp.so.6.0.0
b7483000-b7498000 r-xp 00000000 08:01 7570989    /usr/lib/libICE.so.6.3.0
b7498000-b749a000 rw-p 00014000 08:01 7570989    /usr/lib/libICE.so.6.3.0
b749a000-b749c000 rw-p b749a000 00:00 0 
b749c000-b749e000 r-xp 00000000 08:01 7571017    /usr/lib/libXau.so.6.0.0
b749e000-b749f000 rw-p 00001000 08:01 7571017    /usr/lib/libXau.so.6.0.0
b749f000-b74a7000 r-xp 00000000 08:01 7571024    /usr/lib/libXcursor.so.1.0.2
b74a7000-b74a8000 rw-p 00007000 08:01 7571024    /usr/lib/libXcursor.so.1.0.2
b74a8000-b74ad000 r-xp 00000000 08:01 7571052    /usr/lib/libXrandr.so.2.1.0
b74ad000-b74ae000 rw-p 00005000 08:01 7571052    /usr/lib/libXrandr.so.2.1.0
b74ae000-b74b5000 r-xp 00000000 08:01 7571040    /usr/lib/libXi.so.6.0.0
b74b5000-b74b6000 rw-p 00006000 08:01 7571040    /usr/lib/libXi.so.6.0.0
b74b6000-b74bd000 r-xp 00000000 08:01 7571054    /usr/lib/libXrender.so.1.3.0
b74bd000-b74be000 rw-p 00006000 08:01 7571054    /usr/lib/libXrender.so.1.3.0
b74be000-b74bf000 rw-p b74be000 00:00 0 
b74bf000-b74e2000 r-xp 00000000 08:01 7571225    /usr/lib/libfontconfig.so.1.2.0
b74e2000-b74ea000 rw-p 00023000 08:01 7571225    /usr/lib/libfontconfig.so.1.2.0
b74ea000-b755f000 r-xp 00000000 08:01 7569511    /usr/lib/libcairo.so.2.11.5
b755f000-b7561000 rw-p 00074000 08:01 7569511    /usr/lib/libcairo.so.2.11.5
b7561000-b7564000 r-xp 00000000 08:01 7571321    /usr/lib/libgmodule-2.0.so.0.1400.1
b7564000-b7565000 rw-p 00002000 08:01 7571321    /usr/lib/libgmodule-2.0.so.0.1400.1
b7565000-b757e000 r-xp 00000000 08:01 7571090    /usr/lib/libatk-1.0.so.0.2009.1
b757e000-b7580000 rw-p 00018000 08:01 7571090    /usr/lib/libatk-1.0.so.0.2009.1
b7580000-b7584000 r-xp 00000000 08:01 7571034    /usr/lib/libXfixes.so.3.1.0
b7584000-b7585000 rw-p 00003000 08:01 7571034    /usr/lib/libXfixes.so.3.1.0
b7585000-b7587000 r-xp 00000000 08:01 7571026    /usr/lib/libXdamage.so.1.1.0
b7587000-b7588000 rw-p 00001000 08:01 7571026    /usr/lib/libXdamage.so.1.1.0
b7588000-b7589000 rw-p b7588000 00:00 0 
b7589000-b758b000 r-xp 00000000 08:01 7571022    /usr/lib/libXcomposite.so.1.0.0
b758b000-b758c000 rw-p 00001000 08:01 7571022    /usr/lib/libXcomposite.so.1.0.0
b758c000-b7594000 r-xp 00000000 08:01 7569523    /usr/lib/libpangocairo-1.0.so.0.1800.3
b7594000-b7595000 rw-p 00007000 08:01 7569523    /usr/lib/libpangocairo-1.0.so.0.1800.3
b7595000-b759c000 r-xp 00000000 08:01 5570680    /lib/tls/i686/cmov/librt-2.6.1.so
b759c000-b759e000 rw-p 00006000 08:01 5570680    /lib/tls/i686/cmov/librt-2.6.1.so
b759e000-b75bc000 r-xp 00000000 08:01 7571219    /usr/lib/libexpat.so.1.0.0
b75bc000-b75be000 rw-p 0001e000 08:01 7571219    /usr/lib/libexpat.so.1.0.0
b75be000-b75d2000 r-xp 00000000 08:01 7571795    /usr/lib/libz.so.1.2.3.3
b75d2000-b75d3000 rw-p 00013000 08:01 7571795    /usr/lib/libz.so.1.2.3.3
b75d3000-b75d4000 rw-p b75d3000 00:00 0 
b75d4000-b75db000 r-xp 00000000 08:01 7571007    /usr/lib/libSM.so.6.0.0
b75db000-b75dc000 rw-p 00006000 08:01 7571007    /usr/lib/libSM.so.6.0.0
b75dc000-b75de000 r-xp 00000000 08:01 7571042    /usr/lib/libXinerama.so.1.0.0
b75de000-b75df000 rw-p 00001000 08:01 7571042    /usr/lib/libXinerama.so.1.0.0
b75df000-b75e1000 r-xp 00000000 08:01 5570612    /lib/tls/i686/cmov/libdl-2.6.1.so
b75e1000-b75e3000 rw-p 00001000 08:01 5570612    /lib/tls/i686/cmov/libdl-2.6.1.so
b75e3000-b761d000 r-xp 00000000 08:01 7571361    /usr/lib/libgobject-2.0.so.0.1400.1
b761d000-b761e000 rw-p 0003a000 08:01 7571361    /usr/lib/libgobject-2.0.so.0.1400.1
b761e000-b770b000 r-xp 00000000 08:01 7571011    /usr/lib/libX11.so.6.2.0
b770b000-b770f000 rw-p 000ed000 08:01 7571011    /usr/lib/libX11.so.6.2.0
b770f000-b774a000 r-xp 00000000 08:01 7569521    /usr/lib/libpango-1.0.so.0.1800.3
b774a000-b774c000 rw-p 0003b000 08:01 7569521    /usr/lib/libpango-1.0.so.0.1800.3
b774c000-b774d000 rw-p b774c000 00:00 0 
b774d000-b7764000 r-xp 00000000 08:01 7571273    /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b7764000-b7765000 rw-p 00016000 08:01 7571273    /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b7765000-b7821000 r-xp 00000000 08:01 7571311    /usr/lib/libglib-2.0.so.0.1400.1
b7821000-b7822000 rw-p 000bc000 08:01 7571311    /usr/lib/libglib-2.0.so.0.1400.1
b7822000-b7966000 r-xp 00000000 08:01 5570587    /lib/tls/i686/cmov/libc-2.6.1.so
b7966000-b7967000 r--p 00143000 08:01 5570587    /lib/tls/i686/cmov/libc-2.6.1.so
b7967000-b7969000 rw-p 00144000 08:01 5570587    /lib/tls/i686/cmov/libc-2.6.1.so
b7969000-b796c000 rw-p b7969000 00:00 0 
b796c000-b7976000 r-xp 00000000 08:01 5570627    /lib/libgcc_s.so.1
b7976000-b7977000 rw-p 0000a000 08:01 5570627    /lib/libgcc_s.so.1
b7977000-b799a000 r-xp 00000000 08:01 5570619    /lib/tls/i686/cmov/libm-2.6.1.so
b799a000-b799c000 rw-p 00023000 08:01 5570619    /lib/tls/i686/cmov/libm-2.6.1.so
b799c000-b7a84000 r-xp 00000000 08:01 7571725    /usr/lib/libstdc++.so.6.0.9
b7a84000-b7a87000 r--p 000e8000 08:01 7571725    /usr/lib/libstdc++.so.6.0.9
b7a87000-b7a89000 rw-p 000eb000 08:01 7571725    /usr/lib/libstdc++.so.6.0.9
b7a89000-b7a90000 rw-p b7a89000 00:00 0 
b7a90000-b7add000 r-xp 00000000 08:01 7571058    /usr/lib/libXt.sAborted (core dumped)
linux@laptop:~/Games$ 


It doesn't launch  help

Thanks

---

### Post by Perfect Storm on 2008-02-10
Have the same problem,but havn't the time to figured it out yet. First I thought it might be because I'm running 64-bit but if you running 32-bit then I can rule that out.


By the way _DON'T_ run stuff with **sudo**. Trash it, and start over again.

---

### Post by TechDragon on 2008-02-10
running 32 bit

got it to run by doing this in a term

G_SLICE=always-malloc ./rolauncher

---

