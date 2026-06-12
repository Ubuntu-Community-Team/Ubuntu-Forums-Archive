---
title: "Reinstalling GRUB through Dapper Drake?"
date: 2006-06-22
forum: Desktop Environments
---

### Post by BetaMaster on 2006-06-22
Hey, I recently installed Windows Vista on a partition to check it out. This installed it's own boot loader, which overrides GRUB. How do I reinstall GRUB using the Dapper Drake install/live CD?

If I try booting into Drake and, in terminal, use the command
```
sudo grub-install /dev/hda
```
it gives me an error about not being able to find /boot/, or not being able to create it. I can't remember which, if it's important.

Is there another way to do it? Maybe by booting into Rescue Mode? How do you do that, if so?

Thanks!

---

### Post by BetaMaster on 2006-06-22
Oh, and ideally, I'd like to have a way to add Vista to the bootloader.

---

### Post by lamego on 2006-06-22
I don't know about Vista, but the usual procedure for reinstalling grub is [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

---

