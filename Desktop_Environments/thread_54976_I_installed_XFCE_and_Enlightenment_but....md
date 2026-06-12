---
title: "I installed XFCE and Enlightenment but..."
date: 2005-08-07
forum: Desktop Environments
---

### Post by MkIII_Supra on 2005-08-07
I can't find the entries on the selection menu when I log in. And I can't remember what file to edit or where it is. Guess I got spoiled by SuSE. So can someone please tell me which file and where? I know what to do once there... I think!

---

### Post by jyank on 2005-08-07
Try this:

```
 sudo gedit /usr/share/xsessions/
```

Add

```

 [Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=
Exec=enlightenment
Icon=
Type=Application

```

Do the same for XFCE, but replace enlightenment

---

