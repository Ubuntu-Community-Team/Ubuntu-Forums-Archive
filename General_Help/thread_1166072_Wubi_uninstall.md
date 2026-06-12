---
title: "Wubi uninstall"
date: 2009-05-21
forum: General Help
---

### Post by MichaelZum on 2009-05-21
I installed ubuntu 9.0.4 inside windows and now need to uninstall it. I added a couple applications to ubuntu - Kate and gnuCash and subsequently uninstalled them. When I try to run the uninstall-wubi application in windows I get a message that says "This application has failed to start because the application configuration is incorrect. Reinstalling the application may fix this problem." When I try to boot my Ubuntu disk to attempt to reinstall ubuntu inside windows I get the same message about the boot disk. I don't want to just erase the ubuntu folder as that would probably make things even worse.

---

### Post by zhhansen on 2009-05-23
From [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

**How do I manually uninstall Wubi?**

 Remove C:\ubuntu and C:\wubildr*. [WubiGuide tells that is a safe option]


In Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi line. For Vista, you can use EasyBCD to edit the boot menu. Alternatively you can modify the boot menu via control_panel > system > advanced > startup_and_recovery and pressing "Edit". For Windows 98 you have to edit C:\config.sys, and remove the Wubi block. 
To remove Wubi from the add/remove list, delete the registry key: HKLM\Software\Microsoft\Windows\[CurrentVersion]("https://wiki.ubuntu.com/CurrentVersion")\Uninstall\Wubi 



An easy method of removing this registry key is to paste the following text into a plain editor such as Notepad, close and save the file as something like removeWubiKey.reg (you may wish to go to Folder Options > View and disable the "Hide file extensions for known file types" option to check that the .reg extension has actually been applied). Then you can perform the rest automatically by opening the file in the normal Windows manner, or choosing the "Merge" option from the right click context menu. Note: The formatting is rather strict, so copy the text exactly for best results. *You may need to be logged in as the administrator to delete the key, depending on the version of Windows you are using. User Account Control in Vista may also pop up, in the typical fashion.* 

```
REGEDIT4

[-HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\Wubi]
```After deleting the registry key, Ubuntu may still appear in the program list. If this is the case, you may be asked if you would like to remove the item from the list. 


See if that helps. Wubi - Uninstall has never worked for me, but just deleting the folder did, unless you want to save information that you saved in ubuntu.

---

