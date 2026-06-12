---
title: "Apps not appearing as GUI or in panel"
date: 2008-02-14
forum: Desktop Environments
---

### Post by bigred1 on 2008-02-14
My Ubuntu Gutsy Gibbon 7.1 was working fine, but recently, when I launch an app (including KTorrent and Ekiga), its  Gui does not appear, and there is no icon for the app ni the panel- 

However, *ps -A* does show that the apps exist.

I tried *kill* on the app by its process number, then  restarting it; I also tried  switching "workspaces",  and even restarting the computer, but nothing helps. 

Something is keeping the apps from appearing in the GUI -- so I have no way to access them.

---

### Post by avdzm on 2008-02-14
try running ktorrent n ekiga,
or which ever program u have a problem with in terminal

the error will most likely be reported there

---

### Post by bigred1 on 2008-02-15
OK, I tried this, and Ekiga runs with GUI -- but there is still no icon in the panelwhich would  allow me to recall it once I have minimized it.

Yet running KTorrent from the command line gives the same effect as from the Appplications menu on the panel -- There is no KTorrent GUI, and no icon in the panel, even though   *ps -A* shows that it is running.

The command line output from ktorrent execution is below.

 ```

ask@ask-desktop:/usr/bin$ ktorrent 
ktorrent is already running!
ask@ask-desktop:/usr/bin$ ps -A |grep ktorrent
 6786 ?        00:00:18 ktorrent
ask@askdesktop:/usr/bin$ kill 6786
ask@ask-desktop:/usr/bin$ ktorrent 
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
ask@ask-desktop:/usr/bin$ 
ask@ask-desktop:/usr/bin$ ps -A |grep ktorrent
 7402 pts/0    00:00:18 ktorrent
ask@ask-desktop:/usr/bin$ 
 
```

---

### Post by queency on 2008-07-22
rm .kde/share/config/ktorrentrc

thats worked for me

---

