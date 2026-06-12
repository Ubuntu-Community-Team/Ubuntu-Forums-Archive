---
title: "wine services running when using firefox"
date: 2009-06-15
forum: General Help
---

### Post by scrooge_74 on 2009-06-15
I have notice that if I have wine installed and I  use firefox, it will start some processes by itself. Seems to be when ever I enter a page that has flash in it.

 7156 ?        S      0:00 winewrapper.exe --run -- pluginserver.exe --timeout 3
 7159 ?        Ss     0:00 /opt/cxoffice/lib/../bin/wineserver
 7162 ?        Sl     0:00 C:\windows\system32\services.exe                    
 7164 ?        Sl     0:00 C:\windows\system32\winedevice.exe MountMgr         
 7170 ?        Sl     0:00 pluginserver.exe --timeout 300                      
 7172 ?        Ss     0:00 C:\windows\system32\explorer.exe /desktop  

Anybody noticed that? I'm using 8.04 on this PC

---

