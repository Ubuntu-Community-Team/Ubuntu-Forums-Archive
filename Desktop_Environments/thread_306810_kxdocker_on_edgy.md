---
title: "kxdocker on edgy"
date: 2006-11-25
forum: Desktop Environments
---

### Post by lobstaman on 2006-11-25
I've been trying to get kxdocker to run under ubuntu 6.10 for some time now. I'm running beryl 0.1.2 which is really excellent. I managed to compile kxdocker from source (from [http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download](http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download)) using the instructions at ([http://www.supriyadisw.net/2006/03/kxdocker-on-dapper-drake)](http://www.supriyadisw.net/2006/03/kxdocker-on-dapper-drake)), which seem to be working well. I am even able to launch kxdocker but I keep getting messages about so files missing and x server errors.

I have searched both this forum and the beryl forum but could not find any solution. I have no idea what are X server errors (I am using an intel i8xx graphics card). I believe its configured correctly since I have no other problems with beryl. 

As for the missing so files, I tried already using the xdocker_conf.xml file found at [http://www.ubuntuforums.org/showthread.php?t=232128](http://www.ubuntuforums.org/showthread.php?t=232128) but with no luck.

BTW - kiba-dock works excellent in 6.10 under beryl 0.1.2!

Any ideas? ](*,)

"############################################
############################################

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
kxdocker: WARNING: loading xml...
kxdocker: WARNING: saving xml configuration to backup configuration...
kxdocker: WARNING: loading external xml configurations: addons_50_configurator.xml
kxdocker: WARNING: loading external xml configurations: addons_90_trayiconlogger.xml
kxdocker: WARNING: loading external xml configurations: sensor_ipcontrack.xml
kxdocker: WARNING: loading plugins...
kxdocker: WARNING: xeplugin_register(xMatrix)
kxdocker: WARNING: xeplugin_register(xConfigurator)
kxdocker: WARNING: xeplugin_register(xGDocker)
kxdocker: WARNING: xeplugin_register(xCommand)
kxdocker: WARNING: xeplugin_register(xARP)
kxdocker: WARNING: xeplugin_register(xTaskManager)
kxdocker: WARNING: xeplugin_register(xMounts)
kxdocker: WARNING: xeplugin_register(xAnimator)
kxdocker: WARNING: xeplugin_register(xMouse)
kxdocker: WARNING: xeplugin_register(DCOP)
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x30001c4
/usr/lib/kxdocker/libTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibTask.so: cannot open shared object file: No such file or directory
kxdocker: WARNING: Plugins loaded:
kxdocker: WARNING: [0] xMatrix
kxdocker: WARNING: [1] xConfigurator
kxdocker: WARNING: [2] xGDocker
kxdocker: WARNING: [3] xCommand
kxdocker: WARNING: [4] xARP
kxdocker: WARNING: [5] xTaskManager
kxdocker: WARNING: [6] xMounts
kxdocker: WARNING: [7] xAnimator
kxdocker: WARNING: [8] xMouse
kxdocker: WARNING: [9] DCOP
kxdocker: WARNING: [10] xTray
kxdocker: WARNING: [11] GIPContrack
kxdocker: WARNING: [12] xPillow
/usr/lib/kxdocker/libGSeparator.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGSeparator.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGSeparator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGSeparator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGSeparator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGSeparator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGSeparator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGSeparator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGSeparator.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGSeparator.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGSeparator.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGSeparator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGSeparator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGSeparator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGSeparator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGSeparator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGSeparator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGSeparator.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGSeparator.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGSeparator.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGSeparator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGSeparator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGSeparator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGSeparator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGSeparator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGSeparator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGSeparator.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
kxdocker: WARNING: Going to background...
aaa@zzz:~$ X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x30003a8
dcop: removing anonymous-27045
kxdocker: WARNING: saving xml configuration..."

---

