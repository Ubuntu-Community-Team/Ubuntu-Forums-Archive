---
title: "Enemy Territory crashes during artillery strikes"
date: 2011-02-01
forum: Gaming &amp; Leisure
---

### Post by ploum on 2011-02-01
Hello,

I've installed Enemy Territory from playdeb this weekend (because it's easier and I don't want to mess my installation).

After several hundreds of MB of download, it works great. But I've a reproducable crash: when I'm too close of an Artillery Strike, ET crashes.

```

---------------------------------------
Version Linux: 1.2.9 Aug  4 2010 Enemy Territory, ET 2.60
Map: supply_pro
Signal: Segmentation fault (11)
Siginfo: 0xbfd63d9c
Code: 1
Faulting Memory Ref/Instruction: 0xbfd68000
DSO Information:
0xb775a000	./et-sdl-sound.so
0xb7744000	/lib/libdl.so.2
0xb7626000	/usr/lib/libX11.so.6
0xb7616000	/usr/lib/libXext.so.6
0xb75f0000	/lib/libm.so.6
0xb7493000	/lib/libc.so.6
0xb73a8000	/usr/lib/libstdc++.so.6
0xb738c000	/lib/libgcc_s.so.1
0xb7762000	/lib/ld-linux.so.2
0xb7371000	/usr/lib/libxcb.so.1
0xb736d000	/usr/lib/libXau.so.6
0xb7367000	/usr/lib/libXdmcp.so.6
0xadabd000	/lib/libnss_compat.so.2
0xadaa6000	/lib/libnsl.so.1
0xada9b000	/lib/libnss_nis.so.2
0xada8f000	/lib/libnss_files.so.2
0xac23b000	/usr/lib/mesa/libGL.so.1
0xac237000	/usr/lib/libXdamage.so.1
0xac231000	/usr/lib/libXfixes.so.3
0xac22b000	/usr/lib/libXxf86vm.so.1
0xac221000	/lib/libdrm.so.2
0xac207000	/lib/libpthread.so.0
0xac1fe000	/lib/librt.so.1
0xabed7000	/usr/lib/dri/i965_dri.so
0xabeb0000	/lib/libexpat.so.1
0xabea6000	/usr/lib/libtalloc.so.2
0xabe9b000	/lib/libdrm_intel.so.1
0xab9f5000	/usr/lib/libXcursor.so.1
0xadacd000	/usr/lib/libXrender.so.1
0xab4b3000	/usr/lib/libSDL-1.2.so.0
0xab3ed000	/usr/lib/libasound.so.2
0xab3a8000	/usr/lib/libpulse.so.0
0xab3a5000	/usr/lib/libX11-xcb.so.1
0xab38c000	/usr/lib/libICE.so.6
0xab383000	/usr/lib/libSM.so.6
0xab37d000	/usr/lib/libXtst.so.6
0xab378000	/usr/lib/libxcb-atom.so.1
0xab32e000	/usr/lib/libpulsecommon-0.9.21.so
0xab329000	/lib/libuuid.so.1
0xab31b000	/usr/lib/libXi.so.6
0xab312000	/lib/libwrap.so.0
0xab2aa000	/usr/lib/libsndfile.so.1
0xab26e000	/lib/libdbus-1.so.3
0xab222000	/usr/lib/libFLAC.so.8
0xab0aa000	/usr/lib/libvorbisenc.so.2
0xab082000	/usr/lib/libvorbis.so.0
0xab07b000	/usr/lib/libogg.so.0
0xab543000	/usr/lib/alsa-lib/libasound_module_pcm_pulse.so
0xa2b0a000	/home/ploum/.etwolf/pb/pbcl.so
0xab91e000	/lib/libnss_mdns4_minimal.so.2
0xab918000	/lib/libnss_dns.so.2
0xab904000	/lib/libresolv.so.2
0xa2ab2000	/home/ploum/.etwolf/pb/pbag.so
0xa28d0000	/home/ploum/.etwolf/pb/pbsv.so
0xa3985000	/home/ploum/.etwolf/nq/ui.mp.i386.so
0x86e4e000	/home/ploum/.etwolf/nq/cgame.mp.i386.so
Stack frames: 0 entries
Backtrace:
-8<--------------------------------->8-


```

Does anybody else has this bug? Is there a way to solve it?

---

