---
title: "How to Launch KXDocker1.1.4a"
date: 2006-09-27
forum: Desktop Environments
---

### Post by spacecowboy706 on 2006-09-27
Ubuntu 6.06 with Gnome

I just installed KXDocker1.1.4a by following this guide:

[http://www.supriyadisw.net/2006/03/kxdocker-on-dapper-drake](http://www.supriyadisw.net/2006/03/kxdocker-on-dapper-drake)

everything went smoothly and passed and installed correctly (meaning I didn't get any error messages). I installed the following components:

kxdocker-resources-version.x.x.tar.bz2
kxdocker-configurator-version.x.x.tar.bz2
kxdocker-dcop-version.x.x.tar.bz2
kxdocker-i18n-version.x.x.tar.bz2
kxdocker-trayiconlogger-version.x.x.tar.bz2
kxdocker-taskmanager-version.x.x.tar.bz2
kxdocker-thememanager-version.x.x.tar.bz2
kxdocker-wizard-version.x.x.tar.bz
kxdocker-networker-version.x.x.tar.bz2
kxdocker-gtrash-version.x.x.tar.bz2
kxdocker-gdate-version.x.x.tar.bz2

In the following directory: /myname/Downloads/Software/KXDOCKER

making sure to 1)tar jxvf, 2)cd, 3)Compile, 4)Make, and 5)sudo make install, each and everyone of these.

at the end of the "How-To" it says that all i have to do to launch the Docker is type in: kxdocker ... from the terminal and the application will launch. after typing this in, if i go to System - Preferrences - Sessions -  then click on the Current Session tab, at the bottom of the list it says KXdocker (doesnt that mean that it is working)... it will also put a little penguine icon on the top bar... but I cnat find the dock anywhere. back to the Terminal after i had typed in kxdocker, i get the following:

myname@myname-desktop:~$ kxdocker
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
kbuildsycoca running...
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
kxdocker: WARNING: loading external xml configurations: addons_70_networker.xml
kxdocker: WARNING: loading external xml configurations: addons_90_trayiconlogger.xml
kxdocker: WARNING: loading external xml configurations: sensor_gdate.xml
kxdocker: WARNING: loading external xml configurations: sensor_gtrash.xml
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
/opt/kde/share/apps/kxdocker/plugins/liblibxConfigurator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxConfigurator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxConfigurator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxConfigurator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxConfigurator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxConfigurator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxConfigurator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxConfigurator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxConfigurator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxConfigurator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxConfigurator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxConfigurator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxConfigurator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTray.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTray.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxTray.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTray.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTray.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxTray.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTray.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTray.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxTray.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTray.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTray.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxTray.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTray.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTray.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxTray.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTray.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTray.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxTray.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxXML.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxXML.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxXML.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxXML.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxXML.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxXML.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxXML.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxXML.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxXML.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxXML.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxXML.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxXML.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxXML.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxXML.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxXML.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxXML.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxXML.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxXML.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxCommand.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxCommand.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxCommand.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxCommand.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxCommand.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxCommand.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxCommand.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxCommand.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxCommand.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxCommand.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxCommand.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxCommand.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxCommand.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxCommand.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxCommand.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxCommand.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxCommand.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxCommand.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxARP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxARP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxARP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxARP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxARP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxARP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxARP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxARP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxARP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxARP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxARP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxARP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxARP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxARP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxARP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxARP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxARP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxARP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTaskManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTaskManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxTaskManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTaskManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTaskManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxTaskManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTaskManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTaskManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxTaskManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTaskManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTaskManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxTaskManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTaskManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTaskManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxTaskManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTaskManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTaskManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxTaskManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxMounts.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxMounts.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxMounts.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxMounts.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxMounts.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxMounts.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxMounts.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxMounts.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxMounts.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxMounts.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxMounts.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxMounts.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxMounts.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxMounts.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxMounts.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxMounts.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxMounts.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxMounts.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxAnimator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxAnimator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxAnimator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxAnimator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxAnimator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxAnimator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxAnimator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxAnimator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxAnimator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxAnimator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxAnimator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxAnimator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxAnimator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxAnimator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxAnimator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxAnimator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxAnimator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxAnimator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxMouse.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxMouse.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxMouse.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxMouse.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxMouse.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxMouse.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxMouse.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxMouse.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxMouse.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxMouse.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxMouse.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxMouse.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxMouse.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxMouse.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxMouse.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxMouse.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxMouse.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxMouse.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libDCOP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libDCOP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibDCOP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libDCOP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libDCOP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibDCOP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libDCOP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libDCOP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibDCOP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libDCOP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libDCOP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibDCOP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libDCOP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libDCOP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibDCOP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libDCOP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libDCOP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibDCOP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXThemeManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXThemeManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXThemeManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXThemeManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXThemeManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXThemeManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXThemeManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXThemeManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXThemeManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXThemeManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXThemeManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXThemeManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXThemeManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXThemeManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXThemeManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXThemeManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXThemeManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXThemeManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXNetworker.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXNetworker.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXNetworker.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXNetworker.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXNetworker.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXNetworker.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXNetworker.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXNetworker.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXNetworker.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXNetworker.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXNetworker.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXNetworker.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXNetworker.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXNetworker.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXNetworker.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXNetworker.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXNetworker.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXNetworker.so.so: cannot open shared object file: No such file or directory
kxdocker: WARNING: Plugins loaded:
kxdocker: WARNING: Going to background...

Just out of curiosity, is the launcher unable to open the needed files because of the whole password thing i have to type in all the time or did my install not install correctly? I am still on my first week with linux and am very unsure where to proceed from here as i cant find anything about this through google or jeeves. please help.

---

### Post by wieman01 on 2006-09-28
You can try this thread which also includes a sample Config-file for KXDocker. This is a common problem which you should be able to resolve:

