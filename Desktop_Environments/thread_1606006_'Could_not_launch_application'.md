---
title: "'Could not launch application'"
date: 2010-10-26
forum: Desktop Environments
---

### Post by davidmaxwaterman on 2010-10-26
Hi,

I dragged/dropped an icon from one of the menus under 'Applications' onto the top tool bar for quick access, and I also changed the binary it launches by using the icon's 'properties'/'browse' to select the new binary.

The new binary is '/opt/qtsdk-2010.05/bin/qtcreator'. I can run this same command from the command line and it works 'fine' :

```
[07:59][~]$ /opt/qtsdk-2010.05/bin/qtcreator
[08:04][~]$ 
```

I also have another icon next to it for the binary '/opt/qtsdk-2010.05/qt/bin/assistant' - note that it's in the same directory.

Unfortunately, the qtcreator icon won't launch qtcreator, and displays :

```

Could not launch application
Failed to change to directory '/home/davidmaxwaterman/NokiaQtSDK/QtCreator' (No such file or directory)

```

I don't know what relevance that directory is. There's nothing referring to it at all (I even ran qtcreator from the command line under strace and grepped for NokiaQtSDK, but nothing).

If I manually create that directory using 'mkdir -p ~/NokiaQtSDK/QtCreator', then it suddenly works. If I remove it, it stops working,

What gives?

Max.

---

