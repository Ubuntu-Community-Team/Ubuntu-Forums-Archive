---
title: "kxdocker would not launch on dapper?"
date: 2006-08-08
forum: Desktop Environments
---

### Post by kazuya on 2006-08-08
kxdocker refuses to launch even though I have already installed it as well as the kxdocker-wizard, data, etc.

I have tried from kde and from gnome interface, but no luck. Is there a way I can troubleshoot further.

How should I reinstall it? Could my problem be because I have automatix repo and beerokid repo enabled as well?

---

### Post by wieman01 on 2006-08-08
Could you start it from a terminal ("kxdocker") and post the output please? That'll help.

---

### Post by kazuya on 2006-08-08
thanks I would try that when I get back home today.

---

### Post by kazuya on 2006-08-09
I get this below:

@oris-desktop:~$ kxdocker
Error: KXDocker cannot find Composite Extensions
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kxdocker: WARNING: loading xml...
kxdocker: WARNING: saving xml configuration to backup configuration...
kxdocker: WARNING: loading external xml configurations: addons_50_configurator.xml
kxdocker: WARNING: loading external xml configurations: addons_50_thememanager.xml
kxdocker: WARNING: loading external xml configurations: sensor_gamarok.xml
kxdocker: WARNING: loading external xml configurations: sensor_gapager.xml
kxdocker: WARNING: loading external xml configurations: sensor_gcpu.xml
kxdocker: WARNING: loading external xml configurations: sensor_gdate.xml
kxdocker: WARNING: loading external xml configurations: sensor_gmail.xml
kxdocker: WARNING: loading external xml configurations: sensor_gmount.xml
kxdocker: WARNING: loading external xml configurations: sensor_gnetio.xml
kxdocker: WARNING: loading external xml configurations: sensor_gtrash.xml
kxdocker: WARNING: loading external xml configurations: sensor_ipcontrack.xml
kxdocker: WARNING: loading plugins...
/usr/share/apps/kxdocker/plugins/libxDocker.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxDocker.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxDocker.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxDocker.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxDocker.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxDocker.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxDocker.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxDocker.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxDocker.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxDocker.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxDocker.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxDocker.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxDocker.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxDocker.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxDocker.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxDocker.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxDocker.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxDocker.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxMatrix.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxMatrix.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxMatrix.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxMatrix.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxMatrix.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxMatrix.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxMatrix.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxMatrix.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxMatrix.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxMatrix.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxMatrix.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxMatrix.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxMatrix.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxMatrix.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxMatrix.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxMatrix.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxMatrix.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxMatrix.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxConfigurator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxConfigurator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxConfigurator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxConfigurator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxConfigurator.so: cannot open shared object file: No such file or directory


/usr/share/apps/kxdocker/plugins/liblibKXThemeManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXThemeManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXThemeManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXThemeManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXThemeManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXThemeManager.so.so: cannot open shared object file: No such file or directory
kxdocker: WARNING: Plugins loaded:
kxdocker: WARNING: Going to background...
oris@oris-desktop:~$

---

### Post by wieman01 on 2006-08-10
I remember that I had the same problem initially. So what I did was to remove all unnecessary entries from the kxdocker-config file. The file is here:
> /home/your_user/.kde/share/apps/kxdocker/kxdocker_conf.xml
Could you try the following:

1. Make a safety copy of your xml-config file.
2. Replace your config-file with the one I have enclosed (remove the ".txt" at the end).
3. Restart kxdocker.

Now you should be able run kxdocker and configure it according to your needs. Let me know if you need further help.

---

### Post by kazuya on 2006-08-21
thanks wieman01. You really rock. Even if this fails me somehow, you have thought me something more than I initially asked for. This may help me even better learn where to go to for configuring the file myself to make kxdocker look and act the way I want.

So again, from me.., you rock. I'll try that when I get home today. I have not had internet for like four days now at home.

If I use kxdocker from beerokid, I notice I cannot install kxdocker-data, but everything else, I can install. Is the kxdocker-data required?

---

### Post by wieman01 on 2006-08-22
Glad this thread helpful. Although I am not sure what version of kxdocker you are referring to... I used the one that can be found here:

