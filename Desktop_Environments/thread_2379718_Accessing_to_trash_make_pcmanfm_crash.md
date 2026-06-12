---
title: "Accessing to trash:/// make pcmanfm crash"
date: 2017-12-08
forum: Desktop Environments
---

### Post by esnhouan on 2017-12-08
I've got this problem since the last reboot, if I open the Trash folder or right click on it pcmanfm crashes.

pcmanfm 1.2.4-1ubuntu0.1
Lubuntu 16.04 LTS

dmesg return these two lines at the time of the crash

```
[  429.765289] show_signal_msg: 12 callbacks suppressed
[  429.765297] pcmanfm[2629]: segfault at 1d ip b68c1456 sp bfe67874 error 4 in libc-2.23.so[b6843000+1b0000]
```

Last installed packages are ufraw-batch, zenity, and trash-cli.

trash-cli have been installed to add a right click menu voice to the desktop icon to empty the trash.
Other two packages have been installed because I'm writing some file-managers/actions/*.desktop utilities to batch raw pictures.

I've tried to uninstall trash-cli but the problem persists.

I searched the net but I cannot find a way to have the Trash folder work again. Everything worsk like a charm

---

