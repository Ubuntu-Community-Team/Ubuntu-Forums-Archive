---
title: "Necesito su ayuda con Wubi"
date: 2009-05-23
forum: Ecuador Team
---

### Post by icp77 on 2009-05-23
Me sale este error al querer instalarlo en vista para probarlo:

05-23 10:41 INFO   root: === wubi 9.04 rev128 ===
05-23 10:41 DEBUG  root: Logfile is c:\users\imcome~1\appdata\local\temp\wubi-9.04-rev128.log
05-23 10:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
05-23 10:41 DEBUG  CommonBackend: data_dir=C:\Users\IMCOME~1\AppData\Local\Temp\pylCF80.tmp\data
05-23 10:41 DEBUG  WindowsBackend: 7z=C:\Users\IMCOME~1\AppData\Local\Temp\pylCF80.tmp\bin\7z.exe
05-23 10:41 DEBUG  CommonBackend: Fetching basic info...
05-23 10:41 DEBUG  CommonBackend: original_exe=D:\wubi.exe
05-23 10:41 DEBUG  CommonBackend: platform=win32
05-23 10:41 DEBUG  CommonBackend: osname=nt
05-23 10:41 DEBUG  CommonBackend: language=es_EC
05-23 10:41 DEBUG  CommonBackend: encoding=cp1252
05-23 10:41 DEBUG  WindowsBackend: arch=i386
05-23 10:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\IMCOME~1\AppData\Local\Temp\pylCF80.tmp\data\isolist.ini
05-23 10:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 10:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 10:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 10:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 10:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 10:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 10:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 10:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 10:41 DEBUG  WindowsBackend: Fetching host info...
05-23 10:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 10:41 DEBUG  WindowsBackend: windows version=vista
05-23 10:41 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
05-23 10:41 DEBUG  WindowsBackend: windows_sp=Service Pack 1
05-23 10:41 DEBUG  WindowsBackend: windows_build=6001
05-23 10:41 DEBUG  WindowsBackend: gmt=-5
05-23 10:41 DEBUG  WindowsBackend: country=EC
05-23 10:41 DEBUG  WindowsBackend: timezone=America/Guayaquil
05-23 10:41 DEBUG  WindowsBackend: windows_username=IMCOMEPRO
05-23 10:41 DEBUG  WindowsBackend: user_full_name=IMCOMEPRO
05-23 10:41 DEBUG  WindowsBackend: user_directory=IMCOMEPRO
05-23 10:41 DEBUG  WindowsBackend: windows_language_code=1034
05-23 10:41 DEBUG  WindowsBackend: windows_language=Spanish
05-23 10:41 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) 4 CPU 3.60GHz
05-23 10:41 DEBUG  WindowsBackend: bootloader=vista
05-23 10:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 61004.7695313 mb free )
05-23 10:41 DEBUG  WindowsBackend: drive=Drive(C: hd 61004.7695313 mb free )
05-23 10:41 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-23 10:41 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
05-23 10:41 DEBUG  WindowsBackend: uninstaller_path=None
05-23 10:41 DEBUG  WindowsBackend: previous_target_dir=None
05-23 10:41 DEBUG  WindowsBackend: previous_distro_name=None
05-23 10:41 DEBUG  WindowsBackend: keyboard_id=67776522
05-23 10:41 DEBUG  WindowsBackend: keyboard_layout=ec
05-23 10:41 DEBUG  WindowsBackend: keyboard_variant=
05-23 10:41 DEBUG  CommonBackend: locale=es_EC.UTF-8
05-23 10:41 DEBUG  WindowsBackend: total_memory_mb=2046.07421875
05-23 10:41 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 10:41 DEBUG  CommonBackend: Searching for local CDs
05-23 10:41 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylCF80.tmp is a valid Ubuntu CD
05-23 10:41 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylCF80.tmp\casper\filesystem.squashfs
05-23 10:41 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylCF80.tmp is a valid Ubuntu CD
05-23 10:41 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylCF80.tmp\casper\filesystem.squashfs
05-23 10:41 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylCF80.tmp is a valid Kubuntu CD
05-23 10:41 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylCF80.tmp\casper\filesystem.squashfs
05-23 10:41 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylCF80.tmp is a valid Kubuntu CD
05-23 10:41 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylCF80.tmp\casper\filesystem.squashfs
05-23 10:41 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylCF80.tmp is a valid Xubuntu CD
05-23 10:41 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylCF80.tmp\casper\filesystem.squashfs
05-23 10:41 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylCF80.tmp is a valid Xubuntu CD
05-23 10:41 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylCF80.tmp\casper\filesystem.squashfs
05-23 10:41 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylCF80.tmp is a valid Mythbuntu CD
05-23 10:41 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylCF80.tmp\casper\filesystem.squashfs
05-23 10:41 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylCF80.tmp is a valid Mythbuntu CD
05-23 10:41 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylCF80.tmp\casper\filesystem.squashfs
05-23 10:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 10:41 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
05-23 10:41 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
05-23 10:41 DEBUG  Distro: wrong arch: i386 != amd64
05-23 10:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 10:41 INFO   Distro: Found a valid CD for Ubuntu: D:\
05-23 10:41 INFO   root: Running the CD menu...
05-23 10:41 DEBUG  WindowsFrontend: __init__...
05-23 10:41 DEBUG  WindowsFrontend: on_init...
05-23 10:41 INFO   root: CD menu finished
05-23 10:41 INFO   root: Running the CD menu...
05-23 10:42 INFO   root: CD menu finished
05-23 10:42 INFO   root: Running the CD menu...
05-23 10:42 DEBUG  WindowsFrontend: frontend.on_quit
05-23 10:42 DEBUG  root: application.on_quit
05-23 10:42 INFO   root: sys.exit
05-23 10:44 INFO   root: === wubi 9.04 rev128 ===
05-23 10:44 DEBUG  root: Logfile is c:\users\imcome~1\appdata\local\temp\wubi-9.04-rev128.log
05-23 10:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
05-23 10:44 DEBUG  CommonBackend: data_dir=C:\Users\IMCOME~1\AppData\Local\Temp\pyl8BFF.tmp\data
05-23 10:44 DEBUG  WindowsBackend: 7z=C:\Users\IMCOME~1\AppData\Local\Temp\pyl8BFF.tmp\bin\7z.exe
05-23 10:44 DEBUG  CommonBackend: Fetching basic info...
05-23 10:44 DEBUG  CommonBackend: original_exe=D:\wubi.exe
05-23 10:44 DEBUG  CommonBackend: platform=win32
05-23 10:44 DEBUG  CommonBackend: osname=nt
05-23 10:44 DEBUG  CommonBackend: language=es_EC
05-23 10:44 DEBUG  CommonBackend: encoding=cp1252
05-23 10:44 DEBUG  WindowsBackend: arch=i386
05-23 10:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\IMCOME~1\AppData\Local\Temp\pyl8BFF.tmp\data\isolist.ini
05-23 10:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 10:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 10:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 10:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 10:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 10:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 10:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 10:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 10:44 DEBUG  WindowsBackend: Fetching host info...
05-23 10:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 10:44 DEBUG  WindowsBackend: windows version=vista
05-23 10:44 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
05-23 10:44 DEBUG  WindowsBackend: windows_sp=Service Pack 1
05-23 10:44 DEBUG  WindowsBackend: windows_build=6001
05-23 10:44 DEBUG  WindowsBackend: gmt=-5
05-23 10:44 DEBUG  WindowsBackend: country=EC
05-23 10:44 DEBUG  WindowsBackend: timezone=America/Guayaquil
05-23 10:44 DEBUG  WindowsBackend: windows_username=IMCOMEPRO
05-23 10:44 DEBUG  WindowsBackend: user_full_name=IMCOMEPRO
05-23 10:44 DEBUG  WindowsBackend: user_directory=IMCOMEPRO
05-23 10:44 DEBUG  WindowsBackend: windows_language_code=1034
05-23 10:44 DEBUG  WindowsBackend: windows_language=Spanish
05-23 10:44 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) 4 CPU 3.60GHz
05-23 10:44 DEBUG  WindowsBackend: bootloader=vista
05-23 10:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 61010.2460938 mb free )
05-23 10:44 DEBUG  WindowsBackend: drive=Drive(C: hd 61010.2460938 mb free )
05-23 10:44 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-23 10:44 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
05-23 10:44 DEBUG  WindowsBackend: uninstaller_path=None
05-23 10:44 DEBUG  WindowsBackend: previous_target_dir=None
05-23 10:44 DEBUG  WindowsBackend: previous_distro_name=None
05-23 10:44 DEBUG  WindowsBackend: keyboard_id=67776522
05-23 10:44 DEBUG  WindowsBackend: keyboard_layout=ec
05-23 10:44 DEBUG  WindowsBackend: keyboard_variant=
05-23 10:44 DEBUG  CommonBackend: locale=es_EC.UTF-8
05-23 10:44 DEBUG  WindowsBackend: total_memory_mb=2046.07421875
05-23 10:44 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 10:44 DEBUG  CommonBackend: Searching for local CDs
05-23 10:44 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl8BFF.tmp is a valid Ubuntu CD
05-23 10:44 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl8BFF.tmp\casper\filesystem.squashfs
05-23 10:44 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl8BFF.tmp is a valid Ubuntu CD
05-23 10:44 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl8BFF.tmp\casper\filesystem.squashfs
05-23 10:44 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl8BFF.tmp is a valid Kubuntu CD
05-23 10:44 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl8BFF.tmp\casper\filesystem.squashfs
05-23 10:44 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl8BFF.tmp is a valid Kubuntu CD
05-23 10:44 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl8BFF.tmp\casper\filesystem.squashfs
05-23 10:44 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl8BFF.tmp is a valid Xubuntu CD
05-23 10:44 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl8BFF.tmp\casper\filesystem.squashfs
05-23 10:44 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl8BFF.tmp is a valid Xubuntu CD
05-23 10:44 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl8BFF.tmp\casper\filesystem.squashfs
05-23 10:44 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl8BFF.tmp is a valid Mythbuntu CD
05-23 10:44 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl8BFF.tmp\casper\filesystem.squashfs
05-23 10:44 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl8BFF.tmp is a valid Mythbuntu CD
05-23 10:44 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl8BFF.tmp\casper\filesystem.squashfs
05-23 10:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 10:44 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
05-23 10:44 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
05-23 10:44 DEBUG  Distro: wrong arch: i386 != amd64
05-23 10:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 10:44 INFO   Distro: Found a valid CD for Ubuntu: D:\
05-23 10:44 INFO   root: Running the CD menu...
05-23 10:44 DEBUG  WindowsFrontend: __init__...
05-23 10:44 DEBUG  WindowsFrontend: on_init...
05-23 10:44 INFO   root: CD menu finished
05-23 10:44 INFO   root: Running the installer...
05-23 10:44 INFO   WindowsFrontend: Operation cancelled
05-23 10:44 DEBUG  WindowsFrontend: frontend.quit
05-23 10:44 DEBUG  WindowsFrontend: frontend.on_quit
05-23 10:44 DEBUG  root: application.on_quit
05-23 10:44 INFO   root: sys.exit
05-23 14:45 INFO   root: === wubi 9.04 rev128 ===
05-23 14:45 DEBUG  root: Logfile is c:\users\imcome~1\appdata\local\temp\wubi-9.04-rev128.log
05-23 14:45 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
05-23 14:45 DEBUG  CommonBackend: data_dir=C:\Users\IMCOME~1\AppData\Local\Temp\pyl39F2.tmp\data
05-23 14:45 DEBUG  WindowsBackend: 7z=C:\Users\IMCOME~1\AppData\Local\Temp\pyl39F2.tmp\bin\7z.exe
05-23 14:45 DEBUG  CommonBackend: Fetching basic info...
05-23 14:45 DEBUG  CommonBackend: original_exe=D:\wubi.exe
05-23 14:45 DEBUG  CommonBackend: platform=win32
05-23 14:45 DEBUG  CommonBackend: osname=nt
05-23 14:45 DEBUG  CommonBackend: language=es_EC
05-23 14:45 DEBUG  CommonBackend: encoding=cp1252
05-23 14:45 DEBUG  WindowsBackend: arch=i386
05-23 14:45 DEBUG  CommonBackend: Parsing isolist=C:\Users\IMCOME~1\AppData\Local\Temp\pyl39F2.tmp\data\isolist.ini
05-23 14:45 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 14:45 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 14:45 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 14:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 14:45 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 14:45 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 14:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 14:45 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 14:45 DEBUG  WindowsBackend: Fetching host info...
05-23 14:45 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 14:45 DEBUG  WindowsBackend: windows version=vista
05-23 14:45 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
05-23 14:45 DEBUG  WindowsBackend: windows_sp=Service Pack 1
05-23 14:45 DEBUG  WindowsBackend: windows_build=6001
05-23 14:45 DEBUG  WindowsBackend: gmt=-5
05-23 14:45 DEBUG  WindowsBackend: country=EC
05-23 14:45 DEBUG  WindowsBackend: timezone=America/Guayaquil
05-23 14:45 DEBUG  WindowsBackend: windows_username=IMCOMEPRO
05-23 14:45 DEBUG  WindowsBackend: user_full_name=IMCOMEPRO
05-23 14:45 DEBUG  WindowsBackend: user_directory=IMCOMEPRO
05-23 14:45 DEBUG  WindowsBackend: windows_language_code=1034
05-23 14:45 DEBUG  WindowsBackend: windows_language=Spanish
05-23 14:45 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) 4 CPU 3.60GHz
05-23 14:45 DEBUG  WindowsBackend: bootloader=vista
05-23 14:45 DEBUG  WindowsBackend: system_drive=Drive(C: hd 61022.6328125 mb free )
05-23 14:45 DEBUG  WindowsBackend: drive=Drive(C: hd 61022.6328125 mb free )
05-23 14:45 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-23 14:45 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
05-23 14:45 DEBUG  WindowsBackend: uninstaller_path=None
05-23 14:45 DEBUG  WindowsBackend: previous_target_dir=None
05-23 14:45 DEBUG  WindowsBackend: previous_distro_name=None
05-23 14:45 DEBUG  WindowsBackend: keyboard_id=67776522
05-23 14:45 DEBUG  WindowsBackend: keyboard_layout=ec
05-23 14:45 DEBUG  WindowsBackend: keyboard_variant=
05-23 14:45 DEBUG  CommonBackend: locale=es_EC.UTF-8
05-23 14:45 DEBUG  WindowsBackend: total_memory_mb=2046.07421875
05-23 14:45 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 14:45 DEBUG  CommonBackend: Searching for local CDs
05-23 14:45 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl39F2.tmp is a valid Ubuntu CD
05-23 14:45 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl39F2.tmp\casper\filesystem.squashfs
05-23 14:45 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl39F2.tmp is a valid Ubuntu CD
05-23 14:45 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl39F2.tmp\casper\filesystem.squashfs
05-23 14:45 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl39F2.tmp is a valid Kubuntu CD
05-23 14:45 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl39F2.tmp\casper\filesystem.squashfs
05-23 14:45 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl39F2.tmp is a valid Kubuntu CD
05-23 14:45 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl39F2.tmp\casper\filesystem.squashfs
05-23 14:45 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl39F2.tmp is a valid Xubuntu CD
05-23 14:45 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl39F2.tmp\casper\filesystem.squashfs
05-23 14:45 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl39F2.tmp is a valid Xubuntu CD
05-23 14:45 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl39F2.tmp\casper\filesystem.squashfs
05-23 14:45 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl39F2.tmp is a valid Mythbuntu CD
05-23 14:45 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl39F2.tmp\casper\filesystem.squashfs
05-23 14:45 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl39F2.tmp is a valid Mythbuntu CD
05-23 14:45 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl39F2.tmp\casper\filesystem.squashfs
05-23 14:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 14:45 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
05-23 14:45 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
05-23 14:45 DEBUG  Distro: wrong arch: i386 != amd64
05-23 14:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 14:45 INFO   Distro: Found a valid CD for Ubuntu: D:\
05-23 14:45 INFO   root: Running the CD menu...
05-23 14:45 DEBUG  WindowsFrontend: __init__...
05-23 14:45 DEBUG  WindowsFrontend: on_init...
05-23 14:46 INFO   root: CD menu finished
05-23 14:46 INFO   root: Running the installer...
05-23 14:46 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=Spanish, username=imcomepro
05-23 14:46 INFO   root: Received settings
05-23 14:46 DEBUG  TaskList: # Running tasklist...
05-23 14:46 DEBUG  TaskList: ## Running select_target_dir...
05-23 14:46 INFO   WindowsBackend: Installing into C:\ubuntu
05-23 14:46 DEBUG  TaskList: ## Finished select_target_dir
05-23 14:46 DEBUG  TaskList: ## Running create_dir_structure...
05-23 14:46 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-23 14:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-23 14:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-23 14:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-23 14:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-23 14:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-23 14:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-23 14:46 DEBUG  TaskList: ## Finished create_dir_structure
05-23 14:46 DEBUG  TaskList: ## Running uncompress_target_dir...
05-23 14:46 DEBUG  TaskList: ## Finished uncompress_target_dir
05-23 14:46 DEBUG  TaskList: ## Running create_uninstaller...
05-23 14:46 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-23 14:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-23 14:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-23 14:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-23 14:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-23 14:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
05-23 14:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-23 14:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-23 14:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-23 14:46 DEBUG  TaskList: ## Finished create_uninstaller
05-23 14:46 DEBUG  TaskList: ## Running copy_installation_files...
05-23 14:46 DEBUG  WindowsBackend: Copying C:\Users\IMCOME~1\AppData\Local\Temp\pyl39F2.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-23 14:46 DEBUG  WindowsBackend: Copying C:\Users\IMCOME~1\AppData\Local\Temp\pyl39F2.tmp\winboot -> C:\ubuntu\winboot
05-23 14:46 DEBUG  WindowsBackend: Copying C:\Users\IMCOME~1\AppData\Local\Temp\pyl39F2.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-23 14:46 DEBUG  TaskList: ## Finished copy_installation_files
05-23 14:46 DEBUG  TaskList: ## Running get_iso...
05-23 14:46 DEBUG  TaskList: New task copy_file
05-23 14:46 DEBUG  TaskList: ### Running copy_file...
05-23 14:49 DEBUG  TaskList: ### Finished copy_file
05-23 14:49 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
05-23 14:49 DEBUG  TaskList: # Cancelling tasklist
05-23 14:49 DEBUG  TaskList: New task check_iso
05-23 14:49 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
05-23 14:49 DEBUG  CommonBackend: Searching for local ISO
05-23 14:49 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-23 14:49 DEBUG  TaskList: New task get_metalink
05-23 14:49 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-23 14:49 DEBUG  TaskList: # Cancelling tasklist
05-23 14:49 DEBUG  TaskList: # Finished tasklist
05-23 14:54 INFO   root: === wubi 9.04 rev128 ===
05-23 14:54 DEBUG  root: Logfile is c:\users\imcome~1\appdata\local\temp\wubi-9.04-rev128.log
05-23 14:54 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
05-23 14:54 DEBUG  CommonBackend: data_dir=C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp\data
05-23 14:54 DEBUG  WindowsBackend: 7z=C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp\bin\7z.exe
05-23 14:54 DEBUG  CommonBackend: Fetching basic info...
05-23 14:54 DEBUG  CommonBackend: original_exe=D:\wubi.exe
05-23 14:54 DEBUG  CommonBackend: platform=win32
05-23 14:54 DEBUG  CommonBackend: osname=nt
05-23 14:54 DEBUG  CommonBackend: language=es_EC
05-23 14:54 DEBUG  CommonBackend: encoding=cp1252
05-23 14:54 DEBUG  WindowsBackend: arch=i386
05-23 14:54 DEBUG  CommonBackend: Parsing isolist=C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp\data\isolist.ini
05-23 14:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 14:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 14:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 14:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 14:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 14:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 14:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 14:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 14:54 DEBUG  WindowsBackend: Fetching host info...
05-23 14:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 14:54 DEBUG  WindowsBackend: windows version=vista
05-23 14:54 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
05-23 14:54 DEBUG  WindowsBackend: windows_sp=Service Pack 1
05-23 14:54 DEBUG  WindowsBackend: windows_build=6001
05-23 14:54 DEBUG  WindowsBackend: gmt=-5
05-23 14:54 DEBUG  WindowsBackend: country=EC
05-23 14:54 DEBUG  WindowsBackend: timezone=America/Guayaquil
05-23 14:54 DEBUG  WindowsBackend: windows_username=IMCOMEPRO
05-23 14:54 DEBUG  WindowsBackend: user_full_name=IMCOMEPRO
05-23 14:54 DEBUG  WindowsBackend: user_directory=IMCOMEPRO
05-23 14:54 DEBUG  WindowsBackend: windows_language_code=1034
05-23 14:54 DEBUG  WindowsBackend: windows_language=Spanish
05-23 14:54 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) 4 CPU 3.60GHz
05-23 14:54 DEBUG  WindowsBackend: bootloader=vista
05-23 14:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 60322.0234375 mb free )
05-23 14:54 DEBUG  WindowsBackend: drive=Drive(C: hd 60322.0234375 mb free )
05-23 14:54 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-23 14:54 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
05-23 14:54 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-23 14:54 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-23 14:54 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-23 14:54 DEBUG  WindowsBackend: keyboard_id=67776522
05-23 14:54 DEBUG  WindowsBackend: keyboard_layout=ec
05-23 14:54 DEBUG  WindowsBackend: keyboard_variant=
05-23 14:54 DEBUG  CommonBackend: locale=es_EC.UTF-8
05-23 14:54 DEBUG  WindowsBackend: total_memory_mb=2046.07421875
05-23 14:54 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 14:54 DEBUG  CommonBackend: Searching for local CDs
05-23 14:54 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp is a valid Ubuntu CD
05-23 14:54 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp\casper\filesystem.squashfs
05-23 14:54 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp is a valid Ubuntu CD
05-23 14:54 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp\casper\filesystem.squashfs
05-23 14:54 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp is a valid Kubuntu CD
05-23 14:54 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp\casper\filesystem.squashfs
05-23 14:54 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp is a valid Kubuntu CD
05-23 14:54 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp\casper\filesystem.squashfs
05-23 14:54 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp is a valid Xubuntu CD
05-23 14:54 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp\casper\filesystem.squashfs
05-23 14:54 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp is a valid Xubuntu CD
05-23 14:54 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp\casper\filesystem.squashfs
05-23 14:54 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp is a valid Mythbuntu CD
05-23 14:54 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp\casper\filesystem.squashfs
05-23 14:54 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp is a valid Mythbuntu CD
05-23 14:54 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp\casper\filesystem.squashfs
05-23 14:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 14:54 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
05-23 14:54 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
05-23 14:54 DEBUG  Distro: wrong arch: i386 != amd64
05-23 14:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 14:54 INFO   Distro: Found a valid CD for Ubuntu: D:\
05-23 14:54 INFO   root: Running the CD menu...
05-23 14:54 DEBUG  WindowsFrontend: __init__...
05-23 14:54 DEBUG  WindowsFrontend: on_init...
05-23 14:54 INFO   root: CD menu finished
05-23 14:54 INFO   root: Already installed, running the uninstaller...
05-23 14:54 INFO   root: Running the uninstaller...
05-23 14:54 INFO   CommonBackend: This is the uninstaller running
05-23 14:54 INFO   root: Received settings
05-23 14:54 DEBUG  TaskList: # Running tasklist...
05-23 14:54 DEBUG  TaskList: ## Running Backup ISO...
05-23 14:54 DEBUG  TaskList: ## Finished Backup ISO
05-23 14:54 DEBUG  TaskList: ## Running Remove bootloader entry...
05-23 14:54 DEBUG  WindowsBackend: Could not find bcd id
05-23 14:54 DEBUG  WindowsBackend: undo_bootini C:
05-23 14:54 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 60322.0234375 mb free )
05-23 14:54 DEBUG  WindowsBackend: undo_bootini F:
05-23 14:54 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
05-23 14:54 DEBUG  TaskList: ## Finished Remove bootloader entry
05-23 14:54 DEBUG  TaskList: ## Running Remove target dir...
05-23 14:54 DEBUG  CommonBackend: Deleting C:\ubuntu
05-23 14:54 DEBUG  TaskList: ## Finished Remove target dir
05-23 14:54 DEBUG  TaskList: ## Running Remove registry key...
05-23 14:54 DEBUG  TaskList: ## Finished Remove registry key
05-23 14:54 DEBUG  TaskList: # Finished tasklist
05-23 14:54 INFO   root: Almost finished uninstalling
05-23 14:54 INFO   root: Finished uninstallation
05-23 14:54 DEBUG  CommonBackend: Fetching basic info...
05-23 14:54 DEBUG  CommonBackend: original_exe=D:\wubi.exe
05-23 14:54 DEBUG  CommonBackend: platform=win32
05-23 14:54 DEBUG  CommonBackend: osname=nt
05-23 14:54 DEBUG  CommonBackend: language=es_EC
05-23 14:54 DEBUG  CommonBackend: encoding=cp1252
05-23 14:54 DEBUG  WindowsBackend: arch=i386
05-23 14:54 DEBUG  CommonBackend: Parsing isolist=C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp\data\isolist.ini
05-23 14:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 14:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 14:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 14:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 14:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 14:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 14:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 14:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 14:54 DEBUG  WindowsBackend: Fetching host info...
05-23 14:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 14:54 DEBUG  WindowsBackend: windows version=vista
05-23 14:54 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
05-23 14:54 DEBUG  WindowsBackend: windows_sp=Service Pack 1
05-23 14:54 DEBUG  WindowsBackend: windows_build=6001
05-23 14:54 DEBUG  WindowsBackend: gmt=-5
05-23 14:54 DEBUG  WindowsBackend: country=EC
05-23 14:54 DEBUG  WindowsBackend: timezone=America/Guayaquil
05-23 14:54 DEBUG  WindowsBackend: windows_username=IMCOMEPRO
05-23 14:54 DEBUG  WindowsBackend: user_full_name=IMCOMEPRO
05-23 14:54 DEBUG  WindowsBackend: user_directory=IMCOMEPRO
05-23 14:54 DEBUG  WindowsBackend: windows_language_code=1034
05-23 14:54 DEBUG  WindowsBackend: windows_language=Spanish
05-23 14:54 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) 4 CPU 3.60GHz
05-23 14:54 DEBUG  WindowsBackend: bootloader=vista
05-23 14:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 61021.8476563 mb free )
05-23 14:54 DEBUG  WindowsBackend: drive=Drive(C: hd 61021.8476563 mb free )
05-23 14:54 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-23 14:54 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
05-23 14:54 DEBUG  WindowsBackend: uninstaller_path=None
05-23 14:54 DEBUG  WindowsBackend: previous_target_dir=None
05-23 14:54 DEBUG  WindowsBackend: previous_distro_name=None
05-23 14:54 DEBUG  WindowsBackend: keyboard_id=67776522
05-23 14:54 DEBUG  WindowsBackend: keyboard_layout=ec
05-23 14:54 DEBUG  WindowsBackend: keyboard_variant=
05-23 14:54 DEBUG  CommonBackend: locale=es_EC.UTF-8
05-23 14:54 DEBUG  WindowsBackend: total_memory_mb=2046.07421875
05-23 14:54 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 14:54 DEBUG  CommonBackend: Searching for local CDs
05-23 14:54 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp is a valid Ubuntu CD
05-23 14:54 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp\casper\filesystem.squashfs
05-23 14:54 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp is a valid Ubuntu CD
05-23 14:54 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp\casper\filesystem.squashfs
05-23 14:54 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp is a valid Kubuntu CD
05-23 14:54 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp\casper\filesystem.squashfs
05-23 14:54 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp is a valid Kubuntu CD
05-23 14:54 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp\casper\filesystem.squashfs
05-23 14:54 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp is a valid Xubuntu CD
05-23 14:54 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp\casper\filesystem.squashfs
05-23 14:54 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp is a valid Xubuntu CD
05-23 14:54 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp\casper\filesystem.squashfs
05-23 14:54 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp is a valid Mythbuntu CD
05-23 14:54 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp\casper\filesystem.squashfs
05-23 14:54 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp is a valid Mythbuntu CD
05-23 14:54 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp\casper\filesystem.squashfs
05-23 14:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 14:54 DEBUG  Distro: wrong arch: i386 != amd64
05-23 14:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 14:54 INFO   Distro: Found a valid CD for Ubuntu: D:\
05-23 14:54 INFO   root: Running the installer...
05-23 14:54 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=Spanish, username=imcomepro
05-23 14:54 INFO   root: Received settings
05-23 14:54 DEBUG  TaskList: # Running tasklist...
05-23 14:54 DEBUG  TaskList: ## Running select_target_dir...
05-23 14:54 INFO   WindowsBackend: Installing into C:\ubuntu
05-23 14:54 DEBUG  TaskList: ## Finished select_target_dir
05-23 14:54 DEBUG  TaskList: ## Running create_dir_structure...
05-23 14:54 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-23 14:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-23 14:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-23 14:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-23 14:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-23 14:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-23 14:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-23 14:54 DEBUG  TaskList: ## Finished create_dir_structure
05-23 14:54 DEBUG  TaskList: ## Running uncompress_target_dir...
05-23 14:54 DEBUG  TaskList: ## Finished uncompress_target_dir
05-23 14:54 DEBUG  TaskList: ## Running create_uninstaller...
05-23 14:54 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-23 14:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-23 14:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-23 14:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-23 14:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-23 14:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
05-23 14:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-23 14:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-23 14:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-23 14:54 DEBUG  TaskList: ## Finished create_uninstaller
05-23 14:54 DEBUG  TaskList: ## Running copy_installation_files...
05-23 14:54 DEBUG  WindowsBackend: Copying C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-23 14:54 DEBUG  WindowsBackend: Copying C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp\winboot -> C:\ubuntu\winboot
05-23 14:54 DEBUG  WindowsBackend: Copying C:\Users\IMCOME~1\AppData\Local\Temp\pylCD27.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-23 14:54 DEBUG  TaskList: ## Finished copy_installation_files
05-23 14:54 DEBUG  TaskList: ## Running get_iso...
05-23 14:54 DEBUG  TaskList: New task copy_file
05-23 14:54 DEBUG  TaskList: ### Running copy_file...
05-23 14:54 INFO   WindowsFrontend: Operation cancelled
05-23 14:54 DEBUG  WindowsFrontend: frontend.quit
05-23 14:54 DEBUG  WindowsFrontend: frontend.on_quit
05-23 14:54 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
05-23 14:54 DEBUG  TaskList: # Cancelling tasklist
05-23 14:54 DEBUG  TaskList: ### Finished copy_file
05-23 14:54 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
05-23 14:54 DEBUG  root: application.on_quit
05-23 14:54 DEBUG  root: Forceful exit
05-23 14:54 INFO   root: sys.exit
05-23 14:55 INFO   root: === wubi 9.04 rev128 ===
05-23 14:55 DEBUG  root: Logfile is c:\users\imcome~1\appdata\local\temp\wubi-9.04-rev128.log
05-23 14:55 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
05-23 14:55 DEBUG  CommonBackend: data_dir=C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp\data
05-23 14:55 DEBUG  WindowsBackend: 7z=C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp\bin\7z.exe
05-23 14:55 DEBUG  CommonBackend: Fetching basic info...
05-23 14:55 DEBUG  CommonBackend: original_exe=D:\wubi.exe
05-23 14:55 DEBUG  CommonBackend: platform=win32
05-23 14:55 DEBUG  CommonBackend: osname=nt
05-23 14:55 DEBUG  CommonBackend: language=es_EC
05-23 14:55 DEBUG  CommonBackend: encoding=cp1252
05-23 14:55 DEBUG  WindowsBackend: arch=i386
05-23 14:55 DEBUG  CommonBackend: Parsing isolist=C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp\data\isolist.ini
05-23 14:55 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 14:55 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 14:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 14:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 14:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 14:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 14:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 14:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 14:55 DEBUG  WindowsBackend: Fetching host info...
05-23 14:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 14:55 DEBUG  WindowsBackend: windows version=vista
05-23 14:55 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
05-23 14:55 DEBUG  WindowsBackend: windows_sp=Service Pack 1
05-23 14:55 DEBUG  WindowsBackend: windows_build=6001
05-23 14:55 DEBUG  WindowsBackend: gmt=-5
05-23 14:55 DEBUG  WindowsBackend: country=EC
05-23 14:55 DEBUG  WindowsBackend: timezone=America/Guayaquil
05-23 14:55 DEBUG  WindowsBackend: windows_username=IMCOMEPRO
05-23 14:55 DEBUG  WindowsBackend: user_full_name=IMCOMEPRO
05-23 14:55 DEBUG  WindowsBackend: user_directory=IMCOMEPRO
05-23 14:55 DEBUG  WindowsBackend: windows_language_code=1034
05-23 14:55 DEBUG  WindowsBackend: windows_language=Spanish
05-23 14:55 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) 4 CPU 3.60GHz
05-23 14:55 DEBUG  WindowsBackend: bootloader=vista
05-23 14:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 60990.3359375 mb free )
05-23 14:55 DEBUG  WindowsBackend: drive=Drive(C: hd 60990.3359375 mb free )
05-23 14:55 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-23 14:55 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
05-23 14:55 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-23 14:55 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-23 14:55 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-23 14:55 DEBUG  WindowsBackend: keyboard_id=67776522
05-23 14:55 DEBUG  WindowsBackend: keyboard_layout=ec
05-23 14:55 DEBUG  WindowsBackend: keyboard_variant=
05-23 14:55 DEBUG  CommonBackend: locale=es_EC.UTF-8
05-23 14:55 DEBUG  WindowsBackend: total_memory_mb=2046.07421875
05-23 14:55 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 14:55 DEBUG  CommonBackend: Searching for local CDs
05-23 14:55 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp is a valid Ubuntu CD
05-23 14:55 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp\casper\filesystem.squashfs
05-23 14:55 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp is a valid Ubuntu CD
05-23 14:55 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp\casper\filesystem.squashfs
05-23 14:55 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp is a valid Kubuntu CD
05-23 14:55 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp\casper\filesystem.squashfs
05-23 14:55 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp is a valid Kubuntu CD
05-23 14:55 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp\casper\filesystem.squashfs
05-23 14:55 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp is a valid Xubuntu CD
05-23 14:55 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp\casper\filesystem.squashfs
05-23 14:55 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp is a valid Xubuntu CD
05-23 14:55 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp\casper\filesystem.squashfs
05-23 14:55 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp is a valid Mythbuntu CD
05-23 14:55 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp\casper\filesystem.squashfs
05-23 14:55 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp is a valid Mythbuntu CD
05-23 14:55 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp\casper\filesystem.squashfs
05-23 14:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 14:55 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
05-23 14:55 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
05-23 14:55 DEBUG  Distro: wrong arch: i386 != amd64
05-23 14:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 14:55 INFO   Distro: Found a valid CD for Ubuntu: D:\
05-23 14:55 INFO   root: Running the CD menu...
05-23 14:55 DEBUG  WindowsFrontend: __init__...
05-23 14:55 DEBUG  WindowsFrontend: on_init...
05-23 14:55 INFO   root: CD menu finished
05-23 14:55 INFO   root: Already installed, running the uninstaller...
05-23 14:55 INFO   root: Running the uninstaller...
05-23 14:55 INFO   CommonBackend: This is the uninstaller running
05-23 14:55 INFO   root: Received settings
05-23 14:55 DEBUG  TaskList: # Running tasklist...
05-23 14:55 DEBUG  TaskList: ## Running Backup ISO...
05-23 14:55 DEBUG  TaskList: ## Finished Backup ISO
05-23 14:55 DEBUG  TaskList: ## Running Remove bootloader entry...
05-23 14:55 DEBUG  WindowsBackend: Could not find bcd id
05-23 14:55 DEBUG  WindowsBackend: undo_bootini C:
05-23 14:55 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 60990.3359375 mb free )
05-23 14:55 DEBUG  WindowsBackend: undo_bootini F:
05-23 14:55 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
05-23 14:55 DEBUG  TaskList: ## Finished Remove bootloader entry
05-23 14:55 DEBUG  TaskList: ## Running Remove target dir...
05-23 14:55 DEBUG  CommonBackend: Deleting C:\ubuntu
05-23 14:55 DEBUG  TaskList: ## Finished Remove target dir
05-23 14:55 DEBUG  TaskList: ## Running Remove registry key...
05-23 14:55 DEBUG  TaskList: ## Finished Remove registry key
05-23 14:55 DEBUG  TaskList: # Finished tasklist
05-23 14:55 INFO   root: Almost finished uninstalling
05-23 14:55 INFO   root: Finished uninstallation
05-23 14:55 DEBUG  CommonBackend: Fetching basic info...
05-23 14:55 DEBUG  CommonBackend: original_exe=D:\wubi.exe
05-23 14:55 DEBUG  CommonBackend: platform=win32
05-23 14:55 DEBUG  CommonBackend: osname=nt
05-23 14:55 DEBUG  CommonBackend: language=es_EC
05-23 14:55 DEBUG  CommonBackend: encoding=cp1252
05-23 14:55 DEBUG  WindowsBackend: arch=i386
05-23 14:55 DEBUG  CommonBackend: Parsing isolist=C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp\data\isolist.ini
05-23 14:55 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 14:55 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 14:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 14:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 14:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 14:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 14:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 14:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 14:55 DEBUG  WindowsBackend: Fetching host info...
05-23 14:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 14:55 DEBUG  WindowsBackend: windows version=vista
05-23 14:55 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
05-23 14:55 DEBUG  WindowsBackend: windows_sp=Service Pack 1
05-23 14:55 DEBUG  WindowsBackend: windows_build=6001
05-23 14:55 DEBUG  WindowsBackend: gmt=-5
05-23 14:55 DEBUG  WindowsBackend: country=EC
05-23 14:55 DEBUG  WindowsBackend: timezone=America/Guayaquil
05-23 14:55 DEBUG  WindowsBackend: windows_username=IMCOMEPRO
05-23 14:55 DEBUG  WindowsBackend: user_full_name=IMCOMEPRO
05-23 14:55 DEBUG  WindowsBackend: user_directory=IMCOMEPRO
05-23 14:55 DEBUG  WindowsBackend: windows_language_code=1034
05-23 14:55 DEBUG  WindowsBackend: windows_language=Spanish
05-23 14:55 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) 4 CPU 3.60GHz
05-23 14:55 DEBUG  WindowsBackend: bootloader=vista
05-23 14:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 61021.1484375 mb free )
05-23 14:55 DEBUG  WindowsBackend: drive=Drive(C: hd 61021.1484375 mb free )
05-23 14:55 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-23 14:55 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
05-23 14:55 DEBUG  WindowsBackend: uninstaller_path=None
05-23 14:55 DEBUG  WindowsBackend: previous_target_dir=None
05-23 14:55 DEBUG  WindowsBackend: previous_distro_name=None
05-23 14:55 DEBUG  WindowsBackend: keyboard_id=67776522
05-23 14:55 DEBUG  WindowsBackend: keyboard_layout=ec
05-23 14:55 DEBUG  WindowsBackend: keyboard_variant=
05-23 14:55 DEBUG  CommonBackend: locale=es_EC.UTF-8
05-23 14:55 DEBUG  WindowsBackend: total_memory_mb=2046.07421875
05-23 14:55 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 14:55 DEBUG  CommonBackend: Searching for local CDs
05-23 14:55 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp is a valid Ubuntu CD
05-23 14:55 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp\casper\filesystem.squashfs
05-23 14:55 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp is a valid Ubuntu CD
05-23 14:55 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp\casper\filesystem.squashfs
05-23 14:55 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp is a valid Kubuntu CD
05-23 14:55 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp\casper\filesystem.squashfs
05-23 14:55 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp is a valid Kubuntu CD
05-23 14:55 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp\casper\filesystem.squashfs
05-23 14:55 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp is a valid Xubuntu CD
05-23 14:55 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp\casper\filesystem.squashfs
05-23 14:55 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp is a valid Xubuntu CD
05-23 14:55 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp\casper\filesystem.squashfs
05-23 14:55 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp is a valid Mythbuntu CD
05-23 14:55 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp\casper\filesystem.squashfs
05-23 14:55 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp is a valid Mythbuntu CD
05-23 14:55 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl9941.tmp\casper\filesystem.squashfs
05-23 14:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 14:55 DEBUG  Distro: wrong arch: i386 != amd64
05-23 14:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 14:55 INFO   Distro: Found a valid CD for Ubuntu: D:\
05-23 14:55 INFO   root: Running the installer...
05-23 14:55 INFO   WindowsFrontend: Operation cancelled
05-23 14:55 DEBUG  WindowsFrontend: frontend.quit
05-23 14:55 DEBUG  WindowsFrontend: frontend.on_quit
05-23 14:55 DEBUG  root: application.on_quit
05-23 14:55 INFO   root: sys.exit
05-23 14:55 INFO   root: === wubi 9.04 rev128 ===
05-23 14:55 DEBUG  root: Logfile is c:\users\imcome~1\appdata\local\temp\wubi-9.04-rev128.log
05-23 14:55 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
05-23 14:55 DEBUG  CommonBackend: data_dir=C:\Users\IMCOME~1\AppData\Local\Temp\pylD3F9.tmp\data
05-23 14:55 DEBUG  WindowsBackend: 7z=C:\Users\IMCOME~1\AppData\Local\Temp\pylD3F9.tmp\bin\7z.exe
05-23 14:55 DEBUG  CommonBackend: Fetching basic info...
05-23 14:55 DEBUG  CommonBackend: original_exe=D:\wubi.exe
05-23 14:55 DEBUG  CommonBackend: platform=win32
05-23 14:55 DEBUG  CommonBackend: osname=nt
05-23 14:55 DEBUG  CommonBackend: language=es_EC
05-23 14:55 DEBUG  CommonBackend: encoding=cp1252
05-23 14:55 DEBUG  WindowsBackend: arch=i386
05-23 14:55 DEBUG  CommonBackend: Parsing isolist=C:\Users\IMCOME~1\AppData\Local\Temp\pylD3F9.tmp\data\isolist.ini
05-23 14:55 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 14:55 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 14:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 14:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 14:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 14:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 14:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 14:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 14:55 DEBUG  WindowsBackend: Fetching host info...
05-23 14:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 14:55 DEBUG  WindowsBackend: windows version=vista
05-23 14:55 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
05-23 14:55 DEBUG  WindowsBackend: windows_sp=Service Pack 1
05-23 14:55 DEBUG  WindowsBackend: windows_build=6001
05-23 14:55 DEBUG  WindowsBackend: gmt=-5
05-23 14:55 DEBUG  WindowsBackend: country=EC
05-23 14:55 DEBUG  WindowsBackend: timezone=America/Guayaquil
05-23 14:55 DEBUG  WindowsBackend: windows_username=IMCOMEPRO
05-23 14:55 DEBUG  WindowsBackend: user_full_name=IMCOMEPRO
05-23 14:55 DEBUG  WindowsBackend: user_directory=IMCOMEPRO
05-23 14:55 DEBUG  WindowsBackend: windows_language_code=1034
05-23 14:55 DEBUG  WindowsBackend: windows_language=Spanish
05-23 14:55 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) 4 CPU 3.60GHz
05-23 14:55 DEBUG  WindowsBackend: bootloader=vista
05-23 14:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 61020.5820313 mb free )
05-23 14:55 DEBUG  WindowsBackend: drive=Drive(C: hd 61020.5820313 mb free )
05-23 14:55 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-23 14:55 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
05-23 14:55 DEBUG  WindowsBackend: uninstaller_path=None
05-23 14:55 DEBUG  WindowsBackend: previous_target_dir=None
05-23 14:55 DEBUG  WindowsBackend: previous_distro_name=None
05-23 14:55 DEBUG  WindowsBackend: keyboard_id=67776522
05-23 14:55 DEBUG  WindowsBackend: keyboard_layout=ec
05-23 14:55 DEBUG  WindowsBackend: keyboard_variant=
05-23 14:55 DEBUG  CommonBackend: locale=es_EC.UTF-8
05-23 14:55 DEBUG  WindowsBackend: total_memory_mb=2046.07421875
05-23 14:55 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 14:55 DEBUG  CommonBackend: Searching for local CDs
05-23 14:55 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylD3F9.tmp is a valid Ubuntu CD
05-23 14:55 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylD3F9.tmp\casper\filesystem.squashfs
05-23 14:55 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylD3F9.tmp is a valid Ubuntu CD
05-23 14:55 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylD3F9.tmp\casper\filesystem.squashfs
05-23 14:55 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylD3F9.tmp is a valid Kubuntu CD
05-23 14:55 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylD3F9.tmp\casper\filesystem.squashfs
05-23 14:55 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylD3F9.tmp is a valid Kubuntu CD
05-23 14:55 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylD3F9.tmp\casper\filesystem.squashfs
05-23 14:55 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylD3F9.tmp is a valid Xubuntu CD
05-23 14:55 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylD3F9.tmp\casper\filesystem.squashfs
05-23 14:55 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylD3F9.tmp is a valid Xubuntu CD
05-23 14:55 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylD3F9.tmp\casper\filesystem.squashfs
05-23 14:55 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylD3F9.tmp is a valid Mythbuntu CD
05-23 14:55 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylD3F9.tmp\casper\filesystem.squashfs
05-23 14:55 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pylD3F9.tmp is a valid Mythbuntu CD
05-23 14:55 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pylD3F9.tmp\casper\filesystem.squashfs
05-23 14:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 14:55 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
05-23 14:55 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
05-23 14:55 DEBUG  Distro: wrong arch: i386 != amd64
05-23 14:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 14:55 INFO   Distro: Found a valid CD for Ubuntu: D:\
05-23 14:55 INFO   root: Running the CD menu...
05-23 14:55 DEBUG  WindowsFrontend: __init__...
05-23 14:55 DEBUG  WindowsFrontend: on_init...
05-23 14:55 INFO   root: CD menu finished
05-23 14:55 INFO   root: Running the installer...
05-23 14:55 INFO   WindowsFrontend: Operation cancelled
05-23 14:55 DEBUG  WindowsFrontend: frontend.quit
05-23 14:55 DEBUG  WindowsFrontend: frontend.on_quit
05-23 14:55 DEBUG  root: application.on_quit
05-23 14:55 INFO   root: sys.exit
05-23 14:59 INFO   root: === wubi 9.04 rev128 ===
05-23 14:59 DEBUG  root: Logfile is c:\users\imcome~1\appdata\local\temp\wubi-9.04-rev128.log
05-23 14:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\IMCOMEPRO\\Desktop\\Ubuntu\\wubi.exe"']
05-23 14:59 DEBUG  CommonBackend: data_dir=C:\Users\IMCOME~1\AppData\Local\Temp\pyl5000.tmp\data
05-23 14:59 DEBUG  WindowsBackend: 7z=C:\Users\IMCOME~1\AppData\Local\Temp\pyl5000.tmp\bin\7z.exe
05-23 14:59 DEBUG  CommonBackend: Fetching basic info...
05-23 14:59 DEBUG  CommonBackend: original_exe=C:\Users\IMCOMEPRO\Desktop\Ubuntu\wubi.exe
05-23 14:59 DEBUG  CommonBackend: platform=win32
05-23 14:59 DEBUG  CommonBackend: osname=nt
05-23 14:59 DEBUG  CommonBackend: language=es_EC
05-23 14:59 DEBUG  CommonBackend: encoding=cp1252
05-23 14:59 DEBUG  WindowsBackend: arch=i386
05-23 14:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\IMCOME~1\AppData\Local\Temp\pyl5000.tmp\data\isolist.ini
05-23 14:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 14:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 14:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 14:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 14:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 14:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 14:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 14:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 14:59 DEBUG  WindowsBackend: Fetching host info...
05-23 14:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 14:59 DEBUG  WindowsBackend: windows version=vista
05-23 14:59 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
05-23 14:59 DEBUG  WindowsBackend: windows_sp=Service Pack 1
05-23 14:59 DEBUG  WindowsBackend: windows_build=6001
05-23 14:59 DEBUG  WindowsBackend: gmt=-5
05-23 14:59 DEBUG  WindowsBackend: country=EC
05-23 14:59 DEBUG  WindowsBackend: timezone=America/Guayaquil
05-23 14:59 DEBUG  WindowsBackend: windows_username=IMCOMEPRO
05-23 14:59 DEBUG  WindowsBackend: user_full_name=IMCOMEPRO
05-23 14:59 DEBUG  WindowsBackend: user_directory=IMCOMEPRO
05-23 14:59 DEBUG  WindowsBackend: windows_language_code=1034
05-23 14:59 DEBUG  WindowsBackend: windows_language=Spanish
05-23 14:59 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) 4 CPU 3.60GHz
05-23 14:59 DEBUG  WindowsBackend: bootloader=vista
05-23 14:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 60330.859375 mb free )
05-23 14:59 DEBUG  WindowsBackend: drive=Drive(C: hd 60330.859375 mb free )
05-23 14:59 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-23 14:59 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
05-23 14:59 DEBUG  WindowsBackend: uninstaller_path=None
05-23 14:59 DEBUG  WindowsBackend: previous_target_dir=None
05-23 14:59 DEBUG  WindowsBackend: previous_distro_name=None
05-23 14:59 DEBUG  WindowsBackend: keyboard_id=67776522
05-23 14:59 DEBUG  WindowsBackend: keyboard_layout=ec
05-23 14:59 DEBUG  WindowsBackend: keyboard_variant=
05-23 14:59 DEBUG  CommonBackend: locale=es_EC.UTF-8
05-23 14:59 DEBUG  WindowsBackend: total_memory_mb=2046.07421875
05-23 14:59 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 14:59 DEBUG  CommonBackend: Searching for local CDs
05-23 14:59 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl5000.tmp is a valid Ubuntu CD
05-23 14:59 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl5000.tmp\casper\filesystem.squashfs
05-23 14:59 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl5000.tmp is a valid Ubuntu CD
05-23 14:59 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl5000.tmp\casper\filesystem.squashfs
05-23 14:59 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl5000.tmp is a valid Kubuntu CD
05-23 14:59 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl5000.tmp\casper\filesystem.squashfs
05-23 14:59 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl5000.tmp is a valid Kubuntu CD
05-23 14:59 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl5000.tmp\casper\filesystem.squashfs
05-23 14:59 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl5000.tmp is a valid Xubuntu CD
05-23 14:59 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl5000.tmp\casper\filesystem.squashfs
05-23 14:59 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl5000.tmp is a valid Xubuntu CD
05-23 14:59 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl5000.tmp\casper\filesystem.squashfs
05-23 14:59 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl5000.tmp is a valid Mythbuntu CD
05-23 14:59 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl5000.tmp\casper\filesystem.squashfs
05-23 14:59 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl5000.tmp is a valid Mythbuntu CD
05-23 14:59 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl5000.tmp\casper\filesystem.squashfs
05-23 14:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 14:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 14:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 14:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 14:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-23 14:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 14:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-23 14:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 14:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-23 14:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 14:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-23 14:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 14:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-23 14:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 14:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-23 14:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 14:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-23 14:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 14:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-23 14:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 14:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-23 14:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 14:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-23 14:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 14:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-23 14:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 14:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-23 14:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 14:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-23 14:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 14:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-23 14:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 14:59 INFO   root: Running the installer...
05-23 14:59 DEBUG  WindowsFrontend: __init__...
05-23 14:59 DEBUG  WindowsFrontend: on_init...
05-23 15:00 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=Spanish, username=imcomepro
05-23 15:00 INFO   root: Received settings
05-23 15:00 DEBUG  TaskList: # Running tasklist...
05-23 15:00 DEBUG  TaskList: ## Running select_target_dir...
05-23 15:00 INFO   WindowsBackend: Installing into C:\ubuntu
05-23 15:00 DEBUG  TaskList: ## Finished select_target_dir
05-23 15:00 DEBUG  TaskList: ## Running create_dir_structure...
05-23 15:00 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-23 15:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-23 15:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-23 15:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-23 15:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-23 15:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-23 15:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-23 15:00 DEBUG  TaskList: ## Finished create_dir_structure
05-23 15:00 DEBUG  TaskList: ## Running uncompress_target_dir...
05-23 15:00 DEBUG  TaskList: ## Finished uncompress_target_dir
05-23 15:00 DEBUG  TaskList: ## Running create_uninstaller...
05-23 15:00 DEBUG  WindowsBackend: Copying uninstaller C:\Users\IMCOMEPRO\Desktop\Ubuntu\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-23 15:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-23 15:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-23 15:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-23 15:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-23 15:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
05-23 15:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-23 15:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-23 15:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-23 15:00 DEBUG  TaskList: ## Finished create_uninstaller
05-23 15:00 DEBUG  TaskList: ## Running copy_installation_files...
05-23 15:00 DEBUG  WindowsBackend: Copying C:\Users\IMCOME~1\AppData\Local\Temp\pyl5000.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-23 15:00 DEBUG  WindowsBackend: Copying C:\Users\IMCOME~1\AppData\Local\Temp\pyl5000.tmp\winboot -> C:\ubuntu\winboot
05-23 15:00 DEBUG  WindowsBackend: Copying C:\Users\IMCOME~1\AppData\Local\Temp\pyl5000.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-23 15:00 DEBUG  TaskList: ## Finished copy_installation_files
05-23 15:00 DEBUG  TaskList: ## Running get_iso...
05-23 15:00 DEBUG  CommonBackend: Searching for local CD
05-23 15:00 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl5000.tmp is a valid Ubuntu CD
05-23 15:00 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl5000.tmp\casper\filesystem.squashfs
05-23 15:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 15:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 15:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-23 15:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 15:00 DEBUG  CommonBackend: Searching for local ISO
05-23 15:00 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-23 15:00 DEBUG  TaskList: New task get_metalink
05-23 15:00 DEBUG  TaskList: ### Running get_metalink...
05-23 15:00 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink) > C:\ubuntu\install
05-23 15:00 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.04-desktop-i386.metalink, url=http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink, basename=ubuntu-9.04-desktop-i386.metalink, length=19438, text=None
05-23 15:00 DEBUG  downloader: download finished (read 19438 bytes)
05-23 15:00 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink](http://releases.ubuntu.com/9.04/MD5SUMS-metalink) > C:\ubuntu\install
05-23 15:00 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=413, text=None
05-23 15:00 DEBUG  downloader: download finished (read 413 bytes)
05-23 15:00 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
05-23 15:00 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
05-23 15:00 DEBUG  downloader: download finished (read 189 bytes)
05-23 15:00 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-23 15:00 INFO   saplog: Checking block bindings..
05-23 15:00 INFO   saplog: Key verified successfully.
05-23 15:00 DEBUG  CommonBackend: metalink md5sums:
1ec553ada3a4a18fb977816ccac02dfc  ubuntu-9.04-alternate-amd64.metalink
5daf9cb57325672f0eb768d6c11888e8  ubuntu-9.04-alternate-i386.metalink
3df58e889d3613abc2347a6b0e8f4d04  ubuntu-9.04-desktop-amd64.metalink
542bc6d7988f1d2967d419c089b08f57  ubuntu-9.04-desktop-i386.metalink
ea0b13f00711ef4b2e5c772482033a1f  ubuntu-9.04-server-amd64.metalink
88e47c579eb587c8aae1a7d7737ab3f0  ubuntu-9.04-server-i386.metalink

05-23 15:00 DEBUG  TaskList: ### Finished get_metalink
05-23 15:00 DEBUG  TaskList: New task download
05-23 15:00 DEBUG  TaskList: ### Running download...
05-23 15:00 DEBUG  downloader: downloading [http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-i386.iso](http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-i386.iso) > C:\ubuntu\install\ubuntu-9.04-desktop-i386.iso
05-23 15:00 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.04-desktop-i386.iso, url=http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-i386.iso, basename=ubuntu-9.04-desktop-i386.iso, length=732909568, text=None
05-23 15:01 INFO   WindowsFrontend: Operation cancelled
05-23 15:01 DEBUG  WindowsFrontend: frontend.quit
05-23 15:01 DEBUG  WindowsFrontend: frontend.on_quit
05-23 15:01 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
05-23 15:01 DEBUG  TaskList: # Cancelling tasklist
05-23 15:01 DEBUG  downloader: download finished (read 2088960 bytes)
05-23 15:01 DEBUG  TaskList: ### Finished download
05-23 15:01 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
05-23 15:01 DEBUG  root: application.on_quit
05-23 15:01 DEBUG  root: Forceful exit
05-23 15:01 INFO   root: sys.exit
05-23 15:01 INFO   root: === wubi 9.04 rev128 ===
05-23 15:01 DEBUG  root: Logfile is c:\users\imcome~1\appdata\local\temp\wubi-9.04-rev128.log
05-23 15:01 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\IMCOMEPRO\\Desktop\\Ubuntu\\wubi.exe"']
05-23 15:01 DEBUG  CommonBackend: data_dir=C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp\data
05-23 15:01 DEBUG  WindowsBackend: 7z=C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp\bin\7z.exe
05-23 15:01 DEBUG  CommonBackend: Fetching basic info...
05-23 15:01 DEBUG  CommonBackend: original_exe=C:\Users\IMCOMEPRO\Desktop\Ubuntu\wubi.exe
05-23 15:01 DEBUG  CommonBackend: platform=win32
05-23 15:01 DEBUG  CommonBackend: osname=nt
05-23 15:01 DEBUG  CommonBackend: language=es_EC
05-23 15:01 DEBUG  CommonBackend: encoding=cp1252
05-23 15:01 DEBUG  WindowsBackend: arch=i386
05-23 15:01 DEBUG  CommonBackend: Parsing isolist=C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp\data\isolist.ini
05-23 15:01 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 15:01 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 15:01 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 15:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 15:01 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 15:01 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 15:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 15:01 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 15:01 DEBUG  WindowsBackend: Fetching host info...
05-23 15:01 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 15:01 DEBUG  WindowsBackend: windows version=vista
05-23 15:01 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
05-23 15:01 DEBUG  WindowsBackend: windows_sp=Service Pack 1
05-23 15:01 DEBUG  WindowsBackend: windows_build=6001
05-23 15:01 DEBUG  WindowsBackend: gmt=-5
05-23 15:01 DEBUG  WindowsBackend: country=EC
05-23 15:01 DEBUG  WindowsBackend: timezone=America/Guayaquil
05-23 15:01 DEBUG  WindowsBackend: windows_username=IMCOMEPRO
05-23 15:01 DEBUG  WindowsBackend: user_full_name=IMCOMEPRO
05-23 15:01 DEBUG  WindowsBackend: user_directory=IMCOMEPRO
05-23 15:01 DEBUG  WindowsBackend: windows_language_code=1034
05-23 15:01 DEBUG  WindowsBackend: windows_language=Spanish
05-23 15:01 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) 4 CPU 3.60GHz
05-23 15:01 DEBUG  WindowsBackend: bootloader=vista
05-23 15:01 DEBUG  WindowsBackend: system_drive=Drive(C: hd 60325.7265625 mb free )
05-23 15:01 DEBUG  WindowsBackend: drive=Drive(C: hd 60325.7265625 mb free )
05-23 15:01 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-23 15:01 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
05-23 15:01 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-23 15:01 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-23 15:01 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-23 15:01 DEBUG  WindowsBackend: keyboard_id=67776522
05-23 15:01 DEBUG  WindowsBackend: keyboard_layout=ec
05-23 15:01 DEBUG  WindowsBackend: keyboard_variant=
05-23 15:01 DEBUG  CommonBackend: locale=es_EC.UTF-8
05-23 15:01 DEBUG  WindowsBackend: total_memory_mb=2046.07421875
05-23 15:01 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 15:01 DEBUG  CommonBackend: Searching for local CDs
05-23 15:01 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp is a valid Ubuntu CD
05-23 15:01 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp\casper\filesystem.squashfs
05-23 15:01 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp is a valid Ubuntu CD
05-23 15:01 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp\casper\filesystem.squashfs
05-23 15:01 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp is a valid Kubuntu CD
05-23 15:01 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp\casper\filesystem.squashfs
05-23 15:01 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp is a valid Kubuntu CD
05-23 15:01 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp\casper\filesystem.squashfs
05-23 15:01 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp is a valid Xubuntu CD
05-23 15:01 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp\casper\filesystem.squashfs
05-23 15:01 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp is a valid Xubuntu CD
05-23 15:01 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp\casper\filesystem.squashfs
05-23 15:01 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp is a valid Mythbuntu CD
05-23 15:01 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp\casper\filesystem.squashfs
05-23 15:01 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp is a valid Mythbuntu CD
05-23 15:01 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp\casper\filesystem.squashfs
05-23 15:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 15:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 15:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 15:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 15:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-23 15:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 15:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-23 15:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 15:01 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-23 15:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 15:01 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-23 15:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 15:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-23 15:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 15:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-23 15:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 15:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-23 15:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 15:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-23 15:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 15:01 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-23 15:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 15:01 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-23 15:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 15:01 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-23 15:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 15:01 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-23 15:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 15:01 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-23 15:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 15:01 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-23 15:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 15:01 INFO   root: Already installed, running the uninstaller...
05-23 15:01 INFO   root: Running the uninstaller...
05-23 15:01 INFO   CommonBackend: This is the uninstaller running
05-23 15:01 DEBUG  WindowsFrontend: __init__...
05-23 15:01 DEBUG  WindowsFrontend: on_init...
05-23 15:02 INFO   root: Received settings
05-23 15:02 DEBUG  TaskList: # Running tasklist...
05-23 15:02 DEBUG  TaskList: ## Running Backup ISO...
05-23 15:02 DEBUG  TaskList: ## Finished Backup ISO
05-23 15:02 DEBUG  TaskList: ## Running Remove bootloader entry...
05-23 15:02 DEBUG  WindowsBackend: Could not find bcd id
05-23 15:02 DEBUG  WindowsBackend: undo_bootini C:
05-23 15:02 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 60325.7265625 mb free )
05-23 15:02 DEBUG  WindowsBackend: undo_bootini F:
05-23 15:02 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
05-23 15:02 DEBUG  TaskList: ## Finished Remove bootloader entry
05-23 15:02 DEBUG  TaskList: ## Running Remove target dir...
05-23 15:02 DEBUG  CommonBackend: Deleting C:\ubuntu
05-23 15:02 DEBUG  TaskList: ## Finished Remove target dir
05-23 15:02 DEBUG  TaskList: ## Running Remove registry key...
05-23 15:02 DEBUG  TaskList: ## Finished Remove registry key
05-23 15:02 DEBUG  TaskList: # Finished tasklist
05-23 15:02 INFO   root: Almost finished uninstalling
05-23 15:02 INFO   root: Finished uninstallation
05-23 15:02 DEBUG  CommonBackend: Fetching basic info...
05-23 15:02 DEBUG  CommonBackend: original_exe=C:\Users\IMCOMEPRO\Desktop\Ubuntu\wubi.exe
05-23 15:02 DEBUG  CommonBackend: platform=win32
05-23 15:02 DEBUG  CommonBackend: osname=nt
05-23 15:02 DEBUG  CommonBackend: language=es_EC
05-23 15:02 DEBUG  CommonBackend: encoding=cp1252
05-23 15:02 DEBUG  WindowsBackend: arch=i386
05-23 15:02 DEBUG  CommonBackend: Parsing isolist=C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp\data\isolist.ini
05-23 15:02 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 15:02 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 15:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 15:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 15:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 15:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 15:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 15:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 15:02 DEBUG  WindowsBackend: Fetching host info...
05-23 15:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 15:02 DEBUG  WindowsBackend: windows version=vista
05-23 15:02 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
05-23 15:02 DEBUG  WindowsBackend: windows_sp=Service Pack 1
05-23 15:02 DEBUG  WindowsBackend: windows_build=6001
05-23 15:02 DEBUG  WindowsBackend: gmt=-5
05-23 15:02 DEBUG  WindowsBackend: country=EC
05-23 15:02 DEBUG  WindowsBackend: timezone=America/Guayaquil
05-23 15:02 DEBUG  WindowsBackend: windows_username=IMCOMEPRO
05-23 15:02 DEBUG  WindowsBackend: user_full_name=IMCOMEPRO
05-23 15:02 DEBUG  WindowsBackend: user_directory=IMCOMEPRO
05-23 15:02 DEBUG  WindowsBackend: windows_language_code=1034
05-23 15:02 DEBUG  WindowsBackend: windows_language=Spanish
05-23 15:02 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) 4 CPU 3.60GHz
05-23 15:02 DEBUG  WindowsBackend: bootloader=vista
05-23 15:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 60329.6367188 mb free )
05-23 15:02 DEBUG  WindowsBackend: drive=Drive(C: hd 60329.6367188 mb free )
05-23 15:02 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-23 15:02 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
05-23 15:02 DEBUG  WindowsBackend: uninstaller_path=None
05-23 15:02 DEBUG  WindowsBackend: previous_target_dir=None
05-23 15:02 DEBUG  WindowsBackend: previous_distro_name=None
05-23 15:02 DEBUG  WindowsBackend: keyboard_id=67776522
05-23 15:02 DEBUG  WindowsBackend: keyboard_layout=ec
05-23 15:02 DEBUG  WindowsBackend: keyboard_variant=
05-23 15:02 DEBUG  CommonBackend: locale=es_EC.UTF-8
05-23 15:02 DEBUG  WindowsBackend: total_memory_mb=2046.07421875
05-23 15:02 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 15:02 DEBUG  CommonBackend: Searching for local CDs
05-23 15:02 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp is a valid Ubuntu CD
05-23 15:02 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp\casper\filesystem.squashfs
05-23 15:02 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp is a valid Ubuntu CD
05-23 15:02 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp\casper\filesystem.squashfs
05-23 15:02 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp is a valid Kubuntu CD
05-23 15:02 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp\casper\filesystem.squashfs
05-23 15:02 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp is a valid Kubuntu CD
05-23 15:02 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp\casper\filesystem.squashfs
05-23 15:02 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp is a valid Xubuntu CD
05-23 15:02 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp\casper\filesystem.squashfs
05-23 15:02 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp is a valid Xubuntu CD
05-23 15:02 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp\casper\filesystem.squashfs
05-23 15:02 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp is a valid Mythbuntu CD
05-23 15:02 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp\casper\filesystem.squashfs
05-23 15:02 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp is a valid Mythbuntu CD
05-23 15:02 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl64A7.tmp\casper\filesystem.squashfs
05-23 15:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 15:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 15:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 15:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 15:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-23 15:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 15:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-23 15:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 15:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-23 15:06 INFO   root: === wubi 9.04 rev128 ===
05-23 15:06 DEBUG  root: Logfile is c:\users\imcome~1\appdata\local\temp\wubi-9.04-rev128.log
05-23 15:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
05-23 15:06 DEBUG  CommonBackend: data_dir=C:\Users\IMCOME~1\AppData\Local\Temp\pyl9B7B.tmp\data
05-23 15:06 DEBUG  WindowsBackend: 7z=C:\Users\IMCOME~1\AppData\Local\Temp\pyl9B7B.tmp\bin\7z.exe
05-23 15:06 DEBUG  CommonBackend: Fetching basic info...
05-23 15:06 DEBUG  CommonBackend: original_exe=D:\wubi.exe
05-23 15:06 DEBUG  CommonBackend: platform=win32
05-23 15:06 DEBUG  CommonBackend: osname=nt
05-23 15:06 DEBUG  CommonBackend: language=es_EC
05-23 15:06 DEBUG  CommonBackend: encoding=cp1252
05-23 15:06 DEBUG  WindowsBackend: arch=i386
05-23 15:06 DEBUG  CommonBackend: Parsing isolist=C:\Users\IMCOME~1\AppData\Local\Temp\pyl9B7B.tmp\data\isolist.ini
05-23 15:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 15:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 15:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 15:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 15:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 15:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 15:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 15:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 15:06 DEBUG  WindowsBackend: Fetching host info...
05-23 15:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 15:06 DEBUG  WindowsBackend: windows version=vista
05-23 15:06 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
05-23 15:06 DEBUG  WindowsBackend: windows_sp=Service Pack 1
05-23 15:06 DEBUG  WindowsBackend: windows_build=6001
05-23 15:06 DEBUG  WindowsBackend: gmt=-5
05-23 15:06 DEBUG  WindowsBackend: country=EC
05-23 15:06 DEBUG  WindowsBackend: timezone=America/Guayaquil
05-23 15:06 DEBUG  WindowsBackend: windows_username=IMCOMEPRO
05-23 15:06 DEBUG  WindowsBackend: user_full_name=IMCOMEPRO
05-23 15:06 DEBUG  WindowsBackend: user_directory=IMCOMEPRO
05-23 15:06 DEBUG  WindowsBackend: windows_language_code=1034
05-23 15:06 DEBUG  WindowsBackend: windows_language=Spanish
05-23 15:06 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) 4 CPU 3.60GHz
05-23 15:06 DEBUG  WindowsBackend: bootloader=vista
05-23 15:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 60966.1171875 mb free )
05-23 15:06 DEBUG  WindowsBackend: drive=Drive(C: hd 60966.1171875 mb free )
05-23 15:06 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-23 15:06 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
05-23 15:06 DEBUG  WindowsBackend: uninstaller_path=None
05-23 15:06 DEBUG  WindowsBackend: previous_target_dir=None
05-23 15:06 DEBUG  WindowsBackend: previous_distro_name=None
05-23 15:06 DEBUG  WindowsBackend: keyboard_id=67776522
05-23 15:06 DEBUG  WindowsBackend: keyboard_layout=ec
05-23 15:06 DEBUG  WindowsBackend: keyboard_variant=
05-23 15:06 DEBUG  CommonBackend: locale=es_EC.UTF-8
05-23 15:06 DEBUG  WindowsBackend: total_memory_mb=2046.07421875
05-23 15:06 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 15:06 DEBUG  CommonBackend: Searching for local CDs
05-23 15:06 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl9B7B.tmp is a valid Ubuntu CD
05-23 15:06 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl9B7B.tmp\casper\filesystem.squashfs
05-23 15:06 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl9B7B.tmp is a valid Ubuntu CD
05-23 15:06 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl9B7B.tmp\casper\filesystem.squashfs
05-23 15:06 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl9B7B.tmp is a valid Kubuntu CD
05-23 15:06 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl9B7B.tmp\casper\filesystem.squashfs
05-23 15:06 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl9B7B.tmp is a valid Kubuntu CD
05-23 15:06 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl9B7B.tmp\casper\filesystem.squashfs
05-23 15:06 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl9B7B.tmp is a valid Xubuntu CD
05-23 15:06 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl9B7B.tmp\casper\filesystem.squashfs
05-23 15:06 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl9B7B.tmp is a valid Xubuntu CD
05-23 15:06 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl9B7B.tmp\casper\filesystem.squashfs
05-23 15:06 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl9B7B.tmp is a valid Mythbuntu CD
05-23 15:06 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl9B7B.tmp\casper\filesystem.squashfs
05-23 15:06 DEBUG  Distro:   checking whether C:\Users\IMCOME~1\AppData\Local\Temp\pyl9B7B.tmp is a valid Mythbuntu CD
05-23 15:06 DEBUG  Distro:     does not contain C:\Users\IMCOME~1\AppData\Local\Temp\pyl9B7B.tmp\casper\filesystem.squashfs
05-23 15:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 15:06 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
05-23 15:06 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
05-23 15:06 DEBUG  Distro: wrong arch: i386 != amd64
05-23 15:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 15:06 INFO   Distro: Found a valid CD for Ubuntu: D:\
05-23 15:06 INFO   root: Running the CD menu...
05-23 15:06 DEBUG  WindowsFrontend: __init__...
05-23 15:06 DEBUG  WindowsFrontend: on_init...
05-23 15:07 INFO   root: CD menu finished
05-23 15:07 INFO   root: Running the installer...
05-23 15:09 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=10000MB, distro_name=Ubuntu, language=Spanish, username=imcomepro
05-23 15:09 INFO   root: Received settings
05-23 15:09 DEBUG  TaskList: # Running tasklist...
05-23 15:09 DEBUG  TaskList: ## Running select_target_dir...
05-23 15:09 INFO   WindowsBackend: Installing into C:\ubuntu
05-23 15:09 DEBUG  TaskList: ## Finished select_target_dir
05-23 15:09 DEBUG  TaskList: ## Running create_dir_structure...
05-23 15:09 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-23 15:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-23 15:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-23 15:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-23 15:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-23 15:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-23 15:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-23 15:09 DEBUG  TaskList: ## Finished create_dir_structure
05-23 15:09 DEBUG  TaskList: ## Running uncompress_target_dir...
05-23 15:09 DEBUG  TaskList: ## Finished uncompress_target_dir
05-23 15:09 DEBUG  TaskList: ## Running create_uninstaller...
05-23 15:09 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-23 15:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-23 15:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-23 15:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-23 15:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-23 15:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
05-23 15:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-23 15:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-23 15:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-23 15:10 DEBUG  TaskList: ## Finished create_uninstaller
05-23 15:10 DEBUG  TaskList: ## Running copy_installation_files...
05-23 15:10 DEBUG  WindowsBackend: Copying C:\Users\IMCOME~1\AppData\Local\Temp\pyl9B7B.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-23 15:10 DEBUG  WindowsBackend: Copying C:\Users\IMCOME~1\AppData\Local\Temp\pyl9B7B.tmp\winboot -> C:\ubuntu\winboot
05-23 15:10 DEBUG  WindowsBackend: Copying C:\Users\IMCOME~1\AppData\Local\Temp\pyl9B7B.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-23 15:10 DEBUG  TaskList: ## Finished copy_installation_files
05-23 15:10 DEBUG  TaskList: ## Running get_iso...
05-23 15:10 DEBUG  TaskList: New task copy_file
05-23 15:10 DEBUG  TaskList: ### Running copy_file...
05-23 15:12 DEBUG  TaskList: ### Finished copy_file
05-23 15:12 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
05-23 15:12 DEBUG  TaskList: # Cancelling tasklist
05-23 15:12 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
05-23 15:12 DEBUG  TaskList: New task check_iso
05-23 15:12 DEBUG  CommonBackend: Searching for local ISO
05-23 15:12 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-23 15:12 DEBUG  TaskList: New task get_metalink
05-23 15:12 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-23 15:12 DEBUG  TaskList: # Cancelling tasklist
05-23 15:12 DEBUG  TaskList: # Finished tasklist

