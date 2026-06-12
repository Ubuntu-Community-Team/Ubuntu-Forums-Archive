---
title: "Downgrading Zsnes to 1.42 to solve SMRPG's freezing issue"
date: 2008-07-27
forum: Gaming &amp; Leisure
---

### Post by Ishimaru Chiaki on 2008-07-27
Hello.

Lately, I began to play Super Mario RPG under Zsnes 1.51, and I am currently in a point that I have trouble equipping my characters because when I select the weapon/armor/accessory, the screen freezes most of the time, so I have to save a state just before I try to change equipments.  That issue was less frequent at the beginning, but now, I'm in Marrymore in order to save Princess Peach from her forced marriage with Booster, and I want to upgrade my equipments in order to give me a chance to defeat Bundt (I lost the battle the first time because of item shortage - I bought more Mid mushrooms and maple syrups since).

Since I saw posts from people who have less freeze problems with a previous version (1.42) of zsnes, I first posted on the French forum.  The one who replied gave me the link of the 1.42 deb package, and the command line (to install a specific version).  Since the command line failed, I downloaded the .deb package after I removed the recent version (without removing the dependencies*).  But zsnes doesn't appear anymore in the games application list, and when I try to launch Zsnes or a game with Zsnes, it fails, here's the console contents of my attemps :
```
caroline@caroline-desktop:~$ zsnes

ZSNES v1.42 (c) 1997-2005, ZSNES Team

Be sure to check http://www.zsnes.com/ for the latest version.
Please report crashes to zsnes-devel@lists.sourceforge.net.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE' thoroughly before doing so.

Use ZSNES -? for command line definitions.

*** glibc detected *** zsnes: munmap_chunk(): invalid pointer: 0xbfff4e62 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7c6f61b]
zsnes[0x80de151]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7c16450]
zsnes(__gxx_personality_v0+0xd1)[0x804ba31]
======= Memory map: ========
08048000-082f8000 r-xp 00000000 08:02 180912     /usr/bin/zsnes
082f8000-0834b000 rwxp 002b0000 08:02 180912     /usr/bin/zsnes
0834b000-085d8000 rwxp 0834b000 00:00 0          [heap]
b7a4c000-b7a4e000 rwxp b7a4c000 00:00 0 
b7a4e000-b7a52000 r-xp 00000000 08:02 181844     /usr/lib/libXdmcp.so.6.0.0
b7a52000-b7a53000 rwxp 00003000 08:02 181844     /usr/lib/libXdmcp.so.6.0.0
b7a53000-b7a55000 r-xp 00000000 08:02 181833     /usr/lib/libXau.so.6.0.0
b7a55000-b7a56000 rwxp 00001000 08:02 181833     /usr/lib/libXau.so.6.0.0
b7a56000-b7a6d000 r-xp 00000000 08:02 182674     /usr/lib/libxcb.so.1.0.0
b7a6d000-b7a6e000 rwxp 00016000 08:02 182674     /usr/lib/libxcb.so.1.0.0
b7a6e000-b7a6f000 r-xp 00000000 08:02 182672     /usr/lib/libxcb-xlib.so.0.0.0
b7a6f000-b7a70000 rwxp 00000000 08:02 182672     /usr/lib/libxcb-xlib.so.0.0.0
b7a70000-b7a71000 rwxp b7a70000 00:00 0 
b7a71000-b7a7a000 r-xp 00000000 08:02 182030     /usr/lib/libdrm.so.2.3.0
b7a7a000-b7a7b000 rwxp 00008000 08:02 182030     /usr/lib/libdrm.so.2.3.0
b7a7b000-b7a7f000 r-xp 00000000 08:02 181850     /usr/lib/libXfixes.so.3.1.0
b7a7f000-b7a80000 rwxp 00003000 08:02 181850     /usr/lib/libXfixes.so.3.1.0
b7a80000-b7a82000 r-xp 00000000 08:02 181842     /usr/lib/libXdamage.so.1.1.0
b7a82000-b7a83000 rwxp 00001000 08:02 181842     /usr/lib/libXdamage.so.1.1.0
b7a83000-b7a87000 r-xp 00000000 08:02 181884     /usr/lib/libXxf86vm.so.1.0.0
b7a87000-b7a88000 rwxp 00003000 08:02 181884     /usr/lib/libXxf86vm.so.1.0.0
b7a88000-b7a95000 r-xp 00000000 08:02 181848     /usr/lib/libXext.so.6.4.0
b7a95000-b7a96000 rwxp 0000d000 08:02 181848     /usr/lib/libXext.so.6.4.0
b7a96000-b7b7a000 r-xp 00000000 08:02 181827     /usr/lib/libX11.so.6.2.0
b7b7a000-b7b7d000 rwxp 000e4000 08:02 181827     /usr/lib/libX11.so.6.2.0
b7b7d000-b7b7e000 rwxp b7b7d000 00:00 0 
b7b7e000-b7b90000 r-xp 00000000 08:02 182018     /usr/lib/libdirect-1.0.so.0.1.0
b7b90000-b7b91000 rwxp 00012000 08:02 182018     /usr/lib/libdirect-1.0.so.0.1.0
b7b91000-b7b98000 r-xp 00000000 08:02 182090     /usr/lib/libfusion-1.0.so.0.1.0
b7b98000-b7b99000 rwxp 00006000 08:02 182090     /usr/lib/libfusion-1.0.so.0.1.0
b7b99000-b7bfa000 r-xp 00000000 08:02 182020     /usr/lib/libdirectfb-1.0.so.0.1.0
b7bfa000-b7bfc000 rwxp 00060000 08:02 182020     /usr/lib/libdirectfb-1.0.so.0.1.0
b7bfc000-b7bfe000 r-xp 00000000 08:02 288135     /lib/tls/i686/cmov/libdl-2.7.so
b7bfe000-b7c00000 rwxp 00001000 08:02 288135     /lib/tls/i686/cmov/libdl-2.7.so
b7c00000-b7d49000 r-xp 00000000 08:02 288129     /lib/tls/i686/cmov/libc-2.7.so
b7d49000-b7d4a000 r-xp 00149000 08:02 288129     /lib/tls/i686/cmov/libc-2.7.so
b7d4a000-b7d4c000 rwxp 0014a000 08:02 288129     /lib/tls/i686/cmov/libc-2.7.so
b7d4c000-b7d50000 rwxp b7d4c000 00:00 0 
b7d50000-b7d5a000 r-xp 00000000 08:02 270400     /lib/libgcc_s.so.1
b7d5a000-b7d5b000 rwxp 0000a000 08:02 270400     /lib/libgcc_s.so.1
b7d5b000-b7d7e000 r-xp 00000000 08:02 288137     /lib/tls/i686/cmov/libm-2.7.so
b7d7e000-b7d80000 rwxp 00023000 08:02 288137     /lib/tls/i686/cmov/libm-2.7.so
b7d80000-b7e68000 r-xp 00000000 08:02 182611     /usr/lib/libstdc++.so.6.0.9
b7e68000-b7e6b000 r-xp 000e8000 08:02 182611     /usr/lib/libstdc++.so.6.0.9
b7e6b000-b7e6d000 rwxp 000eb000 08:02 182611     /usAbandon
caroline@caroline-desktop:~$ zsnes ~.zsnes/Super\ Mario\ RPG\ (U).smc
bash: Erreur de syntaxe près du symbole inattendu « ( »
caroline@caroline-desktop:~$ zsnes ~/.zsnes/Super\ Mario\ RPG\ \(U\).smc

ZSNES v1.42 (c) 1997-2005, ZSNES Team

Be sure to check http://www.zsnes.com/ for the latest version.
Please report crashes to zsnes-devel@lists.sourceforge.net.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE' thoroughly before doing so.

Use ZSNES -? for command line definitions.

*** glibc detected *** zsnes: munmap_chunk(): invalid pointer: 0xbfd95e62 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7b9761b]
zsnes[0x80de151]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7b3e450]
zsnes(__gxx_personality_v0+0xd1)[0x804ba31]
======= Memory map: ========
08048000-082f8000 r-xp 00000000 08:02 180912     /usr/bin/zsnes
082f8000-0834b000 rwxp 002b0000 08:02 180912     /usr/bin/zsnes
0834b000-085d8000 rwxp 0834b000 00:00 0          [heap]
b7974000-b7976000 rwxp b7974000 00:00 0 
b7976000-b797a000 r-xp 00000000 08:02 181844     /usr/lib/libXdmcp.so.6.0.0
b797a000-b797b000 rwxp 00003000 08:02 181844     /usr/lib/libXdmcp.so.6.0.0
b797b000-b797d000 r-xp 00000000 08:02 181833     /usr/lib/libXau.so.6.0.0
b797d000-b797e000 rwxp 00001000 08:02 181833     /usr/lib/libXau.so.6.0.0
b797e000-b7995000 r-xp 00000000 08:02 182674     /usr/lib/libxcb.so.1.0.0
b7995000-b7996000 rwxp 00016000 08:02 182674     /usr/lib/libxcb.so.1.0.0
b7996000-b7997000 r-xp 00000000 08:02 182672     /usr/lib/libxcb-xlib.so.0.0.0
b7997000-b7998000 rwxp 00000000 08:02 182672     /usr/lib/libxcb-xlib.so.0.0.0
b7998000-b7999000 rwxp b7998000 00:00 0 
b7999000-b79a2000 r-xp 00000000 08:02 182030     /usr/lib/libdrm.so.2.3.0
b79a2000-b79a3000 rwxp 00008000 08:02 182030     /usr/lib/libdrm.so.2.3.0
b79a3000-b79a7000 r-xp 00000000 08:02 181850     /usr/lib/libXfixes.so.3.1.0
b79a7000-b79a8000 rwxp 00003000 08:02 181850     /usr/lib/libXfixes.so.3.1.0
b79a8000-b79aa000 r-xp 00000000 08:02 181842     /usr/lib/libXdamage.so.1.1.0
b79aa000-b79ab000 rwxp 00001000 08:02 181842     /usr/lib/libXdamage.so.1.1.0
b79ab000-b79af000 r-xp 00000000 08:02 181884     /usr/lib/libXxf86vm.so.1.0.0
b79af000-b79b0000 rwxp 00003000 08:02 181884     /usr/lib/libXxf86vm.so.1.0.0
b79b0000-b79bd000 r-xp 00000000 08:02 181848     /usr/lib/libXext.so.6.4.0
b79bd000-b79be000 rwxp 0000d000 08:02 181848     /usr/lib/libXext.so.6.4.0
b79be000-b7aa2000 r-xp 00000000 08:02 181827     /usr/lib/libX11.so.6.2.0
b7aa2000-b7aa5000 rwxp 000e4000 08:02 181827     /usr/lib/libX11.so.6.2.0
b7aa5000-b7aa6000 rwxp b7aa5000 00:00 0 
b7aa6000-b7ab8000 r-xp 00000000 08:02 182018     /usr/lib/libdirect-1.0.so.0.1.0
b7ab8000-b7ab9000 rwxp 00012000 08:02 182018     /usr/lib/libdirect-1.0.so.0.1.0
b7ab9000-b7ac0000 r-xp 00000000 08:02 182090     /usr/lib/libfusion-1.0.so.0.1.0
b7ac0000-b7ac1000 rwxp 00006000 08:02 182090     /usr/lib/libfusion-1.0.so.0.1.0
b7ac1000-b7b22000 r-xp 00000000 08:02 182020     /usr/lib/libdirectfb-1.0.so.0.1.0
b7b22000-b7b24000 rwxp 00060000 08:02 182020     /usr/lib/libdirectfb-1.0.so.0.1.0
b7b24000-b7b26000 r-xp 00000000 08:02 288135     /lib/tls/i686/cmov/libdl-2.7.so
b7b26000-b7b28000 rwxp 00001000 08:02 288135     /lib/tls/i686/cmov/libdl-2.7.so
b7b28000-b7c71000 r-xp 00000000 08:02 288129     /lib/tls/i686/cmov/libc-2.7.so
b7c71000-b7c72000 r-xp 00149000 08:02 288129     /lib/tls/i686/cmov/libc-2.7.so
b7c72000-b7c74000 rwxp 0014a000 08:02 288129     /lib/tls/i686/cmov/libc-2.7.so
b7c74000-b7c78000 rwxp b7c74000 00:00 0 
b7c78000-b7c82000 r-xp 00000000 08:02 270400     /lib/libgcc_s.so.1
b7c82000-b7c83000 rwxp 0000a000 08:02 270400     /lib/libgcc_s.so.1
b7c83000-b7ca6000 r-xp 00000000 08:02 288137     /lib/tls/i686/cmov/libm-2.7.so
b7ca6000-b7ca8000 rwxp 00023000 08:02 288137     /lib/tls/i686/cmov/libm-2.7.so
b7ca8000-b7d90000 r-xp 00000000 08:02 182611     /usr/lib/libstdc++.so.6.0.9
b7d90000-b7d93000 r-xp 000e8000 08:02 182611     /usr/lib/libstdc++.so.6.0.9
b7d93000-b7d95000 rwxp 000eb000 08:02 182611     /usAbandon
caroline@caroline-desktop:~$
```

