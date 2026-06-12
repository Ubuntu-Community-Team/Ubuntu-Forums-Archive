---
title: "Need help on how to run WoW off windows"
date: 2008-12-21
forum: General Help
---

### Post by Scytes on 2008-12-21
IF any has a guide, or can help me please do. I have tried going through wine explorer then to the Z:\mnt\windows and there is nothing there.

---

### Post by GreenM on 2008-12-21
There should be a .wine/drive_c folder in your home.

I think this should work.
```

wine "c:\Frogram Files\World of Warcraft\wow.exe" -opengl

```

If that's not the right installation directory, go to the drive_c directory and browse around.

Might need to make a few tweaks, [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154) for more information.

---

