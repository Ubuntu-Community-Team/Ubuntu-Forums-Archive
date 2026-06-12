---
title: "GRUB Bootloader tossed on Windows Format"
date: 2009-01-05
forum: General Help
---

### Post by vergeh on 2009-01-05
I'm running on an Asus M2N-SLI Deluxe, and I recently had to format the windows partition of my dual-boot machine (the other system being Ubuntu Feisty). Everything was fine until I loaded the nVidia chipset drivers. Now I'm getting an error when I boot.
```

Bad or Missing command Interpreter
Enter the full shell command line:

```

I've read about this issue before, but nobody seems to be able to fix it. I'm running 3 physical drives.

sda0 [Windows]
sdb0 [NTFS Storage]
sdc0 [Ubuntu]
sdc1 [Ubuntu swap]
sdc2 [NTFS storage]

How might I go about fixing or restoring the grub bootloader?


Edit: I can still access Windows when I boot to the Ubuntu CD< and select Boot from First Hard Drive.

---

### Post by blazemore on 2009-01-05
Wait... It works when you do Boot From First Hard Drive?
That's the same thing as not having the LiveCD in at all. Are any other devices plugged in from which the BIOS might be attempting to boot?

---