[http://www.ubuntuforums.org/showthread.php?t=232128]("http://www.ubuntuforums.org/showthread.php?t=232128")

---

### Post by spacecowboy706 on 2006-09-28
I followed that thread like you instructed and I am now up and working. Many Many thanks for your help.

---

### Post by wieman01 on 2006-09-28
> **spacecowboy706 said:**
> I followed that thread like you instructed and I am now up and working. Many Many thanks for your help.
You're welcome. Let me know if you need help with other nice-to-haves. :-)

---

### Post by spacecowboy706 on 2006-09-28
I have figured out how to add icons just by draggging and dropping them onto the bar and that works fine.... but there are these 5 icons that look like cat5 ends that says: LO, Eth0, Ra0, RaUsb0, Sit0 above them...and i cant figure out how to delet them.

If i just right click and select Remove Now then they will disappear for about 15 or 20 seconds then reappear again. they are on the right side of the dock next to the other programs thatr are running.

How do I get rid of these please?

---

### Post by wieman01 on 2006-09-28
Yes, these are your network devices. For some reason KXDocker does that. I would suggest taking a look at your XML file & eliminating the corresponding lines (if you can find them).

If this does not help, just post your XML config file and I'll see what I can do. How does that sound?

---

### Post by spacecowboy706 on 2006-09-28
Yeh i was stupid on adding icons also.. theres more to that than i thought and I'm learning all that now (which is why i came to linux... cause im so bored on windows) ... but for the cat5 connectors here is the xml file you requested as i dont know what to remove... if you could just give me a briefe explanation of what needs to be removed then just highlight the remove part of it (SO I CAN LEARN) I would be grateful.

here it is:  Would i just delete the Bold section>

<kxdocker version="1.1.4a">
&#8722;
	<general>
<engine InterpolationValue="2" SleepFPS="5000" SleepThreads="1000" MaxIconsShowed="50" SmoothTimeout="25" SleepAnimations="250" AutoResize="1" AutoSave="1" xmlconf="/home/dennis/.kde/share/apps/kxdocker/kxdocker_conf.xml" AndZoomCache="0"/>
&#8722;
	<plugins>
&#8722;
	<plugin name="xMatrix" filename="libKXDesignPanther.so">
<pluginconf/>
</plugin>
&#8722;
	<plugin name="xGDocker" filename="libKXDockerFake.so">
<pluginconf/>
</plugin>
&#8722;
	<plugin name="xCommand" filename="libKXCommand.so">
<pluginconf onClickLeft="popup" onClickMiddle="exec"/>
</plugin>
&#8722;
	<plugin name="xARP" filename="libKXARPManager.so">
<pluginconf AutoAddMounts="yes"/>
</plugin>
&#8722;
	<plugin name="xTaskManager" filename="libKXTaskManager.so">
<pluginconf showWindowsOnlyFromThisDesktop="1" autoAddSeparator="1" fadeMinimized="1" showGroupWindows="1" thumbnailShowIcon="1"/>
</plugin>
&#8722;
	<plugin name="xMounts" filename="libKXMountManager.so">
<pluginconf AutoAddMounts="yes"/>
</plugin>
&#8722;
	<plugin name="xAnimator" filename="libKXAnimator.so">
<pluginconf BounceHigh="200" onClickAnimation="overlay" onRaiseAnimation="micro" onCloseAnimation="poof" onShowAnimation="fade" onHideAnimation="fade"/>
</plugin>
&#8722;
	<plugin name="xMouse" filename="libKXMouse.so">
<pluginconf onRIGHT="" onLEFT="" onBOTTOMRIGHT="0" onBOTTOMLEFT="0" onTOPRIGHT="0" onTOPLEFT="0"/>
</plugin>
&#8722;
	<plugin name="DCOP" filename="libXEPlugin_DCOP.so">
<pluginconf/>
</plugin>
&#8722;
	<plugin name="xConfigurator" filename="libKXConfigurator.so">
<pluginconf/>
</plugin>
&#8722;
	<plugin name="xThemeManager" filename="libKXThemeManager.so">
<pluginconf password="" lasttheme="" username=""/>
</plugin>
&#8722;
	<plugin name="xNetworker" filename="libKXNetworker.so">
<pluginconf showControlIcon="0"/>
</plugin>
&#8722;
	<plugin name="xTray" filename="libXEPlugin_TrayIcon.so">
<pluginconf trobbler="kxdocker/themes/trobblers/default"/>
</plugin>
<pluginspath Path=""/>
<pluginspath Path="kxdocker/"/>
<pluginspath Path="lib/kxdocker/"/>
<pluginspath Path="lib64/kxdocker/"/>
<pluginspath Path="kxdocker/plugins/"/>
<pluginspath Path="share/apps/kxdocker/plugins/"/>
<pluginspath Path="/opt/kde/share/apps/kxdocker/plugins/"/>
<pluginspath Path="/usr/share/apps/kxdocker/plugins/"/>
</plugins>
<icons miniFontFamily="Bitstream Vera Sans Mono" FontOther="135543888" FontRed="255" Size="32" miniFontSize="10" FontOtherBinaryValue="0" SizeBig="128" miniFontOtherBinaryValue="0" FontGreen="255" FontBlue="255" Horiz="0" FontAlias="" Separation="1" Raise="-48" miniFontWeight="50" miniFontItalic="0" FontBold="1" FontItalic="0" miniFontAlias="" miniFontGreen="0" miniFontBlue="0" miniFontOther="16" miniFontBold="0" miniFontRed="0" Design="panther" EnableThumbnail="1" FontWeight="75" FontSize="11" FontFamily="Monospace"/>
<window borderLeft="251" Top="624" SendToForgroundTimeout="0" Align="bottom" Width="2319" FastHide="0" HideMouseEdge="1" HeightDesktop="0" HideMouseCornerLeft="0" Left="0" Height="144" SendToBackground="1" RaiseOnEvents="1" HideMouseCornerRight="0" TopForce="0" LeftForce="0" borderTop="104" AutoHideTimeout="0"/>
&#8722;
	<theme MiniPillowPath="kxdocker/themes/bar/pillow_transparent" BackgroundPath="kxdocker/themes/bar/default" PillowPath="kxdocker/themes/bar/pillow_transparent" ArrowsPath="kxdocker/themes/arrows/" PoofPath="kxdocker/themes/poof">
<background Tiled="0" imgBackgroundRight="background-right.png" imgBackgroundSeparator="background-separator.png" imgBackgroundOver="background-over.png" Desaturate="0" imgBackgroundCenter="background-center.png" imgBackgroundLeft="background-left.png"/>
</theme>
<statistics dockerStarts="2" changedBackgroundTheme="69" dockerFirstStart="1159445394" avgIconsDisplayed="588" avgCounter="66" dockerDaysRunning="0" dockerMinutesRunning="57" dockerSecondsRunning="47" startedConfigurator="0" maxIconsDisplayed="14" dockerHoursRunning="0"/>
<iconspaths Path="kxdocker/themes/icons"/>
</general>
&#8722;
	<objects>
&#8722;
	<objectsicons>
<info OverText="KDE Menu" className="GIcon" Name="KDE Menu" Group="menu" fileName=""/>
<images imgFileName="kmenu" imgFileDrop="kfind.png" PoofName="" imgFileArrow="newwhite.png"/>
<status MiniTextShow="1"/>
<actions onDropExec="kfind "%1"" onClickExec="kxdocker:/docker/kmenu()" iAnimationMask="0"/>
<matchtasks ClassName="kicker" TaskName="kio_uiserver" WindowTitle=""/>
<matchtasks ClassName="kdesktop" TaskName="kdesktop" WindowTitle="KDesktop"/>
<matchtasks ClassName="Kxdocker" TaskName="kxdocker" WindowTitle="KXDocker"/>
<matchdcop dcopName="kio_uiserver"/>
<pluginconfiguration/>
&#8722;
	<actionlist>
<menuaction image="kfind" action="exec" data="kdcop" info="Find DCOP services" MenuTmpID="-122"/>
<menuaction image="connect_creating" action="exec" data="sudo /etc/init.d/apache2 start" info="Apache2 start" MenuTmpID="-123"/>
<menuaction image="connect_no" action="exec" data="sudo /etc/init.d/apache2 stop" info="Apache2 stop" MenuTmpID="-124"/>
<menuaction image="player_play" action="exec" data="sudo /etc/init.d/proftpd start" info="ProFTPD start" MenuTmpID="-125"/>
<menuaction image="player_stop" action="exec" data="sudo /etc/init.d/proftpd stop" info="ProFTPD stop" MenuTmpID="-126"/>
<menuaction image="player_play" action="exec" data="sudo /etc/init.d/samba start" info="Samba start" MenuTmpID="-127"/>
<menuaction image="player_stop" action="exec" data="sudo /etc/init.d/samba stop" info="Samba stop" MenuTmpID="-128"/>
<menuaction image="player_play" action="exec" data="sudo /etc/init.d/postgresql start" info="PostgreSQL start" MenuTmpID="-129"/>
<menuaction image="player_stop" action="exec" data="sudo /etc/init.d/postgresql stop" info="PostgreSQL stop" MenuTmpID="-130"/>
<menuaction image="player_play" action="exec" data="sudo /etc/init.d/mysql start" info="MySQL start" MenuTmpID="-131"/>
<menuaction image="player_stop" action="exec" data="sudo /etc/init.d/mysql stop" info="MySQL stop" MenuTmpID="-132"/>
<menuaction image="connect_creating" action="exec" data="sudo /etc/init.d/net.eth0 restart" info="Restart Ethernet" MenuTmpID="-133"/>
<menuaction image="kwifimanager" action="exec" data="sudo /opt/etc/init.d/ifup.setup.wlan0" info="Start Wifi" MenuTmpID="-134"/>
<menuaction image="kppp" action="exec" data="sudo /opt/bin/share_internet" info="share Internet connection" MenuTmpID="-135"/>
</actionlist>
</objectsicons>
&#8722;
	<objectsicons>
<info OverText="Today" className="GDate" Name="date_sensor" Group="korganizer_group" fileName=""/>
<images imgFileName="cache" imgFileDrop="drop.png" PoofName="" imgFileArrow="arrow.png"/>
<status MiniTextShow="2"/>
<actions onDropExec="" onClickExec="korganizer" iAnimationMask="0"/>
&#8722;
	<pluginconfiguration>
<pluginconf/>
</pluginconfiguration>
&#8722;
	<actionlist>
<menuaction image="package_favourite" action="exec" data="konqueror http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=themes#gdate" info="Download gDate Themes" MenuTmpID="-20"/>
</actionlist>
</objectsicons>
&#8722;
	<objectsicons>
<info OverText="Trash" className="GTrash" Name="Trash" Group="trash" fileName=""/>
<images imgFileName="trashcan_empty" imgFileDrop="trash.png" PoofName="" imgFileArrow="metal.png"/>
<status MiniTextShow="2"/>
<actions onDropExec="kfmclient move "%1" trash:/" onClickExec="kfmclient exec trash:/" iAnimationMask="0"/>
<matchtasks ClassName="" TaskName="" WindowTitle="trash:/ - Konqueror"/>
<matchdcop dcopName=""/>
&#8722;
	<pluginconfiguration>
<pluginconf/>
</pluginconfiguration>
&#8722;
	<actionlist>
<menuaction image="trashcan_empty" action="exec" data="ktrash --empty" info="Empty trash"/>
<menuaction image="down" action="exec" data="konqueror http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=themes#gtrash" info="Download new themes"/>
</actionlist>
</objectsicons>
&#8722;
	<objectsicons>
<info OverText="Web Browser" className="GIcon" Name="Firefox Web Browser" Group="Application;Network;" fileName=""/>
<images imgFileName="mozilla-firefox.png" imgFileDrop="drop.png" PoofName="poof.png" imgFileArrow="arrow.png"/>
<status MiniTextShow="1"/>
<actions onDropExec="firefox %u "%1"" onClickExec="firefox %u" iAnimationMask="0"/>
<matchtasks ClassName="Firefox Web Browser" TaskName="Firefox Web Browser" WindowTitle="Web Browser"/>
<matchdcop dcopName="Firefox Web Browser"/>
&#8722;
	<pluginconfiguration>
<pluginconf/>
</pluginconfiguration>
<actionlist/>
</objectsicons>
&#8722;
	<objectsicons>
<info OverText="IRC Client" className="GIcon" Name="XChat IRC" Group="Application;Network;" fileName=""/>
<images imgFileName="/home/dennis/.icons/OSX/scalable/apps/kopete.png" imgFileDrop="drop.png" PoofName="poof.png" imgFileArrow="arrow.png"/>
<status MiniTextShow="1"/>
<actions onDropExec="xchat "%1"" onClickExec="xchat" iAnimationMask="0"/>
<matchtasks ClassName="XChat IRC" TaskName="XChat IRC" WindowTitle="IRC Client"/>
&#8722;
	<pluginconfiguration>
<pluginconf/>
</pluginconfiguration>
<actionlist/>
</objectsicons>
&#8722;
	<objectsicons>
<info OverText="P2P Client" className="GIcon" Name="Gtk-Gnutella" Group="Application;Network;" fileName=""/>
<images imgFileName="gtk-gnutella.png" imgFileDrop="drop.png" PoofName="poof.png" imgFileArrow="arrow.png"/>
<status MiniTextShow="1"/>
<actions onDropExec="gtk-gnutella "%1"" onClickExec="gtk-gnutella" iAnimationMask="0"/>
<matchtasks ClassName="Gtk-Gnutella" TaskName="Gtk-Gnutella" WindowTitle="P2P Client"/>
&#8722;
	<pluginconfiguration>
<pluginconf/>
</pluginconfiguration>
<actionlist/>
</objectsicons>
</objects>
&#8722;
	[B]<objectsplugins>
<system SystemName="lo"/>
&#8722;
	<objectsicons>
<info OverText="lo" className="GNetIO" Name="lo" Group="lo" fileName=""/>
<images imgFileName="lo" imgFileDrop="drop.png" PoofName="poof.png" imgFileArrow="arrow.png"/>
<status MiniTextShow="1"/>
<actions onDropExec="kbtobexclient %1" onClickExec="konqueror --caption "browse lo" "sdp://lo"" iAnimationMask="0"/>
<matchtasks ClassName="browse lo" TaskName="browse lo" WindowTitle="browse lo"/>
<matchdcop dcopName="browse lo"/>
&#8722;
	<pluginconfiguration>
<pluginconf/>
</pluginconfiguration>
<actionlist/>
</objectsicons>
</objectsplugins>
&#8722;
	<objectsplugins>
<system SystemName="ra0"/>
&#8722;
	<objectsicons>
<info OverText="ra0" className="GNetIO" Name="ra0" Group="ra0" fileName=""/>
<images imgFileName="ra0" imgFileDrop="drop.png" PoofName="poof.png" imgFileArrow="arrow.png"/>
<status MiniTextShow="1"/>
<actions onDropExec="kbtobexclient %1" onClickExec="konqueror --caption "browse ra0" "sdp://ra0"" iAnimationMask="0"/>
<matchtasks ClassName="browse ra0" TaskName="browse ra0" WindowTitle="browse ra0"/>
<matchdcop dcopName="browse ra0"/>
&#8722;
	<pluginconfiguration>
<pluginconf/>
</pluginconfiguration>
<actionlist/>
</objectsicons>
</objectsplugins>
&#8722;
	<objectsplugins>
<system SystemName="eth0"/>
&#8722;
	<objectsicons>
<info OverText="eth0" className="GNetIO" Name="eth0" Group="eth0" fileName=""/>
<images imgFileName="eth0" imgFileDrop="drop.png" PoofName="poof.png" imgFileArrow="arrow.png"/>
<status MiniTextShow="1"/>
<actions onDropExec="kbtobexclient %1" onClickExec="konqueror --caption "browse eth0" "sdp://eth0"" iAnimationMask="0"/>
<matchtasks ClassName="browse eth0" TaskName="browse eth0" WindowTitle="browse eth0"/>
<matchdcop dcopName="browse eth0"/>
&#8722;
	<pluginconfiguration>
<pluginconf/>
</pluginconfiguration>
<actionlist/>
</objectsicons>
</objectsplugins>
&#8722;
	<objectsplugins>
<system SystemName="rausb0"/>
&#8722;
	<objectsicons>
<info OverText="rausb0" className="GNetIO" Name="rausb0" Group="rausb0" fileName=""/>
<images imgFileName="rausb0" imgFileDrop="drop.png" PoofName="poof.png" imgFileArrow="arrow.png"/>
<status MiniTextShow="1"/>
<actions onDropExec="kbtobexclient %1" onClickExec="konqueror --caption "browse rausb0" "sdp://rausb0"" iAnimationMask="0"/>
<matchtasks ClassName="browse rausb0" TaskName="browse rausb0" WindowTitle="browse rausb0"/>
<matchdcop dcopName="browse rausb0"/>
&#8722;
	<pluginconfiguration>
<pluginconf/>
</pluginconfiguration>
<actionlist/>
</objectsicons>
</objectsplugins>
&#8722;
	<objectsplugins>
<system SystemName="sit0"/>
&#8722;
	<objectsicons>
<info OverText="sit0" className="GNetIO" Name="sit0" Group="sit0" fileName=""/>
<images imgFileName="sit0" imgFileDrop="drop.png" PoofName="poof.png" imgFileArrow="arrow.png"/>
<status MiniTextShow="1"/>
<actions onDropExec="kbtobexclient %1" onClickExec="konqueror --caption "browse sit0" "sdp://sit0"" iAnimationMask="0"/>
<matchtasks ClassName="browse sit0" TaskName="browse sit0" WindowTitle="browse sit0"/>
<matchdcop dcopName="browse sit0"/>
&#8722;
	<pluginconfiguration>
<pluginconf/>
</pluginconfiguration>
<actionlist/>
</objectsicons>
</objectsplugins>
</kxdocker>[/B]

---

### Post by wieman01 on 2006-09-28
Am I correct in saying that you have installed THE configurator for KXDocker? So you have a little icon in the task bar?

---

### Post by spacecowboy706 on 2006-09-29
Icon in the taskbar???? not sure what the taskbar is? 

in the kxdock down at the bottom i have the trashcan, firefox web browser, date, and the little penguin with a bite takin out of him <--- labelled KDE menu....

in the bar up top i cannot find anything that has to do with kxdock... the only way i was able to start it (kxdock) up was type in kxdock in the terminal, or add kxdock to the session startup list.

---

### Post by wieman01 on 2006-09-29
Hello Spacecowboy, 

I would try the following: Take out the plugins one by one starting with this one (make a safety copy of the file before you do that):
> <plugin name="xNetworker" filename="libKXNetworker.so">
<pluginconf showControlIcon="0"/>
</plugin>
And see if the icons in question (eth0, etc.) disappear. Try that and let me know if this helps. If not we try something else.

---

### Post by spacecowboy706 on 2006-09-30
I think i have gotten lost somewhere ... I'm supposed to open the kxdocker_conf.xml document and then locate and delete the following:

<plugin name="xNetworker" filename="libKXNetworker.so">
<pluginconf showControlIcon="0"/>
</plugin>

I cannot find that anywhere in the kxdocker_conf.xml document. I did try to remove the section [that i highlighted in my last post] from all the documents in the folder and then restart the docker, but when i do everything gets put right back in and the cat5 connectors reappear. :(

---

### Post by wieman01 on 2006-09-30
Have you installed any kinds of plugin on top of KXDocker? This used to happen to me as well before I reinstalled KXDocker without installing any kind of plugin.

---

### Post by spacecowboy706 on 2006-09-30
These are all the components i installed with the docker:

kxdocker-resources-version.x.x.tar.bz2
kxdocker-configurator-version.x.x.tar.bz2
kxdocker-dcop-version.x.x.tar.bz2
kxdocker-i18n-version.x.x.tar.bz2
kxdocker-trayiconlogger-version.x.x.tar.bz2
kxdocker-taskmanager-version.x.x.tar.bz2
kxdocker-thememanager-version.x.x.tar.bz2
kxdocker-wizard-version.x.x.tar.bz
kxdocker-networker-version.x.x.tar.bz2
kxdocker-gtrash-version.x.x.tar.bz2
kxdocker-gdate-version.x.x.tar.bz2

and the XIA page said it was recommended that you install these components.

I can right click on any of the icons in the dock and i get a Configure option but when i select configure it only brings up a configure option for the icon that I right clicked on. If i try to right click on the docker itself nothing happens.

I tried looking on the XIA page to see if there was a command i could just type in the terminal to launch the docker configurator or wizard, but i couldn't find anything (as im not even really sure what I should be looking for)?

---

### Post by wieman01 on 2006-09-30
There is a little icon in your taskbar, isn't there? See screenshot to understand what I mean. You can click that to configure the docker... And you can disable the network icons.

Actually I would remove KXDocker and reinstall it. You don't really need the plugins. They are a headache. The one that is - in all likelihood - tripping you up is "kxdocker-networker-version.x.x.tar.bz2"... I suspect that this one makes the unnecessary icons appear on your docker bar.

---

### Post by spacecowboy706 on 2006-09-30
good to go... how do we uninstall kxdocker and start over with it?

---

### Post by spacecowboy706 on 2006-09-30
Found how to do it: I had to go to where I installed it at (getting there using the terminal) and then use this for each and every folder in the place where it was installed:

make clean && sudo make uninstall

after that i deleted all the KXDOCKER folders and removed KXDocker from my session startup...

Now the only KXdocker stuff left are the original tar files i downloaded. Whic one of these should i use to RE-Install with and which ones should i leave out?

kxdocker-1.1.4a.tar.bz2

and then all the extras as follows:

kxdocker-resources-version.x.x.tar.bz2
kxdocker-configurator-version.x.x.tar.bz2
kxdocker-dcop-version.x.x.tar.bz2
kxdocker-i18n-version.x.x.tar.bz2
kxdocker-trayiconlogger-version.x.x.tar.bz2
kxdocker-taskmanager-version.x.x.tar.bz2
kxdocker-thememanager-version.x.x.tar.bz2
kxdocker-wizard-version.x.x.tar.bz
kxdocker-networker-version.x.x.tar.bz2
kxdocker-gtrash-version.x.x.tar.bz2
kxdocker-gdate-version.x.x.tar.bz2

---

### Post by wieman01 on 2006-09-30
Hi, 

Excellent! Only install this one now: [COLOR="Red"]kxdocker-1.1.4a.tar.bz2[/COLOR].

And if you get these error messages again, then use my config file (xml) and replace yours with mine.

---

### Post by spacecowboy706 on 2006-09-30
the networker one was the cause.... i reinstalled just the one you said and the cat5 connectors are gone. From that point i was not able to right click on the docker so i installed the required resources:

kxdocker-resources-version.x.x.tar.bz2
kxdocker-configurator-version.x.x.tar.bz2
kxdocker-dcop-version.x.x.tar.bz2
kxdocker-i18n-version.x.x.tar.bz2
kxdocker-trayiconlogger-version.x.x.tar.bz2
kxdocker-thememanager-version.x.x.tar.bz2
kxdocker-wizard-version.x.x.tar.bz
kxdocker-gdate-version.x.x.tar.bz2<---- wasn't really needed ... but i like it :) 

so it is working now as it should, in the exception that I cant figure out how to:

Add additional icons/launchers
Configure the behavior
change themes

that kind of stuff.... but i can figure that out on my own (I Think), the main reason i left windows was to learn something new... and I am definatly learning....

Its kind of funny  a week ago, i didn't know what a tarball was or even 1 type of terminal command for linux.... such is not the case anymore...

As a new linux user i like the difference of it from windows, but i am not the average pc user (with windows i am in the advanced category)... I think that if all the software makers out there for linux distro's could make thier software as easy to install as windows (double click the .exe) there would probably be alot more people making the transition to linux, and actually staying. Personally I like the challenge. :-D 


PS.... I know about repositories and the Synaptic Package manager but it is still not as easy as downloading a program from a web site and clicking on the executable to install it...But then again most of it is free and that makes it worth all the trouble to me.... Hoorah Ubuntu

---

### Post by wieman01 on 2006-09-30
Wow... Finally! :-)

I don't know how to change themes, etc. but there is definitely an icon in the tray, isn't there? This open a configuration box if you righ-click it, doesn't it?

As for adding icons... That's simple. Add another section by editing the XML config file:
> <objectsicons>
   <info OverText="My Secret Files" className="GIcon" Name="My Secret Files" Group="My Secret Files" fileName="" />
   <images imgFileName="Personal 2" imgFileDrop="drop.png" PoofName="poof.png" imgFileArrow="arrow.png" />
   <status MiniTextShow="1" />
   <actions onDropExec="" onClickExec="konqueror /mnt" iAnimationMask="0" />
   <matchtasks ClassName="Konqueror" TaskName="konqueror" WindowTitle="My Files" />
   <matchdcop dcopName="konqueror" />
   <pluginconfiguration>
    <pluginconf/>
   </pluginconfiguration>
   <actionlist/>
  </objectsicons>
As new icon should now appear on the Docker appet which you can edit by right-clicking it. See that?

---

### Post by spacecowboy706 on 2006-09-30
your help on adding the icons works "kinda"... woohoo... 

the only way i could get it to work was to delete the kxdocker_conf.xml document and the text one as well, then make a new one from a text file and put it back in the folder where you deleted the old one at...

all to be done while the docker was shut down... then restarted the system after the changes were made.

or at keast that was how i got it to work. thyanks for the help, It was greatly appreciated.

---

### Post by wieman01 on 2006-09-30
No problem at all. KXDocker is a bit of a hassle but once you get it working you'll love it. :-)

---

### Post by geearf on 2006-10-03
Hello,

I can't get a good config file. I have tried the config file you gave in the other thread, but it's full of bad links (like opt for exemple).

When I try to locate the files it can find, well I don't find them either .. so I don't really know what to change in the file ...
I have installed kxdocker from universe (edgy).

Thanks

---

### Post by wieman01 on 2006-10-03
> **geearf said:**
> Hello,

I can't get a good config file. I have tried the config file you gave in the other thread, but it's full of bad links (like opt for exemple).

When I try to locate the files it can find, well I don't find them either .. so I don't really know what to change in the file ...
I have installed kxdocker from universe (edgy).

Thanks
You can change the icons' settings by right-click & selecting configure... Of course the links are not relevant to you but it offers you an initial configuration which you can customize. See screenshot.

---

### Post by geearf on 2006-10-03
I can't even start the configuration thing :(

QObject::connect: Cannot connect XEPlugin_Command::xParseTo(const QString &, int, void *) to (null)::xParse(const QString &, int, void *)

A bit on the side I tried Kool dock, and this one worked, but it did not feel that nice to me, would kxdocker feels nicer once proper done ?

---

### Post by wieman01 on 2006-10-03
Kool dock is fairly buggy albeit easier to set up. Is this a fresh install of KXDocker? Try to reinstall and skip all the plugin... Perhaps that helps.

Is there any other output when you start the program from a terminal window?

---

### Post by geearf on 2006-10-07
you asked for it :) :