And the deb package link : [http://ftp.handhelds.org/mirror/debian/pool/main/z/zsnes/zsnes_1.420-1_i386.deb](http://ftp.handhelds.org/mirror/debian/pool/main/z/zsnes/zsnes_1.420-1_i386.deb) (I did it with the graphic way).

And the original topic in French : [http://forum.ubuntu-fr.org/viewtopic.php?id=238079](http://forum.ubuntu-fr.org/viewtopic.php?id=238079)

Thanks in advance.

Ishimaru

---

### Post by Ishimaru Chiaki on 2008-07-27
Bump

---

### Post by grossaffe on 2008-07-27
not to get into a religous war or anything, but i've always been partial to the GTK port of SNES9x... I haven't tried mario RPG with it, but I haven't had any problems with it for any games.

---

### Post by Ishimaru Chiaki on 2008-07-28
> **grossaffe said:**
> not to get into a religous war or anything, but i've always been partial to the GTK port of SNES9x... I haven't tried mario RPG with it, but I haven't had any problems with it for any games.

I didn't have any issue with other games on zsnes. I used play SNES games under win95, win98 and winxp, and no problems with the games I was playing, and this year was the first time I try emulated Super Mario RPG.

---

### Post by grossaffe on 2008-07-28
> **Ishimaru Chiaki said:**
> I didn't have any issue with other games on zsnes. I used play SNES games under win95, win98 and winxp, and no problems with the games I was playing, and this year was the first time I try emulated Super Mario RPG.

tell you what, i'll give it a try and see if it freezes.  You say it freezes when equipping things, right?

edit: i've gotten far enough to get the hammer and some armor and haven't experienced any crashes from equipping them.  That is while using SNES9x GTK port.

only thing I noticed is that there are a couple sounds that don't quite match up with the original game but it isn't too often you hear it.  I think its mostly the higher pitched stuff while in a battle.

---

### Post by Ishimaru Chiaki on 2008-07-31
I finally installed snes9x-gtk and tried SMRPG and it hasn't freezed when I updated my equipments.  So, I will continue the gameplay with this emulator.

Problem solved, thanks :)

---

### Post by ynell on 2008-10-16
I actually ran into the equipping bug today and not sure if this is some freak chance thing or what, but the only time it froze was when mallow was level 5. 

I had him equipped already then the bug happened, so i googled and found i wasnt the only person.. but knew i had managed to equip him somehow. Then got the idea to continue the game and try later.. as soon as i leveled up to 6 i decided to try.. and it worked just fine. haven't had problems sense o.O

Edit: and i WAS able to duplicate the bug after rebooting. But as long as he's not level 5, it works just fine for me

---

