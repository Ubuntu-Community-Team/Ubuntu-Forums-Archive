---
title: "Boot code editing?"
date: 2009-01-18
forum: General Help
---

### Post by MaXiMiUS on 2009-01-18
I know there's a windows program (bootsect.exe) that can edit boot codes..

Is there any way to do this on Linux?

I'm trying to find something with behavior similar to bootsect.exe /nt60

Details on bootsect.exe: [http://technet.microsoft.com/en-us/library/cc749177.aspx](http://technet.microsoft.com/en-us/library/cc749177.aspx)

Anyone have any ideas? All I seem to be able to do with GParted is set the "boot" flag.. which sets the -wrong- boot flag in my case (/nt52)

Thanks in advance!

---

### Post by caljohnsmith on 2009-01-18
Using "bootsect /nt60" would install Vista boot code to the boot sector of the partition you specify, and as far as I know there is no direct equivalent of that command in Linux since Vista's boot code is of course proprietary. There are linux programs like "testdisk" that can restore a backup version of the Vista boot sector from the partition, but what exactly are you trying to accomplish? There may be some other way to do what you want with linux, but how about clarifying what your ultimate goal is.

---

