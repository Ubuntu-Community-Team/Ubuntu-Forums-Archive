---
title: "I've f***** my Ubuntu installation, is it possible to recover?"
date: 2005-01-03
forum: Desktop Environments
---

### Post by Ruediger on 2005-01-03
Everything was working fine on my Ubuntu 4.10, until I decided to do an apt-get upgrade, the packages dowloaded fine, after the setup the computer was supposed to reboot but it hang. I pressed the reset button. Now when I boot Grub can't find any of the kernel images (not even the ones marked as recover).

Is there anything I can do to fix this?

---

### Post by Juergen on 2005-01-03
Start with any rescue/live CD and look around on your partitions.
If they are still there (I hope so :-)) you may be able to read the logs and provide some more infos here.

Maybe your kernel somehow vanished while upgrading it - if so, I think it could be possible to re-install it in a chrooted environment (maybe boot-partition full?)

---

### Post by Ruediger on 2005-01-03
[QUOTE=Juergen]Start with any rescue/live CD and look around on your partitions.
If they are still there (I hope so :-)) you may be able to read the logs and provide some more infos here.

Maybe your kernel somehow vanished while upgrading it - if so, I think it could be possible to re-install it in a chrooted environment (maybe boot-partition full?)[/QUOTE]

I am dowloading Knoppix right now. I am a noob, where should I look for the logs? I've no idea what is a chrooted environment....

---

### Post by crane on 2005-01-03
[QUOTE=Ruediger]I am dowloading Knoppix right now. I am a noob, where should I look for the logs? I've no ideia what is a chrooted environment....[/QUOTE]


/var/log is where the log files are stored I believe.


Also check you /boot folder and make sure grub and that info is still there.

---

