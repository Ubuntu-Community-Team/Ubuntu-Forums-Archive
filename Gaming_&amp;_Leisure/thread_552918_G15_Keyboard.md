---
title: "G15 Keyboard"
date: 2007-09-17
forum: Gaming &amp; Leisure
---

### Post by Arukas on 2007-09-17
Hello-

  I happen to have a g15 keyboard, it works fine, but I would like to know if anyone knows if i can get the any programs that will make use of the extra keys like I did in windows? or where even to look?

-Arukas

---

### Post by Sensenseppl on 2007-09-17
Hello Arukas!

I recommend using **xbindkeys** (see [http://hocwp.free.fr/xbindkeys/xbindkeys.html]("http://hocwp.free.fr/xbindkeys/xbindkeys.html")).

I only have german speaking sources, but I think this will help you:
```

#G1
"Command"
    m:0x10 + c:177
    Mod2 + NoSymbol

#G2
"Command"
    m:0x10 + c:152
    Mod2 + NoSymbol

#G3
"Command"
    m:0x10 + c:190
    Mod2 + NoSymbol

#G4
"Command"
    m:0x10 + c:208
    Mod2 + NoSymbol

#G5
"Command"
    m:0x10 + c:129
    Mod2 + NoSymbol

#G6
"Command"
    m:0x10 + c:130
    Mod2 + NoSymbol

#G7
"Command"
    m:0x10 + c:231
    Mod2 + NoSymbol

#G8
"Command"
    m:0x10 + c:209
    Mod2 + NoSymbol

#G9
"Command"
    m:0x10 + c:210
    Mod2 + NoSymbol

#G10
"Command"
    m:0x10 + c:136
    Mod2 + NoSymbol

#G11
"Command"
    m:0x10 + c:220
    Mod2 + NoSymbol

#G12
"Command"
    m:0x10 + c:143
    Mod2 + NoSymbol

#G13
"Command"
    m:0x10 + c:246
    Mod2 + NoSymbol

#G14
"Command"
    m:0x10 + c:251
    Mod2 + NoSymbol

#G15
"Command"
    m:0x10 + c:137
    Mod2 + NoSymbol

#G16
"Command"
    m:0x10 + c:138
    Mod2 + NoSymbol

#G17
"Command"
    m:0x10 + c:182
    Mod2 + NoSymbol

#G18
"Command"
    m:0x10 + c:183
    Mod2 + NoSymbol

#small left-left multimedia-key
"Command"
    m:0x10 + c:170
    Mod2 + NoSymbol

#small left multimedia key
"Command"
    m:0x10 + c:219
    Mod2 + NoSymbol

#small right multimedia key
"Command"
    m:0x10 + c:249
    Mod2 + NoSymbol

#small right-right multimedia key
"Command"
    m:0x10 + c:205
    Mod2 + NoSymbol

#M1
"Command"
    m:0x10 + c:184
    Mod2 + NoSymbol

#M2
"Command"
    m:0x10 + c:93
    Mod2 + Mode_switch

#M3
"Command"
    m:0x10 + c:131
    Mod2 + NoSymbol 

```

Those are all the codes for the special keys on your G15-Keyboard. Just insert a different command instead of "Command" next to the key you want to assign something to.

For example:
```
#M3
"bash mypersonalscript.sh"
    m:0x10 + c:131
    Mod2 + NoSymbol
```

Of course you have to have **uinput** and **g15daemon** loaded correctly.

I hope this helps!

Greetings,
Sensenseppl

---

### Post by Arukas on 2007-09-17
Thanks alot, that has me in the right direction, I appreciate it.

-Arukas

---

