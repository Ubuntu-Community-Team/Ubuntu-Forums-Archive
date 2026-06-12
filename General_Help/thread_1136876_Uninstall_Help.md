---
title: "Uninstall Help"
date: 2009-04-25
forum: General Help
---

### Post by zoso375 on 2009-04-25
I've searched the forums for the same problem, and found many very similar, but none actually help in this case.  I installed Kubuntu 9.04 beta (having used Ubuntu frequently before, I wanted to try KDE).  I guess I still like Gnome.  When 9.04 came out of beta, I downloaded the .iso and tried to install inside Windows.  I'd rather not partition the HD.  However, I cannot uninstall Kubuntu to install Ubuntu.  Some digging tells me that the wubi installer cannot delete bcdedit.exe (file not found).  It is there, of course. At this point, Wubi closes out.  I tried simply deleting the Kubuntu file, and running. According to Wubi, mission accomplished.  However, it doesn't add Ubuntu to the boot menu.  So, my question: how do I finally, completely uninstall 9.04 beta if Wubi can't find bcdedit.exe? Thanks for suggestions in advance.

---

### Post by zoso375 on 2009-04-25
Quick update: Here's the log file.

04-24 20:42 INFO   root: === wubi 9.04 rev128 ===
04-24 20:42 DEBUG  root: Logfile is c:\users\zoso\appdata\local\temp\wubi-9.04-rev128.log
04-24 20:42 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"', '--cdmenu']
04-24 20:42 DEBUG  CommonBackend: data_dir=C:\Users\Zoso\AppData\Local\Temp\pylB70E.tmp\data
04-24 20:42 DEBUG  WindowsBackend: 7z=C:\Users\Zoso\AppData\Local\Temp\pylB70E.tmp\bin\7z.exe
04-24 20:42 DEBUG  CommonBackend: Fetching basic info...
04-24 20:42 DEBUG  CommonBackend: original_exe=F:\wubi.exe
04-24 20:42 DEBUG  CommonBackend: platform=win32
04-24 20:42 DEBUG  CommonBackend: osname=nt
04-24 20:42 DEBUG  CommonBackend: language=en_US
04-24 20:42 DEBUG  CommonBackend: encoding=cp1252
04-24 20:42 DEBUG  WindowsBackend: arch=amd64
04-24 20:42 DEBUG  CommonBackend: Parsing isolist=C:\Users\Zoso\AppData\Local\Temp\pylB70E.tmp\data\isolist.ini
04-24 20:42 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-24 20:42 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-24 20:42 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-24 20:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-24 20:42 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-24 20:42 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-24 20:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-24 20:42 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-24 20:42 DEBUG  WindowsBackend: Fetching host info...
04-24 20:42 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-24 20:42 DEBUG  WindowsBackend: windows version=vista
04-24 20:42 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
04-24 20:42 DEBUG  WindowsBackend: windows_sp=Service Pack 1
04-24 20:42 DEBUG  WindowsBackend: windows_build=6001
04-24 20:42 DEBUG  WindowsBackend: gmt=-5
04-24 20:42 DEBUG  WindowsBackend: country=US
04-24 20:42 DEBUG  WindowsBackend: timezone=America/New_York
04-24 20:42 DEBUG  WindowsBackend: windows_username=Zoso
04-24 20:42 DEBUG  WindowsBackend: user_full_name=Zoso
04-24 20:42 DEBUG  WindowsBackend: user_directory=Zoso
04-24 20:42 DEBUG  WindowsBackend: windows_language_code=1033
04-24 20:42 DEBUG  WindowsBackend: windows_language=English
04-24 20:42 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
04-24 20:42 DEBUG  WindowsBackend: bootloader=vista
04-24 20:42 DEBUG  WindowsBackend: system_drive=Drive(C: hd 135662.664063 mb free )
04-24 20:42 DEBUG  WindowsBackend: drive=Drive(C: hd 135662.664063 mb free )
04-24 20:42 DEBUG  WindowsBackend: drive=Drive(D: hd 696.34375 mb free ntfs)
04-24 20:42 DEBUG  WindowsBackend: drive=Drive(E: hd 8165.1953125 mb free ntfs)
04-24 20:42 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
04-24 20:42 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
04-24 20:42 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
04-24 20:42 DEBUG  WindowsBackend: drive=Drive(J: removable 1902.4375 mb free fat)
04-24 20:42 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
04-24 20:42 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-24 20:42 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-24 20:42 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
04-24 20:42 DEBUG  WindowsBackend: keyboard_id=67699721
04-24 20:42 DEBUG  WindowsBackend: keyboard_layout=us
04-24 20:42 DEBUG  WindowsBackend: keyboard_variant=
04-24 20:42 DEBUG  CommonBackend: locale=en_US.UTF-8
04-24 20:42 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
04-24 20:42 DEBUG  CommonBackend: Searching ISOs on USB devices
04-24 20:42 DEBUG  CommonBackend: Searching for local CDs
04-24 20:42 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pylB70E.tmp is a valid Ubuntu CD
04-24 20:42 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pylB70E.tmp\casper\filesystem.squashfs
04-24 20:42 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pylB70E.tmp is a valid Ubuntu CD
04-24 20:42 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pylB70E.tmp\casper\filesystem.squashfs
04-24 20:42 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pylB70E.tmp is a valid Kubuntu CD
04-24 20:42 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pylB70E.tmp\casper\filesystem.squashfs
04-24 20:42 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pylB70E.tmp is a valid Kubuntu CD
04-24 20:42 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pylB70E.tmp\casper\filesystem.squashfs
04-24 20:42 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pylB70E.tmp is a valid Xubuntu CD
04-24 20:42 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pylB70E.tmp\casper\filesystem.squashfs
04-24 20:42 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pylB70E.tmp is a valid Xubuntu CD
04-24 20:42 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pylB70E.tmp\casper\filesystem.squashfs
04-24 20:42 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pylB70E.tmp is a valid Mythbuntu CD
04-24 20:42 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pylB70E.tmp\casper\filesystem.squashfs
04-24 20:42 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pylB70E.tmp is a valid Mythbuntu CD
04-24 20:42 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pylB70E.tmp\casper\filesystem.squashfs
04-24 20:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-24 20:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 20:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-24 20:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 20:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-24 20:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 20:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-24 20:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 20:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-24 20:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 20:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-24 20:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 20:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-24 20:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 20:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-24 20:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 20:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-24 20:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 20:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-24 20:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 20:42 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-24 20:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 20:42 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-24 20:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 20:42 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-24 20:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 20:42 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-24 20:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 20:42 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-24 20:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 20:42 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-24 20:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 20:42 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-24 20:42 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
04-24 20:42 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
04-24 20:42 INFO   Distro: Found a valid CD for Ubuntu: F:\
04-24 20:42 INFO   root: Running the CD menu...
04-24 20:42 DEBUG  WindowsFrontend: __init__...
04-24 20:42 DEBUG  WindowsFrontend: on_init...
04-24 20:42 INFO   root: CD menu finished
04-24 20:42 INFO   root: Already installed, running the uninstaller...
04-24 20:42 INFO   root: Running the uninstaller...
04-24 20:42 INFO   CommonBackend: Launching previous uninestaller C:\ubuntu\uninstall-wubi.exe
04-24 20:43 DEBUG  root: application.quit
04-24 20:43 DEBUG  WindowsFrontend: frontend.quit
04-24 20:43 DEBUG  WindowsFrontend: frontend.on_quit
04-24 20:43 DEBUG  root: application.on_quit
04-24 20:43 INFO   root: sys.exit
04-24 22:31 INFO   root: === wubi 9.04 rev128 ===
04-24 22:31 DEBUG  root: Logfile is c:\users\zoso\appdata\local\temp\wubi-9.04-rev128.log
04-24 22:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"', '--cdmenu']
04-24 22:31 DEBUG  CommonBackend: data_dir=C:\Users\Zoso\AppData\Local\Temp\pyl9878.tmp\data
04-24 22:31 DEBUG  WindowsBackend: 7z=C:\Users\Zoso\AppData\Local\Temp\pyl9878.tmp\bin\7z.exe
04-24 22:31 DEBUG  CommonBackend: Fetching basic info...
04-24 22:31 DEBUG  CommonBackend: original_exe=F:\wubi.exe
04-24 22:31 DEBUG  CommonBackend: platform=win32
04-24 22:31 DEBUG  CommonBackend: osname=nt
04-24 22:31 DEBUG  CommonBackend: language=en_US
04-24 22:31 DEBUG  CommonBackend: encoding=cp1252
04-24 22:31 DEBUG  WindowsBackend: arch=amd64
04-24 22:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\Zoso\AppData\Local\Temp\pyl9878.tmp\data\isolist.ini
04-24 22:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-24 22:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-24 22:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-24 22:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-24 22:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-24 22:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-24 22:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-24 22:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-24 22:31 DEBUG  WindowsBackend: Fetching host info...
04-24 22:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-24 22:31 DEBUG  WindowsBackend: windows version=vista
04-24 22:31 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
04-24 22:31 DEBUG  WindowsBackend: windows_sp=Service Pack 1
04-24 22:31 DEBUG  WindowsBackend: windows_build=6001
04-24 22:31 DEBUG  WindowsBackend: gmt=-5
04-24 22:31 DEBUG  WindowsBackend: country=US
04-24 22:31 DEBUG  WindowsBackend: timezone=America/New_York
04-24 22:31 DEBUG  WindowsBackend: windows_username=Zoso
04-24 22:31 DEBUG  WindowsBackend: user_full_name=Zoso
04-24 22:31 DEBUG  WindowsBackend: user_directory=Zoso
04-24 22:31 DEBUG  WindowsBackend: windows_language_code=1033
04-24 22:31 DEBUG  WindowsBackend: windows_language=English
04-24 22:31 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
04-24 22:31 DEBUG  WindowsBackend: bootloader=vista
04-24 22:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 153335.757813 mb free )
04-24 22:31 DEBUG  WindowsBackend: drive=Drive(C: hd 153335.757813 mb free )
04-24 22:31 DEBUG  WindowsBackend: drive=Drive(D: hd 696.34375 mb free ntfs)
04-24 22:31 DEBUG  WindowsBackend: drive=Drive(E: hd 8165.1953125 mb free ntfs)
04-24 22:31 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
04-24 22:31 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
04-24 22:31 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
04-24 22:31 DEBUG  WindowsBackend: drive=Drive(J: removable 1902.4375 mb free fat)
04-24 22:31 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
04-24 22:31 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-24 22:31 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-24 22:31 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
04-24 22:31 DEBUG  WindowsBackend: keyboard_id=67699721
04-24 22:31 DEBUG  WindowsBackend: keyboard_layout=us
04-24 22:31 DEBUG  WindowsBackend: keyboard_variant=
04-24 22:31 DEBUG  CommonBackend: locale=en_US.UTF-8
04-24 22:31 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
04-24 22:31 DEBUG  CommonBackend: Searching ISOs on USB devices
04-24 22:31 DEBUG  CommonBackend: Searching for local CDs
04-24 22:31 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl9878.tmp is a valid Ubuntu CD
04-24 22:31 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl9878.tmp\casper\filesystem.squashfs
04-24 22:31 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl9878.tmp is a valid Ubuntu CD
04-24 22:31 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl9878.tmp\casper\filesystem.squashfs
04-24 22:31 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl9878.tmp is a valid Kubuntu CD
04-24 22:31 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl9878.tmp\casper\filesystem.squashfs
04-24 22:31 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl9878.tmp is a valid Kubuntu CD
04-24 22:31 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl9878.tmp\casper\filesystem.squashfs
04-24 22:31 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl9878.tmp is a valid Xubuntu CD
04-24 22:31 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl9878.tmp\casper\filesystem.squashfs
04-24 22:31 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl9878.tmp is a valid Xubuntu CD
04-24 22:31 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl9878.tmp\casper\filesystem.squashfs
04-24 22:31 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl9878.tmp is a valid Mythbuntu CD
04-24 22:31 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl9878.tmp\casper\filesystem.squashfs
04-24 22:31 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl9878.tmp is a valid Mythbuntu CD
04-24 22:31 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl9878.tmp\casper\filesystem.squashfs
04-24 22:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-24 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-24 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-24 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-24 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-24 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-24 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-24 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-24 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-24 22:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-24 22:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-24 22:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-24 22:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-24 22:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-24 22:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-24 22:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-24 22:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-24 22:31 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
04-24 22:31 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
04-24 22:31 INFO   Distro: Found a valid CD for Ubuntu: F:\
04-24 22:31 INFO   root: Running the CD menu...
04-24 22:31 DEBUG  WindowsFrontend: __init__...
04-24 22:31 DEBUG  WindowsFrontend: on_init...
04-24 22:31 INFO   root: CD menu finished
04-24 22:31 INFO   root: Running the installer...
04-24 22:31 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=25000MB, distro_name=Ubuntu, language=English, username=zoso
04-24 22:31 INFO   root: Received settings
04-24 22:31 DEBUG  TaskList: # Running tasklist...
04-24 22:31 DEBUG  TaskList: ## Running select_target_dir...
04-24 22:31 INFO   WindowsBackend: Installing into C:\ubuntu
04-24 22:31 DEBUG  TaskList: ## Finished select_target_dir
04-24 22:31 DEBUG  TaskList: ## Running create_dir_structure...
04-24 22:31 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-24 22:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-24 22:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-24 22:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-24 22:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-24 22:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-24 22:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-24 22:31 DEBUG  TaskList: ## Finished create_dir_structure
04-24 22:31 DEBUG  TaskList: ## Running uncompress_target_dir...
04-24 22:31 DEBUG  TaskList: ## Finished uncompress_target_dir
04-24 22:31 DEBUG  TaskList: ## Running create_uninstaller...
04-24 22:31 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-24 22:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-24 22:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-24 22:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-24 22:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-24 22:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
04-24 22:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-24 22:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-24 22:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-24 22:31 DEBUG  TaskList: ## Finished create_uninstaller
04-24 22:31 DEBUG  TaskList: ## Running copy_installation_files...
04-24 22:31 DEBUG  WindowsBackend: Copying C:\Users\Zoso\AppData\Local\Temp\pyl9878.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-24 22:31 DEBUG  WindowsBackend: Copying C:\Users\Zoso\AppData\Local\Temp\pyl9878.tmp\winboot -> C:\ubuntu\winboot
04-24 22:31 DEBUG  WindowsBackend: Copying C:\Users\Zoso\AppData\Local\Temp\pyl9878.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-24 22:31 DEBUG  TaskList: ## Finished copy_installation_files
04-24 22:31 DEBUG  TaskList: ## Running get_iso...
04-24 22:31 DEBUG  TaskList: New task copy_file
04-24 22:31 DEBUG  TaskList: ### Running copy_file...
04-24 22:34 DEBUG  TaskList: ### Finished copy_file
04-24 22:34 DEBUG  TaskList: New task check_iso
04-24 22:34 DEBUG  TaskList: ### Running check_iso...
04-24 22:34 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
04-24 22:34 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
04-24 22:34 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
04-24 22:34 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
04-24 22:34 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
04-24 22:34 DEBUG  TaskList: New task get_metalink
04-24 22:34 DEBUG  TaskList: #### Running get_metalink...
04-24 22:34 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink) > C:\ubuntu\install
04-24 22:34 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.04-desktop-i386.metalink, url=http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink, basename=ubuntu-9.04-desktop-i386.metalink, length=19438, text=None
04-24 22:34 DEBUG  downloader: download finished (read 19438 bytes)
04-24 22:34 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink](http://releases.ubuntu.com/9.04/MD5SUMS-metalink) > C:\ubuntu\install
04-24 22:34 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=413, text=None
04-24 22:34 DEBUG  downloader: download finished (read 413 bytes)
04-24 22:34 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
04-24 22:34 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
04-24 22:34 DEBUG  downloader: download finished (read 189 bytes)
04-24 22:34 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-24 22:34 INFO   saplog: Checking block bindings..
04-24 22:34 INFO   saplog: Key verified successfully.
04-24 22:34 DEBUG  CommonBackend: metalink md5sums:
1ec553ada3a4a18fb977816ccac02dfc  ubuntu-9.04-alternate-amd64.metalink
5daf9cb57325672f0eb768d6c11888e8  ubuntu-9.04-alternate-i386.metalink
3df58e889d3613abc2347a6b0e8f4d04  ubuntu-9.04-desktop-amd64.metalink
542bc6d7988f1d2967d419c089b08f57  ubuntu-9.04-desktop-i386.metalink
ea0b13f00711ef4b2e5c772482033a1f  ubuntu-9.04-server-amd64.metalink
88e47c579eb587c8aae1a7d7737ab3f0  ubuntu-9.04-server-i386.metalink

04-24 22:34 DEBUG  TaskList: #### Finished get_metalink
04-24 22:34 DEBUG  TaskList: New task get_file_md5
04-24 22:34 DEBUG  TaskList: #### Running get_file_md5...
04-24 22:34 DEBUG  TaskList: #### Finished get_file_md5
04-24 22:34 DEBUG  TaskList: ### Finished check_iso
04-24 22:34 DEBUG  TaskList: ## Finished get_iso
04-24 22:34 DEBUG  TaskList: ## Running extract_kernel...
04-24 22:34 DEBUG  CommonBackend: Copying files from CD F:\
04-24 22:34 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
04-24 22:34 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
04-24 22:34 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = da3a16e8bd2392c4eabf52d8fc22e947 == da3a16e8bd2392c4eabf52d8fc22e947
04-24 22:34 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.gz
04-24 22:34 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.gz md5 = c0b6de16a3614614b9543ce0f474e63c == c0b6de16a3614614b9543ce0f474e63c
04-24 22:34 DEBUG  TaskList: ## Finished extract_kernel
04-24 22:34 DEBUG  TaskList: ## Running choose_disk_sizes...
04-24 22:34 DEBUG  WindowsBackend: total size=25000
  root=24744
  swap=256
  home=0
  usr=0
04-24 22:34 DEBUG  TaskList: ## Finished choose_disk_sizes
04-24 22:34 DEBUG  TaskList: ## Running create_preseed...
04-24 22:34 DEBUG  TaskList: ## Finished create_preseed
04-24 22:34 DEBUG  TaskList: ## Running modify_bootloader...
04-24 22:34 DEBUG  TaskList: New task modify_bcd
04-24 22:34 DEBUG  TaskList: ### Running modify_bcd...
04-24 22:34 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 153335.757813 mb free )
04-24 22:34 DEBUG  WindowsBackend: BCD has already been modified
04-24 22:34 DEBUG  TaskList: ### Finished modify_bcd
04-24 22:34 DEBUG  TaskList: New task modify_bcd
04-24 22:34 DEBUG  TaskList: ### Running modify_bcd...
04-24 22:34 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 696.34375 mb free ntfs)
04-24 22:34 DEBUG  WindowsBackend: BCD has already been modified
04-24 22:34 DEBUG  TaskList: ### Finished modify_bcd
04-24 22:34 DEBUG  TaskList: New task modify_bcd
04-24 22:34 DEBUG  TaskList: ### Running modify_bcd...
04-24 22:34 DEBUG  WindowsBackend: modify_bcd Drive(E: hd 8165.1953125 mb free ntfs)
04-24 22:34 DEBUG  WindowsBackend: BCD has already been modified
04-24 22:34 DEBUG  TaskList: ### Finished modify_bcd
04-24 22:34 DEBUG  TaskList: New task modify_bcd
04-24 22:34 DEBUG  TaskList: ### Running modify_bcd...
04-24 22:34 DEBUG  WindowsBackend: modify_bcd Drive(H: removable 0.0 mb free )
04-24 22:34 DEBUG  WindowsBackend: BCD has already been modified
04-24 22:34 DEBUG  TaskList: ### Finished modify_bcd
04-24 22:34 DEBUG  TaskList: New task modify_bcd
04-24 22:34 DEBUG  TaskList: ### Running modify_bcd...
04-24 22:34 DEBUG  WindowsBackend: modify_bcd Drive(I: removable 0.0 mb free )
04-24 22:34 DEBUG  WindowsBackend: BCD has already been modified
04-24 22:34 DEBUG  TaskList: ### Finished modify_bcd
04-24 22:34 DEBUG  TaskList: New task modify_bcd
04-24 22:34 DEBUG  TaskList: ### Running modify_bcd...
04-24 22:34 DEBUG  WindowsBackend: modify_bcd Drive(J: removable 1902.4375 mb free fat)
04-24 22:34 DEBUG  WindowsBackend: BCD has already been modified
04-24 22:34 DEBUG  TaskList: ### Finished modify_bcd
04-24 22:34 DEBUG  TaskList: New task modify_bcd
04-24 22:34 DEBUG  TaskList: ### Running modify_bcd...
04-24 22:34 DEBUG  WindowsBackend: modify_bcd Drive(K: removable 0.0 mb free )
04-24 22:34 DEBUG  WindowsBackend: BCD has already been modified
04-24 22:34 DEBUG  TaskList: ### Finished modify_bcd
04-24 22:34 DEBUG  TaskList: ## Finished modify_bootloader
04-24 22:34 DEBUG  TaskList: ## Running modify_grub_configuration...
04-24 22:34 DEBUG  TaskList: ## Finished modify_grub_configuration
04-24 22:34 DEBUG  TaskList: ## Running create_virtual_disks...
04-24 22:34 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\root.disk of 24744MB
04-24 22:34 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\swap.disk of 256MB
04-24 22:34 DEBUG  TaskList: ## Finished create_virtual_disks
04-24 22:34 DEBUG  TaskList: ## Running uncompress_files...
04-24 22:34 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
04-24 22:34 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
04-24 22:34 DEBUG  TaskList: ## Finished uncompress_files
04-24 22:34 DEBUG  TaskList: ## Running eject_cd...
04-24 22:35 DEBUG  TaskList: ## Finished eject_cd
04-24 22:35 DEBUG  TaskList: # Finished tasklist
04-24 22:35 INFO   root: Almost finished installing
04-24 22:35 INFO   root: Finished installation
04-24 22:35 INFO   root: Rebooting
04-24 22:35 DEBUG  TaskList: # Running tasklist...
04-24 22:35 DEBUG  TaskList: ## Running reboot...
04-24 22:35 DEBUG  TaskList: ## Finished reboot
04-24 22:35 DEBUG  TaskList: # Finished tasklist
04-24 22:35 DEBUG  root: application.quit
04-24 22:35 DEBUG  WindowsFrontend: frontend.quit
04-24 22:35 DEBUG  WindowsFrontend: frontend.on_quit
04-24 22:35 DEBUG  root: application.on_quit
04-24 22:35 INFO   root: sys.exit
04-24 22:42 INFO   root: === wubi 9.04 rev128 ===
04-24 22:42 DEBUG  root: Logfile is c:\users\zoso\appdata\local\temp\wubi-9.04-rev128.log
04-24 22:42 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"', '--cdmenu']
04-24 22:42 DEBUG  CommonBackend: data_dir=C:\Users\Zoso\AppData\Local\Temp\pyl8D50.tmp\data
04-24 22:42 DEBUG  WindowsBackend: 7z=C:\Users\Zoso\AppData\Local\Temp\pyl8D50.tmp\bin\7z.exe
04-24 22:42 DEBUG  CommonBackend: Fetching basic info...
04-24 22:42 DEBUG  CommonBackend: original_exe=F:\wubi.exe
04-24 22:42 DEBUG  CommonBackend: platform=win32
04-24 22:42 DEBUG  CommonBackend: osname=nt
04-24 22:42 DEBUG  CommonBackend: language=en_US
04-24 22:42 DEBUG  CommonBackend: encoding=cp1252
04-24 22:42 DEBUG  WindowsBackend: arch=amd64
04-24 22:42 DEBUG  CommonBackend: Parsing isolist=C:\Users\Zoso\AppData\Local\Temp\pyl8D50.tmp\data\isolist.ini
04-24 22:42 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-24 22:42 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-24 22:42 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-24 22:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-24 22:42 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-24 22:42 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-24 22:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-24 22:42 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-24 22:42 DEBUG  WindowsBackend: Fetching host info...
04-24 22:42 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-24 22:42 DEBUG  WindowsBackend: windows version=vista
04-24 22:42 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
04-24 22:42 DEBUG  WindowsBackend: windows_sp=Service Pack 1
04-24 22:42 DEBUG  WindowsBackend: windows_build=6001
04-24 22:42 DEBUG  WindowsBackend: gmt=-5
04-24 22:42 DEBUG  WindowsBackend: country=US
04-24 22:42 DEBUG  WindowsBackend: timezone=America/New_York
04-24 22:42 DEBUG  WindowsBackend: windows_username=Zoso
04-24 22:42 DEBUG  WindowsBackend: user_full_name=Zoso
04-24 22:42 DEBUG  WindowsBackend: user_directory=Zoso
04-24 22:42 DEBUG  WindowsBackend: windows_language_code=1033
04-24 22:42 DEBUG  WindowsBackend: windows_language=English
04-24 22:42 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
04-24 22:42 DEBUG  WindowsBackend: bootloader=vista
04-24 22:42 DEBUG  WindowsBackend: system_drive=Drive(C: hd 127633.707031 mb free )
04-24 22:42 DEBUG  WindowsBackend: drive=Drive(C: hd 127633.707031 mb free )
04-24 22:42 DEBUG  WindowsBackend: drive=Drive(D: hd 696.34375 mb free ntfs)
04-24 22:42 DEBUG  WindowsBackend: drive=Drive(E: hd 8165.1953125 mb free ntfs)
04-24 22:42 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
04-24 22:42 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
04-24 22:42 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
04-24 22:42 DEBUG  WindowsBackend: drive=Drive(J: removable 1902.4375 mb free fat)
04-24 22:42 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
04-24 22:42 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-24 22:42 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-24 22:42 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-24 22:42 DEBUG  WindowsBackend: keyboard_id=67699721
04-24 22:42 DEBUG  WindowsBackend: keyboard_layout=us
04-24 22:42 DEBUG  WindowsBackend: keyboard_variant=
04-24 22:42 DEBUG  CommonBackend: locale=en_US.UTF-8
04-24 22:42 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
04-24 22:42 DEBUG  CommonBackend: Searching ISOs on USB devices
04-24 22:42 DEBUG  CommonBackend: Searching for local CDs
04-24 22:42 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl8D50.tmp is a valid Ubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl8D50.tmp\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl8D50.tmp is a valid Ubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl8D50.tmp\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl8D50.tmp is a valid Kubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl8D50.tmp\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl8D50.tmp is a valid Kubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl8D50.tmp\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl8D50.tmp is a valid Xubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl8D50.tmp\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl8D50.tmp is a valid Xubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl8D50.tmp\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl8D50.tmp is a valid Mythbuntu CD
04-24 22:42 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl8D50.tmp\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl8D50.tmp is a valid Mythbuntu CD
04-24 22:42 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl8D50.tmp\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-24 22:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-24 22:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-24 22:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-24 22:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-24 22:42 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
04-24 22:42 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
04-24 22:42 INFO   Distro: Found a valid CD for Ubuntu: F:\
04-24 22:42 INFO   root: Running the CD menu...
04-24 22:42 DEBUG  WindowsFrontend: __init__...
04-24 22:42 DEBUG  WindowsFrontend: on_init...
04-24 22:42 INFO   root: CD menu finished
04-24 22:42 INFO   root: Already installed, running the uninstaller...
04-24 22:42 INFO   root: Running the uninstaller...
04-24 22:42 INFO   CommonBackend: This is the uninstaller running
04-24 22:42 INFO   WindowsFrontend: Operation cancelled
04-24 22:42 DEBUG  WindowsFrontend: frontend.quit
04-24 22:42 DEBUG  WindowsFrontend: frontend.on_quit
04-24 22:42 DEBUG  root: application.on_quit
04-24 22:42 INFO   root: sys.exit
04-24 22:42 INFO   root: === wubi 9.04 rev128 ===
04-24 22:42 DEBUG  root: Logfile is c:\users\zoso\appdata\local\temp\wubi-9.04-rev128.log
04-24 22:42 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"', '--cdmenu']
04-24 22:42 DEBUG  CommonBackend: data_dir=C:\Users\Zoso\AppData\Local\Temp\pyl166.tmp\data
04-24 22:42 DEBUG  WindowsBackend: 7z=C:\Users\Zoso\AppData\Local\Temp\pyl166.tmp\bin\7z.exe
04-24 22:42 DEBUG  CommonBackend: Fetching basic info...
04-24 22:42 DEBUG  CommonBackend: original_exe=F:\wubi.exe
04-24 22:42 DEBUG  CommonBackend: platform=win32
04-24 22:42 DEBUG  CommonBackend: osname=nt
04-24 22:42 DEBUG  CommonBackend: language=en_US
04-24 22:42 DEBUG  CommonBackend: encoding=cp1252
04-24 22:42 DEBUG  WindowsBackend: arch=amd64
04-24 22:42 DEBUG  CommonBackend: Parsing isolist=C:\Users\Zoso\AppData\Local\Temp\pyl166.tmp\data\isolist.ini
04-24 22:42 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-24 22:42 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-24 22:42 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-24 22:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-24 22:42 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-24 22:42 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-24 22:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-24 22:42 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-24 22:42 DEBUG  WindowsBackend: Fetching host info...
04-24 22:42 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-24 22:42 DEBUG  WindowsBackend: windows version=vista
04-24 22:42 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
04-24 22:42 DEBUG  WindowsBackend: windows_sp=Service Pack 1
04-24 22:42 DEBUG  WindowsBackend: windows_build=6001
04-24 22:42 DEBUG  WindowsBackend: gmt=-5
04-24 22:42 DEBUG  WindowsBackend: country=US
04-24 22:42 DEBUG  WindowsBackend: timezone=America/New_York
04-24 22:42 DEBUG  WindowsBackend: windows_username=Zoso
04-24 22:42 DEBUG  WindowsBackend: user_full_name=Zoso
04-24 22:42 DEBUG  WindowsBackend: user_directory=Zoso
04-24 22:42 DEBUG  WindowsBackend: windows_language_code=1033
04-24 22:42 DEBUG  WindowsBackend: windows_language=English
04-24 22:42 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
04-24 22:42 DEBUG  WindowsBackend: bootloader=vista
04-24 22:42 DEBUG  WindowsBackend: system_drive=Drive(C: hd 127633.015625 mb free )
04-24 22:42 DEBUG  WindowsBackend: drive=Drive(C: hd 127633.015625 mb free )
04-24 22:42 DEBUG  WindowsBackend: drive=Drive(D: hd 696.34375 mb free ntfs)
04-24 22:42 DEBUG  WindowsBackend: drive=Drive(E: hd 8165.1953125 mb free ntfs)
04-24 22:42 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
04-24 22:42 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
04-24 22:42 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
04-24 22:42 DEBUG  WindowsBackend: drive=Drive(J: removable 1902.4375 mb free fat)
04-24 22:42 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
04-24 22:42 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-24 22:42 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-24 22:42 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-24 22:42 DEBUG  WindowsBackend: keyboard_id=67699721
04-24 22:42 DEBUG  WindowsBackend: keyboard_layout=us
04-24 22:42 DEBUG  WindowsBackend: keyboard_variant=
04-24 22:42 DEBUG  CommonBackend: locale=en_US.UTF-8
04-24 22:42 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
04-24 22:42 DEBUG  CommonBackend: Searching ISOs on USB devices
04-24 22:42 DEBUG  CommonBackend: Searching for local CDs
04-24 22:42 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl166.tmp is a valid Ubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl166.tmp\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl166.tmp is a valid Ubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl166.tmp\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl166.tmp is a valid Kubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl166.tmp\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl166.tmp is a valid Kubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl166.tmp\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl166.tmp is a valid Xubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl166.tmp\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl166.tmp is a valid Xubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl166.tmp\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl166.tmp is a valid Mythbuntu CD
04-24 22:42 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl166.tmp\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl166.tmp is a valid Mythbuntu CD
04-24 22:42 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl166.tmp\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-24 22:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-24 22:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-24 22:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-24 22:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-24 22:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:42 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-24 22:42 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
04-24 22:42 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
04-24 22:42 INFO   Distro: Found a valid CD for Ubuntu: F:\
04-24 22:42 INFO   root: Running the CD menu...
04-24 22:42 DEBUG  WindowsFrontend: __init__...
04-24 22:42 DEBUG  WindowsFrontend: on_init...
04-24 22:42 INFO   root: CD menu finished
04-24 22:42 INFO   root: Already installed, running the uninstaller...
04-24 22:42 INFO   root: Running the uninstaller...
04-24 22:42 INFO   CommonBackend: This is the uninstaller running
04-24 22:42 INFO   root: Received settings
04-24 22:42 DEBUG  TaskList: # Running tasklist...
04-24 22:42 DEBUG  TaskList: ## Running Backup ISO...
04-24 22:42 DEBUG  TaskList: ## Finished Backup ISO
04-24 22:42 DEBUG  TaskList: ## Running Remove bootloader entry...
04-24 22:42 DEBUG  WindowsBackend: Removing bcd entry {8f45b05d-1bbe-11de-b4e0-001a92231f8d}
04-24 22:42 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {8f45b05d-1bbe-11de-b4e0-001a92231f8d} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\win32\backend.py", line 495, in undo_bootloader
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\win32\backend.py", line 678, in undo_bcd
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 60, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {8f45b05d-1bbe-11de-b4e0-001a92231f8d} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
04-24 22:42 DEBUG  TaskList: # Cancelling tasklist
04-24 22:42 DEBUG  TaskList: # Finished tasklist
04-24 22:42 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {8f45b05d-1bbe-11de-b4e0-001a92231f8d} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 142, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 176, in run_uninstaller
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {8f45b05d-1bbe-11de-b4e0-001a92231f8d} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
04-24 22:46 INFO   root: === wubi 9.04 rev128 ===
04-24 22:46 DEBUG  root: Logfile is c:\users\zoso\appdata\local\temp\wubi-9.04-rev128.log
04-24 22:46 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"', '--cdmenu']
04-24 22:46 DEBUG  CommonBackend: data_dir=C:\Users\Zoso\AppData\Local\Temp\pyl8DBD.tmp\data
04-24 22:46 DEBUG  WindowsBackend: 7z=C:\Users\Zoso\AppData\Local\Temp\pyl8DBD.tmp\bin\7z.exe
04-24 22:46 DEBUG  CommonBackend: Fetching basic info...
04-24 22:46 DEBUG  CommonBackend: original_exe=F:\wubi.exe
04-24 22:46 DEBUG  CommonBackend: platform=win32
04-24 22:46 DEBUG  CommonBackend: osname=nt
04-24 22:46 DEBUG  CommonBackend: language=en_US
04-24 22:46 DEBUG  CommonBackend: encoding=cp1252
04-24 22:46 DEBUG  WindowsBackend: arch=amd64
04-24 22:46 DEBUG  CommonBackend: Parsing isolist=C:\Users\Zoso\AppData\Local\Temp\pyl8DBD.tmp\data\isolist.ini
04-24 22:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-24 22:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-24 22:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-24 22:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-24 22:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-24 22:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-24 22:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-24 22:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-24 22:46 DEBUG  WindowsBackend: Fetching host info...
04-24 22:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-24 22:46 DEBUG  WindowsBackend: windows version=vista
04-24 22:46 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
04-24 22:46 DEBUG  WindowsBackend: windows_sp=Service Pack 1
04-24 22:46 DEBUG  WindowsBackend: windows_build=6001
04-24 22:46 DEBUG  WindowsBackend: gmt=-5
04-24 22:46 DEBUG  WindowsBackend: country=US
04-24 22:46 DEBUG  WindowsBackend: timezone=America/New_York
04-24 22:46 DEBUG  WindowsBackend: windows_username=Zoso
04-24 22:46 DEBUG  WindowsBackend: user_full_name=Zoso
04-24 22:46 DEBUG  WindowsBackend: user_directory=Zoso
04-24 22:46 DEBUG  WindowsBackend: windows_language_code=1033
04-24 22:46 DEBUG  WindowsBackend: windows_language=English
04-24 22:46 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
04-24 22:46 DEBUG  WindowsBackend: bootloader=vista
04-24 22:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 127629.617188 mb free )
04-24 22:46 DEBUG  WindowsBackend: drive=Drive(C: hd 127629.617188 mb free )
04-24 22:46 DEBUG  WindowsBackend: drive=Drive(D: hd 696.34375 mb free ntfs)
04-24 22:46 DEBUG  WindowsBackend: drive=Drive(E: hd 8165.1953125 mb free ntfs)
04-24 22:46 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
04-24 22:46 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
04-24 22:46 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
04-24 22:46 DEBUG  WindowsBackend: drive=Drive(J: removable 1902.4375 mb free fat)
04-24 22:46 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
04-24 22:46 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-24 22:46 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-24 22:46 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-24 22:46 DEBUG  WindowsBackend: keyboard_id=67699721
04-24 22:46 DEBUG  WindowsBackend: keyboard_layout=us
04-24 22:46 DEBUG  WindowsBackend: keyboard_variant=
04-24 22:46 DEBUG  CommonBackend: locale=en_US.UTF-8
04-24 22:46 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
04-24 22:46 DEBUG  CommonBackend: Searching ISOs on USB devices
04-24 22:46 DEBUG  CommonBackend: Searching for local CDs
04-24 22:46 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl8DBD.tmp is a valid Ubuntu CD
04-24 22:46 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl8DBD.tmp\casper\filesystem.squashfs
04-24 22:46 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl8DBD.tmp is a valid Ubuntu CD
04-24 22:46 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl8DBD.tmp\casper\filesystem.squashfs
04-24 22:46 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl8DBD.tmp is a valid Kubuntu CD
04-24 22:46 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl8DBD.tmp\casper\filesystem.squashfs
04-24 22:46 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl8DBD.tmp is a valid Kubuntu CD
04-24 22:46 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl8DBD.tmp\casper\filesystem.squashfs
04-24 22:46 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl8DBD.tmp is a valid Xubuntu CD
04-24 22:46 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl8DBD.tmp\casper\filesystem.squashfs
04-24 22:46 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl8DBD.tmp is a valid Xubuntu CD
04-24 22:46 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl8DBD.tmp\casper\filesystem.squashfs
04-24 22:46 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl8DBD.tmp is a valid Mythbuntu CD
04-24 22:46 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl8DBD.tmp\casper\filesystem.squashfs
04-24 22:46 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl8DBD.tmp is a valid Mythbuntu CD
04-24 22:46 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl8DBD.tmp\casper\filesystem.squashfs
04-24 22:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-24 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-24 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-24 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-24 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-24 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-24 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-24 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-24 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-24 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-24 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-24 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-24 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-24 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-24 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-24 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-24 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-24 22:46 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
04-24 22:46 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
04-24 22:46 INFO   Distro: Found a valid CD for Ubuntu: F:\
04-24 22:46 INFO   root: Running the CD menu...
04-24 22:46 DEBUG  WindowsFrontend: __init__...
04-24 22:46 DEBUG  WindowsFrontend: on_init...
04-24 22:46 INFO   root: CD menu finished
04-24 22:46 INFO   root: Already installed, running the uninstaller...
04-24 22:46 INFO   root: Running the uninstaller...
04-24 22:46 INFO   CommonBackend: This is the uninstaller running
04-24 22:46 INFO   root: Received settings
04-24 22:46 DEBUG  TaskList: # Running tasklist...
04-24 22:46 DEBUG  TaskList: ## Running Backup ISO...
04-24 22:46 DEBUG  TaskList: ## Finished Backup ISO
04-24 22:46 DEBUG  TaskList: ## Running Remove bootloader entry...
04-24 22:46 DEBUG  WindowsBackend: Removing bcd entry {8f45b05d-1bbe-11de-b4e0-001a92231f8d}
04-24 22:46 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {8f45b05d-1bbe-11de-b4e0-001a92231f8d} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\win32\backend.py", line 495, in undo_bootloader
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\win32\backend.py", line 678, in undo_bcd
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 60, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {8f45b05d-1bbe-11de-b4e0-001a92231f8d} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
04-24 22:46 DEBUG  TaskList: # Cancelling tasklist
04-24 22:46 DEBUG  TaskList: # Finished tasklist
04-24 22:46 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {8f45b05d-1bbe-11de-b4e0-001a92231f8d} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 142, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 176, in run_uninstaller
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {8f45b05d-1bbe-11de-b4e0-001a92231f8d} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
04-24 22:57 INFO   root: === wubi 9.04 rev128 ===
04-24 22:57 DEBUG  root: Logfile is c:\users\zoso\appdata\local\temp\wubi-9.04-rev128.log
04-24 22:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"', '--cdmenu']
04-24 22:57 DEBUG  CommonBackend: data_dir=C:\Users\Zoso\AppData\Local\Temp\pyl972.tmp\data
04-24 22:57 DEBUG  WindowsBackend: 7z=C:\Users\Zoso\AppData\Local\Temp\pyl972.tmp\bin\7z.exe
04-24 22:57 DEBUG  CommonBackend: Fetching basic info...
04-24 22:57 DEBUG  CommonBackend: original_exe=F:\wubi.exe
04-24 22:57 DEBUG  CommonBackend: platform=win32
04-24 22:57 DEBUG  CommonBackend: osname=nt
04-24 22:57 DEBUG  CommonBackend: language=en_US
04-24 22:57 DEBUG  CommonBackend: encoding=cp1252
04-24 22:57 DEBUG  WindowsBackend: arch=amd64
04-24 22:57 DEBUG  CommonBackend: Parsing isolist=C:\Users\Zoso\AppData\Local\Temp\pyl972.tmp\data\isolist.ini
04-24 22:57 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-24 22:57 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-24 22:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-24 22:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-24 22:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-24 22:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-24 22:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-24 22:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-24 22:57 DEBUG  WindowsBackend: Fetching host info...
04-24 22:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-24 22:57 DEBUG  WindowsBackend: windows version=vista
04-24 22:57 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
04-24 22:57 DEBUG  WindowsBackend: windows_sp=Service Pack 1
04-24 22:57 DEBUG  WindowsBackend: windows_build=6001
04-24 22:57 DEBUG  WindowsBackend: gmt=-5
04-24 22:57 DEBUG  WindowsBackend: country=US
04-24 22:57 DEBUG  WindowsBackend: timezone=America/New_York
04-24 22:57 DEBUG  WindowsBackend: windows_username=Zoso
04-24 22:57 DEBUG  WindowsBackend: user_full_name=Zoso
04-24 22:57 DEBUG  WindowsBackend: user_directory=Zoso
04-24 22:57 DEBUG  WindowsBackend: windows_language_code=1033
04-24 22:57 DEBUG  WindowsBackend: windows_language=English
04-24 22:57 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
04-24 22:57 DEBUG  WindowsBackend: bootloader=vista
04-24 22:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 153339.636719 mb free )
04-24 22:57 DEBUG  WindowsBackend: drive=Drive(C: hd 153339.636719 mb free )
04-24 22:57 DEBUG  WindowsBackend: drive=Drive(D: hd 696.34375 mb free ntfs)
04-24 22:57 DEBUG  WindowsBackend: drive=Drive(E: hd 8165.1953125 mb free ntfs)
04-24 22:57 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
04-24 22:57 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
04-24 22:58 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
04-24 22:58 DEBUG  WindowsBackend: drive=Drive(J: removable 1902.4375 mb free fat)
04-24 22:58 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
04-24 22:58 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-24 22:58 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-24 22:58 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-24 22:58 DEBUG  WindowsBackend: keyboard_id=67699721
04-24 22:58 DEBUG  WindowsBackend: keyboard_layout=us
04-24 22:58 DEBUG  WindowsBackend: keyboard_variant=
04-24 22:58 DEBUG  CommonBackend: locale=en_US.UTF-8
04-24 22:58 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
04-24 22:58 DEBUG  CommonBackend: Searching ISOs on USB devices
04-24 22:58 DEBUG  CommonBackend: Searching for local CDs
04-24 22:58 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl972.tmp is a valid Ubuntu CD
04-24 22:58 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl972.tmp\casper\filesystem.squashfs
04-24 22:58 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl972.tmp is a valid Ubuntu CD
04-24 22:58 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl972.tmp\casper\filesystem.squashfs
04-24 22:58 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl972.tmp is a valid Kubuntu CD
04-24 22:58 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl972.tmp\casper\filesystem.squashfs
04-24 22:58 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl972.tmp is a valid Kubuntu CD
04-24 22:58 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl972.tmp\casper\filesystem.squashfs
04-24 22:58 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl972.tmp is a valid Xubuntu CD
04-24 22:58 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl972.tmp\casper\filesystem.squashfs
04-24 22:58 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl972.tmp is a valid Xubuntu CD
04-24 22:58 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl972.tmp\casper\filesystem.squashfs
04-24 22:58 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl972.tmp is a valid Mythbuntu CD
04-24 22:58 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl972.tmp\casper\filesystem.squashfs
04-24 22:58 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pyl972.tmp is a valid Mythbuntu CD
04-24 22:58 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pyl972.tmp\casper\filesystem.squashfs
04-24 22:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-24 22:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-24 22:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-24 22:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-24 22:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-24 22:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-24 22:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-24 22:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-24 22:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 22:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-24 22:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-24 22:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-24 22:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-24 22:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-24 22:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-24 22:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-24 22:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-24 22:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 22:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-24 22:58 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
04-24 22:58 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
04-24 22:58 INFO   Distro: Found a valid CD for Ubuntu: F:\
04-24 22:58 INFO   root: Running the CD menu...
04-24 22:58 DEBUG  WindowsFrontend: __init__...
04-24 22:58 DEBUG  WindowsFrontend: on_init...
04-24 22:58 INFO   root: CD menu finished
04-24 22:58 INFO   root: Running the installer...
04-24 22:58 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=25000MB, distro_name=Ubuntu, language=English, username=zoso
04-24 22:58 INFO   root: Received settings
04-24 22:58 DEBUG  TaskList: # Running tasklist...
04-24 22:58 DEBUG  TaskList: ## Running select_target_dir...
04-24 22:58 INFO   WindowsBackend: Installing into C:\ubuntu
04-24 22:58 DEBUG  TaskList: ## Finished select_target_dir
04-24 22:58 DEBUG  TaskList: ## Running create_dir_structure...
04-24 22:58 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-24 22:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-24 22:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-24 22:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-24 22:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-24 22:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-24 22:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-24 22:58 DEBUG  TaskList: ## Finished create_dir_structure
04-24 22:58 DEBUG  TaskList: ## Running uncompress_target_dir...
04-24 22:58 DEBUG  TaskList: ## Finished uncompress_target_dir
04-24 22:58 DEBUG  TaskList: ## Running create_uninstaller...
04-24 22:58 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-24 22:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-24 22:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-24 22:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-24 22:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-24 22:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
04-24 22:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-24 22:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-24 22:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-24 22:58 DEBUG  TaskList: ## Finished create_uninstaller
04-24 22:58 DEBUG  TaskList: ## Running copy_installation_files...
04-24 22:58 DEBUG  WindowsBackend: Copying C:\Users\Zoso\AppData\Local\Temp\pyl972.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-24 22:58 DEBUG  WindowsBackend: Copying C:\Users\Zoso\AppData\Local\Temp\pyl972.tmp\winboot -> C:\ubuntu\winboot
04-24 22:58 DEBUG  WindowsBackend: Copying C:\Users\Zoso\AppData\Local\Temp\pyl972.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-24 22:58 DEBUG  TaskList: ## Finished copy_installation_files
04-24 22:58 DEBUG  TaskList: ## Running get_iso...
04-24 22:58 DEBUG  TaskList: New task copy_file
04-24 22:58 DEBUG  TaskList: ### Running copy_file...
04-24 23:01 DEBUG  TaskList: ### Finished copy_file
04-24 23:01 DEBUG  TaskList: New task check_iso
04-24 23:01 DEBUG  TaskList: ### Running check_iso...
04-24 23:01 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
04-24 23:01 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
04-24 23:01 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
04-24 23:01 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
04-24 23:01 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
04-24 23:01 DEBUG  TaskList: New task get_metalink
04-24 23:01 DEBUG  TaskList: #### Running get_metalink...
04-24 23:01 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink) > C:\ubuntu\install
04-24 23:01 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.04-desktop-i386.metalink, url=http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink, basename=ubuntu-9.04-desktop-i386.metalink, length=19438, text=None
04-24 23:01 DEBUG  downloader: download finished (read 19438 bytes)
04-24 23:01 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink](http://releases.ubuntu.com/9.04/MD5SUMS-metalink) > C:\ubuntu\install
04-24 23:01 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=413, text=None
04-24 23:01 DEBUG  downloader: download finished (read 413 bytes)
04-24 23:01 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
04-24 23:01 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
04-24 23:01 DEBUG  downloader: download finished (read 189 bytes)
04-24 23:01 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-24 23:01 INFO   saplog: Checking block bindings..
04-24 23:01 INFO   saplog: Key verified successfully.
04-24 23:01 DEBUG  CommonBackend: metalink md5sums:
1ec553ada3a4a18fb977816ccac02dfc  ubuntu-9.04-alternate-amd64.metalink
5daf9cb57325672f0eb768d6c11888e8  ubuntu-9.04-alternate-i386.metalink
3df58e889d3613abc2347a6b0e8f4d04  ubuntu-9.04-desktop-amd64.metalink
542bc6d7988f1d2967d419c089b08f57  ubuntu-9.04-desktop-i386.metalink
ea0b13f00711ef4b2e5c772482033a1f  ubuntu-9.04-server-amd64.metalink
88e47c579eb587c8aae1a7d7737ab3f0  ubuntu-9.04-server-i386.metalink

04-24 23:01 DEBUG  TaskList: #### Finished get_metalink
04-24 23:01 DEBUG  TaskList: New task get_file_md5
04-24 23:01 DEBUG  TaskList: #### Running get_file_md5...
04-24 23:01 DEBUG  TaskList: #### Finished get_file_md5
04-24 23:01 DEBUG  TaskList: ### Finished check_iso
04-24 23:01 DEBUG  TaskList: ## Finished get_iso
04-24 23:01 DEBUG  TaskList: ## Running extract_kernel...
04-24 23:01 DEBUG  CommonBackend: Copying files from CD F:\
04-24 23:01 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
04-24 23:01 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
04-24 23:01 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = da3a16e8bd2392c4eabf52d8fc22e947 == da3a16e8bd2392c4eabf52d8fc22e947
04-24 23:01 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.gz
04-24 23:01 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.gz md5 = c0b6de16a3614614b9543ce0f474e63c == c0b6de16a3614614b9543ce0f474e63c
04-24 23:01 DEBUG  TaskList: ## Finished extract_kernel
04-24 23:01 DEBUG  TaskList: ## Running choose_disk_sizes...
04-24 23:01 DEBUG  WindowsBackend: total size=25000
  root=24744
  swap=256
  home=0
  usr=0
04-24 23:01 DEBUG  TaskList: ## Finished choose_disk_sizes
04-24 23:01 DEBUG  TaskList: ## Running create_preseed...
04-24 23:01 DEBUG  TaskList: ## Finished create_preseed
04-24 23:01 DEBUG  TaskList: ## Running modify_bootloader...
04-24 23:01 DEBUG  TaskList: New task modify_bcd
04-24 23:01 DEBUG  TaskList: ### Running modify_bcd...
04-24 23:01 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 153339.636719 mb free )
04-24 23:01 DEBUG  WindowsBackend: BCD has already been modified
04-24 23:01 DEBUG  TaskList: ### Finished modify_bcd
04-24 23:01 DEBUG  TaskList: New task modify_bcd
04-24 23:01 DEBUG  TaskList: ### Running modify_bcd...
04-24 23:01 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 696.34375 mb free ntfs)
04-24 23:01 DEBUG  WindowsBackend: BCD has already been modified
04-24 23:01 DEBUG  TaskList: ### Finished modify_bcd
04-24 23:01 DEBUG  TaskList: New task modify_bcd
04-24 23:01 DEBUG  TaskList: ### Running modify_bcd...
04-24 23:01 DEBUG  WindowsBackend: modify_bcd Drive(E: hd 8165.1953125 mb free ntfs)
04-24 23:01 DEBUG  WindowsBackend: BCD has already been modified
04-24 23:01 DEBUG  TaskList: ### Finished modify_bcd
04-24 23:01 DEBUG  TaskList: New task modify_bcd
04-24 23:01 DEBUG  TaskList: ### Running modify_bcd...
04-24 23:01 DEBUG  WindowsBackend: modify_bcd Drive(H: removable 0.0 mb free )
04-24 23:01 DEBUG  WindowsBackend: BCD has already been modified
04-24 23:01 DEBUG  TaskList: ### Finished modify_bcd
04-24 23:01 DEBUG  TaskList: New task modify_bcd
04-24 23:01 DEBUG  TaskList: ### Running modify_bcd...
04-24 23:01 DEBUG  WindowsBackend: modify_bcd Drive(I: removable 0.0 mb free )
04-24 23:01 DEBUG  WindowsBackend: BCD has already been modified
04-24 23:01 DEBUG  TaskList: ### Finished modify_bcd
04-24 23:01 DEBUG  TaskList: New task modify_bcd
04-24 23:01 DEBUG  TaskList: ### Running modify_bcd...
04-24 23:01 DEBUG  WindowsBackend: modify_bcd Drive(J: removable 1902.4375 mb free fat)
04-24 23:01 DEBUG  WindowsBackend: BCD has already been modified
04-24 23:01 DEBUG  TaskList: ### Finished modify_bcd
04-24 23:01 DEBUG  TaskList: New task modify_bcd
04-24 23:01 DEBUG  TaskList: ### Running modify_bcd...
04-24 23:01 DEBUG  WindowsBackend: modify_bcd Drive(K: removable 0.0 mb free )
04-24 23:01 DEBUG  WindowsBackend: BCD has already been modified
04-24 23:01 DEBUG  TaskList: ### Finished modify_bcd
04-24 23:01 DEBUG  TaskList: ## Finished modify_bootloader
04-24 23:01 DEBUG  TaskList: ## Running modify_grub_configuration...
04-24 23:01 DEBUG  TaskList: ## Finished modify_grub_configuration
04-24 23:01 DEBUG  TaskList: ## Running create_virtual_disks...
04-24 23:01 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\root.disk of 24744MB
04-24 23:01 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\swap.disk of 256MB
04-24 23:01 DEBUG  TaskList: ## Finished create_virtual_disks
04-24 23:01 DEBUG  TaskList: ## Running uncompress_files...
04-24 23:01 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
04-24 23:01 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
04-24 23:01 DEBUG  TaskList: ## Finished uncompress_files
04-24 23:01 DEBUG  TaskList: ## Running eject_cd...
04-24 23:02 DEBUG  TaskList: ## Finished eject_cd
04-24 23:02 DEBUG  TaskList: # Finished tasklist
04-24 23:02 INFO   root: Almost finished installing
04-24 23:02 INFO   root: Finished installation
04-24 23:02 INFO   root: Rebooting
04-24 23:02 DEBUG  TaskList: # Running tasklist...
04-24 23:02 DEBUG  TaskList: ## Running reboot...
04-24 23:02 DEBUG  TaskList: ## Finished reboot
04-24 23:02 DEBUG  TaskList: # Finished tasklist
04-24 23:02 DEBUG  root: application.quit
04-24 23:02 DEBUG  WindowsFrontend: frontend.quit
04-24 23:02 DEBUG  WindowsFrontend: frontend.on_quit
04-24 23:02 DEBUG  root: application.on_quit
04-24 23:02 INFO   root: sys.exit
04-25 13:34 INFO   root: === wubi 9.04 rev128 ===
04-25 13:34 DEBUG  root: Logfile is c:\users\zoso\appdata\local\temp\wubi-9.04-rev128.log
04-25 13:34 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
04-25 13:34 DEBUG  CommonBackend: data_dir=C:\Users\Zoso\AppData\Local\Temp\pylF8BF.tmp\data
04-25 13:34 DEBUG  WindowsBackend: 7z=C:\Users\Zoso\AppData\Local\Temp\pylF8BF.tmp\bin\7z.exe
04-25 13:34 DEBUG  CommonBackend: Fetching basic info...
04-25 13:34 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
04-25 13:34 DEBUG  CommonBackend: platform=win32
04-25 13:34 DEBUG  CommonBackend: osname=nt
04-25 13:34 DEBUG  CommonBackend: language=en_US
04-25 13:34 DEBUG  CommonBackend: encoding=cp1252
04-25 13:34 DEBUG  WindowsBackend: arch=amd64
04-25 13:34 DEBUG  CommonBackend: Parsing isolist=C:\Users\Zoso\AppData\Local\Temp\pylF8BF.tmp\data\isolist.ini
04-25 13:34 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-25 13:34 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-25 13:34 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-25 13:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-25 13:34 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-25 13:34 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-25 13:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-25 13:34 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-25 13:34 DEBUG  WindowsBackend: Fetching host info...
04-25 13:34 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-25 13:34 DEBUG  WindowsBackend: windows version=xp
04-25 13:34 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-25 13:34 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-25 13:34 DEBUG  WindowsBackend: windows_build=2600
04-25 13:34 DEBUG  WindowsBackend: gmt=-5
04-25 13:34 DEBUG  WindowsBackend: country=US
04-25 13:34 DEBUG  WindowsBackend: timezone=America/New_York
04-25 13:34 DEBUG  WindowsBackend: windows_username=Zoso
04-25 13:34 DEBUG  WindowsBackend: user_full_name=Zoso
04-25 13:34 DEBUG  WindowsBackend: user_directory=Zoso
04-25 13:34 DEBUG  WindowsBackend: windows_language_code=1033
04-25 13:34 DEBUG  WindowsBackend: windows_language=English
04-25 13:34 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
04-25 13:34 DEBUG  WindowsBackend: bootloader=xp
04-25 13:34 DEBUG  WindowsBackend: system_drive=Drive(C: hd 126092.875 mb free )
04-25 13:34 DEBUG  WindowsBackend: drive=Drive(C: hd 126092.875 mb free )
04-25 13:34 DEBUG  WindowsBackend: drive=Drive(D: hd 696.34375 mb free ntfs)
04-25 13:34 DEBUG  WindowsBackend: drive=Drive(E: hd 8165.1953125 mb free ntfs)
04-25 13:34 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-25 13:34 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
04-25 13:34 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
04-25 13:34 DEBUG  WindowsBackend: drive=Drive(J: removable 1902.4375 mb free fat)
04-25 13:34 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
04-25 13:34 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-25 13:34 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-25 13:34 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-25 13:34 DEBUG  WindowsBackend: keyboard_id=67699721
04-25 13:34 DEBUG  WindowsBackend: keyboard_layout=us
04-25 13:34 DEBUG  WindowsBackend: keyboard_variant=
04-25 13:34 DEBUG  CommonBackend: locale=en_US.UTF-8
04-25 13:34 DEBUG  WindowsBackend: total_memory_mb=1023.99999905
04-25 13:34 DEBUG  CommonBackend: Searching ISOs on USB devices
04-25 13:34 DEBUG  CommonBackend: Searching for local CDs
04-25 13:34 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pylF8BF.tmp is a valid Ubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pylF8BF.tmp\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pylF8BF.tmp is a valid Ubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pylF8BF.tmp\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pylF8BF.tmp is a valid Kubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pylF8BF.tmp\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pylF8BF.tmp is a valid Kubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pylF8BF.tmp\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pylF8BF.tmp is a valid Xubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pylF8BF.tmp\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pylF8BF.tmp is a valid Xubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pylF8BF.tmp\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pylF8BF.tmp is a valid Mythbuntu CD
04-25 13:34 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pylF8BF.tmp\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether C:\Users\Zoso\AppData\Local\Temp\pylF8BF.tmp is a valid Mythbuntu CD
04-25 13:34 DEBUG  Distro:     does not contain C:\Users\Zoso\AppData\Local\Temp\pylF8BF.tmp\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-25 13:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-25 13:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-25 13:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-25 13:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-25 13:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-25 13:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-25 13:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-25 13:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
04-25 13:34 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
04-25 13:34 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
04-25 13:34 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
04-25 13:34 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
04-25 13:34 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
04-25 13:34 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-25 13:34 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
04-25 13:34 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-25 13:34 INFO   root: Running the uninstaller...
04-25 13:34 INFO   CommonBackend: This is the uninstaller running
04-25 13:34 DEBUG  WindowsFrontend: __init__...
04-25 13:34 DEBUG  WindowsFrontend: on_init...
04-25 13:34 INFO   root: Received settings
04-25 13:34 DEBUG  TaskList: # Running tasklist...
04-25 13:34 DEBUG  TaskList: ## Running Backup ISO...
04-25 13:34 DEBUG  TaskList: ## Finished Backup ISO
04-25 13:34 DEBUG  TaskList: ## Running Remove bootloader entry...
04-25 13:34 DEBUG  WindowsBackend: Removing bcd entry {8f45b05d-1bbe-11de-b4e0-001a92231f8d}
04-25 13:34 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {8f45b05d-1bbe-11de-b4e0-001a92231f8d} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\win32\backend.py", line 495, in undo_bootloader
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\win32\backend.py", line 678, in undo_bcd
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 60, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {8f45b05d-1bbe-11de-b4e0-001a92231f8d} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
04-25 13:34 DEBUG  TaskList: # Cancelling tasklist
04-25 13:34 DEBUG  TaskList: # Finished tasklist
04-25 13:34 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {8f45b05d-1bbe-11de-b4e0-001a92231f8d} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 121, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 176, in run_uninstaller
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {8f45b05d-1bbe-11de-b4e0-001a92231f8d} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=

---

### Post by arafatc on 2009-06-02
i got the same problem too any suggestion ?

---

### Post by zvacet on 2009-06-02
If you just want to change desktop then read [this.]("http://www.psychocats.net/ubuntu/puregnome") If you want to uninstall Wubi I think you will do it same way you remove any program in Windows.

---

### Post by arafatc on 2009-06-04
neither clicking at uninstall icon nor clicking at add remove program in control panel, it doesn't work. here is the screenshot:

[IMG]http://arafatweb.googlepages.com/problemwithubuntu.jpg[/IMG]

here is the log data

[wubi-9.04-rev128.log]("http://arafatweb.googlepages.com/wubi-9.04-rev128.log")

---

