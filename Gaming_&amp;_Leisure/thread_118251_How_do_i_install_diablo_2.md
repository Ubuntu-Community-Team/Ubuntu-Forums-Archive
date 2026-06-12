---
title: "How do i install diablo 2??"
date: 2006-01-16
forum: Gaming &amp; Leisure
---

### Post by REXXER on 2006-01-16
As i said in the title, i have NO IDEA how to install diablo 2 (or any other game for that matter), using wine, HELP!

REXXER

---

### Post by tszanon on 2006-01-16
First time you run wine, it creates a folder ~/.wine. There you can find a subfolder called dosdevices, where there is a c: link (pointing to ~/.wine/drive_c) and z: link (pointing to /). There you should create a d: link (or any letter Windows can recognize as a CD-drive):

```
cd ~/.wine/dosdevices
ln -s /media/cdrom d:
```

Then, insert the installation cd. Type
```
cd ~/.wine/dosdevices/d:
wine Setup.exe
```

And there it is. :-) You probably will need to run winecfg in order to make everything work fine.
You can also check [http://www.winehq.com]("http://www.winehq.com"), section Application DB. Search for Diablo 2. There you will find some solutions to common problems.

---

