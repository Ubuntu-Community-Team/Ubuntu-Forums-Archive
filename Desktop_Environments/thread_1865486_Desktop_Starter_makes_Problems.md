---
title: "Desktop Starter makes Problems"
date: 2011-10-20
forum: Desktop Environments
---

### Post by SeaKing on 2011-10-20
Hey,
I have a problem with creating a desktop starter, it gives me the response that the starter starts a not relaiable application. 

starter: eclipse.desktop

content:
```

[Desktop Entry]
Version=1.0
Name=Eclipse
Comment=Eclipse INDIGO
Exec=~/bin/start_eclipse.sh
Icon=~/opt/eclise/icon.xpm
Terminal=false
Type=Application
Categories=Application

```eclipse itself is running fine.

---

### Post by gsmanners on 2011-10-20
> **SeaKing said:**
> Hey,
```

Exec=~/bin/start_eclipse.sh
Icon=~/opt/eclise/icon.xpm

```

You sure those paths are right?

---

### Post by SeaKing on 2011-10-26
Yes, I've installed it manually. If I exchange ~ with /home/user it works. Now I have the problem, if I use drag and drop to put it in unity launcher and delete the desktop  icon the unity icon disappears as well.

---

### Post by gsmanners on 2011-10-26
I suspect putting it into the launcher only created a symbolic link to it, so when you then deleted the desktop file, it of course deleted the launcher icon. I don't suppose you could create the desktop file in like ~/Documents, open that folder and drag it from there to the launcher (I really have no idea, since I've never tried that and I'm not going to be using Unity for at least another couple weeks.)

---

