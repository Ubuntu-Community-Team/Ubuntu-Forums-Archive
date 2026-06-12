---
title: "Hello all !! new to ubuntu and ran into a error"
date: 2009-05-25
forum: General Help
---

### Post by Animemike on 2009-05-25
Hi all just leeched ubuntu and gone for the "install in windows" one (to start with ;))
 
Very close tot he end i get a permissions error creating a Log and it fails 
ive checked the hardhard and there is loads of files there so am not sure it its missing anything or not
 
How can i tell if its install ok? / or fix this problem
 
Cheers
Mike:P

---

### Post by lisati on 2009-05-25
Normally wubi (the "install within windows" program) creates a log in the Windows temporary directory - if you can find it and post it, that might of some help to anyone trying to help you. You can find the Windows temporary directory by clicking Start->Run and entering the following: ```
%temp%
```

---

### Post by Animemike on 2009-05-25
> **lisati said:**
> Normally wubi (the "install within windows" program) creates a log in the Windows temporary directory - if you can find it and post it, that might of some help to anyone trying to help you. You can find the Windows temporary directory by clicking Start->Run and entering the following: ```
%temp%
```
 
Hey thanks for that heres the log
 
```
05-26 00:28 INFO   root: === wubi 9.04 rev128 ===
05-26 00:28 DEBUG  root: Logfile is c:\users\animem~1\appdata\local\temp\wubi-9.04-rev128.log
05-26 00:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"', '--cdmenu']
05-26 00:28 DEBUG  CommonBackend: data_dir=C:\Users\ANIMEM~1\AppData\Local\Temp\pyl8729.tmp\data
05-26 00:28 DEBUG  WindowsBackend: 7z=C:\Users\ANIMEM~1\AppData\Local\Temp\pyl8729.tmp\bin\7z.exe
05-26 00:28 DEBUG  CommonBackend: Fetching basic info...
05-26 00:28 DEBUG  CommonBackend: original_exe=F:\wubi.exe
05-26 00:28 DEBUG  CommonBackend: platform=win32
05-26 00:28 DEBUG  CommonBackend: osname=nt
05-26 00:28 DEBUG  CommonBackend: language=en_GB
05-26 00:28 DEBUG  CommonBackend: encoding=cp1252
05-26 00:28 DEBUG  WindowsBackend: arch=amd64
05-26 00:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\ANIMEM~1\AppData\Local\Temp\pyl8729.tmp\data\isolist.ini
05-26 00:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-26 00:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-26 00:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-26 00:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-26 00:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-26 00:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-26 00:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-26 00:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-26 00:28 DEBUG  WindowsBackend: Fetching host info...
05-26 00:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-26 00:28 DEBUG  WindowsBackend: windows version=vista
05-26 00:28 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
05-26 00:28 DEBUG  WindowsBackend: windows_sp=Service Pack 1
05-26 00:28 DEBUG  WindowsBackend: windows_build=6001
05-26 00:28 DEBUG  WindowsBackend: gmt=0
05-26 00:28 DEBUG  WindowsBackend: country=GB
05-26 00:28 DEBUG  WindowsBackend: timezone=Europe/London
05-26 00:28 DEBUG  WindowsBackend: windows_username=Animemike
05-26 00:28 DEBUG  WindowsBackend: user_full_name=Animemike
05-26 00:28 DEBUG  WindowsBackend: user_directory=Animemike
05-26 00:28 DEBUG  WindowsBackend: windows_language_code=1033
05-26 00:28 DEBUG  WindowsBackend: windows_language=English
05-26 00:28 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
05-26 00:28 DEBUG  WindowsBackend: bootloader=vista
05-26 00:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 819168.558594 mb free )
05-26 00:28 DEBUG  WindowsBackend: drive=Drive(C: hd 819168.558594 mb free )
05-26 00:28 DEBUG  WindowsBackend: drive=Drive(D: hd 634115.675781 mb free ntfs)
05-26 00:28 DEBUG  WindowsBackend: drive=Drive(E: hd 99905.703125 mb free ntfs)
05-26 00:28 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
05-26 00:28 DEBUG  WindowsBackend: drive=Drive(G: hd 882547.851563 mb free ntfs)
05-26 00:28 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
05-26 00:28 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
05-26 00:28 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
05-26 00:28 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
05-26 00:28 DEBUG  WindowsBackend: uninstaller_path=None
05-26 00:28 DEBUG  WindowsBackend: previous_target_dir=None
05-26 00:28 DEBUG  WindowsBackend: previous_distro_name=None
05-26 00:28 DEBUG  WindowsBackend: keyboard_id=134809609
05-26 00:28 DEBUG  WindowsBackend: keyboard_layout=gb
05-26 00:28 DEBUG  WindowsBackend: keyboard_variant=
05-26 00:28 DEBUG  CommonBackend: locale=en_GB.UTF-8
05-26 00:28 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
05-26 00:28 DEBUG  CommonBackend: Searching ISOs on USB devices
05-26 00:28 DEBUG  CommonBackend: Searching for local CDs
05-26 00:28 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pyl8729.tmp is a valid Ubuntu CD
05-26 00:28 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pyl8729.tmp\casper\filesystem.squashfs
05-26 00:28 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pyl8729.tmp is a valid Ubuntu CD
05-26 00:28 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pyl8729.tmp\casper\filesystem.squashfs
05-26 00:28 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pyl8729.tmp is a valid Kubuntu CD
05-26 00:28 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pyl8729.tmp\casper\filesystem.squashfs
05-26 00:28 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pyl8729.tmp is a valid Kubuntu CD
05-26 00:28 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pyl8729.tmp\casper\filesystem.squashfs
05-26 00:28 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pyl8729.tmp is a valid Xubuntu CD
05-26 00:28 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pyl8729.tmp\casper\filesystem.squashfs
05-26 00:28 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pyl8729.tmp is a valid Xubuntu CD
05-26 00:28 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pyl8729.tmp\casper\filesystem.squashfs
05-26 00:28 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pyl8729.tmp is a valid Mythbuntu CD
05-26 00:28 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pyl8729.tmp\casper\filesystem.squashfs
05-26 00:28 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pyl8729.tmp is a valid Mythbuntu CD
05-26 00:28 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pyl8729.tmp\casper\filesystem.squashfs
05-26 00:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-26 00:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-26 00:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-26 00:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-26 00:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-26 00:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-26 00:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-26 00:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-26 00:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-26 00:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-26 00:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-26 00:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-26 00:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-26 00:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-26 00:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-26 00:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-26 00:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-26 00:28 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
05-26 00:28 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
05-26 00:28 INFO   Distro: Found a valid CD for Ubuntu: F:\
05-26 00:28 INFO   root: Running the CD menu...
05-26 00:28 DEBUG  WindowsFrontend: __init__...
05-26 00:28 DEBUG  WindowsFrontend: on_init...
05-26 00:28 INFO   root: CD menu finished
05-26 00:28 INFO   root: Running the installer...
05-26 00:29 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=17000MB, distro_name=Ubuntu, language=English, username=animemike
05-26 00:29 INFO   root: Received settings
05-26 00:29 DEBUG  TaskList: # Running tasklist...
05-26 00:29 DEBUG  TaskList: ## Running select_target_dir...
05-26 00:29 INFO   WindowsBackend: Installing into E:\ubuntu
05-26 00:29 DEBUG  TaskList: ## Finished select_target_dir
05-26 00:29 DEBUG  TaskList: ## Running create_dir_structure...
05-26 00:29 DEBUG  CommonBackend: Creating dir E:\ubuntu
05-26 00:29 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
05-26 00:29 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
05-26 00:29 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
05-26 00:29 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
05-26 00:29 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
05-26 00:29 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
05-26 00:29 DEBUG  TaskList: ## Finished create_dir_structure
05-26 00:29 DEBUG  TaskList: ## Running uncompress_target_dir...
05-26 00:29 DEBUG  TaskList: ## Finished uncompress_target_dir
05-26 00:29 DEBUG  TaskList: ## Running create_uninstaller...
05-26 00:29 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
05-26 00:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
05-26 00:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
05-26 00:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-26 00:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
05-26 00:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
05-26 00:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-26 00:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-26 00:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-26 00:29 DEBUG  TaskList: ## Finished create_uninstaller
05-26 00:29 DEBUG  TaskList: ## Running copy_installation_files...
05-26 00:29 DEBUG  WindowsBackend: Copying C:\Users\ANIMEM~1\AppData\Local\Temp\pyl8729.tmp\data\custom-installation -> E:\ubuntu\install\custom-installation
05-26 00:29 DEBUG  WindowsBackend: Copying C:\Users\ANIMEM~1\AppData\Local\Temp\pyl8729.tmp\winboot -> E:\ubuntu\winboot
05-26 00:29 DEBUG  WindowsBackend: Copying C:\Users\ANIMEM~1\AppData\Local\Temp\pyl8729.tmp\data\images\Ubuntu.ico -> E:\ubuntu\Ubuntu.ico
05-26 00:29 DEBUG  TaskList: ## Finished copy_installation_files
05-26 00:29 DEBUG  TaskList: ## Running get_iso...
05-26 00:29 DEBUG  TaskList: New task copy_file
05-26 00:29 DEBUG  TaskList: ### Running copy_file...
05-26 00:32 DEBUG  TaskList: ### Finished copy_file
05-26 00:32 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
05-26 00:32 DEBUG  TaskList: # Cancelling tasklist
05-26 00:32 DEBUG  TaskList: New task check_iso
05-26 00:32 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
05-26 00:32 DEBUG  CommonBackend: Searching for local ISO
05-26 00:32 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-26 00:32 DEBUG  TaskList: New task get_metalink
05-26 00:32 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-26 00:32 DEBUG  TaskList: # Cancelling tasklist
05-26 00:32 DEBUG  TaskList: # Finished tasklist
05-26 00:37 INFO   root: === wubi 9.04 rev128 ===
05-26 00:37 DEBUG  root: Logfile is c:\users\animem~1\appdata\local\temp\wubi-9.04-rev128.log
05-26 00:37 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"', '--cdmenu']
05-26 00:37 DEBUG  CommonBackend: data_dir=C:\Users\ANIMEM~1\AppData\Local\Temp\pylCC91.tmp\data
05-26 00:37 DEBUG  WindowsBackend: 7z=C:\Users\ANIMEM~1\AppData\Local\Temp\pylCC91.tmp\bin\7z.exe
05-26 00:37 DEBUG  CommonBackend: Fetching basic info...
05-26 00:37 DEBUG  CommonBackend: original_exe=F:\wubi.exe
05-26 00:37 DEBUG  CommonBackend: platform=win32
05-26 00:37 DEBUG  CommonBackend: osname=nt
05-26 00:37 DEBUG  CommonBackend: language=en_GB
05-26 00:37 DEBUG  CommonBackend: encoding=cp1252
05-26 00:37 DEBUG  WindowsBackend: arch=amd64
05-26 00:37 DEBUG  CommonBackend: Parsing isolist=C:\Users\ANIMEM~1\AppData\Local\Temp\pylCC91.tmp\data\isolist.ini
05-26 00:37 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-26 00:37 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-26 00:37 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-26 00:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-26 00:37 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-26 00:37 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-26 00:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-26 00:37 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-26 00:37 DEBUG  WindowsBackend: Fetching host info...
05-26 00:37 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-26 00:37 DEBUG  WindowsBackend: windows version=vista
05-26 00:37 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
05-26 00:37 DEBUG  WindowsBackend: windows_sp=Service Pack 1
05-26 00:37 DEBUG  WindowsBackend: windows_build=6001
05-26 00:37 DEBUG  WindowsBackend: gmt=0
05-26 00:37 DEBUG  WindowsBackend: country=GB
05-26 00:37 DEBUG  WindowsBackend: timezone=Europe/London
05-26 00:37 DEBUG  WindowsBackend: windows_username=Animemike
05-26 00:37 DEBUG  WindowsBackend: user_full_name=Animemike
05-26 00:37 DEBUG  WindowsBackend: user_directory=Animemike
05-26 00:37 DEBUG  WindowsBackend: windows_language_code=1033
05-26 00:37 DEBUG  WindowsBackend: windows_language=English
05-26 00:37 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
05-26 00:37 DEBUG  WindowsBackend: bootloader=vista
05-26 00:37 DEBUG  WindowsBackend: system_drive=Drive(C: hd 797621.839844 mb free )
05-26 00:37 DEBUG  WindowsBackend: drive=Drive(C: hd 797621.839844 mb free )
05-26 00:37 DEBUG  WindowsBackend: drive=Drive(D: hd 653792.445313 mb free ntfs)
05-26 00:37 DEBUG  WindowsBackend: drive=Drive(E: hd 99205.7890625 mb free ntfs)
05-26 00:37 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
05-26 00:37 DEBUG  WindowsBackend: drive=Drive(G: hd 882547.851563 mb free ntfs)
05-26 00:37 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
05-26 00:37 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
05-26 00:37 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
05-26 00:37 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
05-26 00:37 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
05-26 00:37 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
05-26 00:37 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-26 00:37 DEBUG  WindowsBackend: keyboard_id=134809609
05-26 00:37 DEBUG  WindowsBackend: keyboard_layout=gb
05-26 00:37 DEBUG  WindowsBackend: keyboard_variant=
05-26 00:37 DEBUG  CommonBackend: locale=en_GB.UTF-8
05-26 00:37 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
05-26 00:37 DEBUG  CommonBackend: Searching ISOs on USB devices
05-26 00:37 DEBUG  CommonBackend: Searching for local CDs
05-26 00:37 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pylCC91.tmp is a valid Ubuntu CD
05-26 00:37 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pylCC91.tmp\casper\filesystem.squashfs
05-26 00:37 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pylCC91.tmp is a valid Ubuntu CD
05-26 00:37 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pylCC91.tmp\casper\filesystem.squashfs
05-26 00:37 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pylCC91.tmp is a valid Kubuntu CD
05-26 00:37 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pylCC91.tmp\casper\filesystem.squashfs
05-26 00:37 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pylCC91.tmp is a valid Kubuntu CD
05-26 00:37 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pylCC91.tmp\casper\filesystem.squashfs
05-26 00:37 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pylCC91.tmp is a valid Xubuntu CD
05-26 00:37 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pylCC91.tmp\casper\filesystem.squashfs
05-26 00:37 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pylCC91.tmp is a valid Xubuntu CD
05-26 00:37 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pylCC91.tmp\casper\filesystem.squashfs
05-26 00:37 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pylCC91.tmp is a valid Mythbuntu CD
05-26 00:37 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pylCC91.tmp\casper\filesystem.squashfs
05-26 00:37 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pylCC91.tmp is a valid Mythbuntu CD
05-26 00:37 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pylCC91.tmp\casper\filesystem.squashfs
05-26 00:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-26 00:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-26 00:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-26 00:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-26 00:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-26 00:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-26 00:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-26 00:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-26 00:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-26 00:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-26 00:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-26 00:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-26 00:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:37 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-26 00:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:37 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-26 00:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:37 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-26 00:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:37 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-26 00:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-26 00:37 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
05-26 00:37 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
05-26 00:37 INFO   Distro: Found a valid CD for Ubuntu: F:\
05-26 00:37 INFO   root: Running the CD menu...
05-26 00:37 DEBUG  WindowsFrontend: __init__...
05-26 00:37 DEBUG  WindowsFrontend: on_init...
05-26 00:37 INFO   root: CD menu finished
05-26 00:37 INFO   root: Already installed, running the uninstaller...
05-26 00:37 INFO   root: Running the uninstaller...
05-26 00:37 INFO   CommonBackend: This is the uninstaller running
05-26 00:38 DEBUG  WindowsFrontend: frontend.on_quit
05-26 00:38 DEBUG  root: application.on_quit
05-26 00:38 INFO   root: sys.exit
05-26 00:39 INFO   root: === wubi 9.04 rev128 ===
05-26 00:39 DEBUG  root: Logfile is c:\users\animem~1\appdata\local\temp\wubi-9.04-rev128.log
05-26 00:39 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
05-26 00:39 DEBUG  CommonBackend: data_dir=C:\Users\ANIMEM~1\AppData\Local\Temp\pyl52D0.tmp\data
05-26 00:39 DEBUG  WindowsBackend: 7z=C:\Users\ANIMEM~1\AppData\Local\Temp\pyl52D0.tmp\bin\7z.exe
05-26 00:39 DEBUG  CommonBackend: Fetching basic info...
05-26 00:39 DEBUG  CommonBackend: original_exe=E:\ubuntu\uninstall-wubi.exe
05-26 00:39 DEBUG  CommonBackend: platform=win32
05-26 00:39 DEBUG  CommonBackend: osname=nt
05-26 00:39 DEBUG  CommonBackend: language=en_GB
05-26 00:39 DEBUG  CommonBackend: encoding=cp1252
05-26 00:39 DEBUG  WindowsBackend: arch=amd64
05-26 00:39 DEBUG  CommonBackend: Parsing isolist=C:\Users\ANIMEM~1\AppData\Local\Temp\pyl52D0.tmp\data\isolist.ini
05-26 00:39 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-26 00:39 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-26 00:39 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-26 00:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-26 00:39 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-26 00:39 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-26 00:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-26 00:39 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-26 00:39 DEBUG  WindowsBackend: Fetching host info...
05-26 00:39 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-26 00:39 DEBUG  WindowsBackend: windows version=vista
05-26 00:39 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
05-26 00:39 DEBUG  WindowsBackend: windows_sp=Service Pack 1
05-26 00:39 DEBUG  WindowsBackend: windows_build=6001
05-26 00:39 DEBUG  WindowsBackend: gmt=0
05-26 00:39 DEBUG  WindowsBackend: country=GB
05-26 00:39 DEBUG  WindowsBackend: timezone=Europe/London
05-26 00:39 DEBUG  WindowsBackend: windows_username=Animemike
05-26 00:39 DEBUG  WindowsBackend: user_full_name=Animemike
05-26 00:39 DEBUG  WindowsBackend: user_directory=Animemike
05-26 00:39 DEBUG  WindowsBackend: windows_language_code=1033
05-26 00:39 DEBUG  WindowsBackend: windows_language=English
05-26 00:39 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
05-26 00:39 DEBUG  WindowsBackend: bootloader=vista
05-26 00:39 DEBUG  WindowsBackend: system_drive=Drive(C: hd 790403.703125 mb free )
05-26 00:39 DEBUG  WindowsBackend: drive=Drive(C: hd 790403.703125 mb free )
05-26 00:39 DEBUG  WindowsBackend: drive=Drive(D: hd 661315.03125 mb free ntfs)
05-26 00:39 DEBUG  WindowsBackend: drive=Drive(E: hd 99205.7890625 mb free ntfs)
05-26 00:39 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
05-26 00:39 DEBUG  WindowsBackend: drive=Drive(G: hd 882547.851563 mb free ntfs)
05-26 00:39 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
05-26 00:39 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
05-26 00:39 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
05-26 00:39 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
05-26 00:39 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
05-26 00:39 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
05-26 00:39 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-26 00:39 DEBUG  WindowsBackend: keyboard_id=134809609
05-26 00:39 DEBUG  WindowsBackend: keyboard_layout=gb
05-26 00:39 DEBUG  WindowsBackend: keyboard_variant=
05-26 00:39 DEBUG  CommonBackend: locale=en_GB.UTF-8
05-26 00:39 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
05-26 00:39 DEBUG  CommonBackend: Searching ISOs on USB devices
05-26 00:39 DEBUG  CommonBackend: Searching for local CDs
05-26 00:39 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pyl52D0.tmp is a valid Ubuntu CD
05-26 00:39 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pyl52D0.tmp\casper\filesystem.squashfs
05-26 00:39 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pyl52D0.tmp is a valid Ubuntu CD
05-26 00:39 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pyl52D0.tmp\casper\filesystem.squashfs
05-26 00:39 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pyl52D0.tmp is a valid Kubuntu CD
05-26 00:39 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pyl52D0.tmp\casper\filesystem.squashfs
05-26 00:39 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pyl52D0.tmp is a valid Kubuntu CD
05-26 00:39 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pyl52D0.tmp\casper\filesystem.squashfs
05-26 00:39 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pyl52D0.tmp is a valid Xubuntu CD
05-26 00:39 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pyl52D0.tmp\casper\filesystem.squashfs
05-26 00:39 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pyl52D0.tmp is a valid Xubuntu CD
05-26 00:39 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pyl52D0.tmp\casper\filesystem.squashfs
05-26 00:39 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pyl52D0.tmp is a valid Mythbuntu CD
05-26 00:39 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pyl52D0.tmp\casper\filesystem.squashfs
05-26 00:39 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pyl52D0.tmp is a valid Mythbuntu CD
05-26 00:39 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pyl52D0.tmp\casper\filesystem.squashfs
05-26 00:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-26 00:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-26 00:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-26 00:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-26 00:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-26 00:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-26 00:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-26 00:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-26 00:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-26 00:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-26 00:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-26 00:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-26 00:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-26 00:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-26 00:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-26 00:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-26 00:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:39 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-26 00:39 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
05-26 00:39 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
05-26 00:39 INFO   Distro: Found a valid CD for Ubuntu: F:\
05-26 00:39 INFO   root: Running the uninstaller...
05-26 00:39 INFO   CommonBackend: This is the uninstaller running
05-26 00:39 DEBUG  WindowsFrontend: __init__...
05-26 00:39 DEBUG  WindowsFrontend: on_init...
05-26 00:39 INFO   root: Received settings
05-26 00:39 DEBUG  TaskList: # Running tasklist...
05-26 00:39 DEBUG  TaskList: ## Running Backup ISO...
05-26 00:39 DEBUG  TaskList: ## Finished Backup ISO
05-26 00:39 DEBUG  TaskList: ## Running Remove bootloader entry...
05-26 00:39 DEBUG  WindowsBackend: Could not find bcd id
05-26 00:39 DEBUG  WindowsBackend: undo_bootini C:
05-26 00:39 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 790403.703125 mb free )
05-26 00:39 DEBUG  WindowsBackend: undo_bootini D:
05-26 00:39 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 661315.03125 mb free ntfs)
05-26 00:39 DEBUG  WindowsBackend: undo_bootini E:
05-26 00:39 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 99205.7890625 mb free ntfs)
05-26 00:39 DEBUG  WindowsBackend: undo_bootini G:
05-26 00:39 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 882547.851563 mb free ntfs)
05-26 00:39 DEBUG  WindowsBackend: undo_bootini H:
05-26 00:39 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
05-26 00:39 DEBUG  WindowsBackend: undo_bootini I:
05-26 00:39 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
05-26 00:39 DEBUG  WindowsBackend: undo_bootini J:
05-26 00:39 DEBUG  WindowsBackend: undo_configsys Drive(J: removable 0.0 mb free )
05-26 00:39 DEBUG  WindowsBackend: undo_bootini K:
05-26 00:39 DEBUG  WindowsBackend: undo_configsys Drive(K: removable 0.0 mb free )
05-26 00:39 DEBUG  TaskList: ## Finished Remove bootloader entry
05-26 00:39 DEBUG  TaskList: ## Running Remove target dir...
05-26 00:39 DEBUG  CommonBackend: Deleting E:\ubuntu
05-26 00:39 DEBUG  TaskList: ## Finished Remove target dir
05-26 00:39 DEBUG  TaskList: ## Running Remove registry key...
05-26 00:39 DEBUG  TaskList: ## Finished Remove registry key
05-26 00:39 DEBUG  TaskList: # Finished tasklist
05-26 00:39 INFO   root: Almost finished uninstalling
05-26 00:40 INFO   root: Finished uninstallation
05-26 00:40 DEBUG  root: application.quit
05-26 00:40 DEBUG  WindowsFrontend: frontend.quit
05-26 00:40 DEBUG  WindowsFrontend: frontend.on_quit
05-26 00:40 DEBUG  root: application.on_quit
05-26 00:40 INFO   root: sys.exit
05-26 00:40 INFO   root: === wubi 9.04 rev128 ===
05-26 00:40 DEBUG  root: Logfile is c:\users\animem~1\appdata\local\temp\wubi-9.04-rev128.log
05-26 00:40 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"', '--cdmenu']
05-26 00:40 DEBUG  CommonBackend: data_dir=C:\Users\ANIMEM~1\AppData\Local\Temp\pylA498.tmp\data
05-26 00:40 DEBUG  WindowsBackend: 7z=C:\Users\ANIMEM~1\AppData\Local\Temp\pylA498.tmp\bin\7z.exe
05-26 00:40 DEBUG  CommonBackend: Fetching basic info...
05-26 00:40 DEBUG  CommonBackend: original_exe=F:\wubi.exe
05-26 00:40 DEBUG  CommonBackend: platform=win32
05-26 00:40 DEBUG  CommonBackend: osname=nt
05-26 00:40 DEBUG  CommonBackend: language=en_GB
05-26 00:40 DEBUG  CommonBackend: encoding=cp1252
05-26 00:40 DEBUG  WindowsBackend: arch=amd64
05-26 00:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\ANIMEM~1\AppData\Local\Temp\pylA498.tmp\data\isolist.ini
05-26 00:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-26 00:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-26 00:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-26 00:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-26 00:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-26 00:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-26 00:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-26 00:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-26 00:40 DEBUG  WindowsBackend: Fetching host info...
05-26 00:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-26 00:40 DEBUG  WindowsBackend: windows version=vista
05-26 00:40 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
05-26 00:40 DEBUG  WindowsBackend: windows_sp=Service Pack 1
05-26 00:40 DEBUG  WindowsBackend: windows_build=6001
05-26 00:40 DEBUG  WindowsBackend: gmt=0
05-26 00:40 DEBUG  WindowsBackend: country=GB
05-26 00:40 DEBUG  WindowsBackend: timezone=Europe/London
05-26 00:40 DEBUG  WindowsBackend: windows_username=Animemike
05-26 00:40 DEBUG  WindowsBackend: user_full_name=Animemike
05-26 00:40 DEBUG  WindowsBackend: user_directory=Animemike
05-26 00:40 DEBUG  WindowsBackend: windows_language_code=1033
05-26 00:40 DEBUG  WindowsBackend: windows_language=English
05-26 00:40 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
05-26 00:40 DEBUG  WindowsBackend: bootloader=vista
05-26 00:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 789611.292969 mb free )
05-26 00:40 DEBUG  WindowsBackend: drive=Drive(C: hd 789611.292969 mb free )
05-26 00:40 DEBUG  WindowsBackend: drive=Drive(D: hd 661982.628906 mb free ntfs)
05-26 00:40 DEBUG  WindowsBackend: drive=Drive(E: hd 99905.703125 mb free ntfs)
05-26 00:40 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
05-26 00:40 DEBUG  WindowsBackend: drive=Drive(G: hd 882547.851563 mb free ntfs)
05-26 00:40 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
05-26 00:40 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
05-26 00:40 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
05-26 00:40 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
05-26 00:40 DEBUG  WindowsBackend: uninstaller_path=None
05-26 00:40 DEBUG  WindowsBackend: previous_target_dir=None
05-26 00:40 DEBUG  WindowsBackend: previous_distro_name=None
05-26 00:40 DEBUG  WindowsBackend: keyboard_id=134809609
05-26 00:40 DEBUG  WindowsBackend: keyboard_layout=gb
05-26 00:40 DEBUG  WindowsBackend: keyboard_variant=
05-26 00:40 DEBUG  CommonBackend: locale=en_GB.UTF-8
05-26 00:40 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
05-26 00:40 DEBUG  CommonBackend: Searching ISOs on USB devices
05-26 00:40 DEBUG  CommonBackend: Searching for local CDs
05-26 00:40 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pylA498.tmp is a valid Ubuntu CD
05-26 00:40 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pylA498.tmp\casper\filesystem.squashfs
05-26 00:40 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pylA498.tmp is a valid Ubuntu CD
05-26 00:40 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pylA498.tmp\casper\filesystem.squashfs
05-26 00:40 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pylA498.tmp is a valid Kubuntu CD
05-26 00:40 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pylA498.tmp\casper\filesystem.squashfs
05-26 00:40 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pylA498.tmp is a valid Kubuntu CD
05-26 00:40 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pylA498.tmp\casper\filesystem.squashfs
05-26 00:40 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pylA498.tmp is a valid Xubuntu CD
05-26 00:40 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pylA498.tmp\casper\filesystem.squashfs
05-26 00:40 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pylA498.tmp is a valid Xubuntu CD
05-26 00:40 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pylA498.tmp\casper\filesystem.squashfs
05-26 00:40 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pylA498.tmp is a valid Mythbuntu CD
05-26 00:40 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pylA498.tmp\casper\filesystem.squashfs
05-26 00:40 DEBUG  Distro:   checking whether C:\Users\ANIMEM~1\AppData\Local\Temp\pylA498.tmp is a valid Mythbuntu CD
05-26 00:40 DEBUG  Distro:     does not contain C:\Users\ANIMEM~1\AppData\Local\Temp\pylA498.tmp\casper\filesystem.squashfs
05-26 00:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-26 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-26 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-26 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-26 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-26 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-26 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-26 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-26 00:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 00:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-26 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-26 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-26 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-26 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-26 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-26 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-26 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-26 00:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 00:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-26 00:40 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
05-26 00:40 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
05-26 00:40 INFO   Distro: Found a valid CD for Ubuntu: F:\
05-26 00:40 INFO   root: Running the CD menu...
05-26 00:40 DEBUG  WindowsFrontend: __init__...
05-26 00:40 DEBUG  WindowsFrontend: on_init...
05-26 00:40 INFO   root: CD menu finished
05-26 00:40 INFO   root: Running the installer...
05-26 00:40 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=17000MB, distro_name=Ubuntu, language=English, username=animemike
05-26 00:40 INFO   root: Received settings
05-26 00:40 DEBUG  TaskList: # Running tasklist...
05-26 00:40 DEBUG  TaskList: ## Running select_target_dir...
05-26 00:40 INFO   WindowsBackend: Installing into E:\ubuntu
05-26 00:40 DEBUG  TaskList: ## Finished select_target_dir
05-26 00:40 DEBUG  TaskList: ## Running create_dir_structure...
05-26 00:40 DEBUG  CommonBackend: Creating dir E:\ubuntu
05-26 00:40 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
05-26 00:40 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
05-26 00:40 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
05-26 00:40 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
05-26 00:40 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
05-26 00:40 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
05-26 00:40 DEBUG  TaskList: ## Finished create_dir_structure
05-26 00:40 DEBUG  TaskList: ## Running uncompress_target_dir...
05-26 00:40 DEBUG  TaskList: ## Finished uncompress_target_dir
05-26 00:40 DEBUG  TaskList: ## Running create_uninstaller...
05-26 00:40 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
05-26 00:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
05-26 00:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
05-26 00:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-26 00:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
05-26 00:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
05-26 00:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-26 00:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-26 00:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-26 00:40 DEBUG  TaskList: ## Finished create_uninstaller
05-26 00:40 DEBUG  TaskList: ## Running copy_installation_files...
05-26 00:40 DEBUG  WindowsBackend: Copying C:\Users\ANIMEM~1\AppData\Local\Temp\pylA498.tmp\data\custom-installation -> E:\ubuntu\install\custom-installation
05-26 00:40 DEBUG  WindowsBackend: Copying C:\Users\ANIMEM~1\AppData\Local\Temp\pylA498.tmp\winboot -> E:\ubuntu\winboot
05-26 00:40 DEBUG  WindowsBackend: Copying C:\Users\ANIMEM~1\AppData\Local\Temp\pylA498.tmp\data\images\Ubuntu.ico -> E:\ubuntu\Ubuntu.ico
05-26 00:40 DEBUG  TaskList: ## Finished copy_installation_files
05-26 00:40 DEBUG  TaskList: ## Running get_iso...
05-26 00:40 DEBUG  TaskList: New task copy_file
05-26 00:40 DEBUG  TaskList: ### Running copy_file...
05-26 00:45 DEBUG  TaskList: ### Finished copy_file
05-26 00:45 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
05-26 00:45 DEBUG  TaskList: # Cancelling tasklist
05-26 00:45 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
05-26 00:45 DEBUG  TaskList: New task check_iso
05-26 00:45 DEBUG  CommonBackend: Searching for local ISO
05-26 00:45 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-26 00:45 DEBUG  TaskList: New task get_metalink
05-26 00:45 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-26 00:45 DEBUG  TaskList: # Cancelling tasklist
05-26 00:45 DEBUG  TaskList: # Finished tasklist

```

---

### Post by Animemike on 2009-05-25
Fixed it if anyone else has this problem you need the ISO in the same file^^
 
Didnt work from the CD/DVD
 
Cheers

---

### Post by Animemike on 2009-05-25
Just got back in and how do i try it  lol? 
How do i lauch it in vista?

Cheers

---

