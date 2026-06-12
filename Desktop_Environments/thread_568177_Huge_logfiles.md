---
title: "Huge logfiles"
date: 2007-10-05
forum: Desktop Environments
---

### Post by jpgv on 2007-10-05
Hi,

I just installed xubuntu in my old laptop thinking it would be the best idea to keep my aging hardware running. 

The problem is it is creating huge log files: kernel.log, syslog and messages, 2.7 GB a piece, filling up all my disk, making the system very slow and, ultimately, crashing it. I've seen these files, literaly, growing 4 or 5 Mb a second. 

Does anyone know what is the problem here?

Thanks, jpgv

---

### Post by jpgv on 2007-10-05
Btw, I forgot to mention, it is the Feitsy version I'm using.

---

### Post by jpgv on 2007-10-09
Hey.
Nobody answered here, but I solved the problem and thought it would be good idea to let people who might visit the thread know what was the problem (not that I understand what's happening behind, but now the computer works).

Anyway, the problem was with ACPI.  Xubuntu didn't like ACPI for some reason, so I added an instruction in Grub's menu.lst not to load ACPI.  And problem solved.  Sorry I can't be more specific, but for some reason I can't find anymore the thread were I found that approach.

---

