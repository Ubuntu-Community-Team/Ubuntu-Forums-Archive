---
title: "Unable to boot from CD"
date: 2011-03-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kuro114 on 2011-03-06
Hi, 
I had ubuntu alongside my windows 7, however I couldnt get my wireless adapter to work so I thought it would be smart to uninstall it then re-install it and hope for the best. Unfortunately I just can't re-install it. I have been trying to boot it from the disc however I keep getting forwarded to an error in notepad:

03-04 20:26 INFO   root: === wubi 10.10 rev197 ===
03-04 20:26 DEBUG  root: Logfile is c:\users\sparta~1\appdata\local\temp\wubi-10.10-rev197.log
03-04 20:26 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
03-04 20:26 DEBUG  CommonBackend: data_dir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp\data
03-04 20:26 DEBUG  WindowsBackend: 7z=C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp\bin\7z.exe
03-04 20:26 DEBUG  CommonBackend: Fetching basic info...
03-04 20:26 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-04 20:26 DEBUG  CommonBackend: platform=win32
03-04 20:26 DEBUG  CommonBackend: osname=nt
03-04 20:26 DEBUG  CommonBackend: language=en_US
03-04 20:26 DEBUG  CommonBackend: encoding=cp1252
03-04 20:26 DEBUG  WindowsBackend: arch=amd64
03-04 20:26 DEBUG  CommonBackend: Parsing isolist=C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp\data\isolist.ini
03-04 20:26 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-04 20:26 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-04 20:26 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-04 20:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-04 20:26 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-04 20:26 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-04 20:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-04 20:26 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-04 20:26 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-04 20:26 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-04 20:26 DEBUG  WindowsBackend: Fetching host info...
03-04 20:26 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-04 20:26 DEBUG  WindowsBackend: windows version=vista
03-04 20:26 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-04 20:26 DEBUG  WindowsBackend: windows_sp=None
03-04 20:26 DEBUG  WindowsBackend: windows_build=7600
03-04 20:26 DEBUG  WindowsBackend: gmt=-8
03-04 20:26 DEBUG  WindowsBackend: country=US
03-04 20:26 DEBUG  WindowsBackend: timezone=America/Los_Angeles
03-04 20:26 DEBUG  WindowsBackend: windows_username=SPARTAN 114
03-04 20:26 DEBUG  WindowsBackend: user_full_name=SPARTAN 114
03-04 20:26 DEBUG  WindowsBackend: user_directory=C:\Users\SPARTAN 114
03-04 20:26 DEBUG  WindowsBackend: windows_language_code=1033
03-04 20:26 DEBUG  WindowsBackend: windows_language=English
03-04 20:26 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
03-04 20:26 DEBUG  WindowsBackend: bootloader=vista
03-04 20:26 DEBUG  WindowsBackend: system_drive=Drive(C: hd 92856.8007813 mb free ntfs)
03-04 20:26 DEBUG  WindowsBackend: drive=Drive(C: hd 92856.8007813 mb free ntfs)
03-04 20:26 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-04 20:26 DEBUG  WindowsBackend: uninstaller_path=None
03-04 20:26 DEBUG  WindowsBackend: previous_target_dir=None
03-04 20:26 DEBUG  WindowsBackend: previous_distro_name=None
03-04 20:26 DEBUG  WindowsBackend: keyboard_id=67699721
03-04 20:26 DEBUG  WindowsBackend: keyboard_layout=us
03-04 20:26 DEBUG  WindowsBackend: keyboard_variant=
03-04 20:26 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-04 20:26 DEBUG  CommonBackend: locale=en_US.UTF-8
03-04 20:26 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-04 20:26 DEBUG  CommonBackend: Searching ISOs on USB devices
03-04 20:26 DEBUG  CommonBackend: Searching for local CDs
03-04 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp is a valid Ubuntu CD
03-04 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp\casper\filesystem.squashfs
03-04 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp is a valid Ubuntu CD
03-04 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp\casper\filesystem.squashfs
03-04 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp is a valid Ubuntu Netbook CD
03-04 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp\casper\filesystem.squashfs
03-04 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp is a valid Kubuntu CD
03-04 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp\casper\filesystem.squashfs
03-04 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp is a valid Kubuntu CD
03-04 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp\casper\filesystem.squashfs
03-04 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp is a valid Kubuntu Netbook CD
03-04 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp\casper\filesystem.squashfs
03-04 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp is a valid Xubuntu CD
03-04 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp\casper\filesystem.squashfs
03-04 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp is a valid Xubuntu CD
03-04 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp\casper\filesystem.squashfs
03-04 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp is a valid Mythbuntu CD
03-04 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp\casper\filesystem.squashfs
03-04 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp is a valid Mythbuntu CD
03-04 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp\casper\filesystem.squashfs
03-04 20:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 20:26 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-04 20:26 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-04 20:26 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-04 20:26 INFO   root: Running the CD menu...
03-04 20:26 DEBUG  WindowsFrontend: __init__...
03-04 20:26 DEBUG  WindowsFrontend: on_init...
03-04 20:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp\translations, languages=['en_US', 'en']
03-04 20:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl1AC9.tmp\translations, languages=['en_US', 'en']
03-04 20:26 INFO   root: CD menu finished
03-04 20:26 INFO   root: Rebooting
03-04 20:26 DEBUG  TaskList: # Running tasklist...
03-04 20:26 DEBUG  TaskList: ## Running reboot...
03-04 20:26 DEBUG  TaskList: ## Finished reboot
03-04 20:26 DEBUG  TaskList: # Finished tasklist
03-04 20:26 DEBUG  root: application.quit
03-04 20:26 DEBUG  WindowsFrontend: frontend.quit
03-04 20:26 DEBUG  WindowsFrontend: frontend.on_quit
03-04 20:26 DEBUG  root: application.on_quit
03-04 20:26 INFO   root: sys.exit
03-04 20:29 INFO   root: === wubi 10.10 rev197 ===
03-04 20:29 DEBUG  root: Logfile is c:\users\sparta~1\appdata\local\temp\wubi-10.10-rev197.log
03-04 20:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
03-04 20:29 DEBUG  CommonBackend: data_dir=C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp\data
03-04 20:29 DEBUG  WindowsBackend: 7z=C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp\bin\7z.exe
03-04 20:29 DEBUG  CommonBackend: Fetching basic info...
03-04 20:29 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-04 20:29 DEBUG  CommonBackend: platform=win32
03-04 20:29 DEBUG  CommonBackend: osname=nt
03-04 20:29 DEBUG  CommonBackend: language=en_US
03-04 20:29 DEBUG  CommonBackend: encoding=cp1252
03-04 20:29 DEBUG  WindowsBackend: arch=amd64
03-04 20:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp\data\isolist.ini
03-04 20:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-04 20:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-04 20:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-04 20:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-04 20:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-04 20:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-04 20:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-04 20:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-04 20:29 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-04 20:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-04 20:29 DEBUG  WindowsBackend: Fetching host info...
03-04 20:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-04 20:29 DEBUG  WindowsBackend: windows version=vista
03-04 20:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-04 20:29 DEBUG  WindowsBackend: windows_sp=None
03-04 20:29 DEBUG  WindowsBackend: windows_build=7600
03-04 20:29 DEBUG  WindowsBackend: gmt=-8
03-04 20:29 DEBUG  WindowsBackend: country=US
03-04 20:29 DEBUG  WindowsBackend: timezone=America/Los_Angeles
03-04 20:29 DEBUG  WindowsBackend: windows_username=SPARTAN 114
03-04 20:29 DEBUG  WindowsBackend: user_full_name=SPARTAN 114
03-04 20:29 DEBUG  WindowsBackend: user_directory=C:\Users\SPARTAN 114
03-04 20:29 DEBUG  WindowsBackend: windows_language_code=1033
03-04 20:29 DEBUG  WindowsBackend: windows_language=English
03-04 20:29 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
03-04 20:29 DEBUG  WindowsBackend: bootloader=vista
03-04 20:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 92859.75 mb free ntfs)
03-04 20:29 DEBUG  WindowsBackend: drive=Drive(C: hd 92859.75 mb free ntfs)
03-04 20:29 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-04 20:29 DEBUG  WindowsBackend: uninstaller_path=None
03-04 20:29 DEBUG  WindowsBackend: previous_target_dir=None
03-04 20:29 DEBUG  WindowsBackend: previous_distro_name=None
03-04 20:29 DEBUG  WindowsBackend: keyboard_id=67699721
03-04 20:29 DEBUG  WindowsBackend: keyboard_layout=us
03-04 20:29 DEBUG  WindowsBackend: keyboard_variant=
03-04 20:29 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-04 20:29 DEBUG  CommonBackend: locale=en_US.UTF-8
03-04 20:29 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-04 20:29 DEBUG  CommonBackend: Searching ISOs on USB devices
03-04 20:29 DEBUG  CommonBackend: Searching for local CDs
03-04 20:29 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp is a valid Ubuntu CD
03-04 20:29 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp\casper\filesystem.squashfs
03-04 20:29 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp is a valid Ubuntu CD
03-04 20:29 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp\casper\filesystem.squashfs
03-04 20:29 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp is a valid Ubuntu Netbook CD
03-04 20:29 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp\casper\filesystem.squashfs
03-04 20:29 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp is a valid Kubuntu CD
03-04 20:29 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp\casper\filesystem.squashfs
03-04 20:29 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp is a valid Kubuntu CD
03-04 20:29 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp\casper\filesystem.squashfs
03-04 20:29 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp is a valid Kubuntu Netbook CD
03-04 20:29 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp\casper\filesystem.squashfs
03-04 20:29 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp is a valid Xubuntu CD
03-04 20:29 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp\casper\filesystem.squashfs
03-04 20:29 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp is a valid Xubuntu CD
03-04 20:29 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp\casper\filesystem.squashfs
03-04 20:29 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp is a valid Mythbuntu CD
03-04 20:29 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp\casper\filesystem.squashfs
03-04 20:29 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp is a valid Mythbuntu CD
03-04 20:29 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp\casper\filesystem.squashfs
03-04 20:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 20:29 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-04 20:29 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-04 20:29 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-04 20:29 INFO   root: Running the CD menu...
03-04 20:29 DEBUG  WindowsFrontend: __init__...
03-04 20:29 DEBUG  WindowsFrontend: on_init...
03-04 20:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp\translations, languages=['en_US', 'en']
03-04 20:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp\translations, languages=['en_US', 'en']
03-04 20:29 INFO   root: CD menu finished
03-04 20:29 INFO   root: Running the installer...
03-04 20:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp\translations, languages=['en_US', 'en']
03-04 20:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp\translations, languages=['en_US', 'en']
03-04 20:30 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=10000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=spartan114
03-04 20:30 INFO   root: Received settings
03-04 20:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp\translations, languages=['en_US', 'en']
03-04 20:30 DEBUG  TaskList: # Running tasklist...
03-04 20:30 DEBUG  TaskList: ## Running select_target_dir...
03-04 20:30 INFO   WindowsBackend: Installing into C:\ubuntu
03-04 20:30 DEBUG  TaskList: ## Finished select_target_dir
03-04 20:30 DEBUG  TaskList: ## Running create_dir_structure...
03-04 20:30 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-04 20:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-04 20:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-04 20:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-04 20:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-04 20:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-04 20:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-04 20:30 DEBUG  TaskList: ## Finished create_dir_structure
03-04 20:30 DEBUG  TaskList: ## Running uncompress_target_dir...
03-04 20:30 DEBUG  TaskList: ## Finished uncompress_target_dir
03-04 20:30 DEBUG  TaskList: ## Running create_uninstaller...
03-04 20:30 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-04 20:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-04 20:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-04 20:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-04 20:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-04 20:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-04 20:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-04 20:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-04 20:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-04 20:30 DEBUG  TaskList: ## Finished create_uninstaller
03-04 20:30 DEBUG  TaskList: ## Running copy_installation_files...
03-04 20:30 DEBUG  WindowsBackend: Copying C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-04 20:30 DEBUG  WindowsBackend: Copying C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp\winboot -> C:\ubuntu\winboot
03-04 20:30 DEBUG  WindowsBackend: Copying C:\Users\SPARTA~1\AppData\Local\Temp\pylF3DF.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-04 20:30 DEBUG  TaskList: ## Finished copy_installation_files
03-04 20:30 DEBUG  TaskList: ## Running get_iso...
03-04 20:30 DEBUG  TaskList: New task copy_file
03-04 20:30 DEBUG  TaskList: ### Running copy_file...
03-04 20:32 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
03-04 20:32 DEBUG  TaskList: # Cancelling tasklist
03-04 20:32 DEBUG  TaskList: New task check_iso
03-04 20:32 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
03-04 20:32 DEBUG  CommonBackend: Searching for local ISO
03-04 20:32 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-04 20:32 DEBUG  TaskList: New task get_metalink
03-04 20:32 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
03-04 20:32 DEBUG  TaskList: # Cancelling tasklist
03-04 20:32 DEBUG  TaskList: # Finished tasklist
03-04 20:37 INFO   root: === wubi 10.10 rev197 ===
03-04 20:37 DEBUG  root: Logfile is c:\users\sparta~1\appdata\local\temp\wubi-10.10-rev197.log
03-04 20:37 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
03-04 20:37 DEBUG  CommonBackend: data_dir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\data
03-04 20:37 DEBUG  WindowsBackend: 7z=C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\bin\7z.exe
03-04 20:37 DEBUG  CommonBackend: Fetching basic info...
03-04 20:37 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-04 20:37 DEBUG  CommonBackend: platform=win32
03-04 20:37 DEBUG  CommonBackend: osname=nt
03-04 20:37 DEBUG  CommonBackend: language=en_US
03-04 20:37 DEBUG  CommonBackend: encoding=cp1252
03-04 20:37 DEBUG  WindowsBackend: arch=amd64
03-04 20:37 DEBUG  CommonBackend: Parsing isolist=C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\data\isolist.ini
03-04 20:37 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-04 20:37 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-04 20:37 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-04 20:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-04 20:37 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-04 20:37 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-04 20:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-04 20:37 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-04 20:37 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-04 20:37 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-04 20:37 DEBUG  WindowsBackend: Fetching host info...
03-04 20:37 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-04 20:37 DEBUG  WindowsBackend: windows version=vista
03-04 20:37 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-04 20:37 DEBUG  WindowsBackend: windows_sp=None
03-04 20:37 DEBUG  WindowsBackend: windows_build=7600
03-04 20:37 DEBUG  WindowsBackend: gmt=-8
03-04 20:37 DEBUG  WindowsBackend: country=US
03-04 20:37 DEBUG  WindowsBackend: timezone=America/Los_Angeles
03-04 20:37 DEBUG  WindowsBackend: windows_username=SPARTAN 114
03-04 20:37 DEBUG  WindowsBackend: user_full_name=SPARTAN 114
03-04 20:37 DEBUG  WindowsBackend: user_directory=C:\Users\SPARTAN 114
03-04 20:37 DEBUG  WindowsBackend: windows_language_code=1033
03-04 20:37 DEBUG  WindowsBackend: windows_language=English
03-04 20:37 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
03-04 20:37 DEBUG  WindowsBackend: bootloader=vista
03-04 20:37 DEBUG  WindowsBackend: system_drive=Drive(C: hd 92164.390625 mb free ntfs)
03-04 20:37 DEBUG  WindowsBackend: drive=Drive(C: hd 92164.390625 mb free ntfs)
03-04 20:37 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-04 20:37 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-04 20:37 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-04 20:37 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-04 20:37 DEBUG  WindowsBackend: keyboard_id=67699721
03-04 20:37 DEBUG  WindowsBackend: keyboard_layout=us
03-04 20:37 DEBUG  WindowsBackend: keyboard_variant=
03-04 20:37 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-04 20:37 DEBUG  CommonBackend: locale=en_US.UTF-8
03-04 20:37 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-04 20:37 DEBUG  CommonBackend: Searching ISOs on USB devices
03-04 20:37 DEBUG  CommonBackend: Searching for local CDs
03-04 20:37 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp is a valid Ubuntu CD
03-04 20:37 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\casper\filesystem.squashfs
03-04 20:37 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp is a valid Ubuntu CD
03-04 20:37 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\casper\filesystem.squashfs
03-04 20:37 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp is a valid Ubuntu Netbook CD
03-04 20:37 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\casper\filesystem.squashfs
03-04 20:37 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp is a valid Kubuntu CD
03-04 20:37 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\casper\filesystem.squashfs
03-04 20:37 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp is a valid Kubuntu CD
03-04 20:37 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\casper\filesystem.squashfs
03-04 20:37 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp is a valid Kubuntu Netbook CD
03-04 20:37 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\casper\filesystem.squashfs
03-04 20:37 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp is a valid Xubuntu CD
03-04 20:37 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\casper\filesystem.squashfs
03-04 20:37 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp is a valid Xubuntu CD
03-04 20:37 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\casper\filesystem.squashfs
03-04 20:37 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp is a valid Mythbuntu CD
03-04 20:37 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\casper\filesystem.squashfs
03-04 20:37 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp is a valid Mythbuntu CD
03-04 20:37 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\casper\filesystem.squashfs
03-04 20:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 20:37 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-04 20:37 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-04 20:37 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-04 20:37 INFO   root: Running the CD menu...
03-04 20:37 DEBUG  WindowsFrontend: __init__...
03-04 20:37 DEBUG  WindowsFrontend: on_init...
03-04 20:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\translations, languages=['en_US', 'en']
03-04 20:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\translations, languages=['en_US', 'en']
03-04 20:38 INFO   root: CD menu finished
03-04 20:38 INFO   root: Already installed, running the uninstaller...
03-04 20:38 INFO   root: Running the uninstaller...
03-04 20:38 INFO   CommonBackend: This is the uninstaller running
03-04 20:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\translations, languages=['en_US', 'en']
03-04 20:38 INFO   root: Received settings
03-04 20:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\translations, languages=['en_US', 'en']
03-04 20:38 DEBUG  TaskList: # Running tasklist...
03-04 20:38 DEBUG  TaskList: ## Running Backup ISO...
03-04 20:38 DEBUG  TaskList: ## Finished Backup ISO
03-04 20:38 DEBUG  TaskList: ## Running Remove bootloader entry...
03-04 20:38 DEBUG  WindowsBackend: Could not find bcd id
03-04 20:38 DEBUG  WindowsBackend: undo_bootini C:
03-04 20:38 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 92164.390625 mb free ntfs)
03-04 20:38 DEBUG  TaskList: ## Finished Remove bootloader entry
03-04 20:38 DEBUG  TaskList: ## Running Remove target dir...
03-04 20:38 DEBUG  CommonBackend: Deleting C:\ubuntu
03-04 20:38 DEBUG  TaskList: ## Finished Remove target dir
03-04 20:38 DEBUG  TaskList: ## Running Remove registry key...
03-04 20:38 DEBUG  TaskList: ## Finished Remove registry key
03-04 20:38 DEBUG  TaskList: # Finished tasklist
03-04 20:38 INFO   root: Almost finished uninstalling
03-04 20:38 INFO   root: Finished uninstallation
03-04 20:38 DEBUG  CommonBackend: Fetching basic info...
03-04 20:38 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-04 20:38 DEBUG  CommonBackend: platform=win32
03-04 20:38 DEBUG  CommonBackend: osname=nt
03-04 20:38 DEBUG  WindowsBackend: arch=amd64
03-04 20:38 DEBUG  CommonBackend: Parsing isolist=C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\data\isolist.ini
03-04 20:38 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-04 20:38 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-04 20:38 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-04 20:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-04 20:38 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-04 20:38 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-04 20:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-04 20:38 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-04 20:38 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-04 20:38 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-04 20:38 DEBUG  WindowsBackend: Fetching host info...
03-04 20:38 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-04 20:38 DEBUG  WindowsBackend: windows version=vista
03-04 20:38 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-04 20:38 DEBUG  WindowsBackend: windows_sp=None
03-04 20:38 DEBUG  WindowsBackend: windows_build=7600
03-04 20:38 DEBUG  WindowsBackend: gmt=-8
03-04 20:38 DEBUG  WindowsBackend: country=US
03-04 20:38 DEBUG  WindowsBackend: timezone=America/Los_Angeles
03-04 20:38 DEBUG  WindowsBackend: windows_username=SPARTAN 114
03-04 20:38 DEBUG  WindowsBackend: user_full_name=SPARTAN 114
03-04 20:38 DEBUG  WindowsBackend: user_directory=C:\Users\SPARTAN 114
03-04 20:38 DEBUG  WindowsBackend: windows_language_code=1033
03-04 20:38 DEBUG  WindowsBackend: windows_language=English
03-04 20:38 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
03-04 20:38 DEBUG  WindowsBackend: bootloader=vista
03-04 20:38 DEBUG  WindowsBackend: system_drive=Drive(C: hd 92884.6679688 mb free ntfs)
03-04 20:38 DEBUG  WindowsBackend: drive=Drive(C: hd 92884.6679688 mb free ntfs)
03-04 20:38 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-04 20:38 DEBUG  WindowsBackend: uninstaller_path=None
03-04 20:38 DEBUG  WindowsBackend: previous_target_dir=None
03-04 20:38 DEBUG  WindowsBackend: previous_distro_name=None
03-04 20:38 DEBUG  WindowsBackend: keyboard_id=67699721
03-04 20:38 DEBUG  WindowsBackend: keyboard_layout=us
03-04 20:38 DEBUG  WindowsBackend: keyboard_variant=
03-04 20:38 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-04 20:38 DEBUG  CommonBackend: Searching ISOs on USB devices
03-04 20:38 DEBUG  CommonBackend: Searching for local CDs
03-04 20:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp is a valid Ubuntu CD
03-04 20:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\casper\filesystem.squashfs
03-04 20:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp is a valid Ubuntu CD
03-04 20:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\casper\filesystem.squashfs
03-04 20:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp is a valid Ubuntu Netbook CD
03-04 20:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\casper\filesystem.squashfs
03-04 20:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp is a valid Kubuntu CD
03-04 20:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\casper\filesystem.squashfs
03-04 20:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp is a valid Kubuntu CD
03-04 20:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\casper\filesystem.squashfs
03-04 20:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp is a valid Kubuntu Netbook CD
03-04 20:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\casper\filesystem.squashfs
03-04 20:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp is a valid Xubuntu CD
03-04 20:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\casper\filesystem.squashfs
03-04 20:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp is a valid Xubuntu CD
03-04 20:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\casper\filesystem.squashfs
03-04 20:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp is a valid Mythbuntu CD
03-04 20:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\casper\filesystem.squashfs
03-04 20:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp is a valid Mythbuntu CD
03-04 20:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\casper\filesystem.squashfs
03-04 20:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 20:38 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-04 20:38 INFO   root: Running the CD boot helper...
03-04 20:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\translations, languages=['en_US', 'en']
03-04 20:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\translations, languages=['en_US', 'en']
03-04 20:38 INFO   root: CD boot helper confirmed
03-04 20:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\translations, languages=['en_US', 'en']
03-04 20:38 DEBUG  TaskList: # Running tasklist...
03-04 20:38 DEBUG  TaskList: ## Running select_target_dir...
03-04 20:38 INFO   WindowsBackend: Installing into C:\ubuntu
03-04 20:38 DEBUG  TaskList: ## Finished select_target_dir
03-04 20:38 DEBUG  TaskList: ## Running create_dir_structure...
03-04 20:38 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-04 20:38 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-04 20:38 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-04 20:38 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-04 20:38 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-04 20:38 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-04 20:38 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-04 20:38 DEBUG  TaskList: ## Finished create_dir_structure
03-04 20:38 DEBUG  TaskList: ## Running uncompress_target_dir...
03-04 20:38 DEBUG  TaskList: ## Finished uncompress_target_dir
03-04 20:38 DEBUG  TaskList: ## Running create_uninstaller...
03-04 20:38 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-04 20:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-04 20:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-04 20:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-04 20:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-04 20:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-04 20:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-04 20:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-04 20:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-04 20:38 DEBUG  TaskList: ## Finished create_uninstaller
03-04 20:38 DEBUG  TaskList: ## Running copy_installation_files...
03-04 20:38 DEBUG  WindowsBackend: Copying C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-04 20:38 DEBUG  WindowsBackend: Copying C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\winboot -> C:\ubuntu\winboot
03-04 20:38 DEBUG  WindowsBackend: Copying C:\Users\SPARTA~1\AppData\Local\Temp\pyl8055.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-04 20:38 DEBUG  TaskList: ## Finished copy_installation_files
03-04 20:38 DEBUG  TaskList: ## Running use_cd...
03-04 20:38 DEBUG  TaskList: New task copy_file
03-04 20:38 DEBUG  TaskList: ### Running copy_file...
03-04 20:40 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
03-04 20:40 DEBUG  TaskList: # Cancelling tasklist
03-04 20:40 DEBUG  TaskList: New task check_iso
03-04 20:40 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
03-04 20:40 DEBUG  TaskList: ## Finished use_cd
03-04 20:40 DEBUG  TaskList: # Finished tasklist
03-04 20:45 INFO   root: === wubi 10.10 rev197 ===
03-04 20:45 DEBUG  root: Logfile is c:\users\sparta~1\appdata\local\temp\wubi-10.10-rev197.log
03-04 20:45 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
03-04 20:45 DEBUG  CommonBackend: data_dir=C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp\data
03-04 20:45 DEBUG  WindowsBackend: 7z=C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp\bin\7z.exe
03-04 20:45 DEBUG  CommonBackend: Fetching basic info...
03-04 20:45 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-04 20:45 DEBUG  CommonBackend: platform=win32
03-04 20:45 DEBUG  CommonBackend: osname=nt
03-04 20:45 DEBUG  CommonBackend: language=en_US
03-04 20:45 DEBUG  CommonBackend: encoding=cp1252
03-04 20:45 DEBUG  WindowsBackend: arch=amd64
03-04 20:45 DEBUG  CommonBackend: Parsing isolist=C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp\data\isolist.ini
03-04 20:45 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-04 20:45 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-04 20:45 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-04 20:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-04 20:45 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-04 20:45 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-04 20:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-04 20:45 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-04 20:45 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-04 20:45 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-04 20:45 DEBUG  WindowsBackend: Fetching host info...
03-04 20:45 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-04 20:45 DEBUG  WindowsBackend: windows version=vista
03-04 20:45 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-04 20:45 DEBUG  WindowsBackend: windows_sp=None
03-04 20:45 DEBUG  WindowsBackend: windows_build=7600
03-04 20:45 DEBUG  WindowsBackend: gmt=-8
03-04 20:45 DEBUG  WindowsBackend: country=US
03-04 20:45 DEBUG  WindowsBackend: timezone=America/Los_Angeles
03-04 20:45 DEBUG  WindowsBackend: windows_username=SPARTAN 114
03-04 20:45 DEBUG  WindowsBackend: user_full_name=SPARTAN 114
03-04 20:45 DEBUG  WindowsBackend: user_directory=C:\Users\SPARTAN 114
03-04 20:45 DEBUG  WindowsBackend: windows_language_code=1033
03-04 20:45 DEBUG  WindowsBackend: windows_language=English
03-04 20:45 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
03-04 20:45 DEBUG  WindowsBackend: bootloader=vista
03-04 20:45 DEBUG  WindowsBackend: system_drive=Drive(C: hd 92191.15625 mb free ntfs)
03-04 20:45 DEBUG  WindowsBackend: drive=Drive(C: hd 92191.15625 mb free ntfs)
03-04 20:45 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-04 20:45 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-04 20:45 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-04 20:45 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-04 20:45 DEBUG  WindowsBackend: keyboard_id=67699721
03-04 20:45 DEBUG  WindowsBackend: keyboard_layout=us
03-04 20:45 DEBUG  WindowsBackend: keyboard_variant=
03-04 20:45 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-04 20:45 DEBUG  CommonBackend: locale=en_US.UTF-8
03-04 20:45 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-04 20:45 DEBUG  CommonBackend: Searching ISOs on USB devices
03-04 20:45 DEBUG  CommonBackend: Searching for local CDs
03-04 20:45 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp is a valid Ubuntu CD
03-04 20:45 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp\casper\filesystem.squashfs
03-04 20:45 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp is a valid Ubuntu CD
03-04 20:45 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp\casper\filesystem.squashfs
03-04 20:45 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp is a valid Ubuntu Netbook CD
03-04 20:45 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp\casper\filesystem.squashfs
03-04 20:45 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp is a valid Kubuntu CD
03-04 20:45 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp\casper\filesystem.squashfs
03-04 20:45 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp is a valid Kubuntu CD
03-04 20:45 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp\casper\filesystem.squashfs
03-04 20:45 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp is a valid Kubuntu Netbook CD
03-04 20:45 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp\casper\filesystem.squashfs
03-04 20:45 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp is a valid Xubuntu CD
03-04 20:45 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp\casper\filesystem.squashfs
03-04 20:45 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp is a valid Xubuntu CD
03-04 20:45 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp\casper\filesystem.squashfs
03-04 20:45 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp is a valid Mythbuntu CD
03-04 20:45 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp\casper\filesystem.squashfs
03-04 20:45 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp is a valid Mythbuntu CD
03-04 20:45 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp\casper\filesystem.squashfs
03-04 20:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 20:45 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-04 20:45 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-04 20:45 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-04 20:45 INFO   root: Running the CD menu...
03-04 20:45 DEBUG  WindowsFrontend: __init__...
03-04 20:45 DEBUG  WindowsFrontend: on_init...
03-04 20:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp\translations, languages=['en_US', 'en']
03-04 20:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylB3C4.tmp\translations, languages=['en_US', 'en']
03-04 20:46 INFO   root: CD menu finished
03-04 20:46 INFO   root: Rebooting
03-04 20:46 DEBUG  TaskList: # Running tasklist...
03-04 20:46 DEBUG  TaskList: ## Running reboot...
03-04 20:46 DEBUG  TaskList: ## Finished reboot
03-04 20:46 DEBUG  TaskList: # Finished tasklist
03-04 20:46 DEBUG  root: application.quit
03-04 20:46 DEBUG  WindowsFrontend: frontend.quit
03-04 20:46 DEBUG  WindowsFrontend: frontend.on_quit
03-04 20:46 DEBUG  root: application.on_quit
03-04 20:46 INFO   root: sys.exit
03-04 20:50 INFO   root: === wubi 10.10 rev197 ===
03-04 20:50 DEBUG  root: Logfile is c:\users\sparta~1\appdata\local\temp\wubi-10.10-rev197.log
03-04 20:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
03-04 20:50 DEBUG  CommonBackend: data_dir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\data
03-04 20:50 DEBUG  WindowsBackend: 7z=C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\bin\7z.exe
03-04 20:50 DEBUG  CommonBackend: Fetching basic info...
03-04 20:50 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-04 20:50 DEBUG  CommonBackend: platform=win32
03-04 20:50 DEBUG  CommonBackend: osname=nt
03-04 20:50 DEBUG  CommonBackend: language=en_US
03-04 20:50 DEBUG  CommonBackend: encoding=cp1252
03-04 20:50 DEBUG  WindowsBackend: arch=amd64
03-04 20:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\data\isolist.ini
03-04 20:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-04 20:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-04 20:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-04 20:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-04 20:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-04 20:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-04 20:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-04 20:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-04 20:50 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-04 20:50 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-04 20:50 DEBUG  WindowsBackend: Fetching host info...
03-04 20:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-04 20:50 DEBUG  WindowsBackend: windows version=vista
03-04 20:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-04 20:50 DEBUG  WindowsBackend: windows_sp=None
03-04 20:50 DEBUG  WindowsBackend: windows_build=7600
03-04 20:50 DEBUG  WindowsBackend: gmt=-8
03-04 20:50 DEBUG  WindowsBackend: country=US
03-04 20:50 DEBUG  WindowsBackend: timezone=America/Los_Angeles
03-04 20:50 DEBUG  WindowsBackend: windows_username=SPARTAN 114
03-04 20:50 DEBUG  WindowsBackend: user_full_name=SPARTAN 114
03-04 20:50 DEBUG  WindowsBackend: user_directory=C:\Users\SPARTAN 114
03-04 20:50 DEBUG  WindowsBackend: windows_language_code=1033
03-04 20:50 DEBUG  WindowsBackend: windows_language=English
03-04 20:50 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
03-04 20:50 DEBUG  WindowsBackend: bootloader=vista
03-04 20:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 92197.0625 mb free ntfs)
03-04 20:50 DEBUG  WindowsBackend: drive=Drive(C: hd 92197.0625 mb free ntfs)
03-04 20:50 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-04 20:50 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-04 20:50 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-04 20:50 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-04 20:50 DEBUG  WindowsBackend: keyboard_id=67699721
03-04 20:50 DEBUG  WindowsBackend: keyboard_layout=us
03-04 20:50 DEBUG  WindowsBackend: keyboard_variant=
03-04 20:50 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-04 20:50 DEBUG  CommonBackend: locale=en_US.UTF-8
03-04 20:50 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-04 20:50 DEBUG  CommonBackend: Searching ISOs on USB devices
03-04 20:50 DEBUG  CommonBackend: Searching for local CDs
03-04 20:50 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp is a valid Ubuntu CD
03-04 20:50 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
03-04 20:50 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp is a valid Ubuntu CD
03-04 20:50 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
03-04 20:50 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp is a valid Ubuntu Netbook CD
03-04 20:50 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
03-04 20:50 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp is a valid Kubuntu CD
03-04 20:50 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
03-04 20:50 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp is a valid Kubuntu CD
03-04 20:50 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
03-04 20:50 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp is a valid Kubuntu Netbook CD
03-04 20:50 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
03-04 20:50 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp is a valid Xubuntu CD
03-04 20:50 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
03-04 20:50 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp is a valid Xubuntu CD
03-04 20:50 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
03-04 20:50 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp is a valid Mythbuntu CD
03-04 20:50 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
03-04 20:50 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp is a valid Mythbuntu CD
03-04 20:50 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
03-04 20:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 20:50 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-04 20:50 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-04 20:50 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-04 20:50 INFO   root: Running the CD menu...
03-04 20:50 DEBUG  WindowsFrontend: __init__...
03-04 20:50 DEBUG  WindowsFrontend: on_init...
03-04 20:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\translations, languages=['en_US', 'en']
03-04 20:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\translations, languages=['en_US', 'en']
03-04 20:50 INFO   root: CD menu finished
03-04 20:50 INFO   root: Already installed, running the uninstaller...
03-04 20:50 INFO   root: Running the uninstaller...
03-04 20:50 INFO   CommonBackend: This is the uninstaller running
03-04 20:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\translations, languages=['en_US', 'en']
03-04 20:50 INFO   root: Received settings
03-04 20:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\translations, languages=['en_US', 'en']
03-04 20:50 DEBUG  TaskList: # Running tasklist...
03-04 20:50 DEBUG  TaskList: ## Running Backup ISO...
03-04 20:50 DEBUG  TaskList: ## Finished Backup ISO
03-04 20:50 DEBUG  TaskList: ## Running Remove bootloader entry...
03-04 20:50 DEBUG  WindowsBackend: Could not find bcd id
03-04 20:50 DEBUG  WindowsBackend: undo_bootini C:
03-04 20:50 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 92197.0625 mb free ntfs)
03-04 20:50 DEBUG  TaskList: ## Finished Remove bootloader entry
03-04 20:50 DEBUG  TaskList: ## Running Remove target dir...
03-04 20:50 DEBUG  CommonBackend: Deleting C:\ubuntu
03-04 20:50 DEBUG  TaskList: ## Finished Remove target dir
03-04 20:50 DEBUG  TaskList: ## Running Remove registry key...
03-04 20:50 DEBUG  TaskList: ## Finished Remove registry key
03-04 20:50 DEBUG  TaskList: # Finished tasklist
03-04 20:50 INFO   root: Almost finished uninstalling
03-04 20:50 INFO   root: Finished uninstallation
03-04 20:50 DEBUG  CommonBackend: Fetching basic info...
03-04 20:50 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-04 20:50 DEBUG  CommonBackend: platform=win32
03-04 20:50 DEBUG  CommonBackend: osname=nt
03-04 20:50 DEBUG  WindowsBackend: arch=amd64
03-04 20:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\data\isolist.ini
03-04 20:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-04 20:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-04 20:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-04 20:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-04 20:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-04 20:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-04 20:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-04 20:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-04 20:50 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-04 20:50 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-04 20:50 DEBUG  WindowsBackend: Fetching host info...
03-04 20:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-04 20:50 DEBUG  WindowsBackend: windows version=vista
03-04 20:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-04 20:50 DEBUG  WindowsBackend: windows_sp=None
03-04 20:50 DEBUG  WindowsBackend: windows_build=7600
03-04 20:50 DEBUG  WindowsBackend: gmt=-8
03-04 20:50 DEBUG  WindowsBackend: country=US
03-04 20:50 DEBUG  WindowsBackend: timezone=America/Los_Angeles
03-04 20:50 DEBUG  WindowsBackend: windows_username=SPARTAN 114
03-04 20:50 DEBUG  WindowsBackend: user_full_name=SPARTAN 114
03-04 20:50 DEBUG  WindowsBackend: user_directory=C:\Users\SPARTAN 114
03-04 20:50 DEBUG  WindowsBackend: windows_language_code=1033
03-04 20:50 DEBUG  WindowsBackend: windows_language=English
03-04 20:50 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
03-04 20:50 DEBUG  WindowsBackend: bootloader=vista
03-04 20:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 92890.6210938 mb free ntfs)
03-04 20:50 DEBUG  WindowsBackend: drive=Drive(C: hd 92890.6210938 mb free ntfs)
03-04 20:50 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-04 20:50 DEBUG  WindowsBackend: uninstaller_path=None
03-04 20:50 DEBUG  WindowsBackend: previous_target_dir=None
03-04 20:50 DEBUG  WindowsBackend: previous_distro_name=None
03-04 20:50 DEBUG  WindowsBackend: keyboard_id=67699721
03-04 20:50 DEBUG  WindowsBackend: keyboard_layout=us
03-04 20:50 DEBUG  WindowsBackend: keyboard_variant=
03-04 20:50 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-04 20:50 DEBUG  CommonBackend: Searching ISOs on USB devices
03-04 20:50 DEBUG  CommonBackend: Searching for local CDs
03-04 20:50 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp is a valid Ubuntu CD
03-04 20:50 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
03-04 20:50 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp is a valid Ubuntu CD
03-04 20:50 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
03-04 20:50 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp is a valid Ubuntu Netbook CD
03-04 20:50 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
03-04 20:50 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp is a valid Kubuntu CD
03-04 20:50 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
03-04 20:50 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp is a valid Kubuntu CD
03-04 20:50 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
03-04 20:50 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp is a valid Kubuntu Netbook CD
03-04 20:50 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
03-04 20:50 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp is a valid Xubuntu CD
03-04 20:50 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
03-04 20:50 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp is a valid Xubuntu CD
03-04 20:50 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
03-04 20:50 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp is a valid Mythbuntu CD
03-04 20:50 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
03-04 20:50 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp is a valid Mythbuntu CD
03-04 20:50 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
03-04 20:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 20:50 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-04 20:50 INFO   root: Running the installer...
03-04 20:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\translations, languages=['en_US', 'en']
03-04 20:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\translations, languages=['en_US', 'en']
03-04 20:50 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=spartan114
03-04 20:50 INFO   root: Received settings
03-04 20:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\translations, languages=['en_US', 'en']
03-04 20:50 DEBUG  TaskList: # Running tasklist...
03-04 20:50 DEBUG  TaskList: ## Running select_target_dir...
03-04 20:50 INFO   WindowsBackend: Installing into C:\ubuntu
03-04 20:50 DEBUG  TaskList: ## Finished select_target_dir
03-04 20:50 DEBUG  TaskList: ## Running create_dir_structure...
03-04 20:50 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-04 20:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-04 20:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-04 20:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-04 20:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-04 20:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-04 20:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-04 20:50 DEBUG  TaskList: ## Finished create_dir_structure
03-04 20:50 DEBUG  TaskList: ## Running uncompress_target_dir...
03-04 20:50 DEBUG  TaskList: ## Finished uncompress_target_dir
03-04 20:50 DEBUG  TaskList: ## Running create_uninstaller...
03-04 20:50 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-04 20:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-04 20:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-04 20:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-04 20:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-04 20:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-04 20:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-04 20:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-04 20:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-04 20:50 DEBUG  TaskList: ## Finished create_uninstaller
03-04 20:50 DEBUG  TaskList: ## Running copy_installation_files...
03-04 20:50 DEBUG  WindowsBackend: Copying C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-04 20:50 DEBUG  WindowsBackend: Copying C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\winboot -> C:\ubuntu\winboot
03-04 20:50 DEBUG  WindowsBackend: Copying C:\Users\SPARTA~1\AppData\Local\Temp\pyl643E.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-04 20:50 DEBUG  TaskList: ## Finished copy_installation_files
03-04 20:50 DEBUG  TaskList: ## Running get_iso...
03-04 20:50 DEBUG  TaskList: New task copy_file
03-04 20:50 DEBUG  TaskList: ### Running copy_file...
03-04 20:53 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
03-04 20:53 DEBUG  TaskList: # Cancelling tasklist
03-04 20:53 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
03-04 20:53 DEBUG  TaskList: New task check_iso
03-04 20:53 DEBUG  CommonBackend: Searching for local ISO
03-04 20:53 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-04 20:53 DEBUG  TaskList: New task get_metalink
03-04 20:53 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
03-04 20:53 DEBUG  TaskList: # Cancelling tasklist
03-04 20:53 DEBUG  TaskList: # Finished tasklist
03-04 20:55 INFO   root: === wubi 10.10 rev197 ===
03-04 20:55 DEBUG  root: Logfile is c:\users\sparta~1\appdata\local\temp\wubi-10.10-rev197.log
03-04 20:55 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
03-04 20:55 DEBUG  CommonBackend: data_dir=C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\data
03-04 20:55 DEBUG  WindowsBackend: 7z=C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\bin\7z.exe
03-04 20:55 DEBUG  CommonBackend: Fetching basic info...
03-04 20:55 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-04 20:55 DEBUG  CommonBackend: platform=win32
03-04 20:55 DEBUG  CommonBackend: osname=nt
03-04 20:55 DEBUG  CommonBackend: language=en_US
03-04 20:55 DEBUG  CommonBackend: encoding=cp1252
03-04 20:55 DEBUG  WindowsBackend: arch=amd64
03-04 20:55 DEBUG  CommonBackend: Parsing isolist=C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\data\isolist.ini
03-04 20:55 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-04 20:55 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-04 20:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-04 20:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-04 20:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-04 20:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-04 20:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-04 20:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-04 20:55 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-04 20:55 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-04 20:55 DEBUG  WindowsBackend: Fetching host info...
03-04 20:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-04 20:55 DEBUG  WindowsBackend: windows version=vista
03-04 20:55 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-04 20:55 DEBUG  WindowsBackend: windows_sp=None
03-04 20:55 DEBUG  WindowsBackend: windows_build=7600
03-04 20:55 DEBUG  WindowsBackend: gmt=-8
03-04 20:55 DEBUG  WindowsBackend: country=US
03-04 20:55 DEBUG  WindowsBackend: timezone=America/Los_Angeles
03-04 20:55 DEBUG  WindowsBackend: windows_username=SPARTAN 114
03-04 20:55 DEBUG  WindowsBackend: user_full_name=SPARTAN 114
03-04 20:55 DEBUG  WindowsBackend: user_directory=C:\Users\SPARTAN 114
03-04 20:55 DEBUG  WindowsBackend: windows_language_code=1033
03-04 20:55 DEBUG  WindowsBackend: windows_language=English
03-04 20:55 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
03-04 20:55 DEBUG  WindowsBackend: bootloader=vista
03-04 20:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 92195.4960938 mb free ntfs)
03-04 20:55 DEBUG  WindowsBackend: drive=Drive(C: hd 92195.4960938 mb free ntfs)
03-04 20:55 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-04 20:55 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-04 20:55 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-04 20:55 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-04 20:55 DEBUG  WindowsBackend: keyboard_id=67699721
03-04 20:55 DEBUG  WindowsBackend: keyboard_layout=us
03-04 20:55 DEBUG  WindowsBackend: keyboard_variant=
03-04 20:55 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-04 20:55 DEBUG  CommonBackend: locale=en_US.UTF-8
03-04 20:55 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-04 20:55 DEBUG  CommonBackend: Searching ISOs on USB devices
03-04 20:55 DEBUG  CommonBackend: Searching for local CDs
03-04 20:55 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp is a valid Ubuntu CD
03-04 20:55 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\casper\filesystem.squashfs
03-04 20:55 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp is a valid Ubuntu CD
03-04 20:55 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\casper\filesystem.squashfs
03-04 20:55 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp is a valid Ubuntu Netbook CD
03-04 20:55 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\casper\filesystem.squashfs
03-04 20:55 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp is a valid Kubuntu CD
03-04 20:55 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\casper\filesystem.squashfs
03-04 20:55 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp is a valid Kubuntu CD
03-04 20:55 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\casper\filesystem.squashfs
03-04 20:55 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp is a valid Kubuntu Netbook CD
03-04 20:55 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\casper\filesystem.squashfs
03-04 20:55 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp is a valid Xubuntu CD
03-04 20:55 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\casper\filesystem.squashfs
03-04 20:55 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp is a valid Xubuntu CD
03-04 20:55 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\casper\filesystem.squashfs
03-04 20:55 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp is a valid Mythbuntu CD
03-04 20:55 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\casper\filesystem.squashfs
03-04 20:55 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp is a valid Mythbuntu CD
03-04 20:55 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\casper\filesystem.squashfs
03-04 20:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 20:55 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-04 20:55 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-04 20:55 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-04 20:55 INFO   root: Running the CD menu...
03-04 20:55 DEBUG  WindowsFrontend: __init__...
03-04 20:55 DEBUG  WindowsFrontend: on_init...
03-04 20:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\translations, languages=['en_US', 'en']
03-04 20:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\translations, languages=['en_US', 'en']
03-04 20:55 INFO   root: CD menu finished
03-04 20:55 INFO   root: Already installed, running the uninstaller...
03-04 20:55 INFO   root: Running the uninstaller...
03-04 20:55 INFO   CommonBackend: This is the uninstaller running
03-04 20:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\translations, languages=['en_US', 'en']
03-04 20:55 INFO   root: Received settings
03-04 20:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\translations, languages=['en_US', 'en']
03-04 20:55 DEBUG  TaskList: # Running tasklist...
03-04 20:55 DEBUG  TaskList: ## Running Backup ISO...
03-04 20:55 DEBUG  TaskList: ## Finished Backup ISO
03-04 20:55 DEBUG  TaskList: ## Running Remove bootloader entry...
03-04 20:55 DEBUG  WindowsBackend: Could not find bcd id
03-04 20:55 DEBUG  WindowsBackend: undo_bootini C:
03-04 20:55 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 92195.4960938 mb free ntfs)
03-04 20:55 DEBUG  TaskList: ## Finished Remove bootloader entry
03-04 20:55 DEBUG  TaskList: ## Running Remove target dir...
03-04 20:55 DEBUG  CommonBackend: Deleting C:\ubuntu
03-04 20:55 DEBUG  TaskList: ## Finished Remove target dir
03-04 20:55 DEBUG  TaskList: ## Running Remove registry key...
03-04 20:55 DEBUG  TaskList: ## Finished Remove registry key
03-04 20:55 DEBUG  TaskList: # Finished tasklist
03-04 20:55 INFO   root: Almost finished uninstalling
03-04 20:55 INFO   root: Finished uninstallation
03-04 20:55 DEBUG  CommonBackend: Fetching basic info...
03-04 20:55 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-04 20:55 DEBUG  CommonBackend: platform=win32
03-04 20:55 DEBUG  CommonBackend: osname=nt
03-04 20:55 DEBUG  WindowsBackend: arch=amd64
03-04 20:55 DEBUG  CommonBackend: Parsing isolist=C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\data\isolist.ini
03-04 20:55 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-04 20:55 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-04 20:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-04 20:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-04 20:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-04 20:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-04 20:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-04 20:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-04 20:55 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-04 20:55 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-04 20:55 DEBUG  WindowsBackend: Fetching host info...
03-04 20:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-04 20:55 DEBUG  WindowsBackend: windows version=vista
03-04 20:55 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-04 20:55 DEBUG  WindowsBackend: windows_sp=None
03-04 20:55 DEBUG  WindowsBackend: windows_build=7600
03-04 20:55 DEBUG  WindowsBackend: gmt=-8
03-04 20:55 DEBUG  WindowsBackend: country=US
03-04 20:55 DEBUG  WindowsBackend: timezone=America/Los_Angeles
03-04 20:55 DEBUG  WindowsBackend: windows_username=SPARTAN 114
03-04 20:55 DEBUG  WindowsBackend: user_full_name=SPARTAN 114
03-04 20:55 DEBUG  WindowsBackend: user_directory=C:\Users\SPARTAN 114
03-04 20:55 DEBUG  WindowsBackend: windows_language_code=1033
03-04 20:55 DEBUG  WindowsBackend: windows_language=English
03-04 20:55 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
03-04 20:55 DEBUG  WindowsBackend: bootloader=vista
03-04 20:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 92889.0742188 mb free ntfs)
03-04 20:55 DEBUG  WindowsBackend: drive=Drive(C: hd 92889.0742188 mb free ntfs)
03-04 20:55 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-04 20:55 DEBUG  WindowsBackend: uninstaller_path=None
03-04 20:55 DEBUG  WindowsBackend: previous_target_dir=None
03-04 20:55 DEBUG  WindowsBackend: previous_distro_name=None
03-04 20:55 DEBUG  WindowsBackend: keyboard_id=67699721
03-04 20:55 DEBUG  WindowsBackend: keyboard_layout=us
03-04 20:55 DEBUG  WindowsBackend: keyboard_variant=
03-04 20:55 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-04 20:55 DEBUG  CommonBackend: Searching ISOs on USB devices
03-04 20:55 DEBUG  CommonBackend: Searching for local CDs
03-04 20:55 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp is a valid Ubuntu CD
03-04 20:55 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\casper\filesystem.squashfs
03-04 20:55 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp is a valid Ubuntu CD
03-04 20:55 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\casper\filesystem.squashfs
03-04 20:55 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp is a valid Ubuntu Netbook CD
03-04 20:55 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\casper\filesystem.squashfs
03-04 20:55 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp is a valid Kubuntu CD
03-04 20:55 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\casper\filesystem.squashfs
03-04 20:55 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp is a valid Kubuntu CD
03-04 20:55 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\casper\filesystem.squashfs
03-04 20:55 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp is a valid Kubuntu Netbook CD
03-04 20:55 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\casper\filesystem.squashfs
03-04 20:55 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp is a valid Xubuntu CD
03-04 20:55 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\casper\filesystem.squashfs
03-04 20:55 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp is a valid Xubuntu CD
03-04 20:55 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\casper\filesystem.squashfs
03-04 20:55 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp is a valid Mythbuntu CD
03-04 20:55 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\casper\filesystem.squashfs
03-04 20:55 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp is a valid Mythbuntu CD
03-04 20:55 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\casper\filesystem.squashfs
03-04 20:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 20:55 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-04 20:55 INFO   root: Running the installer...
03-04 20:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\translations, languages=['en_US', 'en']
03-04 20:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\translations, languages=['en_US', 'en']
03-04 20:56 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=spartan114
03-04 20:56 INFO   root: Received settings
03-04 20:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\translations, languages=['en_US', 'en']
03-04 20:56 DEBUG  TaskList: # Running tasklist...
03-04 20:56 DEBUG  TaskList: ## Running select_target_dir...
03-04 20:56 INFO   WindowsBackend: Installing into C:\ubuntu
03-04 20:56 DEBUG  TaskList: ## Finished select_target_dir
03-04 20:56 DEBUG  TaskList: ## Running create_dir_structure...
03-04 20:56 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-04 20:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-04 20:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-04 20:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-04 20:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-04 20:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-04 20:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-04 20:56 DEBUG  TaskList: ## Finished create_dir_structure
03-04 20:56 DEBUG  TaskList: ## Running uncompress_target_dir...
03-04 20:56 DEBUG  TaskList: ## Finished uncompress_target_dir
03-04 20:56 DEBUG  TaskList: ## Running create_uninstaller...
03-04 20:56 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-04 20:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-04 20:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-04 20:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-04 20:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-04 20:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-04 20:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-04 20:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-04 20:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-04 20:56 DEBUG  TaskList: ## Finished create_uninstaller
03-04 20:56 DEBUG  TaskList: ## Running copy_installation_files...
03-04 20:56 DEBUG  WindowsBackend: Copying C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-04 20:56 DEBUG  WindowsBackend: Copying C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\winboot -> C:\ubuntu\winboot
03-04 20:56 DEBUG  WindowsBackend: Copying C:\Users\SPARTA~1\AppData\Local\Temp\pylFD61.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-04 20:56 DEBUG  TaskList: ## Finished copy_installation_files
03-04 20:56 DEBUG  TaskList: ## Running get_iso...
03-04 20:56 DEBUG  TaskList: New task copy_file
03-04 20:56 DEBUG  TaskList: ### Running copy_file...
03-04 20:56 DEBUG  WindowsFrontend: frontend.on_quit
03-04 20:56 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
03-04 20:56 DEBUG  TaskList: # Cancelling tasklist
03-04 20:56 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
03-04 20:56 DEBUG  root: application.on_quit
03-04 20:56 DEBUG  root: Forceful exit
03-04 20:56 INFO   root: sys.exit
03-04 20:57 INFO   root: === wubi 10.10 rev197 ===
03-04 20:57 DEBUG  root: Logfile is c:\users\sparta~1\appdata\local\temp\wubi-10.10-rev197.log
03-04 20:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
03-04 20:57 DEBUG  CommonBackend: data_dir=C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp\data
03-04 20:57 DEBUG  WindowsBackend: 7z=C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp\bin\7z.exe
03-04 20:57 DEBUG  CommonBackend: Fetching basic info...
03-04 20:57 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
03-04 20:57 DEBUG  CommonBackend: platform=win32
03-04 20:57 DEBUG  CommonBackend: osname=nt
03-04 20:57 DEBUG  CommonBackend: language=en_US
03-04 20:57 DEBUG  CommonBackend: encoding=cp1252
03-04 20:57 DEBUG  WindowsBackend: arch=amd64
03-04 20:57 DEBUG  CommonBackend: Parsing isolist=C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp\data\isolist.ini
03-04 20:57 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-04 20:57 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-04 20:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-04 20:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-04 20:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-04 20:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-04 20:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-04 20:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-04 20:57 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-04 20:57 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-04 20:57 DEBUG  WindowsBackend: Fetching host info...
03-04 20:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-04 20:57 DEBUG  WindowsBackend: windows version=vista
03-04 20:57 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-04 20:57 DEBUG  WindowsBackend: windows_sp=None
03-04 20:57 DEBUG  WindowsBackend: windows_build=7600
03-04 20:57 DEBUG  WindowsBackend: gmt=-8
03-04 20:57 DEBUG  WindowsBackend: country=US
03-04 20:57 DEBUG  WindowsBackend: timezone=America/Los_Angeles
03-04 20:57 DEBUG  WindowsBackend: windows_username=SPARTAN 114
03-04 20:57 DEBUG  WindowsBackend: user_full_name=SPARTAN 114
03-04 20:57 DEBUG  WindowsBackend: user_directory=C:\Users\SPARTAN 114
03-04 20:57 DEBUG  WindowsBackend: windows_language_code=1033
03-04 20:57 DEBUG  WindowsBackend: windows_language=English
03-04 20:57 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
03-04 20:57 DEBUG  WindowsBackend: bootloader=vista
03-04 20:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 92867.2226563 mb free ntfs)
03-04 20:57 DEBUG  WindowsBackend: drive=Drive(C: hd 92867.2226563 mb free ntfs)
03-04 20:57 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-04 20:57 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-04 20:57 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-04 20:57 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-04 20:57 DEBUG  WindowsBackend: keyboard_id=67699721
03-04 20:57 DEBUG  WindowsBackend: keyboard_layout=us
03-04 20:57 DEBUG  WindowsBackend: keyboard_variant=
03-04 20:57 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-04 20:57 DEBUG  CommonBackend: locale=en_US.UTF-8
03-04 20:57 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-04 20:57 DEBUG  CommonBackend: Searching ISOs on USB devices
03-04 20:57 DEBUG  CommonBackend: Searching for local CDs
03-04 20:57 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp is a valid Ubuntu CD
03-04 20:57 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp\casper\filesystem.squashfs
03-04 20:57 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp is a valid Ubuntu CD
03-04 20:57 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp\casper\filesystem.squashfs
03-04 20:57 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp is a valid Ubuntu Netbook CD
03-04 20:57 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp\casper\filesystem.squashfs
03-04 20:57 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp is a valid Kubuntu CD
03-04 20:57 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp\casper\filesystem.squashfs
03-04 20:57 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp is a valid Kubuntu CD
03-04 20:57 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp\casper\filesystem.squashfs
03-04 20:57 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp is a valid Kubuntu Netbook CD
03-04 20:57 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp\casper\filesystem.squashfs
03-04 20:57 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp is a valid Xubuntu CD
03-04 20:57 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp\casper\filesystem.squashfs
03-04 20:57 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp is a valid Xubuntu CD
03-04 20:57 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp\casper\filesystem.squashfs
03-04 20:57 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp is a valid Mythbuntu CD
03-04 20:57 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp\casper\filesystem.squashfs
03-04 20:57 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp is a valid Mythbuntu CD
03-04 20:57 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp\casper\filesystem.squashfs
03-04 20:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 20:57 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-04 20:57 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-04 20:57 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-04 20:57 INFO   root: Running the uninstaller...
03-04 20:57 INFO   CommonBackend: This is the uninstaller running
03-04 20:57 DEBUG  WindowsFrontend: __init__...
03-04 20:57 DEBUG  WindowsFrontend: on_init...
03-04 20:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp\translations, languages=['en_US', 'en']
03-04 20:57 INFO   root: === wubi 10.10 rev197 ===
03-04 20:57 DEBUG  root: Logfile is c:\users\sparta~1\appdata\local\temp\wubi-10.10-rev197.log
03-04 20:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
03-04 20:57 DEBUG  CommonBackend: data_dir=C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp\data
03-04 20:57 DEBUG  WindowsBackend: 7z=C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp\bin\7z.exe
03-04 20:57 DEBUG  CommonBackend: Fetching basic info...
03-04 20:57 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
03-04 20:57 DEBUG  CommonBackend: platform=win32
03-04 20:57 DEBUG  CommonBackend: osname=nt
03-04 20:57 DEBUG  CommonBackend: language=en_US
03-04 20:57 DEBUG  CommonBackend: encoding=cp1252
03-04 20:57 DEBUG  WindowsBackend: arch=amd64
03-04 20:57 DEBUG  CommonBackend: Parsing isolist=C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp\data\isolist.ini
03-04 20:57 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-04 20:57 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-04 20:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-04 20:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-04 20:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-04 20:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-04 20:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-04 20:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-04 20:57 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-04 20:57 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-04 20:57 DEBUG  WindowsBackend: Fetching host info...
03-04 20:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-04 20:57 DEBUG  WindowsBackend: windows version=vista
03-04 20:57 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-04 20:57 DEBUG  WindowsBackend: windows_sp=None
03-04 20:57 DEBUG  WindowsBackend: windows_build=7600
03-04 20:57 DEBUG  WindowsBackend: gmt=-8
03-04 20:57 DEBUG  WindowsBackend: country=US
03-04 20:57 DEBUG  WindowsBackend: timezone=America/Los_Angeles
03-04 20:57 DEBUG  WindowsBackend: windows_username=SPARTAN 114
03-04 20:57 DEBUG  WindowsBackend: user_full_name=SPARTAN 114
03-04 20:57 DEBUG  WindowsBackend: user_directory=C:\Users\SPARTAN 114
03-04 20:57 DEBUG  WindowsBackend: windows_language_code=1033
03-04 20:57 DEBUG  WindowsBackend: windows_language=English
03-04 20:57 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
03-04 20:57 DEBUG  WindowsBackend: bootloader=vista
03-04 20:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 92873.3515625 mb free ntfs)
03-04 20:57 DEBUG  WindowsBackend: drive=Drive(C: hd 92873.3515625 mb free ntfs)
03-04 20:57 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-04 20:57 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-04 20:57 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-04 20:57 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-04 20:57 DEBUG  WindowsBackend: keyboard_id=67699721
03-04 20:57 DEBUG  WindowsBackend: keyboard_layout=us
03-04 20:57 DEBUG  WindowsBackend: keyboard_variant=
03-04 20:57 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-04 20:57 DEBUG  CommonBackend: locale=en_US.UTF-8
03-04 20:57 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-04 20:57 DEBUG  CommonBackend: Searching ISOs on USB devices
03-04 20:57 DEBUG  CommonBackend: Searching for local CDs
03-04 20:57 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp is a valid Ubuntu CD
03-04 20:57 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp\casper\filesystem.squashfs
03-04 20:57 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp is a valid Ubuntu CD
03-04 20:57 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp\casper\filesystem.squashfs
03-04 20:57 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp is a valid Ubuntu Netbook CD
03-04 20:57 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp\casper\filesystem.squashfs
03-04 20:57 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp is a valid Kubuntu CD
03-04 20:57 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp\casper\filesystem.squashfs
03-04 20:57 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp is a valid Kubuntu CD
03-04 20:57 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp\casper\filesystem.squashfs
03-04 20:57 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp is a valid Kubuntu Netbook CD
03-04 20:57 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp\casper\filesystem.squashfs
03-04 20:57 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp is a valid Xubuntu CD
03-04 20:57 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp\casper\filesystem.squashfs
03-04 20:57 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp is a valid Xubuntu CD
03-04 20:57 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp\casper\filesystem.squashfs
03-04 20:57 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp is a valid Mythbuntu CD
03-04 20:57 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp\casper\filesystem.squashfs
03-04 20:57 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp is a valid Mythbuntu CD
03-04 20:57 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp\casper\filesystem.squashfs
03-04 20:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 20:57 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-04 20:57 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-04 20:57 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-04 20:57 INFO   root: Running the uninstaller...
03-04 20:57 INFO   CommonBackend: This is the uninstaller running
03-04 20:57 DEBUG  WindowsFrontend: __init__...
03-04 20:57 DEBUG  WindowsFrontend: on_init...
03-04 20:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp\translations, languages=['en_US', 'en']
03-04 20:58 INFO   root: Received settings
03-04 20:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp\translations, languages=['en_US', 'en']
03-04 20:58 DEBUG  TaskList: # Running tasklist...
03-04 20:58 DEBUG  TaskList: ## Running Backup ISO...
03-04 20:58 DEBUG  TaskList: ## Finished Backup ISO
03-04 20:58 DEBUG  TaskList: ## Running Remove bootloader entry...
03-04 20:58 DEBUG  WindowsBackend: Could not find bcd id
03-04 20:58 DEBUG  WindowsBackend: undo_bootini C:
03-04 20:58 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 92873.3515625 mb free ntfs)
03-04 20:58 DEBUG  TaskList: ## Finished Remove bootloader entry
03-04 20:58 DEBUG  TaskList: ## Running Remove target dir...
03-04 20:58 DEBUG  CommonBackend: Deleting C:\ubuntu
03-04 20:58 DEBUG  TaskList: ## Finished Remove target dir
03-04 20:58 DEBUG  TaskList: ## Running Remove registry key...
03-04 20:58 DEBUG  TaskList: ## Finished Remove registry key
03-04 20:58 DEBUG  TaskList: # Finished tasklist
03-04 20:58 INFO   root: Almost finished uninstalling
03-04 20:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylE37B.tmp\translations, languages=['en_US', 'en']
03-04 20:58 INFO   root: Finished uninstallation
03-04 20:58 DEBUG  root: application.quit
03-04 20:58 DEBUG  WindowsFrontend: frontend.quit
03-04 20:58 DEBUG  WindowsFrontend: frontend.on_quit
03-04 20:58 DEBUG  root: application.on_quit
03-04 20:58 INFO   root: sys.exit
03-04 20:58 INFO   root: Received settings
03-04 20:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp\translations, languages=['en_US', 'en']
03-04 20:58 DEBUG  TaskList: # Running tasklist...
03-04 20:58 DEBUG  TaskList: ## Running Backup ISO...
03-04 20:58 DEBUG  TaskList: ## Finished Backup ISO
03-04 20:58 DEBUG  TaskList: ## Running Remove bootloader entry...
03-04 20:58 DEBUG  WindowsBackend: Could not find bcd id
03-04 20:58 DEBUG  WindowsBackend: undo_bootini C:
03-04 20:58 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 92867.2226563 mb free ntfs)
03-04 20:58 DEBUG  TaskList: ## Finished Remove bootloader entry
03-04 20:58 DEBUG  TaskList: ## Running Remove target dir...
03-04 20:58 DEBUG  CommonBackend: Cannot find C:\ubuntu
03-04 20:58 DEBUG  TaskList: ## Finished Remove target dir
03-04 20:58 DEBUG  TaskList: ## Running Remove registry key...
03-04 20:58 ERROR  registry: Cannot delete registry key Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
[Errno 2] The system cannot find the file specified
Traceback (most recent call last):
  File "\lib\wubi\backends\win32\registry.py", line 56, in delete_key
