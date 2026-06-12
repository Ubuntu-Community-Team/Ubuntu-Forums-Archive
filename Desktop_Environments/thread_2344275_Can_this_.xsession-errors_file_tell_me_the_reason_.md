---
title: "Can this .xsession-errors file tell me the reason my program keeps closing by itself?"
date: 2016-11-23
forum: Desktop Environments
---

### Post by pauldst on 2016-11-23
I am running a video tracking program that closes at the same spot of the video every time I run it. I used ls -lart to find out what file was altered at the moment of the crash and it said it was this .xsession-errors file. I have no idea what the error is trying to tell me and wondered if anyone can tell me what the general problem is. I am also running Ubuntu 12.04 because that is the only version that the software is compatible with.

```

gnome-session[1101]: WARNING: Session 'ubuntu' runnable check failed: Exited with code 1
unity-2d-panel: [DEBUG] Scanning panel plugin directory "/usr/lib/unity-2d/plugins/panel" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-appindicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-appname.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-indicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-legacytray.so" 
unity-2d-shell: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core pointer 
unity-2d-shell: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core keyboard 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-separator.so" 
unity-2d-panel: [DEBUG] Configured plugins list is: ("appname", "!legacytray", "indicator") 
** Message: applet now removed from the notification area
unity-2d-shell: [DEBUG] static void WindowImageProvider::activateComposite(): Server supports the Composite extension (ver 0.4)
** Message: using fallback from indicator to GtkStatusIcon
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+S" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+T" 
unity-2d-panel: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core pointer 
unity-2d-panel: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core keyboard 
unity-2d-panel: [WARNING] X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 18 (X_ChangeProperty)
  Resource id:  0x0
unity-2d-panel: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F10" 
** Message: moving back from GtkStatusIcon to indicator
unity-2d-shell: [WARNING] Object::connect: No such signal Lenses::roleNamesChanged(QHash<int,QByteArray>) in /build/buildd/unity-2d-5.12.0/libunity-2d-private/src/qsortfilterproxymodelqml.cpp:65
unity-2d-shell: [WARNING] void QSortFilterProxyModelQML::setSourceModelQObject(QObject*): received a sourceModel that does not notify of changes of its roleNames 
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

unity-2d-shell: [WARNING] file:///usr/share/unity-2d/shell/hud/Hud.qml:145: TypeError: Result of expression 'shellManager.hudShell' [null] is not an object.
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+0" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+0" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+3" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+3" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+4" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+4" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+5" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+5" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+6" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+6" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+7" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+7" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+8" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+8" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+9" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+9" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://nautilus.desktop" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://nautilus.desktop" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+A" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+F" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+M" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+V" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://empathy.desktop" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://empathy.desktop" 

** (zeitgeist-datahub:2209): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application62801462") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application62801462") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application62801462") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application62801462") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application62801462") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application62801462") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application62801462") 
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
unity-2d-shell: [WARNING] Wnck: Received a timestamp of 0; window activation may not function properly.

Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2a006a4 (Biotrack_P)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

** (update-notifier:2305): WARNING **: log file empty (logrotate?) /var/log/dpkg.log


** (update-notifier:2305): WARNING **: log file empty (logrotate?) /var/log/apt/term.log

unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application829906520") 
QMetaObject::connectSlotsByName: No matching signal for on_blobBirthAreaThresholdSpinBox_valueChanged(int)
unity-2d-shell: [WARNING] libindicator: Unable to load keyfile from file '': No such file or directory
OpenCV Error: Sizes of input arguments do not match (The operation is neither 'array op array' (where arrays have the same size and the same number of channels), nor 'array op scalar', nor 'scalar op array') in arithm_op, file /home/biotracking/Downloads/OpenCV-2.4.3/modules/core/src/arithm.cpp, line 1273
Qt has caught an exception thrown from an event handler. Throwing
exceptions from an event handler is not supported in Qt. You must
reimplement QApplication::notify() and catch all exceptions there.

terminate called after throwing an instance of 'cv::Exception'
  what():  /home/biotracking/Downloads/OpenCV-2.4.3/modules/core/src/arithm.cpp:1273: error: (-209) The operation is neither 'array op array' (where arrays have the same size and the same number of channels), nor 'array op scalar', nor 'scalar op array' in function arithm_op

unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0xdc1ad0") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xdc1ad0") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xdc1ad0") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xdc1ad0") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xdc1ad0") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0xdc1ad0") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xdc1ad0") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xdc1ad0")
```

---

### Post by QIII on 2016-11-23
Hello!

Please use default font, weight and color unless there is a good reason to draw particular attention to a portion of your post.

Also use code tags around text returned by the terminal.

To use code tags you may:

1.  Click the # button above the text entry box, place your cursor between the code tags and add your text.

2.  Add your text, highlight it and then click the # button.

3.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.

Thanks.

---

### Post by ajgreeny on 2016-11-23
You may get some more information about the problem if you open the video-player application using terminal code, eg if using vlc ```
vlc /path/to/videofile
```
Could also be related to this bug which seems to not be squashed so far.

---

### Post by pauldst on 2016-11-25
The video itself runs fine. It's when i put the video in the tracking program. How would I find out more information about the problem by opening it in terminal?

---

