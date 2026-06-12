---
title: "Shutting down"
date: 2009-01-02
forum: General Help
---

### Post by OinkOink2 on 2009-01-02
Hi all,

I was wondering if there was a way to have the Usplash screen of Ubuntu after GRUB, but upon shutdown/restart just simply have the text version of everything that is going on?

Cheers.

---

### Post by ajgreeny on 2009-01-02
Not that I'm aware of, though you can edit the grub menu kernel line whenever you want by hitting "e" on the chosen OS in grub menu and then choosing the kernel line, "e" again and remove the words "quiet splash" from the end of the line, then hit enter and then "b" to boot.   You can also edit your /boot/grub/menu.lst file and remove just the word quiet if you want to get a minimal text output along with the splash.  Try it at one boot using the way I said above, and if you like it edit the menu.lst file permanently.

---