Gracias de antemano por la ayuda que me puedan brindar quiero probar ubuntu linux.

icp77

---

### Post by estebandid0 on 2009-05-23
Simplemente tu CD esta defectuoso, bajalo nuevamente, o consigue de algun amigo, o quemalo nuevamente aveces pasa

---

### Post by icp77 on 2009-05-24
Hola,

gracias por responder, probé el cd en la que dice probar si tiene errores el cd, dice que no tiene errores, quería consultar otra cosa por favor, tengo un pc pentium IV y la tengo instalada con windows xp y fedora 8, funcionan bien los 2, pero quiero borrar el fedora 8 e instalar ubuntu 9.04.

Me pueden guiar en este paso por favor..

Luis

---

### Post by icp77 on 2009-05-27
A quien le interese,

ya pude instalarlo correctamente, cuando tienes instalado xp primero, y vas a crear particiones para otro OS, es bueno crear una partición swap, para luego instalar ubuntu en la siguiente partición, no cambiar en avanzadas el gestor de arranque, que fue lo que hice primero, murio el ruindows, y me toco recuperar el boot y mbr del xp. :o

Cuando lo instales, solo dejen el gestor de arranque como viene por default en ubuntu..

Ya que no tuve mucha ayuda en este foro para saber esto, jejeje, lo importante es que se pudo hacer y estoy probando ubuntu..

Suerte..

---

### Post by Petrux on 2009-05-28
F.Y.I
El foro te ha ayudado, quiza la pregunta especifica estuvo mal indicada.
En tu caso lo primero que hubiera hecho, es probar en otro equipo y con otro cd de ubuntu.
Si no has seguido los pasos necesarios o tuviste iniciativa propia de hacerlo como creias conveniente, los resultados pueden resultar inesperados.
En internet tambien hay una gran avalancha de manuales de instalacion, o mucho mejor aqui en la lista, hay muchos compañeros que ayudan, siempre y cuando hagas las preguntas correctas.
Bueno esta primera experiencia te ha servido para aprender cosas muy valiosas y demostrar que en Ubuntu es muy facil recuperar procesos.

Saludos

---

### Post by icp77 on 2009-05-31
Hola,
 
gracias de todas formas, igual tendre preguntas en otras ocasiones, para poder aprender más sobre ubuntu, varía un poco de fedora 10, que es el que he usado ya por 1 año mas o menos..
 
Saludos

---

