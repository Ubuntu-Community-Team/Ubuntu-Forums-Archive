---
title: "Run program in wine from Thunar"
date: 2014-10-28
forum: Desktop Environments
---

### Post by peterthebike on 2014-10-28
Is there a way to change the default action in Thunar for a DOS/Windows executable from opening it in Archive Manager to Wine Windows Program Loader?

---

### Post by Toz on 2014-10-28
Right-click the executable and select the "Open with Other Application..." option. In the "Open With" dialog that pops up, ensure that "Use as default for this kind of file" is checked and select "Wine Windows Program Loader". 

From here on in, the wine program loader will become the default for windows executables. To confirm it, view the contents of ~/.local/share/applications/mimeapps.list and you should see something like:
```
application/x-ms-dos-executable=wine.desktop;file-roller.desktop;
```

---

### Post by peterthebike on 2014-10-28
Thanks. I should have remembered that.:oops:

---

