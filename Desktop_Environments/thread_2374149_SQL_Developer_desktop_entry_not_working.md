---
title: "SQL Developer desktop entry not working"
date: 2017-10-13
forum: Desktop Environments
---

### Post by sigmano on 2017-10-13
I have created a desktop entry for SQL Developer:

```

[Desktop Entry] Type=Application
Terminal=false
Name=SQL Developer
Icon=/usr/lib/sqldeveloper/icon.png
Exec=/usr/lib/sqldeveloper/sqldeveloper.sh
```

File info:
```
ls -l /usr/share/applications/sqldeveloper.desktop
-rw-r--r-- 1 sindre sindre 0 okt.  13 08:27 /usr/share/applications/sqldeveloper.desktop

```

When I click "Search" I cant se the desktop entry. When I click it SQL manager icons goes to the launcher desktops, then disappears after a couple of seconds.

I can start SQL manager with */usr/lib/sqldeveloper/sqldeveloper.sh *without any problems.

---

