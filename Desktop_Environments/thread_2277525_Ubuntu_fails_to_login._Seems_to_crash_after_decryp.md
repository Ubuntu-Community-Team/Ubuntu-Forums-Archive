---
title: "Ubuntu fails to login. Seems to crash after decrypting drive."
date: 2015-05-09
forum: Desktop Environments
---

### Post by curtis16 on 2015-05-09
This doesn't seem to be the typical issue people have with lightdm or gdm. My. Xsession-errors file seems to show that there was an error with an OpenConnection call (no such file or directory) and then it seems that gnome-session crashes (I get a huge and mostly unreadable crash file from that showing that it loads up all the extensions and themes and then crashes.) The lightdm log shows that it can't find configuration session "default" though I have that set to gnome in my Xsessions file. Also my install seems to think it's trisquel...

UPDATE: Besides the weird stuff going with my install misidentifying itself and some devices not getting properly loaded, reinstalling ubuntu-gnome-desktop seems to have done the trick. No idea what caused this problem however.

---

