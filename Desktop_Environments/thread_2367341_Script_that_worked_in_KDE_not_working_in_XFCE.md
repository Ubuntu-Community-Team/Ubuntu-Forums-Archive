---
title: "Script that worked in KDE not working in XFCE"
date: 2017-07-29
forum: Desktop Environments
---

### Post by accounts0 on 2017-07-29
I had this script working in KDE:

```
#!/bin/bash
sleep 15
amixer -D pulse sset Master 24%
exec /usr/bin/amarok -l "/home/cb/Music/WebRadio/SomaFM_GrooveSalad.pls"
qdbus org.kde.amarok /Player org.freedesktop.MediaPlayer.VolumeSet 100
qdbus org.kde.amarok /amarok/MainWindow org.qtproject.Qt.QWidget.hide

```

When I try to run it in XFCE, with qdbus installed but not qdbus-qt5, I get these errors:

```

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 15729 [24%] [on]
  Front Right: Playback 15729 [24%] [on]
Cannot find 'org.freedesktop.MediaPlayer.VolumeSet' in object /Player at org.kde.amarok
Service 'org.kde.amarok' does not exist.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
amarok(6175)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:


(amarok:6175): Gtk-WARNING **: Theme directory  of theme oxygen has no size field


QWidget::insertAction: Attempt to insert null action
amarok(6175)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (0,-1) are not possible
Could not parse stylesheet of widget 0x2e41f680
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (200,-1) are not possible
********************************************************************************************** 
** AMAROK WAS STARTED IN NORMAL MODE. IF YOU WANT TO SEE DEBUGGING INFORMATION, PLEASE USE: ** 
** amarok --debug                                                                           ** 
********************************************************************************************** 
cb@Triborough:~/Scripts$ QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
Calling appendChild() on a null node does nothing.
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.

```

And if I install both qdbus & qdbus-qt5 I get these errors:

```

[FONT=monospace][COLOR=#000000]Simple mixer control 'Master',0[/COLOR]
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 15729 [24%] [on]
  Front Right: Playback 15729 [24%] [on]
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
amarok(6852)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:

(amarok:6852): Gtk-WARNING **: Theme directory  of theme oxygen has no size field

QWidget::insertAction: Attempt to insert null action
amarok(6852)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (0,-1) are not possible
Could not parse stylesheet of widget 0x2e1eae50
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (200,-1) are not possible
**********************************************************************************************  
** AMAROK WAS STARTED IN NORMAL MODE. IF YOU WANT TO SEE DEBUGGING INFORMATION, PLEASE USE: **  
** amarok --debug                                                                           **  
**********************************************************************************************  
cb@Triborough:~/Scripts$ QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (200,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (200,-1) are not possible
Calling appendChild() on a null node does nothing.
amarok(6852)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(6852)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(6852)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
Calling appendChild() on a null node does nothing.
[/FONT]
```

---

### Post by accounts0 on 2017-07-29
Now after a reboot I'm able to run the qdbus commands successfully one at a time in konsole, but they won't run in my script- even with adding 'sleep 15' between them.


Here is my script:


```

#!/bin/bash
sleep 15
amixer -D pulse sset Master 24%
sleep 5
exec /usr/bin/amarok --debug -l "/home/cb/Music/WebRadio/SomaFM_GrooveSalad.pls"
sleep 5
qdbus org.kde.amarok /Player org.freedesktop.MediaPlayer.VolumeSet 100
sleep 5
qdbus org.kde.amarok /amarok/MainWindow org.qtproject.Qt.QWidget.hide

```


And this is the debug output when it fails to execute the commands in the script:
[http://sebsauvage.net/paste/?373310867f3aaa0e#m8A8xwNZ99fnpVXXAMBOMTYPukVJR3k6Ryk2JHHrZO4=](http://sebsauvage.net/paste/?373310867f3aaa0e#m8A8xwNZ99fnpVXXAMBOMTYPukVJR3k6Ryk2JHHrZO4=)




Not sure how to proceed, help is appreciated.

---

