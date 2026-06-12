---
title: "DVD-RW Read-only filesystem"
date: 2006-08-01
forum: Desktop Environments
---

### Post by wombat20 on 2006-08-01
I've managed to write some files to my Maxell DVD-RW discs with my NEC drive, but I don't seem to be able to delete things from these discs (at least in Dapper, not tried any other way).

It complains of "Read-only filesystem" when I try to rm a file.  I've also tried numerous programs to delete or reformat the disc, but with no luck.

Do I need to mount it in a special way and which file do I edit so that this happens automatically?

Any advice appreciated.  :)

---

### Post by orb9220 on 2006-08-01
Well in XP if you could do this if you installed nero or roxio because they installed a special driver that was called Mt. Rainer that treated your rw  as a giant floppy. was InCD in nero I think. Don't know about in linux.

Need to search in forums about Multi-session Cd's and DVD's and see. If you are trying to drag and drop files to cd and to delete like from nautilus  then the answer I believe is No.

Sorry couldn't be more help.

---

### Post by mchatel on 2006-08-01
Yes, as Orb9220 has already mentioned, perhaps you were probably used to using a packet-writing method of DVD-RW access or something similar, if you were using Windows previously.  Like he said, that method could treat a re-writeable disc as one big floppy drive, if one chose to use it that way.  Continuously writing and deleting to it, on the fly.  However, it's unreliable.  I've lost data using that method under Windows before (DirectCD).  Not sure if packet-writing is available under Linux or not.  Probably, in some form or another.

Anyway, the default behaviour for DVD-RW discs is to treat them as DVD-Rs, in that you write to them, and that's it.  If you want to write to them again (which you can), you have to erase the disc first (some applications do this automatically for you), and you write new info to it again.

---

### Post by wombat20 on 2006-08-03
So... has anyone got ReWritable discs to work under Ubuntu?

Or is it a write-off.  :rolleyes:

---

