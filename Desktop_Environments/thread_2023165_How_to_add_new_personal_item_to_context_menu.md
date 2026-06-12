---
title: "How to add new personal item to context menu?"
date: 2012-07-12
forum: Desktop Environments
---

### Post by wonkyroger on 2012-07-12
I have created desktop file (like existing desktop files) ~/.local/share/applications/myprogram.desktop
```
[Desktop Entry]
Type=Application
Name=myprogram
MimeType=text/plain;
Exec='/home/user/myprogram' %f
NoDisplay=true
StartupNotify=true
Icon=1E64_myprogram.0
```

And also I have created /usr/share/applications/myprogram.desktop
```
[Desktop Entry]
Name=myprogramm
Name[ru]=&#1052;&#1086;&#1103;&#1055;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1084;&#1072;
Exec=/home/user/myprogram
Terminal=false
Type=Application
Icon=myprogram
```

Nautilus has been restarted. But new item in context menu doesn't appears.
Please help anyone.

---