```
kxdocker
KXDocker Will use Composite Extensions!
QSettings::sync: filename is null/empty
kxdocker: WARNING: Cannot find updated resources: you may need to update or reinstall KXDocker resources, checkout [http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources](http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources)
kxdocker: WARNING: loading xml...
kxdocker: WARNING: saving xml configuration to backup configuration...
kxdocker: WARNING: loading plugins...
kxdocker: WARNING: xeplugin_register(xMatrix)
/usr/lib/kxdocker/liblibKXConfigurator.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibKXConfigurator.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/libliblibKXConfigurator.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibKXConfigurator.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibKXConfigurator.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/libliblibKXConfigurator.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibKXConfigurator.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibKXConfigurator.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/libliblibKXConfigurator.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibKXConfigurator.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibKXConfigurator.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/libliblibKXConfigurator.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibKXConfigurator.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibKXConfigurator.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/libliblibKXConfigurator.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibKXConfigurator.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibKXConfigurator.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/libliblibKXConfigurator.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibKXConfigurator.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibKXConfigurator.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/libliblibKXConfigurator.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibKXConfigurator.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibKXConfigurator.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/libliblibKXConfigurator.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibKXConfigurator.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibKXConfigurator.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/libliblibKXConfigurator.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
kxdocker: WARNING: xeplugin_register(xGDocker)
kxdocker: WARNING: xeplugin_register(xCommand)
/usr/lib/kxdocker/liblibKXARPManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibKXARPManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/libliblibKXARPManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibKXARPManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibKXARPManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/libliblibKXARPManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibKXARPManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibKXARPManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/libliblibKXARPManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibKXTaskManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibKXTaskManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/libliblibKXTaskManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibKXTaskManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibKXTaskManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/libliblibKXTaskManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibKXTaskManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibKXTaskManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/libliblibKXTaskManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibKXMountManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibKXMountManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/libliblibKXMountManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibKXMountManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibKXMountManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/libliblibKXMountManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibKXMountManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibKXMountManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/libliblibKXMountManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
kxdocker: WARNING: xeplugin_register(xAnimator)
kxdocker: WARNING: xeplugin_register(xMouse)
/usr/lib/kxdocker/liblibXEPlugin_DCOP.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibXEPlugin_DCOP.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/libliblibXEPlugin_DCOP.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibXEPlugin_DCOP.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibXEPlugin_DCOP.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/libliblibXEPlugin_DCOP.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibXEPlugin_DCOP.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/liblibXEPlugin_DCOP.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/lib/kxdocker/libliblibXEPlugin_DCOP.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/opt/kde/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
/usr/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type
QSettings::sync: filename is null/empty
kxdocker: WARNING: Plugins loaded:
kxdocker: WARNING: [0] xMatrix
kxdocker: WARNING: [1] xGDocker
kxdocker: WARNING: [2] xCommand
kxdocker: WARNING: [3] xAnimator
kxdocker: WARNING: [4] xMouse
kxdocker: WARNING: [5] xPillow
kxdocker: WARNING: Going to background...

```

"Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou répertoire de ce type" means "Cannot open the shared object file. No file or directory of this type".

And I guess most of these come from the fact that the links in the config file are wrong.

I just installed kxdocker with kxdocker-data from the repos. Should I try something else ?

Thanks

---

### Post by geearf on 2006-10-07
just got these : 

```
Grabbing the mouse failed with "AlreadyGrabbed"
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x42000df
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x42000df
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x42000df
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x42000df

```

---

### Post by wieman01 on 2006-10-07
Mmm... That's odd. All these error message relate to plugins you have not installed. Please show me your config file & I'll try to highlight which lines you need to remove. I guess it won't be too difficult to get rid of these error messages.

---

### Post by geearf on 2006-10-08
Well I used the one you provided, because by default there seems to be none.

But the links to the various files / directories are wrong, I guess this is the main problem.

---

### Post by wieman01 on 2006-10-08
> **geearf said:**
> Well I used the one you provided, because by default there seems to be none.

But the links to the various files / directories are wrong, I guess this is the main problem.
Actually I don't think the file links are a problem. Others have used the file as well... The system would consider them dead links, that's all. I am afraid all I can suggest is reinstall KXDocker. Sorry for that. :-(

---

### Post by geearf on 2006-10-08
Well I did to get the same thing :)

Maybe I should get all the files and compile them, maybe the one in the repos is no good.

