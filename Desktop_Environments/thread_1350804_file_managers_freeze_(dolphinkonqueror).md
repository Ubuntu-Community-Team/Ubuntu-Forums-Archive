---
title: "file managers freeze (dolphin/konqueror)"
date: 2009-12-09
forum: Desktop Environments
---

### Post by Tagi on 2009-12-09
Every time I try to run dolphin or konqueror they freeze and I have to terminate their processes. Konqueror works fine as a web browser only managing files freezes it.
 
Konsole:
$ dolphin
kbuildsycoca4 running...
"KConfigIni: In file /usr/share/applications/wine-browsedrive.desktop, line 2: " "Invalid escape sequence "\ "."
"KConfigIni: In file /usr/share/applications/wine-browsedrive.desktop, line 5: " "Invalid escape sequence "\-"."
"KConfigIni: In file /usr/share/applications/wine-browsedrive.desktop, line 8: " "Invalid escape sequence "\ "."
"KConfigIni: In file /usr/share/applications/wine-browsedrive.desktop, line 11: " "Invalid escape sequence "\-"."
QBuffer::seek: Invalid pos: 1677751040
QBuffer::seek: Invalid pos: 1845519360
QBuffer::seek: Invalid pos: 1627419136
QBuffer::seek: Invalid pos: 1677751040

$ konqueror
kbuildsycoca4 running...
"KConfigIni: In file /usr/share/applications/wine-browsedrive.desktop, line 2: " "Invalid escape sequence "\ "."
"KConfigIni: In file /usr/share/applications/wine-browsedrive.desktop, line 5: " "Invalid escape sequence "\-"."
"KConfigIni: In file /usr/share/applications/wine-browsedrive.desktop, line 8: " "Invalid escape sequence "\ "."
"KConfigIni: In file /usr/share/applications/wine-browsedrive.desktop, line 11: " "Invalid escape sequence "\-"."
QBuffer::seek: Invalid pos: 1677751040
QBuffer::seek: Invalid pos: 1677751040
QBuffer::seek: Invalid pos: 1845519360
QBuffer::seek: Invalid pos: 1627419136
QBuffer::seek: Invalid pos: 1677751040
QBuffer::seek: Invalid pos: 1677751040
QBuffer::seek: Invalid pos: 1677751040


I am running Kubuntu 9.10 / kde 4.3.2

---

### Post by SuperSonic4 on 2009-12-09
Does it freeze when you're trying to move about and highlight files? I remember having much the same problem (dolphin would freeze but would come back) in KDE 4.3.x

Thankfully this is no longer the case in KDE 4.4

---

### Post by Tagi on 2009-12-11
Yes dolphin and konqueror freeze when I move my pointer over file or folder icon. I updated my KDE to version 4.3.4 but it didn't help. Is there any other option to fix this than updating the KDE to version 4.4. I am little uncertain on updating and even kde.org says: "4.4 is not stable software, as such, it is not suitable for everyday or production use."

---

