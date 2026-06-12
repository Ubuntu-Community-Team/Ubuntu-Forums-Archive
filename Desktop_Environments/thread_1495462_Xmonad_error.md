---
title: "Xmonad error"
date: 2010-05-28
forum: Desktop Environments
---

### Post by handjob_the_sofa_surfer on 2010-05-28
Hi again. My previous thread regarding wmii2 problem received no attention whatsoever. I hope that someone at least can help me with Xmonad problem.

I get this error after pressing M-q

```

Error detected while loading xmonad configuration file: /home/handjob/.xmonad/xmonad.hs
/usr/bin/ld: reopening xmonad.o: No such file or directory

/usr/bin/ld:xmonad.o: bfd_stat failed: No such file or directory
/usr/bin/ld: reopening xmonad.o: No such file or directory

/usr/bin/ld:xmonad.o: bfd_stat failed: No such file or directory
/usr/bin/ld: reopening xmonad.o: No such file or directory

/usr/bin/ld:xmonad.o: bfd_stat failed: No such file or directory
/usr/bin/ld: reopening xmonad.o: No such file or directory

/usr/bin/ld:xmonad.o: bfd_stat failed: No such file or directory
/usr/bin/ld: reopening xmonad.o: No such file or directory

/usr/bin/ld: BFD (GNU Binutils for Ubuntu) 2.20.1-system.20100303 internal error, aborting at ../../bfd/merge.c line 872 in _bfd_merged_section_offset

/usr/bin/ld: Please report this bug.

collect2: ld returned 1 exit status

Please check the file for errors.

```The mentioned "xmonad.o" file is present in ~/.xmonad/ directory.

Despite appearing, nothing wrong happens, but the message itself is a kind of nuance.

---

