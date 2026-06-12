---
title: "Something has changed in the .desktop files..."
date: 2016-02-11
forum: Desktop Environments
---

### Post by actionmystique on 2016-02-11
Hello guys,


I've been successfully using the following /usr/share/applications/gns3.desktop for quite some time in Ubuntu 15.10:
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
TryExec=gns3
Exec=gns3 %f
Name=GNS3
Comment=GNS3 Graphical Network Simulator
Icon=/usr/share/icons/GNS3/gns3.ico
Categories=Education;
MimeType=application/x-gns3;
GenericName[en_US]=Graphical Network Simulator
```
However,  launching GNS3 by double-clicking that file has stopped working for a few weeks, following some unknown package update:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=267234&stc=1[/IMG]
Of course, gns3 is launched correctly from the CLI.  The permissions are OK.
I'm experiencing the same issue with all other self-made desktop files, so it is not linked to GNS3, but to some field inside the desktop file.
Has anybody some insight regarding what Canonical has changed in the meantime?

---

### Post by actionmystique on 2016-02-12
**desktop-file-validate gns3.desktop** indicates no error nor warning.

However, if I change "Exec=gns3" by "Exec=/usr/local/bin/gns3", now it works.
Here's the strange part:
```
root@samsung-ubuntu:/ #env | grep -i path
PATH=/usr/local/ssl/bin:/usr/local/sbin:**/usr/local/bin**:/usr/sbin:/usr/bin:/usr/games:/sbin:/bin
```
So, the path is already set correctly, but this issue must have something to do with the fact that I launch it through Nemo run as root.
If I launch it through nemo as non-root, the application starts normally.
Since I haven't changed the contents of the .desktop files, **something has changed in the way the environment is passed - or not passed should I say - during that call**.

There is another issue with some other desktop files even when they are launched as a non-root user.
For example, **Android SDK Manager**:
```
[Desktop Entry]
Version=1.0
Name=Android SDK Manager
Type=Application
Comment=Android SDK Manager
Terminal=true
**Exec=/home/actionmystique/Program-Files/Ubuntu/android-sdk/tools/android**
Icon=/home/actionmystique/Program-Files/Ubuntu/android-sdk/docs/images/tools/sdk-manager-studio.png
Categories=ConsoleOnly;System;
GenericName=Memory Viewer
```

The program has the right permissions:
```
ll android -rwxr-xr-x 1 actionmystique actionmystique 3498 Dec 13 11:46 android

```
But, it cannot be launched from within Nemo nor Nautilus. Nothing happens this time, no error windows pops up.
If I launch it from the CLI, it works fine, but the common following error show up in the terminal:
```
./android (Android SDK Manager:25981): GLib-CRITICAL **: Source ID 89 was not found when attempting to remove it
``` 
**Does that mean that now, launching apps through their desktop file cannot tolerate errors or warnings during the call**?
This error has always been there and it used to be possible to run the app from the desktop file.

Same issue with **Smartgit **which cannot be run from Nemo nor Nautilus but can be launched from the CLI:
```
./smartgit.sh 
Java HotSpot(TM) 64-Bit Server VM warning: You have loaded library /home/actionmystique/.smartgit/7/jna-tmp/com/sun/jna/linux-x86/libjnidispatch.so which might have disabled stack guard. The VM will try to fix the stack guard now.
It's highly recommended that you fix the library with 'execstack -c <libfile>', or link it with '-z noexecstack'.
```

**As a summary, the way applications can be run from their desktop files has been modified and some extremely tight controls have been added making the whole process impossible for some programs. Too much control kills....**

---

### Post by ian-weisser on 2016-02-12
gns3: It is unwise and unsafe to assume that a different environment (root) will automatically inherit variables from a different environment (user).
There are too many places and processes that can override the environment variables, leading to unexpected consequences...or a crash.

Android SDK: Seems like a different issue. Consider filing a bug report for that warning.

Smartgit: Seems like a different issue from the other two. Have you tested the solution that the warning recommends? Consider filing a bug (and patch) for the issue.

---

