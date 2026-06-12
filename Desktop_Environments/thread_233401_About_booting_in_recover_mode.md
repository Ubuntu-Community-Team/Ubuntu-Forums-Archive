---
title: "About booting in recover mode"
date: 2006-08-10
forum: Desktop Environments
---

### Post by cobbweb on 2006-08-10
Two questions, first, how can I disable the recovery mode option when grub loads up? Aslo, how can I force my computer to boot in recovery mode by default one time? Thank you,

 Cobbweb

---

### Post by rowanparker on 2006-08-10
1. Just edit your /boot/grub/menu.lst file and comment out the recovery ones.
2. Can't you just select it at boot?

---

### Post by Tomosaur on 2006-08-10
You can easily edit your default to boot into the recovery mode, but why you would want to do that is beyond me. It's not a very good idea to remove the recovery mode option, since if booting fails one time,getting grub to load the recovery mode from its built in command line is an irritating process.

---

### Post by cobbweb on 2006-08-10
> **Tomosaur said:**
> You can easily edit your default to boot into the recovery mode, but why you would want to do that is beyond me. It's not a very good idea to remove the recovery mode option, since if booting fails one time,getting grub to load the recovery mode from its built in command line is an irritating process.

I know what im asking is not good practic, but I am trying to learn a concept . So this is the situation. If I load into the my boot loader and the recovery mode doesn't show up, can I somonehow load into recovery mode still? If it's possible, does anyone have a link or can explain how I can do this? Thanks, 

 Cobbweb

---

### Post by Ramses de Norre on 2006-08-10
Yes, you can press 'e' on a regular line to edit it and add 'single' to the kernel options. This is what distinguises the recovery entries from the others in menu.lst too.

To lock this method down you can set a grub passwd.

---

