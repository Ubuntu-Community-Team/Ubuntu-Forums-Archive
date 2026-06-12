---
title: "QNativeImage: Unable to attach to shared memory segment on KDE QT application"
date: 2015-11-12
forum: Desktop Environments
---

### Post by baskar007 on 2015-11-12
Hi All,

Just 1 week before I updated my 14.04 kubuntu to 15.10 (no pure update, clean install)

Everything looks/works good.

It seems like I am facing QT related bug in app KDE+QT based apps.

I am getting following error & grey screen when opening apps like Klog, qBittorrent, kdialog etc... 

```

[FONT=monospace][COLOR=#000000]QNativeImage: Unable to attach to shared memory segment.  [/COLOR]
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
QNativeImage: Unable to attach to shared memory segment.  
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0

[/FONT]
```


Regarding grey screen please find attached screenshot with this post.

[ATTACH=CONFIG]265514[/ATTACH]

Do any one know solutions for this issue ?

Thanks in advance.

Baskar M.

---

### Post by baskar007 on 2015-11-12
Hi ,

Finally I can fix this issue by disabling MITSHM lib.

This can be done by adding following line to ~/.profile file. (ie: system env var)

[B]QT_X11_NO_MITSHM=1


Thanks.


[/B]

---

