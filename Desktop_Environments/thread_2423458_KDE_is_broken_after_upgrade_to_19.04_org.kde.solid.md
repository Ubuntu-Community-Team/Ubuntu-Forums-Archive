---
title: "KDE is broken after upgrade to 19.04: org.kde.solid.udisks2: Error getting props"
date: 2019-07-23
forum: Desktop Environments
---

### Post by aleks2 on 2019-07-23
After upgrade to 19.04 KDE doesn't start, just blank screen freeze. When starting KDevelop from lxde it freezes also and slowly floods the following in terminal:
```
`aa``
org.kde.solid.udisks2: Error getting props: "org.freedesktop.DBus.Error.NoReply" "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."
org.kde.solid.udisks2: Error getting props: "org.freedesktop.DBus.Error.NoReply" "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."
org.kde.solid.udisks2: Error getting props: "org.freedesktop.DBus.Error.NoReply" "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."
...
```
```
It's worth to mention that SDDM is also broken: it just freezes without entering to graphics mode. LXDM starts though.


After ~10 minutes it finally started:
```
```
org.kde.solid.udisks2: Error getting props: "org.freedesktop.DBus.Error.NoReply" "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."
kdeinit5: preparing to launch '/usr/lib/x86_64-linux-gnu/libexec/kf5/klauncher'
kdeinit5: Launched KLauncher, pid = 29609, result = 0
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kdeinit5: opened connection to :0.0
kdeinit5: Got EXEC_NEW '/usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kio/man.so' from launcher.
kdeinit5: preparing to launch '/usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kio/man.so'
log_kio_man: STARTING
kdeinit5: Got EXEC_NEW '/usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kio/file.so' from launcher.
kdeinit5: preparing to launch '/usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kio/file.so'
log_kio_man: QUrl("man://")
kdeinit5: Got EXEC_NEW '/usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kio/file.so' from launcher.
kdeinit5: preparing to launch '/usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kio/file.so'
log_kio_man: After if
log_kio_man: After if
log_kio_man: After if
...
```
```

---

### Post by wildmanne39 on 2019-07-23
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by aleks2 on 2019-07-24
Solved after upgrade Plasma to 5.16:


[http://ubuntuhandbook.org/index.php/2019/06/install-kde-plasma-desktop-5-16-kubuntu-19-04/](http://ubuntuhandbook.org/index.php/2019/06/install-kde-plasma-desktop-5-16-kubuntu-19-04/)

---

