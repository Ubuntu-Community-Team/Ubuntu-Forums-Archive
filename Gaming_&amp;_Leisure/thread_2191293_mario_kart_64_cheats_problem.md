---
title: "mario kart 64 cheats problem"
date: 2013-12-01
forum: Gaming &amp; Leisure
---

### Post by carega on 2013-12-01
Hello I'm having a problem with mario kart 64 in mupen64plus. I'm trying to use some cheats and the following problem comes up:

```
mupen64plus --cheats 19,0-4 Documentos/juegos/n64/Mario\ Kart\ 64\ \(USA\).n64
 __  __                         __   _  _   ____  _             
|  \/  |_   _ _ __   ___ _ __  / /_ | || | |  _ \| |_   _ ___ 
| |\/| | | | | '_ \ / _ \ '_ \| '_ \| || |_| |_) | | | | / __|  
| |  | | |_| | |_) |  __/ | | | (_) |__   _|  __/| | |_| \__ \  
|_|  |_|\__,_| .__/ \___|_| |_|\___/   |_| |_|   |_|\__,_|___/  
             |_|         http://code.google.com/p/mupen64plus/  
Mupen64Plus Console User-Interface Version 1.99.4

UI-console: attached to core library 'Mupen64Plus Core' version 1.99.4
            Includes support for Dynamic Recompiler.
Core: Goodname: Mario Kart 64 (U) [!]
Core: Name: MARIOKART64
Core: MD5: 3A67D9986F54EB282924FCA4CD5F6DFF
Core: CRC: 3e5055b6 2e92da52
Core: Imagetype: .v64 (byteswapped)
Core: Rom size: 12582912 bytes (or 12 Mb or 96 Megabits)
Core: Version: 1446
Core: Manufacturer: Nintendo
Core: Country: USA
UI-Console: activated cheat code 19: Press L To Levitate\Player 1
Violación de segmento (`core' generado)
```

Can anyone tell me what's going on? according to the help on mupen64 I'm writing the cheats correctly. Thanks!

---

### Post by dannyboy79 on 2013-12-01
i don't see any error?

---

### Post by carega on 2013-12-01
well this is an error: > Violación de segmento (`core' generado)

It says in english "Segment Violation ('core' generalized)" or something like that.

---

### Post by deadflowr on 2013-12-01
Does the game play without the --cheats parameter?
or does it also generate a segmentation fault?

---

### Post by carega on 2013-12-05
It plays perfectly without the --cheats parameter. In fact, when I use cheats that do not have an option it works as well, as you can see mupen recognized cheat #19 
UI-Console: activated cheat code 19: Press L To Levitate\Player 1

---

