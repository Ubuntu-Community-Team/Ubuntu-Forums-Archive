---
title: "emulation"
date: 2011-02-05
forum: Gaming &amp; Leisure
---

### Post by captainstan on 2011-02-05
just wondering if there were any sega genesis or playstation 1 emulators

---

### Post by thomasw_lrd on 2011-02-05
pcsx.  Works great.  It's even in the repositories.

---

### Post by mips on 2011-02-06
[http://www.zophar.net/linux.html](http://www.zophar.net/linux.html)

For Sega you probably looking at something like Gens.

---

### Post by dfreer on 2011-02-06
Playstation 1: pSX, ePSXe, pcsx

---

### Post by DoktorSeven on 2011-02-06
Gens/GS for Genesis/Mega Drive emulation.
[http://www.segaretro.org/Gens/GS](http://www.segaretro.org/Gens/GS)

If you use 64-bit Ubuntu: No 64bit version but you can install it by installing 32bit libraries then using **dpkg -i --force-architecture Gens_2.16.7_i386.deb**

---

### Post by Rustybolts on 2011-02-06
[Playdeb]("http://www.playdeb.net/updates/Ubuntu/10.10/?category=Emulator") has a few emulators (easy to install go [here]("http://archive.getdeb.net/install_deb/playdeb_0.3-1%7Egetdeb1_all.deb") first though)

---

### Post by honeybear on 2011-02-06
you may manage with

```
/usr/games/dgen -X 2  -Y 2  -f  -j   
*.bin
*.smc
```
```


/usr/games/pcsx -nogui -cdfile  
*.bin

```

---

### Post by thatguruguy on 2011-02-06
[pcsx-r]("http://pcsxr.codeplex.com/")

---

