---
title: "XP Patition disappearing act"
date: 2007-09-04
forum: Dell  Ubuntu Support
---

### Post by joos13 on 2007-09-04
I dual boot XP and Feisty on my Latitude D610 and have had no problems until now.  I have the dual boot set up so that GRUB loads when I turn on the computer and then press ESC to get into the boot options if I want to boot XP.  However, today when I went to load XP, the "Windows XP" option did not show up in the list of boot options.  I have not messed iwth the GRUB recently.  Anyone have suggestions/prior experience with this?

---

### Post by thelocust on 2007-09-04
your kernel probably updated and wrote over you menu.lst file. Did you ever back it up?

---

### Post by joos13 on 2007-09-04
ahh i imagine you are correct.  i believe it was yesterday or the day before that the kernel files updated as part of a system update.  NO, I did not back up said file.  How do I go about restoring it?  thanks for the help.

---

### Post by thelocust on 2007-09-04
Double check your /boot/grub file for anything starting with menu.lst sometimes oddball programs automatically back it up for you. If you sea any open it up and check to see if your part to boot windows is in there if so just copy that section over to the new one. If not paste the output of this command.

```
sudo fdisk -l
```

---