Thanks

---

### Post by wieman01 on 2006-10-08
Oh... I was not aware that you had installed it via Synaptic/Aptitude. Yes, the version we're referring to is the latest one that you need to compile yourself from source. Please try that first, the one in the repositories is more than outdated.

---

### Post by spacecowboy706 on 2006-10-08
I had to have these files;

kxdocker-1.1.4a.tar.bz2
kxdocker-resources-1.1.0.tar.bz2 
kxdocker-configurator-1.0.2.tar.bz2
kxdocker-dcop-1.0.0.tar.bz2
kxdocker-i18n-1.0.2.tar.bz2
kxdocker-trayiconlogger-1.0.0.tar.bz2


from this page;

[http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download](http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download)

just to get the whole thing working, with wieman01 's help of course. He will get you there, since he is the best helper on this site :-D

---

### Post by wieman01 on 2006-10-08
> **spacecowboy706 said:**
> I had to have these files;

kxdocker-1.1.4a.tar.bz2
kxdocker-resources-1.1.0.tar.bz2 
kxdocker-configurator-1.0.2.tar.bz2
kxdocker-dcop-1.0.0.tar.bz2
kxdocker-i18n-1.0.2.tar.bz2
kxdocker-trayiconlogger-1.0.0.tar.bz2


from this page;

