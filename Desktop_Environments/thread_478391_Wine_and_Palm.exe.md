---
title: "Wine and Palm.exe"
date: 2007-06-19
forum: Desktop Environments
---

### Post by Seeker84 on 2007-06-19
So I tried JPilot and didn't like the GUI for it, I didn't like not seeing the day planned out like on the device itself.  So I figured let's try out wine see if it likes me enough to run the program.  So I go into Terminal, get to where palm.exe is on my NTFS partition and I type in "wine palm.exe"  "First chance exception:  page fault on read access"  I don't know enough about wine's debugger nor do I know where to start on it.  But I ran winedbg palm.exe and it gives me this:
```

First chance exception: page fault on read access to 0x00000020 in 32-bit code (0x67cd70a9).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:67cd70a9 ESP:0034f300 EBP:67cf8a20 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:00001430 ECX:00000000 EDX:00198c78
 ESI:00000000 EDI:0082d548
Stack dump:
0x0034f300:  0082d548 0082d100 00001430 00423718
0x0034f310:  0082d100 0034fb2c 0034f430 00423360
0x0034f320:  0082e068 0082e0b8 56002800 00000000
0x0034f330:  00000000 000000c8 00000078 00000005
0x0034f340:  00000005 00000005 00000005 00000000
0x0034f350:  00000000 00000019 00000016 00000050
Backtrace:
=>1 0x67cd70a9 in palmui (+0x70a9) (0x67cf8a20)
  2 0x0424548b (0x08244c8b)
  3 0x00000000 (0x00000000)
0x67cd70a9: movl        0x20(%esi),%eax

```pe in normally
```

wine palm.exe
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
wine: Unhandled page fault on read access to 0x00000020 at address 0x67cd70a9 (thread 0009), starting debugger...

```

Now the palm OS is version 4.1.4.  I've checked wine Appdb and I don't know if I'm reading it right but I think it is supported.

here's what I would ty

Any help would be appreciated.

---

### Post by Seeker84 on 2007-06-20
Has anyone tried to get the palm desktop to work with wine?

---

### Post by Seeker84 on 2007-06-21
Still waiting on some feedback.

---

### Post by Seeker84 on 2007-07-07
Still here waiting to see if anyone has the same issuses

---

### Post by GorBo on 2007-10-05
Maybe this will help: [http://wiki.winehq.org/JamesLiggett/](http://wiki.winehq.org/JamesLiggett/)

The only reason I'm running Windows XP in a VMWare Player is syncing. I have tried native linux solutions (jpilot, gpilotd+Evolution, KDE apps) and have not been satisfied with the results. On the page there you'll find some links to instructions on running Palm software under wine. The page is somewhat old though.

---

