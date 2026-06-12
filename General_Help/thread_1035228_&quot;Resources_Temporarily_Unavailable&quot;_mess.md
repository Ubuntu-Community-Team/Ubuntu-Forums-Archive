---
title: "&quot;Resources Temporarily Unavailable&quot; message"
date: 2009-01-09
forum: General Help
---

### Post by WPDOS_user1954 on 2009-01-09
In terminal, the command "xsel" works fine, running the xsel application as intended.  But calling it from DOSEMU via the "unix" command, ie "unix xsel ...." doesn't.  Nothing happens.

The log file gives "Resources temporarily unavailable" as an error message.

Anyone any ideas?

Thanks,

Malcolm

---

### Post by -grubby on 2009-01-09
Wait, what do you need to launch xsel from the DOS Emulator? If it works fine in the terminal, I don't see why it should be a problem.

---

### Post by WPDOS_user1954 on 2009-01-09
The reason it is called from within the DOS emulator is that the calling is done by a DOS application, WordPerfect, which shells out to the DOS command line to issue the xsel command.

Malcolm

---