[http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download](http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download)

just to get the whole thing working, with wieman01 's help of course. He will get you there, since he is the best helper on this site :-D
Excellent, dude. Thank you.

---

### Post by jstad on 2007-01-04
I am stuck on the simple step of:

sudo apt-get install build-essensial xlibs-dev libqt3-mt-dev libqt3-compat-header kdelibs4-dev kdebase-dev

I run the command and recieve the following error:
> 
jsmestad@smubb:~/Desktop/kxdocker-1.1.4a$ sudo apt-get install libqt3-compat-headers kdelibs4-dev kdebase-dev libarts1-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdelibs4-dev: Depends: libqt3-mt-dev (>= 3:3.3.5) but it is not going to be installed
                Depends: libavahi-qt3-dev (>= 0.4) but it is not going to be installed
  libarts1-dev: Depends: libqt3-mt-dev (>= 3:3.3.5) but it is not going to be installed
E: Broken packages


I even tried going into Synaptic and downloading each piece by selecting it but each time it says it can't for some dependency or another. When I try to get that dependency, it tells me it needs other dependencies as well. Its like a vicious circle! ](*,)

---

### Post by habtish on 2007-01-06
Try this..
```
sudo apt-get install build-essential xlibs-dev libqt3-mt-dev  kdelibs4-dev kdebase-dev


```

The link you'd followed has a typo in some of those packages. Note the difference in build-essential from what you posted. Hope this works for you...

---

### Post by Afteraffekt on 2007-01-07
Iv gotten every error explained in this thread, and have downloaded the xml file and applied it and i now haw the multiple icons on the docker...but i cant configure them due to the query string error that was last stated..what do i do?

When I start kxdocker I get:

```
Error: KXDocker cannot find Composite Extensions
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kxdocker: WARNING: Cannot find updated resources: you may need to update or reinstall KXDocker resources, checkout http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources
kxdocker: WARNING: loading xml...
kxdocker: WARNING: saving xml configuration to backup configuration...
kxdocker: WARNING: loading external xml configurations: addons_50_configurator.xml
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
Hello, KXDocker is going to use FAKE Transparency
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
/usr/lib/kxdocker/liblibXEPlugin_DCOP.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibXEPlugin_DCOP.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibXEPlugin_DCOP.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libliblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
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

Cont in next post..too long lol

---

### Post by Afteraffekt on 2007-01-07
When I go to configure an icon i get:

```
QObject::connect: Cannot connect XEPlugin_Command::xParseTo(const QString &, int, void *) to (null)::xParse(const QString &, int, void *)

