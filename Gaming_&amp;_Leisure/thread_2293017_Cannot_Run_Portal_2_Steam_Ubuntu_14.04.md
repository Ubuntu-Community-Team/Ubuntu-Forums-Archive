---
title: "Cannot Run Portal 2 Steam Ubuntu 14.04"
date: 2015-09-01
forum: Gaming &amp; Leisure
---

### Post by ethan27 on 2015-09-01
Hello I love portal 2 and would like to play it on my Ubuntu machine. The only problem is it will not open. I will click play and it says launching Portal 2 then the message disappears and it syncs and does not open the game. I am opted into the beta. Any help would be highly appreciated. The Terminal output by running Steam in terminal the opening Portal 2 in the Steam GUI was:

LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/ethan/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
pid 15065 != 15064, skipping destruction (fork without exec?)
ERROR: ld.so: object '/home/ethan/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/ethan/.steam/ubuntu12_64/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS64): ignored.
libGL error: unable to load driver: r600_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: r600
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  155 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Value in failed request:  0x0
  Serial number of failed request:  80
  Current serial number in output stream:  81
Game removed: AppID 620 "Portal 2", ProcID 15062

---

### Post by efflandt on 2015-09-02
Do any other Source games work on Steam (like Team Fortress 2 which is free to install, but takes a while to download, and some disk space)?

What graphics card/chip do you have and are you using default graphics drivers or proprietary drivers? Nvidia graphics chips and nvidia driver packages work best. I have heard that if you have AMD/ATI graphics that it is best to install Steam "before" installing proprietary graphics drivers. Otherwise you may get some clues about missing libs or unable to find some 32-bit libs in 64-bit Linux from the **Steam for Linux** forum [http://steamcommunity.com/app/221410/discussions/](http://steamcommunity.com/app/221410/discussions/)

One thing to try if certain games do not work is to right click on the game in Steam Library and go to **Properties** > **LOCAL FILES** > **VERIFY INTEGRITY OF GAME CACHE...** which re-downloads any corrupt or missing game files, but it looks like an issue with Steam files/libs before it gets to the game.
 
I have been running Linux Steam since it was beta in Jan 2013, originally in 64-bit Ubuntu 12.04 and currently in 64-bit 14.04 (from 14.04.1) with copied over home game files on my desktop (some different paths), or Steam and games installed from scratch in 14.04 on my laptop (which is the paths yours is using).

---

### Post by ethan27 on 2015-09-02
Source games work as I've ran CS:GO and the original Portal fine. The GPU/APU is an AMD A8 with 7000 series graphics. The path I use /home/.steam/steam/steamapps/common/Portal 2. I hope this answers your questions.

---

### Post by efflandt on 2015-09-02
I guess I should have tried Portal 2 when they recently had a free weekend and/or sale. I wonder if that uses the Source 3 engine yet (maybe that was just a test video using the Steam Controller). Current System Requirements for Linux Portal 2 do not look very demanding for 2 GB RAM, old graphics, or OpenGL 2.1.

---

### Post by ethan27 on 2015-09-02
I have 6 GB of RAM. I run the Open Source driver. Last time I tried the proprietary driver I had to reinstall Ubuntu. Any leads on this though? It's really bugging me. Any help is highly appreciated.

---

### Post by efflandt on 2015-09-02
You may find something web searching "r600_dri.so", although, some of that info is old. It seems like it might be related to the version of libstdc++.so.6 that steam provides.

This may help even though it is in an Arch forum because it specifically mentions Portal 2 (especially last reply #10). But note that any older path that begins ~/.local/Steam/ on more recently installed Steam (yours) would begin ~/.steam/steam/ and if you do not want to remove those libstdc++.so.6 files, you could rename (mv) them with a .bak extension, so they would be ignored for testing, but still there.

---

### Post by ethan27 on 2015-09-02
I'm a big noob so what is the exact directory like /.steam/steam/steamapps/common/Portal 2/?

---

### Post by ethan27 on 2015-09-02
Never mind I changed the .6 to .bak and it ran but it said it would not sync my data should I be worried?

---

### Post by ethan27 on 2015-09-02
For some reason it actually synced thanks efflandt! You saved me a lot of time and effort.

---