[http://www.kde-apps.org/content/show.php?content=10958]("http://www.kde-apps.org/content/show.php?content=10958")

Perhaps it helps using the latest version found there if that's not the version you have installed.

Anyway, let us know if this works for you.

---

### Post by kazuya on 2006-09-14
Solved for me. I had already reinstalled Kubuntu, and disabled beerokid repo and reinstalled kxdocker again. with the .39. I shall see what kxdocker I have since upgrading to Kde 3.5.4, which seems snappy to me.

Please SOLVE.

---

### Post by wieman01 on 2006-09-14
Does that mean your problem's solved? Or are you still planning to upgrade to KXDocker v1.x?

---

### Post by daradib on 2006-11-10
I use Edgy Eft and I had an error in kxdocker. (See [http://www.ubuntuforums.org/showthread.php?t=214001&page=2)](http://www.ubuntuforums.org/showthread.php?t=214001&page=2)). wieman01, I used your file and it really works (except the configuration was located in /usr/share/apps/kxdocker/). Thank you so much.

---

### Post by pavel_kbc on 2006-12-04
i am using ubuntu 6.10 edgy(gnome) and i got your conf file . its also has error. wieman01

/usr/share/apps/kxdocker/plugins/libliblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXConfigurator.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXConfigurator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXConfigurator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXConfigurator.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXConfigurator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXConfigurator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
kxdocker: WARNING: xeplugin_register(xGDocker)
kxdocker: WARNING: xeplugin_register(xCommand)
/usr/lib/kxdocker/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
kxdocker: WARNING: xeplugin_register(xAnimator)
kxdocker: WARNING: xeplugin_register(xMouse)
kxdocker: WARNING: xeplugin_register(DCOP)
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x300004e
QObject::connect: No such slot XEPlugin_DCOPBase::xGetParameterList(QStringList*)
QObject::connect:  (sender name:   'xXML')
QObject::connect:  (receiver name: 'DCOP')
kxdocker: WARNING: Plugins loaded:
kxdocker: WARNING: [0] xMatrix
kxdocker: WARNING: [1] xGDocker
kxdocker: WARNING: [2] xCommand
kxdocker: WARNING: [3] xAnimator
kxdocker: WARNING: [4] xMouse
kxdocker: WARNING: [5] DCOP
kxdocker: WARNING: [6] xTray
kxdocker: WARNING: [7] GMail
kxdocker: WARNING: [8] xPillow
kxdocker: WARNING: Going to background...
root@r00t-suck-on-that:/home/r00t-fck# kxdocker: WARNING: saving xml configuration...
Qt-subapplication: Fatal IO error: client killed

root@r00t-suck-on-that:/home/r00t-fck# kxdocker
KXDocker Will use Composite Extensions!
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kxdocker: WARNING: loading xml...
kxdocker: WARNING: saving xml configuration to backup configuration...
kxdocker: WARNING: loading external xml configurations: addons_90_trayiconlogger.xml
kxdocker: WARNING: loading external xml configurations: sensor_gmail.xml
kxdocker: WARNING: loading external xml configurations: sensor_gtrash.xml
kxdocker: WARNING: loading plugins...
kxdocker: WARNING: xeplugin_register(xMatrix)
/usr/lib/kxdocker/liblibKXConfigurator.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXConfigurator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXConfigurator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXConfigurator.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXConfigurator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXConfigurator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXConfigurator.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXConfigurator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXConfigurator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXConfigurator.so.so: cannot open shared object file: No such file or directory
kxdocker: WARNING: xeplugin_register(xGDocker)
kxdocker: WARNING: xeplugin_register(xCommand)
/usr/lib/kxdocker/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
kxdocker: WARNING: xeplugin_register(xAnimator)
kxdocker: WARNING: xeplugin_register(xMouse)
kxdocker: WARNING: xeplugin_register(DCOP)
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x300004e
kxdocker: WARNING: Plugins loaded:
kxdocker: WARNING: [0] xMatrix
kxdocker: WARNING: [1] xGDocker
kxdocker: WARNING: [2] xCommand
kxdocker: WARNING: [3] xAnimator
kxdocker: WARNING: [4] xMouse
kxdocker: WARNING: [5] DCOP
kxdocker: WARNING: [6] xTray
kxdocker: WARNING: [7] GMail
kxdocker: WARNING: [8] xPillow
kxdocker: WARNING: Going to background...
root@r00t-suck-on-that:/home/r00t-fck# X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

---

### Post by wieman01 on 2006-12-04
What version of KXDocker are you using? I hope you have compile from source & have not taken the version that is in the repositories. The latter is a very outdated one, I would not use it (0.39 or so),,, Get the latest one.

---

### Post by negative1 on 2007-05-05
I installed your xml config file in root (it won't let me modify it when using my regular user, which is really irritating.) It loads more icons when I run it in root and the window border is gone, but when I switch back over to my regular username it reverts back to the KDE menu apple penguin with window border.... which really doesnt make any sense. I'm using Fiesty and I've been trying really hard to get kxdocker to work right, but I just can't figure it out. I'm getting the same errors everyone else was getting. I'm running the newest version of kxdocker also and to get it to actually launch I had to apply the debdiff patch that was in response to some other bug.

```


KXDocker Will use Composite Extensions!
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kxdocker: WARNING: Cannot find updated resources: you may need to update or reinstall KXDocker resources, checkout http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources
kxdocker: WARNING: loading xml...
kxdocker: WARNING: saving xml configuration to backup configuration...
kxdocker: WARNING: loading plugins...
/opt/kde/share/apps/kxdocker/plugins/liblibKXDesignPanther.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXDesignPanther.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXDesignPanther.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXDesignPanther.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXDesignPanther.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXDesignPanther.so.so: cannot open shared object file: No such file or directory
kxdocker: WARNING: xeplugin_register(xMatrix)
/opt/kde/share/apps/kxdocker/plugins/liblibKXDockerComposite.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXDockerComposite.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXDockerComposite.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXDockerComposite.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXDockerComposite.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXDockerComposite.so.so: cannot open shared object file: No such file or directory
kxdocker: WARNING: xeplugin_register(xGDocker)
/opt/kde/share/apps/kxdocker/plugins/liblibKXCommand.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXCommand.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXCommand.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXCommand.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXCommand.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXCommand.so.so: cannot open shared object file: No such file or directory
kxdocker: WARNING: xeplugin_register(xCommand)
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXAnimator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXAnimator.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXAnimator.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXAnimator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXAnimator.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXAnimator.so.so: cannot open shared object file: No such file or directory
kxdocker: WARNING: xeplugin_register(xAnimator)
/opt/kde/share/apps/kxdocker/plugins/liblibKXMouse.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMouse.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXMouse.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMouse.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMouse.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXMouse.so.so: cannot open shared object file: No such file or directory
kxdocker: WARNING: xeplugin_register(xMouse)
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
kxdocker: WARNING: Plugins loaded:
kxdocker: WARNING: [0] xMatrix
kxdocker: WARNING: [1] xGDocker
kxdocker: WARNING: [2] xCommand
kxdocker: WARNING: [3] xAnimator
kxdocker: WARNING: [4] xMouse
kxdocker: WARNING: [5] xPillow
kxdocker: WARNING: Going to background...


```

---

