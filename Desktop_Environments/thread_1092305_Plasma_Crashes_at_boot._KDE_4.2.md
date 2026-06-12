---
title: "Plasma Crashes at boot. KDE 4.2"
date: 2009-03-10
forum: Desktop Environments
---

### Post by xaviermerino on 2009-03-10
Hi!.. I have searched through internet and it seems that plasma crashes when you install KDE 4.2.1 (sometimes..) but mine was fine. Today when I try log into my account, plasma crashes with signal 11. The Crash Handler said that the error log was unusable, so I decided to open plasma with Konsole to see the output. I can't seem to understand what is there. Can some one help me how to fix it?

This is Konsole's output:

```
xavier@xaviermerino:~$ plasma
<unknown program name>(7141)/ checkComposite: Plasma has an argb visual 0x91f79b8 83886081
<unknown program name>(7141)/ checkComposite: Plasma can use COMPOSITE for effects on 0x91efef8                                                                                             
QLayout: Attempting to add QLayout "" to QWidget "", which already has a layout               
plasma(7142) Controls::setDisplayedButtons: Minimum size before changing buttons: QSizeF(0, 0)
plasma(7142) Controls::setDisplayedButtons: Layout: QObject(0x0)                              
plasma(7142) showHideButton: Button minimum size: QSizeF(18, 18)                              
plasma(7142) showHideButton: Button preferred size: QSizeF(50, 50)                            
plasma(7142) showHideButton: Button minimum size: QSizeF(18, 18)                              
plasma(7142) showHideButton: Button preferred size: QSizeF(50, 50)                            
plasma(7142) showHideButton: Button minimum size: QSizeF(18, 18)                              
plasma(7142) showHideButton: Button preferred size: QSizeF(50, 50)                            
plasma(7142) showHideButton: Button minimum size: QSizeF(18, 18)                              
plasma(7142) showHideButton: Button preferred size: QSizeF(50, 50)                            
plasma(7142) Controls::setDisplayedButtons: Minimum size after changing buttons: QSizeF(0, 0) 
plasma(7142) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: /home/xavier/.kde/share/apps/RecentDocuments/plasma.desktop not found"                                   
plasma(7142) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: /home/xavier/.kde/share/apps/RecentDocuments/ePSXe.exe.desktop not found"                                
plasma(7142) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: /home/xavier/.kde/share/apps/RecentDocuments/Source Builds.desktop not found"                            
plasma(7142) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: /home/xavier/.kde/share/apps/RecentDocuments/gpupete177.zip.desktop not found"                           
plasma(7142) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: /home/xavier/.kde/share/apps/RecentDocuments/Desktop.desktop not found"                                  
plasma(7142) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: /home/xavier/.kde/share/apps/RecentDocuments/cdrom0.desktop not found"                                   
plasma(7142) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: /home/xavier/.kde/share/apps/RecentDocuments/gpuPeteXGL2.cfg.desktop not found"                          
plasma(7142) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: /home/xavier/.kde/share/apps/RecentDocuments/epsxe170.zip.desktop not found"                             
plasma(7142) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: /home/xavier/.kde/share/apps/RecentDocuments/DMW3 by Dreamchaser.rar[2].desktop not found"               
plasma(7142) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: /home/xavier/.kde/share/apps/RecentDocuments/DMW3 by Dreamchaser.rar.desktop not found"                  
plasma(7142) Solid::Control::ManagerBasePrivate::loadBackend: Backend loaded:  "HAL-Power"    
Object::connect: Attempt to bind non-signal TaskManager::TaskGroup::editRequest()             
QCoreApplication::postEvent: Unexpected null receiver                                         
KCrash: Application 'plasma' crashing...                                                      
sock_file=/home/xavier/.kde/socket-xaviermerino/kdeinit4__0                                   
plasma(7141): Communication problem with  "plasma" , it probably crashed.                     
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" "                                                                   

xavier@xaviermerino:~$ <unknown program name>(7147)/ checkComposite: Plasma has an argb visual 0x93c79b8 85983233                                                                           
<unknown program name>(7147)/ checkComposite: Plasma can use COMPOSITE for effects on 0x93bfef8                                                                                             
QLayout: Attempting to add QLayout "" to QWidget "", which already has a layout               
plasma(7149) Controls::setDisplayedButtons: Minimum size before changing buttons: QSizeF(0, 0)
plasma(7149) Controls::setDisplayedButtons: Layout: QObject(0x0)                              
plasma(7149) showHideButton: Button minimum size: QSizeF(18, 18)                              
plasma(7149) showHideButton: Button preferred size: QSizeF(50, 50)
plasma(7149) showHideButton: Button minimum size: QSizeF(18, 18)
plasma(7149) showHideButton: Button preferred size: QSizeF(50, 50)
plasma(7149) showHideButton: Button minimum size: QSizeF(18, 18)
plasma(7149) showHideButton: Button preferred size: QSizeF(50, 50)
plasma(7149) showHideButton: Button minimum size: QSizeF(18, 18)
plasma(7149) showHideButton: Button preferred size: QSizeF(50, 50)
plasma(7149) Controls::setDisplayedButtons: Minimum size after changing buttons: QSizeF(0, 0)
plasma(7149) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: /home/xavier/.kde/share/apps/RecentDocuments/plasma.desktop not found"
plasma(7149) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: /home/xavier/.kde/share/apps/RecentDocuments/ePSXe.exe.desktop not found"
plasma(7149) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: /home/xavier/.kde/share/apps/RecentDocuments/Source Builds.desktop not found"
plasma(7149) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: /home/xavier/.kde/share/apps/RecentDocuments/gpupete177.zip.desktop not found"
plasma(7149) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: /home/xavier/.kde/share/apps/RecentDocuments/Desktop.desktop not found"
plasma(7149) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: /home/xavier/.kde/share/apps/RecentDocuments/cdrom0.desktop not found"
plasma(7149) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: /home/xavier/.kde/share/apps/RecentDocuments/gpuPeteXGL2.cfg.desktop not found"
plasma(7149) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: /home/xavier/.kde/share/apps/RecentDocuments/epsxe170.zip.desktop not found"
plasma(7149) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: /home/xavier/.kde/share/apps/RecentDocuments/DMW3 by Dreamchaser.rar[2].desktop not found"
plasma(7149) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: /home/xavier/.kde/share/apps/RecentDocuments/DMW3 by Dreamchaser.rar.desktop not found"
plasma(7149) Solid::Control::ManagerBasePrivate::loadBackend: Backend loaded:  "HAL-Power":(
Object::connect: Attempt to bind non-signal TaskManager::TaskGroup::editRequest()
QCoreApplication::postEvent: Unexpected null receiver
plasma(7147): Communication problem with  "plasma" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply(timeout by message bus)" "
```

---

### Post by LeetZorro on 2009-04-03
Hello,
Don't know if you are still having this issue, but I had the same problem when I added a second monitor. To resolve it, I removed my .kde directory and restarted plasma (it locked up on me when I just started it from the terminal, so you should do it by logging out and logging back in). Obviously, this wiped my kde configuration, but rather than deleting it I moved it to a backup directory and restored some configs that way. 

Hope this helps

---

