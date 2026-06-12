---
title: "Can't shutdown from desktop."
date: 2017-10-13
forum: Desktop Environments
---

### Post by jimford on 2017-10-13
I can't shutdown from the desktop (but can from the command line).

I guess it's a module that's become corrupted. Any ideas what one it could be so I can reinstall it, please?

Jim

---

### Post by ajgreeny on 2017-10-13
Hit ESC at boot and shutdown and you should see scrolling text at both. The output at shutdown may give you a clue to the problem.

---

### Post by jimford on 2017-10-13
> **ajgreeny said:**
> Hit ESC at boot and shutdown and you should see scrolling text at both. The output at shutdown may give you a clue to the problem.

Thanks for the reply.

Hitting ESC doesn't do anything on shutdown and only brings up the 'grub' boot page on startup.

Jim

---

### Post by ajgreeny on 2017-10-13
OK, you are using a UEFI system.

Temporary changes for a single boot can be made from the grub menu (after hitting ESC) by pressing E to edit the boot stanza.  In the screen that appears move to the line ending with the words "quiet splash" using the cursor keys and delete those two words only then hit Ctrl+X or F10 to boot
I think that is the keypresses but it's a long time since I've done it, however it tells you at the bottom so you'll see if I'm remembering wrongly.

That will make the system boot to a text output for both the start and shutdown and you may then see where the problem lies.

---