```

And When I go to install ANY plugin I get this error at the end of the "make"

```
nfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'void XEPlugin_Configurator::popup_plugin_casella_add()':
xeplugin_configurator.cpp:798: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp:800: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'void XEPlugin_Configurator::popup_icon_casella_del()':
xeplugin_configurator.cpp:813: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:815: error: 'XSGObjectIcon' was not declared in this scope
xeplugin_configurator.cpp:815: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:816: error: invalid use of member (did you forget the '&' ?)
xeplugin_configurator.cpp:817: error: invalid use of member (did you forget the '&' ?)
xeplugin_configurator.cpp:817: error: base operand of '->' is not a pointer
xeplugin_configurator.cpp:819: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:822: error: invalid use of undefined type 'struct XEConfiguration'
xeplugin_configurator.h:112: error: forward declaration of 'struct XEConfiguration'
xeplugin_configurator.cpp:824: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::plugins_selectionChanged(QListViewItem*)':
xeplugin_configurator.cpp:864: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:866: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:876: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:879: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp:880: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp:883: error: 'XEObject' has not been declared
xeplugin_configurator.cpp:883: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp:890: error: 'XEObject' has not been declared
xeplugin_configurator.cpp:890: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp:894: error: 'XEObject' has not been declared
xeplugin_configurator.cpp:894: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp:908: error: 'XEObject' has not been declared
xeplugin_configurator.cpp:908: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::aliases_itemRenamed(QListViewItem*)':
xeplugin_configurator.cpp:919: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:921: error: 'XSCfgMatchIcons' was not declared in this scope
xeplugin_configurator.cpp:921: error: 'newalias' was not declared in this scope
xeplugin_configurator.cpp:921: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'void XEPlugin_Configurator::popup_theme_casella_default()':
xeplugin_configurator.cpp:965: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:968: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'void XEPlugin_Configurator::popup_theme_casella_add()':
xeplugin_configurator.cpp:989: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:992: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'void XEPlugin_Configurator::popup_theme_casella_del()':
xeplugin_configurator.cpp:1004: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1007: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_size_valueChanged(int)':
xeplugin_configurator.cpp:1015: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1016: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1017: error: invalid use of undefined type 'struct XGDocker'
xeplugin_configurator.h:113: error: forward declaration of 'struct XGDocker'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_sizebig_valueChanged(int)':
xeplugin_configurator.cpp:1025: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1027: error: invalid use of undefined type 'struct XGDocker'
xeplugin_configurator.h:113: error: forward declaration of 'struct XGDocker'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_space_valueChanged(int)':
xeplugin_configurator.cpp:1033: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1034: error: invalid use of undefined type 'struct XGDocker'
xeplugin_configurator.h:113: error: forward declaration of 'struct XGDocker'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_design_textChanged(const QString&)':
xeplugin_configurator.cpp:1040: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1041: error: invalid use of undefined type 'struct XGDocker'
xeplugin_configurator.h:113: error: forward declaration of 'struct XGDocker'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_autofit_toggled(bool)':
xeplugin_configurator.cpp:1047: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1048: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_thumbnails_toggled(bool)':
xeplugin_configurator.cpp:1054: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1055: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_max_valueChanged(int)':
xeplugin_configurator.cpp:1061: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_top_valueChanged(int)':
xeplugin_configurator.cpp:1067: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1068: error: invalid use of undefined type 'struct XGDocker'
xeplugin_configurator.h:113: error: forward declaration of 'struct XGDocker'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_left_valueChanged(int)':
xeplugin_configurator.cpp:1074: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1075: error: invalid use of undefined type 'struct XGDocker'
xeplugin_configurator.h:113: error: forward declaration of 'struct XGDocker'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_autosendbackground_toggled(bool)':
xeplugin_configurator.cpp:1081: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1082: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_autoraise_toggled(bool)':
xeplugin_configurator.cpp:1088: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1089: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_fasthiding_toggled(bool)':
xeplugin_configurator.cpp:1095: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1096: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_raiseleft_toggled(bool)':
xeplugin_configurator.cpp:1102: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1103: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_raiseright_toggled(bool)':
xeplugin_configurator.cpp:1109: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1110: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_hide_valueChanged(int)':
xeplugin_configurator.cpp:1116: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_raise_valueChanged(int)':
xeplugin_configurator.cpp:1122: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_desktop_valueChanged(int)':
xeplugin_configurator.cpp:1128: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::pluginPars_itemRenamed(QListViewItem*)':
xeplugin_configurator.cpp:1134: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1138: error: 'XEObject' has not been declared
xeplugin_configurator.cpp:1138: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp:1144: error: 'XEObject' has not been declared
xeplugin_configurator.cpp:1144: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_plugin_name_textChanged(const QString&)':
xeplugin_configurator.cpp:1153: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1155: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_plugin_so_textChanged(const QString&)':
xeplugin_configurator.cpp:1166: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1168: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_interpolation_valueChanged(int)':
xeplugin_configurator.cpp:1175: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'void XEPlugin_Configurator::cfg_update_stats()':
xeplugin_configurator.cpp:1186: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1195: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1196: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1201: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1205: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1206: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1207: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1210: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1211: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1213: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_sleep_valueChanged(int)':
xeplugin_configurator.cpp:1221: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_smooth_valueChanged(int)':
xeplugin_configurator.cpp:1227: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_threads_valueChanged(int)':
xeplugin_configurator.cpp:1233: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_animations_valueChanged(int)':
xeplugin_configurator.cpp:1239: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'void XEPlugin_Configurator::popup_alias_casella_disable()':
xeplugin_configurator.cpp:1249: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1251: error: 'XSCfgMatchIcons' was not declared in this scope
xeplugin_configurator.cpp:1251: error: 'newalias' was not declared in this scope
xeplugin_configurator.cpp:1251: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1253: error: 'XSGObjectIcon' was not declared in this scope
xeplugin_configurator.cpp:1254: error: invalid use of member (did you forget the '&' ?)
xeplugin_configurator.cpp:1257: error: invalid use of member (did you forget the '&' ?)
xeplugin_configurator.cpp:1257: error: base operand of '->' is not a pointer
xeplugin_configurator.cpp: In member function 'void XEPlugin_Configurator::popup_icon_casella_configura()':
xeplugin_configurator.cpp:1272: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1274: error: 'XSGObjectIcon' was not declared in this scope
xeplugin_configurator.cpp:1274: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1275: error: invalid use of member (did you forget the '&' ?)
xeplugin_configurator.cpp:1276: error: invalid use of member (did you forget the '&' ?)
xeplugin_configurator.cpp:1276: error: base operand of '->' is not a pointer
xeplugin_configurator.cpp:1278: error: invalid use of member (did you forget the '&' ?)
xeplugin_configurator.cpp: In member function 'void XEPlugin_Configurator::popup_icon_casella_disable()':
xeplugin_configurator.cpp:1291: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1293: error: 'XSGObjectIcon' was not declared in this scope
xeplugin_configurator.cpp:1293: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1294: error: invalid use of member (did you forget the '&' ?)
xeplugin_configurator.cpp:1295: error: invalid use of member (did you forget the '&' ?)
xeplugin_configurator.cpp:1295: error: base operand of '->' is not a pointer
xeplugin_configurator.cpp:1297: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1300: error: invalid use of undefined type 'struct XEConfiguration'
xeplugin_configurator.h:112: error: forward declaration of 'struct XEConfiguration'
xeplugin_configurator.cpp:1302: error: invalid use of member (did you forget the '&' ?)
xeplugin_configurator.cpp:1302: error: base operand of '->' is not a pointer
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::store_clicked()':
xeplugin_configurator.cpp:1310: error: 'XEObject' has not been declared
xeplugin_configurator.cpp: In member function 'void XEPlugin_Configurator::popup_icon_casella_aggiungi()':
xeplugin_configurator.cpp:1325: error: 'XSGObjectIcon' was not declared in this scope
xeplugin_configurator.cpp:1325: error: 'addedCfg' was not declared in this scope
xeplugin_configurator.cpp:1325: error: invalid use of undefined type 'struct XEConfiguration'
xeplugin_configurator.h:112: error: forward declaration of 'struct XEConfiguration'
xeplugin_configurator.cpp:1356: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1357: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1359: error: invalid use of undefined type 'struct XGDocker'
xeplugin_configurator.h:113: error: forward declaration of 'struct XGDocker'
xeplugin_configurator.cpp:1359: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::WindowAlign_textChanged(const QString&)':
xeplugin_configurator.cpp:1369: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::WindowAlign_activated(const QString&)':
xeplugin_configurator.cpp:1375: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
make[2]: *** [xeplugin_configurator.lo] Error 1
make[2]: Leaving directory `/home/travis/Desktop/kxdocker-configurator-1.0.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/travis/Desktop/kxdocker-configurator-1.0.2'
make: *** [all] Error 2

```

id show the entire code but terminal doesnt let me go back that far...wtf is wrong?

Im so stumped, iv now ran out of ideas...

---

### Post by Afteraffekt on 2007-01-09
Any help on this? It seems more of an error by the creator than me, and thats what my friends tell me.

---

### Post by wieman01 on 2007-01-09
KXDocker is fairly buggy. There is not much that I can do. Sorry for that.

---

### Post by Vlatko on 2007-01-18
alright, this is what i get. i installed the version 1.1.4a via adept. kubuntu edgy here.

```
vlatko@vlatko-desktop:~$ kxdocker
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
kxdocker: WARNING: Warning user kxdocker_conf.xml may be corrupt: loading last backup!
kxdocker: WARNING: Warning user, and backup configurations are corrupt! I'm going to load system kxdocker_conf.xml !!!
kxdocker: WARNING: Warning user, backup, system configurations are corrupt! please install right kxdocker_conf.xml
ERROR: Communication problem with kxdocker, it probably crashed.
vlatko@vlatko-desktop:~$               
```

---

### Post by iangoth on 2007-02-12
> **Afteraffekt said:**
> When I go to configure an icon i get:

```
QObject::connect: Cannot connect XEPlugin_Command::xParseTo(const QString &, int, void *) to (null)::xParse(const QString &, int, void *)

```

And When I go to install ANY plugin I get this error at the end of the "make"