WindowsError: [Errno 2] The system cannot find the file specified
03-04 20:58 DEBUG  TaskList: ## Finished Remove registry key
03-04 20:58 DEBUG  TaskList: # Finished tasklist
03-04 20:58 INFO   root: Almost finished uninstalling
03-04 20:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylE3B9.tmp\translations, languages=['en_US', 'en']
03-04 20:58 INFO   root: Finished uninstallation
03-04 20:58 DEBUG  root: application.quit
03-04 20:58 DEBUG  WindowsFrontend: frontend.quit
03-04 20:58 DEBUG  WindowsFrontend: frontend.on_quit
03-04 20:58 DEBUG  root: application.on_quit
03-04 20:58 INFO   root: sys.exit
03-04 22:31 INFO   root: === wubi 10.10 rev197 ===
03-04 22:31 DEBUG  root: Logfile is c:\users\sparta~1\appdata\local\temp\wubi-10.10-rev197.log
03-04 22:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
03-04 22:31 DEBUG  CommonBackend: data_dir=C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp\data
03-04 22:31 DEBUG  WindowsBackend: 7z=C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp\bin\7z.exe
03-04 22:31 DEBUG  CommonBackend: Fetching basic info...
03-04 22:31 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-04 22:31 DEBUG  CommonBackend: platform=win32
03-04 22:31 DEBUG  CommonBackend: osname=nt
03-04 22:31 DEBUG  CommonBackend: language=en_US
03-04 22:31 DEBUG  CommonBackend: encoding=cp1252
03-04 22:31 DEBUG  WindowsBackend: arch=amd64
03-04 22:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp\data\isolist.ini
03-04 22:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-04 22:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-04 22:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-04 22:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-04 22:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-04 22:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-04 22:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-04 22:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-04 22:31 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-04 22:31 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-04 22:31 DEBUG  WindowsBackend: Fetching host info...
03-04 22:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-04 22:31 DEBUG  WindowsBackend: windows version=vista
03-04 22:31 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-04 22:31 DEBUG  WindowsBackend: windows_sp=None
03-04 22:31 DEBUG  WindowsBackend: windows_build=7600
03-04 22:31 DEBUG  WindowsBackend: gmt=-8
03-04 22:31 DEBUG  WindowsBackend: country=US
03-04 22:31 DEBUG  WindowsBackend: timezone=America/Los_Angeles
03-04 22:31 DEBUG  WindowsBackend: windows_username=SPARTAN 114
03-04 22:31 DEBUG  WindowsBackend: user_full_name=SPARTAN 114
03-04 22:31 DEBUG  WindowsBackend: user_directory=C:\Users\SPARTAN 114
03-04 22:31 DEBUG  WindowsBackend: windows_language_code=1033
03-04 22:31 DEBUG  WindowsBackend: windows_language=English
03-04 22:31 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
03-04 22:31 DEBUG  WindowsBackend: bootloader=vista
03-04 22:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 92888.71875 mb free ntfs)
03-04 22:31 DEBUG  WindowsBackend: drive=Drive(C: hd 92888.71875 mb free ntfs)
03-04 22:31 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-04 22:31 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-04 22:31 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-04 22:31 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-04 22:31 DEBUG  WindowsBackend: keyboard_id=67699721
03-04 22:31 DEBUG  WindowsBackend: keyboard_layout=us
03-04 22:31 DEBUG  WindowsBackend: keyboard_variant=
03-04 22:31 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-04 22:31 DEBUG  CommonBackend: locale=en_US.UTF-8
03-04 22:31 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-04 22:31 DEBUG  CommonBackend: Searching ISOs on USB devices
03-04 22:31 DEBUG  CommonBackend: Searching for local CDs
03-04 22:31 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp is a valid Ubuntu CD
03-04 22:31 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp\casper\filesystem.squashfs
03-04 22:31 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp is a valid Ubuntu CD
03-04 22:31 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp\casper\filesystem.squashfs
03-04 22:31 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp is a valid Ubuntu Netbook CD
03-04 22:31 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp\casper\filesystem.squashfs
03-04 22:31 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp is a valid Kubuntu CD
03-04 22:31 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp\casper\filesystem.squashfs
03-04 22:31 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp is a valid Kubuntu CD
03-04 22:31 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp\casper\filesystem.squashfs
03-04 22:31 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp is a valid Kubuntu Netbook CD
03-04 22:31 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp\casper\filesystem.squashfs
03-04 22:31 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp is a valid Xubuntu CD
03-04 22:31 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp\casper\filesystem.squashfs
03-04 22:31 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp is a valid Xubuntu CD
03-04 22:31 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp\casper\filesystem.squashfs
03-04 22:31 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp is a valid Mythbuntu CD
03-04 22:31 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp\casper\filesystem.squashfs
03-04 22:31 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp is a valid Mythbuntu CD
03-04 22:31 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp\casper\filesystem.squashfs
03-04 22:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 22:31 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-04 22:31 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-04 22:31 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-04 22:31 INFO   root: Running the CD menu...
03-04 22:31 DEBUG  WindowsFrontend: __init__...
03-04 22:31 DEBUG  WindowsFrontend: on_init...
03-04 22:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp\translations, languages=['en_US', 'en']
03-04 22:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylB598.tmp\translations, languages=['en_US', 'en']
03-04 22:31 INFO   root: CD menu finished
03-04 22:31 INFO   root: Already installed, running the uninstaller...
03-04 22:31 INFO   root: Running the uninstaller...
03-04 22:31 INFO   CommonBackend: Launching previous uninestaller C:\ubuntu\uninstall-wubi.exe
03-04 22:31 DEBUG  root: application.quit
03-04 22:31 DEBUG  WindowsFrontend: frontend.quit
03-04 22:31 DEBUG  WindowsFrontend: frontend.on_quit
03-04 22:31 DEBUG  root: application.on_quit
03-04 22:31 INFO   root: sys.exit
03-04 22:32 INFO   root: === wubi 10.10 rev197 ===
03-04 22:32 DEBUG  root: Logfile is c:\users\sparta~1\appdata\local\temp\wubi-10.10-rev197.log
03-04 22:32 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
03-04 22:32 DEBUG  CommonBackend: data_dir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp\data
03-04 22:32 DEBUG  WindowsBackend: 7z=C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp\bin\7z.exe
03-04 22:32 DEBUG  CommonBackend: Fetching basic info...
03-04 22:32 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-04 22:32 DEBUG  CommonBackend: platform=win32
03-04 22:32 DEBUG  CommonBackend: osname=nt
03-04 22:32 DEBUG  CommonBackend: language=en_US
03-04 22:32 DEBUG  CommonBackend: encoding=cp1252
03-04 22:32 DEBUG  WindowsBackend: arch=amd64
03-04 22:32 DEBUG  CommonBackend: Parsing isolist=C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp\data\isolist.ini
03-04 22:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-04 22:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-04 22:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-04 22:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-04 22:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-04 22:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-04 22:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-04 22:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-04 22:32 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-04 22:32 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-04 22:32 DEBUG  WindowsBackend: Fetching host info...
03-04 22:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-04 22:32 DEBUG  WindowsBackend: windows version=vista
03-04 22:32 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-04 22:32 DEBUG  WindowsBackend: windows_sp=None
03-04 22:32 DEBUG  WindowsBackend: windows_build=7600
03-04 22:32 DEBUG  WindowsBackend: gmt=-8
03-04 22:32 DEBUG  WindowsBackend: country=US
03-04 22:32 DEBUG  WindowsBackend: timezone=America/Los_Angeles
03-04 22:32 DEBUG  WindowsBackend: windows_username=SPARTAN 114
03-04 22:32 DEBUG  WindowsBackend: user_full_name=SPARTAN 114
03-04 22:32 DEBUG  WindowsBackend: user_directory=C:\Users\SPARTAN 114
03-04 22:32 DEBUG  WindowsBackend: windows_language_code=1033
03-04 22:32 DEBUG  WindowsBackend: windows_language=English
03-04 22:32 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
03-04 22:32 DEBUG  WindowsBackend: bootloader=vista
03-04 22:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 92889.4179688 mb free ntfs)
03-04 22:32 DEBUG  WindowsBackend: drive=Drive(C: hd 92889.4179688 mb free ntfs)
03-04 22:32 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-04 22:32 DEBUG  WindowsBackend: uninstaller_path=None
03-04 22:32 DEBUG  WindowsBackend: previous_target_dir=None
03-04 22:32 DEBUG  WindowsBackend: previous_distro_name=None
03-04 22:32 DEBUG  WindowsBackend: keyboard_id=67699721
03-04 22:32 DEBUG  WindowsBackend: keyboard_layout=us
03-04 22:32 DEBUG  WindowsBackend: keyboard_variant=
03-04 22:32 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-04 22:32 DEBUG  CommonBackend: locale=en_US.UTF-8
03-04 22:32 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-04 22:32 DEBUG  CommonBackend: Searching ISOs on USB devices
03-04 22:32 DEBUG  CommonBackend: Searching for local CDs
03-04 22:32 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp is a valid Ubuntu CD
03-04 22:32 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp\casper\filesystem.squashfs
03-04 22:32 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp is a valid Ubuntu CD
03-04 22:32 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp\casper\filesystem.squashfs
03-04 22:32 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp is a valid Ubuntu Netbook CD
03-04 22:32 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp\casper\filesystem.squashfs
03-04 22:32 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp is a valid Kubuntu CD
03-04 22:32 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp\casper\filesystem.squashfs
03-04 22:32 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp is a valid Kubuntu CD
03-04 22:32 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp\casper\filesystem.squashfs
03-04 22:32 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp is a valid Kubuntu Netbook CD
03-04 22:32 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp\casper\filesystem.squashfs
03-04 22:32 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp is a valid Xubuntu CD
03-04 22:32 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp\casper\filesystem.squashfs
03-04 22:32 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp is a valid Xubuntu CD
03-04 22:32 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp\casper\filesystem.squashfs
03-04 22:32 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp is a valid Mythbuntu CD
03-04 22:32 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp\casper\filesystem.squashfs
03-04 22:32 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp is a valid Mythbuntu CD
03-04 22:32 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp\casper\filesystem.squashfs
03-04 22:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 22:32 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-04 22:32 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-04 22:32 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-04 22:32 INFO   root: Running the CD menu...
03-04 22:32 DEBUG  WindowsFrontend: __init__...
03-04 22:32 DEBUG  WindowsFrontend: on_init...
03-04 22:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp\translations, languages=['en_US', 'en']
03-04 22:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp\translations, languages=['en_US', 'en']
03-04 22:32 INFO   root: CD menu finished
03-04 22:32 INFO   root: Running the installer...
03-04 22:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp\translations, languages=['en_US', 'en']
03-04 22:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp\translations, languages=['en_US', 'en']
03-04 22:32 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=spartan114
03-04 22:32 INFO   root: Received settings
03-04 22:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp\translations, languages=['en_US', 'en']
03-04 22:32 DEBUG  TaskList: # Running tasklist...
03-04 22:32 DEBUG  TaskList: ## Running select_target_dir...
03-04 22:32 INFO   WindowsBackend: Installing into C:\ubuntu
03-04 22:32 DEBUG  TaskList: ## Finished select_target_dir
03-04 22:32 DEBUG  TaskList: ## Running create_dir_structure...
03-04 22:32 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-04 22:32 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-04 22:32 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-04 22:32 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-04 22:32 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-04 22:32 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-04 22:32 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-04 22:32 DEBUG  TaskList: ## Finished create_dir_structure
03-04 22:32 DEBUG  TaskList: ## Running uncompress_target_dir...
03-04 22:32 DEBUG  TaskList: ## Finished uncompress_target_dir
03-04 22:32 DEBUG  TaskList: ## Running create_uninstaller...
03-04 22:32 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-04 22:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-04 22:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-04 22:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-04 22:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-04 22:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-04 22:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-04 22:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-04 22:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-04 22:32 DEBUG  TaskList: ## Finished create_uninstaller
03-04 22:32 DEBUG  TaskList: ## Running copy_installation_files...
03-04 22:32 DEBUG  WindowsBackend: Copying C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-04 22:32 DEBUG  WindowsBackend: Copying C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp\winboot -> C:\ubuntu\winboot
03-04 22:32 DEBUG  WindowsBackend: Copying C:\Users\SPARTA~1\AppData\Local\Temp\pyl4E6D.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-04 22:32 DEBUG  TaskList: ## Finished copy_installation_files
03-04 22:32 DEBUG  TaskList: ## Running get_iso...
03-04 22:32 DEBUG  TaskList: New task copy_file
03-04 22:32 DEBUG  TaskList: ### Running copy_file...
03-04 22:34 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
03-04 22:34 DEBUG  TaskList: # Cancelling tasklist
03-04 22:34 DEBUG  TaskList: New task check_iso
03-04 22:34 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
03-04 22:34 DEBUG  CommonBackend: Searching for local ISO
03-04 22:34 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-04 22:34 DEBUG  TaskList: New task get_metalink
03-04 22:34 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
03-04 22:34 DEBUG  TaskList: # Cancelling tasklist
03-04 22:34 DEBUG  TaskList: # Finished tasklist
03-04 22:38 INFO   root: === wubi 10.10 rev197 ===
03-04 22:38 DEBUG  root: Logfile is c:\users\sparta~1\appdata\local\temp\wubi-10.10-rev197.log
03-04 22:38 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
03-04 22:38 DEBUG  CommonBackend: data_dir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\data
03-04 22:38 DEBUG  WindowsBackend: 7z=C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\bin\7z.exe
03-04 22:38 DEBUG  CommonBackend: Fetching basic info...
03-04 22:38 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-04 22:38 DEBUG  CommonBackend: platform=win32
03-04 22:38 DEBUG  CommonBackend: osname=nt
03-04 22:38 DEBUG  CommonBackend: language=en_US
03-04 22:38 DEBUG  CommonBackend: encoding=cp1252
03-04 22:38 DEBUG  WindowsBackend: arch=amd64
03-04 22:38 DEBUG  CommonBackend: Parsing isolist=C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\data\isolist.ini
03-04 22:38 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-04 22:38 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-04 22:38 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-04 22:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-04 22:38 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-04 22:38 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-04 22:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-04 22:38 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-04 22:38 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-04 22:38 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-04 22:38 DEBUG  WindowsBackend: Fetching host info...
03-04 22:38 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-04 22:38 DEBUG  WindowsBackend: windows version=vista
03-04 22:38 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-04 22:38 DEBUG  WindowsBackend: windows_sp=None
03-04 22:38 DEBUG  WindowsBackend: windows_build=7600
03-04 22:38 DEBUG  WindowsBackend: gmt=-8
03-04 22:38 DEBUG  WindowsBackend: country=US
03-04 22:38 DEBUG  WindowsBackend: timezone=America/Los_Angeles
03-04 22:38 DEBUG  WindowsBackend: windows_username=SPARTAN 114
03-04 22:38 DEBUG  WindowsBackend: user_full_name=SPARTAN 114
03-04 22:38 DEBUG  WindowsBackend: user_directory=C:\Users\SPARTAN 114
03-04 22:38 DEBUG  WindowsBackend: windows_language_code=1033
03-04 22:38 DEBUG  WindowsBackend: windows_language=English
03-04 22:38 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
03-04 22:38 DEBUG  WindowsBackend: bootloader=vista
03-04 22:38 DEBUG  WindowsBackend: system_drive=Drive(C: hd 92192.7734375 mb free ntfs)
03-04 22:38 DEBUG  WindowsBackend: drive=Drive(C: hd 92192.7734375 mb free ntfs)
03-04 22:38 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-04 22:38 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-04 22:38 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-04 22:38 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-04 22:38 DEBUG  WindowsBackend: keyboard_id=67699721
03-04 22:38 DEBUG  WindowsBackend: keyboard_layout=us
03-04 22:38 DEBUG  WindowsBackend: keyboard_variant=
03-04 22:38 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-04 22:38 DEBUG  CommonBackend: locale=en_US.UTF-8
03-04 22:38 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-04 22:38 DEBUG  CommonBackend: Searching ISOs on USB devices
03-04 22:38 DEBUG  CommonBackend: Searching for local CDs
03-04 22:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp is a valid Ubuntu CD
03-04 22:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\casper\filesystem.squashfs
03-04 22:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp is a valid Ubuntu CD
03-04 22:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\casper\filesystem.squashfs
03-04 22:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp is a valid Ubuntu Netbook CD
03-04 22:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\casper\filesystem.squashfs
03-04 22:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp is a valid Kubuntu CD
03-04 22:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\casper\filesystem.squashfs
03-04 22:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp is a valid Kubuntu CD
03-04 22:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\casper\filesystem.squashfs
03-04 22:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp is a valid Kubuntu Netbook CD
03-04 22:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\casper\filesystem.squashfs
03-04 22:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp is a valid Xubuntu CD
03-04 22:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\casper\filesystem.squashfs
03-04 22:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp is a valid Xubuntu CD
03-04 22:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\casper\filesystem.squashfs
03-04 22:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp is a valid Mythbuntu CD
03-04 22:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\casper\filesystem.squashfs
03-04 22:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp is a valid Mythbuntu CD
03-04 22:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\casper\filesystem.squashfs
03-04 22:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 22:38 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-04 22:38 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-04 22:38 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-04 22:38 INFO   root: Running the CD menu...
03-04 22:38 DEBUG  WindowsFrontend: __init__...
03-04 22:38 DEBUG  WindowsFrontend: on_init...
03-04 22:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\translations, languages=['en_US', 'en']
03-04 22:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\translations, languages=['en_US', 'en']
03-04 22:38 INFO   root: CD menu finished
03-04 22:38 INFO   root: Already installed, running the uninstaller...
03-04 22:38 INFO   root: Running the uninstaller...
03-04 22:38 INFO   CommonBackend: This is the uninstaller running
03-04 22:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\translations, languages=['en_US', 'en']
03-04 22:38 INFO   root: Received settings
03-04 22:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\translations, languages=['en_US', 'en']
03-04 22:38 DEBUG  TaskList: # Running tasklist...
03-04 22:38 DEBUG  TaskList: ## Running Backup ISO...
03-04 22:38 DEBUG  TaskList: ## Finished Backup ISO
03-04 22:38 DEBUG  TaskList: ## Running Remove bootloader entry...
03-04 22:38 DEBUG  WindowsBackend: Could not find bcd id
03-04 22:38 DEBUG  WindowsBackend: undo_bootini C:
03-04 22:38 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 92192.7734375 mb free ntfs)
03-04 22:38 DEBUG  TaskList: ## Finished Remove bootloader entry
03-04 22:38 DEBUG  TaskList: ## Running Remove target dir...
03-04 22:38 DEBUG  CommonBackend: Deleting C:\ubuntu
03-04 22:38 DEBUG  TaskList: ## Finished Remove target dir
03-04 22:38 DEBUG  TaskList: ## Running Remove registry key...
03-04 22:38 DEBUG  TaskList: ## Finished Remove registry key
03-04 22:38 DEBUG  TaskList: # Finished tasklist
03-04 22:38 INFO   root: Almost finished uninstalling
03-04 22:38 INFO   root: Finished uninstallation
03-04 22:38 DEBUG  CommonBackend: Fetching basic info...
03-04 22:38 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-04 22:38 DEBUG  CommonBackend: platform=win32
03-04 22:38 DEBUG  CommonBackend: osname=nt
03-04 22:38 DEBUG  WindowsBackend: arch=amd64
03-04 22:38 DEBUG  CommonBackend: Parsing isolist=C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\data\isolist.ini
03-04 22:38 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-04 22:38 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-04 22:38 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-04 22:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-04 22:38 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-04 22:38 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-04 22:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-04 22:38 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-04 22:38 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-04 22:38 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-04 22:38 DEBUG  WindowsBackend: Fetching host info...
03-04 22:38 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-04 22:38 DEBUG  WindowsBackend: windows version=vista
03-04 22:38 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-04 22:38 DEBUG  WindowsBackend: windows_sp=None
03-04 22:38 DEBUG  WindowsBackend: windows_build=7600
03-04 22:38 DEBUG  WindowsBackend: gmt=-8
03-04 22:38 DEBUG  WindowsBackend: country=US
03-04 22:38 DEBUG  WindowsBackend: timezone=America/Los_Angeles
03-04 22:38 DEBUG  WindowsBackend: windows_username=SPARTAN 114
03-04 22:38 DEBUG  WindowsBackend: user_full_name=SPARTAN 114
03-04 22:38 DEBUG  WindowsBackend: user_directory=C:\Users\SPARTAN 114
03-04 22:38 DEBUG  WindowsBackend: windows_language_code=1033
03-04 22:38 DEBUG  WindowsBackend: windows_language=English
03-04 22:38 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
03-04 22:38 DEBUG  WindowsBackend: bootloader=vista
03-04 22:38 DEBUG  WindowsBackend: system_drive=Drive(C: hd 92886.3476563 mb free ntfs)
03-04 22:38 DEBUG  WindowsBackend: drive=Drive(C: hd 92886.3476563 mb free ntfs)
03-04 22:38 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-04 22:38 DEBUG  WindowsBackend: uninstaller_path=None
03-04 22:38 DEBUG  WindowsBackend: previous_target_dir=None
03-04 22:38 DEBUG  WindowsBackend: previous_distro_name=None
03-04 22:38 DEBUG  WindowsBackend: keyboard_id=67699721
03-04 22:38 DEBUG  WindowsBackend: keyboard_layout=us
03-04 22:38 DEBUG  WindowsBackend: keyboard_variant=
03-04 22:38 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-04 22:38 DEBUG  CommonBackend: Searching ISOs on USB devices
03-04 22:38 DEBUG  CommonBackend: Searching for local CDs
03-04 22:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp is a valid Ubuntu CD
03-04 22:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\casper\filesystem.squashfs
03-04 22:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp is a valid Ubuntu CD
03-04 22:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\casper\filesystem.squashfs
03-04 22:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp is a valid Ubuntu Netbook CD
03-04 22:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\casper\filesystem.squashfs
03-04 22:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp is a valid Kubuntu CD
03-04 22:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\casper\filesystem.squashfs
03-04 22:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp is a valid Kubuntu CD
03-04 22:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\casper\filesystem.squashfs
03-04 22:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp is a valid Kubuntu Netbook CD
03-04 22:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\casper\filesystem.squashfs
03-04 22:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp is a valid Xubuntu CD
03-04 22:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\casper\filesystem.squashfs
03-04 22:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp is a valid Xubuntu CD
03-04 22:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\casper\filesystem.squashfs
03-04 22:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp is a valid Mythbuntu CD
03-04 22:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\casper\filesystem.squashfs
03-04 22:38 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp is a valid Mythbuntu CD
03-04 22:38 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\casper\filesystem.squashfs
03-04 22:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-04 22:38 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-04 22:38 INFO   root: Running the installer...
03-04 22:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\translations, languages=['en_US', 'en']
03-04 22:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\translations, languages=['en_US', 'en']
03-04 22:39 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=spartan114
03-04 22:39 INFO   root: Received settings
03-04 22:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\translations, languages=['en_US', 'en']
03-04 22:39 DEBUG  TaskList: # Running tasklist...
03-04 22:39 DEBUG  TaskList: ## Running select_target_dir...
03-04 22:39 INFO   WindowsBackend: Installing into C:\ubuntu
03-04 22:39 DEBUG  TaskList: ## Finished select_target_dir
03-04 22:39 DEBUG  TaskList: ## Running create_dir_structure...
03-04 22:39 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-04 22:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-04 22:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-04 22:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-04 22:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-04 22:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-04 22:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-04 22:39 DEBUG  TaskList: ## Finished create_dir_structure
03-04 22:39 DEBUG  TaskList: ## Running uncompress_target_dir...
03-04 22:39 DEBUG  TaskList: ## Finished uncompress_target_dir
03-04 22:39 DEBUG  TaskList: ## Running create_uninstaller...
03-04 22:39 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-04 22:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-04 22:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-04 22:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-04 22:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-04 22:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-04 22:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-04 22:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-04 22:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-04 22:39 DEBUG  TaskList: ## Finished create_uninstaller
03-04 22:39 DEBUG  TaskList: ## Running copy_installation_files...
03-04 22:39 DEBUG  WindowsBackend: Copying C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-04 22:39 DEBUG  WindowsBackend: Copying C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\winboot -> C:\ubuntu\winboot
03-04 22:39 DEBUG  WindowsBackend: Copying C:\Users\SPARTA~1\AppData\Local\Temp\pyl279C.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-04 22:39 DEBUG  TaskList: ## Finished copy_installation_files
03-04 22:39 DEBUG  TaskList: ## Running get_iso...
03-04 22:39 DEBUG  TaskList: New task copy_file
03-04 22:39 DEBUG  TaskList: ### Running copy_file...
03-04 22:41 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
03-04 22:41 DEBUG  TaskList: # Cancelling tasklist
03-04 22:41 DEBUG  TaskList: New task check_iso
03-04 22:41 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
03-04 22:41 DEBUG  CommonBackend: Searching for local ISO
03-04 22:41 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-04 22:41 DEBUG  TaskList: New task get_metalink
03-04 22:41 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
03-04 22:41 DEBUG  TaskList: # Cancelling tasklist
03-04 22:41 DEBUG  TaskList: # Finished tasklist
03-06 20:26 INFO   root: === wubi 10.10 rev197 ===
03-06 20:26 DEBUG  root: Logfile is c:\users\sparta~1\appdata\local\temp\wubi-10.10-rev197.log
03-06 20:26 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
03-06 20:26 DEBUG  CommonBackend: data_dir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp\data
03-06 20:26 DEBUG  WindowsBackend: 7z=C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp\bin\7z.exe
03-06 20:26 DEBUG  CommonBackend: Fetching basic info...
03-06 20:26 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-06 20:26 DEBUG  CommonBackend: platform=win32
03-06 20:26 DEBUG  CommonBackend: osname=nt
03-06 20:26 DEBUG  CommonBackend: language=en_US
03-06 20:26 DEBUG  CommonBackend: encoding=cp1252
03-06 20:26 DEBUG  WindowsBackend: arch=amd64
03-06 20:26 DEBUG  CommonBackend: Parsing isolist=C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp\data\isolist.ini
03-06 20:26 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-06 20:26 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-06 20:26 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-06 20:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-06 20:26 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-06 20:26 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-06 20:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-06 20:26 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-06 20:26 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-06 20:26 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-06 20:26 DEBUG  WindowsBackend: Fetching host info...
03-06 20:26 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-06 20:26 DEBUG  WindowsBackend: windows version=vista
03-06 20:26 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-06 20:26 DEBUG  WindowsBackend: windows_sp=None
03-06 20:26 DEBUG  WindowsBackend: windows_build=7600
03-06 20:26 DEBUG  WindowsBackend: gmt=-8
03-06 20:26 DEBUG  WindowsBackend: country=US
03-06 20:26 DEBUG  WindowsBackend: timezone=America/Los_Angeles
03-06 20:26 DEBUG  WindowsBackend: windows_username=SPARTAN 114
03-06 20:26 DEBUG  WindowsBackend: user_full_name=SPARTAN 114
03-06 20:26 DEBUG  WindowsBackend: user_directory=C:\Users\SPARTAN 114
03-06 20:26 DEBUG  WindowsBackend: windows_language_code=1033
03-06 20:26 DEBUG  WindowsBackend: windows_language=English
03-06 20:26 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
03-06 20:26 DEBUG  WindowsBackend: bootloader=vista
03-06 20:26 DEBUG  WindowsBackend: system_drive=Drive(C: hd 75484.3828125 mb free ntfs)
03-06 20:26 DEBUG  WindowsBackend: drive=Drive(C: hd 75484.3828125 mb free ntfs)
03-06 20:26 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-06 20:26 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-06 20:26 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-06 20:26 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-06 20:26 DEBUG  WindowsBackend: keyboard_id=67699721
03-06 20:26 DEBUG  WindowsBackend: keyboard_layout=us
03-06 20:26 DEBUG  WindowsBackend: keyboard_variant=
03-06 20:26 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-06 20:26 DEBUG  CommonBackend: locale=en_US.UTF-8
03-06 20:26 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-06 20:26 DEBUG  CommonBackend: Searching ISOs on USB devices
03-06 20:26 DEBUG  CommonBackend: Searching for local CDs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp is a valid Ubuntu CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp is a valid Ubuntu CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp is a valid Ubuntu Netbook CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp is a valid Kubuntu CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp is a valid Kubuntu CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp is a valid Kubuntu Netbook CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp is a valid Xubuntu CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp is a valid Xubuntu CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp is a valid Mythbuntu CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp is a valid Mythbuntu CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-06 20:26 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-06 20:26 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-06 20:26 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-06 20:26 INFO   root: Running the CD menu...
03-06 20:26 DEBUG  WindowsFrontend: __init__...
03-06 20:26 DEBUG  WindowsFrontend: on_init...
03-06 20:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp\translations, languages=['en_US', 'en']
03-06 20:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pyl89EA.tmp\translations, languages=['en_US', 'en']
03-06 20:26 INFO   WindowsFrontend: Operation cancelled
03-06 20:26 DEBUG  WindowsFrontend: frontend.quit
03-06 20:26 DEBUG  WindowsFrontend: frontend.on_quit
03-06 20:26 DEBUG  root: application.on_quit
03-06 20:26 INFO   root: sys.exit
03-06 20:26 INFO   root: === wubi 10.10 rev197 ===
03-06 20:26 DEBUG  root: Logfile is c:\users\sparta~1\appdata\local\temp\wubi-10.10-rev197.log
03-06 20:26 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
03-06 20:26 DEBUG  CommonBackend: data_dir=C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\data
03-06 20:26 DEBUG  WindowsBackend: 7z=C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\bin\7z.exe
03-06 20:26 DEBUG  CommonBackend: Fetching basic info...
03-06 20:26 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-06 20:26 DEBUG  CommonBackend: platform=win32
03-06 20:26 DEBUG  CommonBackend: osname=nt
03-06 20:26 DEBUG  CommonBackend: language=en_US
03-06 20:26 DEBUG  CommonBackend: encoding=cp1252
03-06 20:26 DEBUG  WindowsBackend: arch=amd64
03-06 20:26 DEBUG  CommonBackend: Parsing isolist=C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\data\isolist.ini
03-06 20:26 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-06 20:26 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-06 20:26 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-06 20:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-06 20:26 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-06 20:26 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-06 20:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-06 20:26 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-06 20:26 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-06 20:26 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-06 20:26 DEBUG  WindowsBackend: Fetching host info...
03-06 20:26 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-06 20:26 DEBUG  WindowsBackend: windows version=vista
03-06 20:26 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-06 20:26 DEBUG  WindowsBackend: windows_sp=None
03-06 20:26 DEBUG  WindowsBackend: windows_build=7600
03-06 20:26 DEBUG  WindowsBackend: gmt=-8
03-06 20:26 DEBUG  WindowsBackend: country=US
03-06 20:26 DEBUG  WindowsBackend: timezone=America/Los_Angeles
03-06 20:26 DEBUG  WindowsBackend: windows_username=SPARTAN 114
03-06 20:26 DEBUG  WindowsBackend: user_full_name=SPARTAN 114
03-06 20:26 DEBUG  WindowsBackend: user_directory=C:\Users\SPARTAN 114
03-06 20:26 DEBUG  WindowsBackend: windows_language_code=1033
03-06 20:26 DEBUG  WindowsBackend: windows_language=English
03-06 20:26 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
03-06 20:26 DEBUG  WindowsBackend: bootloader=vista
03-06 20:26 DEBUG  WindowsBackend: system_drive=Drive(C: hd 75262.2265625 mb free ntfs)
03-06 20:26 DEBUG  WindowsBackend: drive=Drive(C: hd 75262.2265625 mb free ntfs)
03-06 20:26 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-06 20:26 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-06 20:26 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-06 20:26 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-06 20:26 DEBUG  WindowsBackend: keyboard_id=67699721
03-06 20:26 DEBUG  WindowsBackend: keyboard_layout=us
03-06 20:26 DEBUG  WindowsBackend: keyboard_variant=
03-06 20:26 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-06 20:26 DEBUG  CommonBackend: locale=en_US.UTF-8
03-06 20:26 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-06 20:26 DEBUG  CommonBackend: Searching ISOs on USB devices
03-06 20:26 DEBUG  CommonBackend: Searching for local CDs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp is a valid Ubuntu CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp is a valid Ubuntu CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp is a valid Ubuntu Netbook CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp is a valid Kubuntu CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp is a valid Kubuntu CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp is a valid Kubuntu Netbook CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp is a valid Xubuntu CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp is a valid Xubuntu CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp is a valid Mythbuntu CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp is a valid Mythbuntu CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-06 20:26 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-06 20:26 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-06 20:26 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-06 20:26 INFO   root: Running the CD menu...
03-06 20:26 DEBUG  WindowsFrontend: __init__...
03-06 20:26 DEBUG  WindowsFrontend: on_init...
03-06 20:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\translations, languages=['en_US', 'en']
03-06 20:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\translations, languages=['en_US', 'en']
03-06 20:26 INFO   root: CD menu finished
03-06 20:26 INFO   root: Already installed, running the uninstaller...
03-06 20:26 INFO   root: Running the uninstaller...
03-06 20:26 INFO   CommonBackend: This is the uninstaller running
03-06 20:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\translations, languages=['en_US', 'en']
03-06 20:26 INFO   root: Received settings
03-06 20:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\translations, languages=['en_US', 'en']
03-06 20:26 DEBUG  TaskList: # Running tasklist...
03-06 20:26 DEBUG  TaskList: ## Running Backup ISO...
03-06 20:26 DEBUG  TaskList: ## Finished Backup ISO
03-06 20:26 DEBUG  TaskList: ## Running Remove bootloader entry...
03-06 20:26 DEBUG  WindowsBackend: Could not find bcd id
03-06 20:26 DEBUG  WindowsBackend: undo_bootini C:
03-06 20:26 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 75262.2265625 mb free ntfs)
03-06 20:26 DEBUG  TaskList: ## Finished Remove bootloader entry
03-06 20:26 DEBUG  TaskList: ## Running Remove target dir...
03-06 20:26 DEBUG  CommonBackend: Deleting C:\ubuntu
03-06 20:26 DEBUG  TaskList: ## Finished Remove target dir
03-06 20:26 DEBUG  TaskList: ## Running Remove registry key...
03-06 20:26 DEBUG  TaskList: ## Finished Remove registry key
03-06 20:26 DEBUG  TaskList: # Finished tasklist
03-06 20:26 INFO   root: Almost finished uninstalling
03-06 20:26 INFO   root: Finished uninstallation
03-06 20:26 DEBUG  CommonBackend: Fetching basic info...
03-06 20:26 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-06 20:26 DEBUG  CommonBackend: platform=win32
03-06 20:26 DEBUG  CommonBackend: osname=nt
03-06 20:26 DEBUG  WindowsBackend: arch=amd64
03-06 20:26 DEBUG  CommonBackend: Parsing isolist=C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\data\isolist.ini
03-06 20:26 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-06 20:26 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-06 20:26 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-06 20:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-06 20:26 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-06 20:26 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-06 20:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-06 20:26 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-06 20:26 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-06 20:26 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-06 20:26 DEBUG  WindowsBackend: Fetching host info...
03-06 20:26 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-06 20:26 DEBUG  WindowsBackend: windows version=vista
03-06 20:26 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-06 20:26 DEBUG  WindowsBackend: windows_sp=None
03-06 20:26 DEBUG  WindowsBackend: windows_build=7600
03-06 20:26 DEBUG  WindowsBackend: gmt=-8
03-06 20:26 DEBUG  WindowsBackend: country=US
03-06 20:26 DEBUG  WindowsBackend: timezone=America/Los_Angeles
03-06 20:26 DEBUG  WindowsBackend: windows_username=SPARTAN 114
03-06 20:26 DEBUG  WindowsBackend: user_full_name=SPARTAN 114
03-06 20:26 DEBUG  WindowsBackend: user_directory=C:\Users\SPARTAN 114
03-06 20:26 DEBUG  WindowsBackend: windows_language_code=1033
03-06 20:26 DEBUG  WindowsBackend: windows_language=English
03-06 20:26 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
03-06 20:26 DEBUG  WindowsBackend: bootloader=vista
03-06 20:26 DEBUG  WindowsBackend: system_drive=Drive(C: hd 75902.6640625 mb free ntfs)
03-06 20:26 DEBUG  WindowsBackend: drive=Drive(C: hd 75902.6640625 mb free ntfs)
03-06 20:26 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-06 20:26 DEBUG  WindowsBackend: uninstaller_path=None
03-06 20:26 DEBUG  WindowsBackend: previous_target_dir=None
03-06 20:26 DEBUG  WindowsBackend: previous_distro_name=None
03-06 20:26 DEBUG  WindowsBackend: keyboard_id=67699721
03-06 20:26 DEBUG  WindowsBackend: keyboard_layout=us
03-06 20:26 DEBUG  WindowsBackend: keyboard_variant=
03-06 20:26 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
03-06 20:26 DEBUG  CommonBackend: Searching ISOs on USB devices
03-06 20:26 DEBUG  CommonBackend: Searching for local CDs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp is a valid Ubuntu CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp is a valid Ubuntu CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp is a valid Ubuntu Netbook CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp is a valid Kubuntu CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp is a valid Kubuntu CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp is a valid Kubuntu Netbook CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp is a valid Xubuntu CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp is a valid Xubuntu CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp is a valid Mythbuntu CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp is a valid Mythbuntu CD
03-06 20:26 DEBUG  Distro:     does not contain C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\casper\filesystem.squashfs
03-06 20:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-06 20:26 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-06 20:26 INFO   root: Running the installer...
03-06 20:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\translations, languages=['en_US', 'en']
03-06 20:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\translations, languages=['en_US', 'en']
03-06 20:27 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=spartan114
03-06 20:27 INFO   root: Received settings
03-06 20:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\translations, languages=['en_US', 'en']
03-06 20:27 DEBUG  TaskList: # Running tasklist...
03-06 20:27 DEBUG  TaskList: ## Running select_target_dir...
03-06 20:27 INFO   WindowsBackend: Installing into C:\ubuntu
03-06 20:27 DEBUG  TaskList: ## Finished select_target_dir
03-06 20:27 DEBUG  TaskList: ## Running create_dir_structure...
03-06 20:27 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-06 20:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-06 20:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-06 20:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-06 20:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-06 20:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-06 20:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-06 20:27 DEBUG  TaskList: ## Finished create_dir_structure
03-06 20:27 DEBUG  TaskList: ## Running uncompress_target_dir...
03-06 20:27 DEBUG  TaskList: ## Finished uncompress_target_dir
03-06 20:27 DEBUG  TaskList: ## Running create_uninstaller...
03-06 20:27 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-06 20:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-06 20:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-06 20:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-06 20:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-06 20:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-06 20:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-06 20:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-06 20:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-06 20:27 DEBUG  TaskList: ## Finished create_uninstaller
03-06 20:27 DEBUG  TaskList: ## Running copy_installation_files...
03-06 20:27 DEBUG  WindowsBackend: Copying C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-06 20:27 DEBUG  WindowsBackend: Copying C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\winboot -> C:\ubuntu\winboot
03-06 20:27 DEBUG  WindowsBackend: Copying C:\Users\SPARTA~1\AppData\Local\Temp\pylFE20.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-06 20:27 DEBUG  TaskList: ## Finished copy_installation_files
03-06 20:27 DEBUG  TaskList: ## Running get_iso...
03-06 20:27 DEBUG  TaskList: New task copy_file
03-06 20:27 DEBUG  TaskList: ### Running copy_file...
03-06 20:30 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
03-06 20:30 DEBUG  TaskList: # Cancelling tasklist
03-06 20:30 DEBUG  TaskList: New task check_iso
03-06 20:30 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
03-06 20:30 DEBUG  CommonBackend: Searching for local ISO
03-06 20:30 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-06 20:30 DEBUG  TaskList: New task get_metalink
03-06 20:30 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
03-06 20:30 DEBUG  TaskList: # Cancelling tasklist
03-06 20:30 DEBUG  TaskList: # Finished tasklist
 

any idea what this means or how to fix it?

---

### Post by bcbc on 2011-03-07
Errno 13 is usually either a bad cd or possibly an incompatibility with the optical drive. Did you install from this CD the first time?

If you want to install wubi, place the wubi.exe and the desktop ISO in the same folder and run it from there. As described [here]("https://wiki.ubuntu.com/WubiGuide#How do I install Wubi on a machine with no Internet connection?").

You can also test the CD by booting from it, hitting the space bar when you see the keyboard icon bottom centre, and then select to check the CD from the extended menu. ([It's a good idea]("https://wiki.ubuntu.com/WubiGuide#Warning") to have an Ubuntu CD as a rescue disk).

---

### Post by Bucky Ball on 2011-03-07
You say you had it installed *alongside* Windows? That is a dual-boot and looks to me like you are attempting to boot the install cd (not wubi) on a running Windows system. This won't work.

You need to boot from the CD; in other words, get into the BIOS when you boot the computer up and change the boot device to your optical drive. Shove the Ubuntu LiveCD in (the desktop install CD) and carry on. ;)

---

