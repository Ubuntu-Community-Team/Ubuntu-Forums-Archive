---
title: "Servicemenu - Dolphin - KDE3"
date: 2008-05-28
forum: Desktop Environments
---

### Post by anywebloco on 2008-05-28
Does anyone know how I can create a servicemenu in d3lphin that will move files in the way that the desktop rightclick menu does?

**Solved**

[Desktop Entry]
ServiceTypes=all/allfiles,inode/directory
Actions=MoveTo
Encoding=UTF-8

[Desktop Action MoveTo]
Name=Move To
Icon=folder_red_open
Exec=mv %F `kdialog --getexistingdirectory ~/`

Credit to [http://kubuntuforums.net/forums/index.php?topic=3088743.0](http://kubuntuforums.net/forums/index.php?topic=3088743.0)

---