```
nfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'void XEPlugin_Configurator::popup_plugin_casella_add()':
xeplugin_configurator.cpp:798: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp:800: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'void XEPlugin_Configurator::popup_icon_casella_del()':
xeplugin_configurator.cpp:813: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:815: error: 'XSGObjectIcon' was not declared in this scope
xeplugin_configurator.cpp:815: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:816: error: invalid use of member (did you forget the '&' ?)
xeplugin_configurator.cpp:817: error: invalid use of member (did you forget the '&' ?)
xeplugin_configurator.cpp:817: error: base operand of '->' is not a pointer
xeplugin_configurator.cpp:819: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:822: error: invalid use of undefined type 'struct XEConfiguration'
xeplugin_configurator.h:112: error: forward declaration of 'struct XEConfiguration'
xeplugin_configurator.cpp:824: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::plugins_selectionChanged(QListViewItem*)':
xeplugin_configurator.cpp:864: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:866: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:876: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:879: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp:880: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp:883: error: 'XEObject' has not been declared
xeplugin_configurator.cpp:883: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp:890: error: 'XEObject' has not been declared
xeplugin_configurator.cpp:890: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp:894: error: 'XEObject' has not been declared
xeplugin_configurator.cpp:894: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp:908: error: 'XEObject' has not been declared
xeplugin_configurator.cpp:908: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::aliases_itemRenamed(QListViewItem*)':
xeplugin_configurator.cpp:919: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:921: error: 'XSCfgMatchIcons' was not declared in this scope
xeplugin_configurator.cpp:921: error: 'newalias' was not declared in this scope
xeplugin_configurator.cpp:921: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'void XEPlugin_Configurator::popup_theme_casella_default()':
xeplugin_configurator.cpp:965: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:968: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'void XEPlugin_Configurator::popup_theme_casella_add()':
xeplugin_configurator.cpp:989: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:992: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'void XEPlugin_Configurator::popup_theme_casella_del()':
xeplugin_configurator.cpp:1004: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1007: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_size_valueChanged(int)':
xeplugin_configurator.cpp:1015: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1016: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1017: error: invalid use of undefined type 'struct XGDocker'
xeplugin_configurator.h:113: error: forward declaration of 'struct XGDocker'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_sizebig_valueChanged(int)':
xeplugin_configurator.cpp:1025: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1027: error: invalid use of undefined type 'struct XGDocker'
xeplugin_configurator.h:113: error: forward declaration of 'struct XGDocker'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_space_valueChanged(int)':
xeplugin_configurator.cpp:1033: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1034: error: invalid use of undefined type 'struct XGDocker'
xeplugin_configurator.h:113: error: forward declaration of 'struct XGDocker'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_design_textChanged(const QString&)':
xeplugin_configurator.cpp:1040: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1041: error: invalid use of undefined type 'struct XGDocker'
xeplugin_configurator.h:113: error: forward declaration of 'struct XGDocker'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_autofit_toggled(bool)':
xeplugin_configurator.cpp:1047: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1048: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_thumbnails_toggled(bool)':
xeplugin_configurator.cpp:1054: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1055: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_max_valueChanged(int)':
xeplugin_configurator.cpp:1061: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_top_valueChanged(int)':
xeplugin_configurator.cpp:1067: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1068: error: invalid use of undefined type 'struct XGDocker'
xeplugin_configurator.h:113: error: forward declaration of 'struct XGDocker'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_left_valueChanged(int)':
xeplugin_configurator.cpp:1074: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1075: error: invalid use of undefined type 'struct XGDocker'
xeplugin_configurator.h:113: error: forward declaration of 'struct XGDocker'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_autosendbackground_toggled(bool)':
xeplugin_configurator.cpp:1081: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1082: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_autoraise_toggled(bool)':
xeplugin_configurator.cpp:1088: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1089: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_fasthiding_toggled(bool)':
xeplugin_configurator.cpp:1095: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1096: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_raiseleft_toggled(bool)':
xeplugin_configurator.cpp:1102: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1103: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_raiseright_toggled(bool)':
xeplugin_configurator.cpp:1109: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1110: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_hide_valueChanged(int)':
xeplugin_configurator.cpp:1116: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_raise_valueChanged(int)':
xeplugin_configurator.cpp:1122: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_desktop_valueChanged(int)':
xeplugin_configurator.cpp:1128: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::pluginPars_itemRenamed(QListViewItem*)':
xeplugin_configurator.cpp:1134: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1138: error: 'XEObject' has not been declared
xeplugin_configurator.cpp:1138: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp:1144: error: 'XEObject' has not been declared
xeplugin_configurator.cpp:1144: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_plugin_name_textChanged(const QString&)':
xeplugin_configurator.cpp:1153: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1155: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_plugin_so_textChanged(const QString&)':
xeplugin_configurator.cpp:1166: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1168: error: invalid use of undefined type 'struct XSGObjectPlugin'
xeplugin_configurator.h:124: error: forward declaration of 'struct XSGObjectPlugin'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_interpolation_valueChanged(int)':
xeplugin_configurator.cpp:1175: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'void XEPlugin_Configurator::cfg_update_stats()':
xeplugin_configurator.cpp:1186: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1195: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1196: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1201: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1205: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1206: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1207: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1210: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1211: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1213: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_sleep_valueChanged(int)':
xeplugin_configurator.cpp:1221: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_smooth_valueChanged(int)':
xeplugin_configurator.cpp:1227: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_threads_valueChanged(int)':
xeplugin_configurator.cpp:1233: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::cfg_animations_valueChanged(int)':
xeplugin_configurator.cpp:1239: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'void XEPlugin_Configurator::popup_alias_casella_disable()':
xeplugin_configurator.cpp:1249: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1251: error: 'XSCfgMatchIcons' was not declared in this scope
xeplugin_configurator.cpp:1251: error: 'newalias' was not declared in this scope
xeplugin_configurator.cpp:1251: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1253: error: 'XSGObjectIcon' was not declared in this scope
xeplugin_configurator.cpp:1254: error: invalid use of member (did you forget the '&' ?)
xeplugin_configurator.cpp:1257: error: invalid use of member (did you forget the '&' ?)
xeplugin_configurator.cpp:1257: error: base operand of '->' is not a pointer
xeplugin_configurator.cpp: In member function 'void XEPlugin_Configurator::popup_icon_casella_configura()':
xeplugin_configurator.cpp:1272: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1274: error: 'XSGObjectIcon' was not declared in this scope
xeplugin_configurator.cpp:1274: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1275: error: invalid use of member (did you forget the '&' ?)
xeplugin_configurator.cpp:1276: error: invalid use of member (did you forget the '&' ?)
xeplugin_configurator.cpp:1276: error: base operand of '->' is not a pointer
xeplugin_configurator.cpp:1278: error: invalid use of member (did you forget the '&' ?)
xeplugin_configurator.cpp: In member function 'void XEPlugin_Configurator::popup_icon_casella_disable()':
xeplugin_configurator.cpp:1291: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1293: error: 'XSGObjectIcon' was not declared in this scope
xeplugin_configurator.cpp:1293: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1294: error: invalid use of member (did you forget the '&' ?)
xeplugin_configurator.cpp:1295: error: invalid use of member (did you forget the '&' ?)
xeplugin_configurator.cpp:1295: error: base operand of '->' is not a pointer
xeplugin_configurator.cpp:1297: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1300: error: invalid use of undefined type 'struct XEConfiguration'
xeplugin_configurator.h:112: error: forward declaration of 'struct XEConfiguration'
xeplugin_configurator.cpp:1302: error: invalid use of member (did you forget the '&' ?)
xeplugin_configurator.cpp:1302: error: base operand of '->' is not a pointer
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::store_clicked()':
xeplugin_configurator.cpp:1310: error: 'XEObject' has not been declared
xeplugin_configurator.cpp: In member function 'void XEPlugin_Configurator::popup_icon_casella_aggiungi()':
xeplugin_configurator.cpp:1325: error: 'XSGObjectIcon' was not declared in this scope
xeplugin_configurator.cpp:1325: error: 'addedCfg' was not declared in this scope
xeplugin_configurator.cpp:1325: error: invalid use of undefined type 'struct XEConfiguration'
xeplugin_configurator.h:112: error: forward declaration of 'struct XEConfiguration'
xeplugin_configurator.cpp:1356: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1357: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:1359: error: invalid use of undefined type 'struct XGDocker'
xeplugin_configurator.h:113: error: forward declaration of 'struct XGDocker'
xeplugin_configurator.cpp:1359: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::WindowAlign_textChanged(const QString&)':
xeplugin_configurator.cpp:1369: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp: In member function 'virtual void XEPlugin_Configurator::WindowAlign_activated(const QString&)':
xeplugin_configurator.cpp:1375: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
make[2]: *** [xeplugin_configurator.lo] Error 1
make[2]: Leaving directory `/home/travis/Desktop/kxdocker-configurator-1.0.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/travis/Desktop/kxdocker-configurator-1.0.2'
make: *** [all] Error 2

```

id show the entire code but terminal doesnt let me go back that far...wtf is wrong?

Im so stumped, iv now ran out of ideas...

Woohoo, my first post! :mrgreen:

I had the same problem. I got it to work by compiling all the plugins using just ./configure, without any of those extra options suggested in the guide.

---