### Post by BbUiDgZ on 2011-02-01
EDIT: check out this thread
[http://ubuntuforums.org/showthread.php?t=362231](http://ubuntuforums.org/showthread.php?t=362231) 

your using hacked sound so the game uses asla instead of OSS - I'd recommend installing the linux installer provided by ID software [HERE](http://ftp.games.skynet.be/pub/wolfenstein/et-linux-2.60.x86.run)


I have played ET for 8 years now and never seen this. I have it installed via the .run file suppied by ID software.

by the console output you've posted it looks like a sound problem.
You may want to change your sound prefs to test.

you'll find the ET me (HBC)Remasters [HERE](http://hbc.forumup.org) ;)

---

### Post by ploum on 2011-02-01
I've reported [https://bugs.launchpad.net/getdeb.net/+bug/711257](https://bugs.launchpad.net/getdeb.net/+bug/711257)

---

### Post by ploum on 2011-02-03
It's very strange because I've not been able to reproduce the bug on an empty server. But it happens nearly all the time but on a quite busy server. I also see some graphical artefacts while the whole place is shattering (which is normal, to make it more realistic). Then, pof, crash.

It doesn't seem to depend of any mod.


But I must admit that, what I hate in ET, is this download frenzy. Each server seems to have his own mod. Since a few days, my keymap config is not saved anymore and reset at each restart (I didn't change anything but a few mods were downloaded in the meantime)

---

### Post by mastablasta on 2011-02-04
> **ploum said:**
>  
But I must admit that, what I hate in ET, is this download frenzy. Each server seems to have his own mod. Since a few days, my keymap config is not saved anymore and reset at each restart (I didn't change anything but a few mods were downloaded in the meantime)
 
YES!
And also i hate because most servers use those XP save settings and then you can't do anything to people that are playing htere all the time. i stopped playing the game cause public server got so annoying to me. i keep getting kicked off (voted out) for planting mines, using rifle grenade, using maschine gune, using sniper rifle and using panzerfaust. i had a few (very few) very enjoyable games, but mostly the were kicking me off.
 
not to meniton people started using cheats of some sort as they saw me through the bushes, walls etc... frustrating. 
 
i played a bit of FPS games before. not much, yet no none had such hostile crowd towards me or my tactics. i mean if the game allows using panzerfaust then i can use it (it has it's drawbacks too). it's not cheating or being newb or noob or whatever...

---

### Post by BbUiDgZ on 2011-02-06
> **mastablasta said:**
> YES!
And also i hate because most servers use those XP save settings and then you can't do anything to people that are playing htere all the time. i stopped playing the game cause public server got so annoying to me. i keep getting kicked off (voted out) for planting mines, using rifle grenade, using maschine gune, using sniper rifle and using panzerfaust. i had a few (very few) very enjoyable games, but mostly the were kicking me off.
 
not to meniton people started using cheats of some sort as they saw me through the bushes, walls etc... frustrating. 
 
i played a bit of FPS games before. not much, yet no none had such hostile crowd towards me or my tactics. i mean if the game allows using panzerfaust then i can use it (it has it's drawbacks too). it's not cheating or being newb or noob or whatever...

first off ET is 10 years old hence the downloads
second off if you want to save your config for each mod (etpro, jaymod,NQ) make sure you start your game in that mode mode ```
+fs_game "etpro"
``` and exec your config ```
+exec nameofyourconfig.cfg
```

the run cmd for my game looks like this
```

et +com_hunkmegs "512" +set fs_game "etpro" +exec "hbcremasters.cfg" +exec "binds.cfg" +password "mypasswd" +connect 213.163.70.120:27960

```

like i said in my first post, you may want to run the game without the alsa hack and just use OSS.

---

### Post by ploum on 2011-02-07
I'm launching the game from within XQF. It thus makes no sense to have a "+fsgame etmod" line because ET switch automatically to the mod related to the server I'm connecting.

---

### Post by BbUiDgZ on 2011-02-08
> **ploum said:**
> I'm launching the game from within XQF. It thus makes no sense to have a "+fsgame etmod" line because ET switch automatically to the mod related to the server I'm connecting.
yeah but if your loading the game in etmain it aint gona load your config in etpro/jaymod/NQ/whatever :|

[img]http://grow-room.org/purplehaze/8thday.jpg[/img]

---

### Post by ploum on 2011-02-13
> **BbUiDgZ said:**
> yeah but if your loading the game in etmain it aint gona load your config in etpro/jaymod/NQ/whatever :|


That explains my problem with keys. Have you any idea on how I could solve that? Which file is loaded then?

---

### Post by BbUiDgZ on 2011-02-17
> **ploum said:**
> That explains my problem with keys. Have you any idea on how I could solve that? Which file is loaded then?
```
et +seta fs_game "etpro" +exec yourconfig.cfg
```

---

