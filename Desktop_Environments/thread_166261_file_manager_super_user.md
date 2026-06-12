---
title: "file manager super user"
date: 2006-04-26
forum: Desktop Environments
---

### Post by tattrat on 2006-04-26
Hi all!

Is it possible to run file manager in super user mode? If so, how is it done?

Thank in advance.

---

### Post by Sutekh on 2006-04-26
```
gksudo nautilus
```

---

### Post by tattrat on 2006-04-26
Thank you for the instaneous response!

---

### Post by Sutekh on 2006-04-26
No problem!  It just jumped in my face when I opened the forums :)

---

### Post by index_0@ya.com on 2006-04-26
hi,
is thr anyway to put this as shortcut into the nautilus menu ?


thx..

---

### Post by Sutekh on 2006-04-26
You could try this script.
[url=http://www.ubuntuforums.org/showpost.php?p=117168&postcount=5]
http://www.ubuntuforums.org/showpost.php?p=117168&postcount=5[/url]

It allows you to right-click a  folder and browse as root

Otherwise you could add a GNOME menu entry or a panel launcher.

---

### Post by Efwis on 2006-04-26
to add the shortcut do the following:

   1. Start a new desktop configuration file in the /usr/share/applications directory.
```

sudo gedit /usr/share/applications/Nautilus-root.desktop
```

A blank file called Nautilus-root.desktop opens in gedit.
   2. Add the following lines to the new file:
```

[Desktop Entry]
Name=File Browser (Root)
Comment=Browse the filesystem with the file manager
Exec=gksudo "nautilus --browser %U"
Icon=file-manager
Terminal=false
Type=Application
Categories=Application;System;
```

   3. Save the file and close gedit. 
   4. To start Nautilus as the root user, choose Applications &#8594; System Tools &#8594; File Browser (Root)

Information taken from the Ubuntu 5.10 Starter Guide in the included Help files.

---

