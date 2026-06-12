---
title: "Wubi 9.04 install fails"
date: 2009-04-27
forum: General Help
---

### Post by kmand on 2009-04-27
I'm having trouble installing wubi 9.04 on an XP Pro SP3 Pentium 3 Thinkpad.

The log shows the failure at:

04-27 09:14 DEBUG  TaskList: ## Running create_virtual_disks...
04-27 09:14 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\root.disk of 6744MB
04-27 09:14 ERROR  Virtualdisk: Failed to extend file. Not enough free space?
None
04-27 09:14 ERROR  Virtualdisk: WriteFile() failed!
None
.....  (many repeats of WriteFile failed)

The C: filesystem has 16GB free, so its not a space problem. Its a FAT32.


Here is a full listing of the log up to the write failure:
04-27 09:08 INFO   root: === wubi 9.04 rev128 ===
04-27 09:08 DEBUG  root: Logfile is c:\docume~1\km\locals~1\temp\wubi-9.04-rev128.log
04-27 09:08 DEBUG  root: sys.argv = ['main.pyo', '--exefile="Z:\\wubi.exe"', '--cdmenu']
04-27 09:08 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\km\LOCALS~1\Temp\pyl8.tmp\data
04-27 09:08 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\km\LOCALS~1\Temp\pyl8.tmp\bin\7z.exe
04-27 09:08 DEBUG  CommonBackend: Fetching basic info...
04-27 09:08 DEBUG  CommonBackend: original_exe=Z:\wubi.exe
04-27 09:08 DEBUG  CommonBackend: platform=win32
04-27 09:08 DEBUG  CommonBackend: osname=nt
04-27 09:08 DEBUG  CommonBackend: language=en_US
04-27 09:08 DEBUG  CommonBackend: encoding=cp1252
04-27 09:08 DEBUG  WindowsBackend: arch=i386
04-27 09:08 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\km\LOCALS~1\Temp\pyl8.tmp\data\isolist.ini 
04-27 09:08 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-27 09:08 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-27 09:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-27 09:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-27 09:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-27 09:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-27 09:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-27 09:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-27 09:08 DEBUG  WindowsBackend: Fetching host info...
04-27 09:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi   
04-27 09:08 DEBUG  WindowsBackend: windows version=2000
04-27 09:08 DEBUG  WindowsBackend: windows_version2=Microsoft Windows 2000
04-27 09:08 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-27 09:08 DEBUG  WindowsBackend: windows_build=2600
04-27 09:08 DEBUG  WindowsBackend: gmt=-8
04-27 09:08 DEBUG  WindowsBackend: country=US
04-27 09:08 DEBUG  WindowsBackend: timezone=America/Los_Angeles
04-27 09:08 DEBUG  WindowsBackend: windows_username=km
04-27 09:08 DEBUG  WindowsBackend: user_full_name=km
04-27 09:08 DEBUG  WindowsBackend: user_directory=km
04-27 09:08 DEBUG  WindowsBackend: windows_language_code=1033
04-27 09:08 DEBUG  WindowsBackend: windows_language=English
04-27 09:08 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) III Mobile CPU      1133MHz
04-27 09:08 DEBUG  WindowsBackend: bootloader=xp
04-27 09:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 17105.21875 mb free )
04-27 09:08 DEBUG  WindowsBackend: drive=Drive(C: hd 17105.21875 mb free )
04-27 09:08 DEBUG  WindowsBackend: drive=Drive(Z: cd 0.0 mb free cdfs)
04-27 09:08 DEBUG  WindowsBackend: uninstaller_path=None  
04-27 09:08 DEBUG  WindowsBackend: previous_target_dir=None
04-27 09:08 DEBUG  WindowsBackend: previous_distro_name=None
04-27 09:08 DEBUG  WindowsBackend: keyboard_id=67699721
04-27 09:08 DEBUG  WindowsBackend: keyboard_layout=us
04-27 09:08 DEBUG  WindowsBackend: keyboard_variant=
04-27 09:08 DEBUG  CommonBackend: locale=en_US.UTF-8
04-27 09:08 DEBUG  WindowsBackend: total_memory_mb=638.984375
04-27 09:08 DEBUG  CommonBackend: Searching for local CDs
04-27 09:08 DEBUG  Distro:   checking whether C:\DOCUME~1\km\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu CD
04-27 09:08 DEBUG  Distro:     does not contain C:\DOCUME~1\km\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
04-27 09:08 DEBUG  Distro:   checking whether C:\DOCUME~1\km\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu CD
04-27 09:08 DEBUG  Distro:     does not contain C:\DOCUME~1\km\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
04-27 09:08 DEBUG  Distro:   checking whether C:\DOCUME~1\km\LOCALS~1\Temp\pyl8.tmp is a valid Kubuntu CD
04-27 09:08 DEBUG  Distro:     does not contain C:\DOCUME~1\km\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
04-27 09:08 DEBUG  Distro:   checking whether C:\DOCUME~1\km\LOCALS~1\Temp\pyl8.tmp is a valid Kubuntu CD
04-27 09:08 DEBUG  Distro:     does not contain C:\DOCUME~1\km\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
04-27 09:08 DEBUG  Distro:   checking whether C:\DOCUME~1\km\LOCALS~1\Temp\pyl8.tmp is a valid Xubuntu CD
04-27 09:08 DEBUG  Distro:     does not contain C:\DOCUME~1\km\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
04-27 09:08 DEBUG  Distro:   checking whether C:\DOCUME~1\km\LOCALS~1\Temp\pyl8.tmp is a valid Xubuntu CD
04-27 09:08 DEBUG  Distro:     does not contain C:\DOCUME~1\km\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
04-27 09:08 DEBUG  Distro:   checking whether C:\DOCUME~1\km\LOCALS~1\Temp\pyl8.tmp is a valid Mythbuntu CD
04-27 09:08 DEBUG  Distro:     does not contain C:\DOCUME~1\km\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
04-27 09:08 DEBUG  Distro:   checking whether C:\DOCUME~1\km\LOCALS~1\Temp\pyl8.tmp is a valid Mythbuntu CD
04-27 09:08 DEBUG  Distro:     does not contain C:\DOCUME~1\km\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
04-27 09:08 DEBUG  Distro:   checking whether Z:\ is a valid Ubuntu CD
04-27 09:08 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
04-27 09:08 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386>
04-27 09:08 DEBUG  Distro: wrong arch: i386 != amd64 
04-27 09:08 DEBUG  Distro:   checking whether Z:\ is a valid Ubuntu CD
04-27 09:08 INFO   Distro: Found a valid CD for Ubuntu: Z:\
04-27 09:08 INFO   root: Running the CD menu...
04-27 09:08 DEBUG  WindowsFrontend: __init__...
04-27 09:08 DEBUG  WindowsFrontend: on_init...
04-27 09:08 INFO   root: CD menu finished
04-27 09:08 INFO   root: Running the installer...
04-27 09:09 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=7000MB, distro_name=Ubuntu, language=English, username=km
04-27 09:09 INFO   root: Received settings
04-27 09:09 DEBUG  TaskList: # Running tasklist...
04-27 09:09 DEBUG  TaskList: ## Running select_target_dir...
04-27 09:09 INFO   WindowsBackend: Installing into C:\ubuntu
04-27 09:09 DEBUG  TaskList: ## Finished select_target_dir
04-27 09:09 DEBUG  TaskList: ## Running create_dir_structure...
04-27 09:09 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-27 09:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-27 09:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-27 09:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-27 09:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-27 09:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-27 09:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-27 09:09 DEBUG  TaskList: ## Finished create_dir_structure
04-27 09:09 DEBUG  TaskList: ## Running uncompress_target_dir...
04-27 09:09 ERROR  WindowsBackend: Error executing command
>>command=compact C:\ubuntu /U /A /F
>>retval=1
>>stderr=^M
 Uncompressing files in C:\^M
^M
ubuntu [ERR]^M
ubuntu: The file system does not support compression.^M
^M
0 files within 1 directories were uncompressed.^M
^M

>>stdout=
04-27 09:09 DEBUG  TaskList: ## Finished uncompress_target_dir
04-27 09:09 DEBUG  TaskList: ## Running create_uninstaller...
04-27 09:09 DEBUG  WindowsBackend: Copying uninstaller Z:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-27 09:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-27 09:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-27 09:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-27 09:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-27 09:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
04-27 09:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-27 09:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-27 09:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-27 09:09 DEBUG  TaskList: ## Finished create_uninstaller
04-27 09:09 DEBUG  TaskList: ## Running copy_installation_files...
04-27 09:09 DEBUG  WindowsBackend: Copying C:\DOCUME~1\km\LOCALS~1\Temp\pyl8.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-27 09:09 DEBUG  WindowsBackend: Copying C:\DOCUME~1\km\LOCALS~1\Temp\pyl8.tmp\winboot -> C:\ubuntu\winboot
04-27 09:09 DEBUG  WindowsBackend: Copying C:\DOCUME~1\km\LOCALS~1\Temp\pyl8.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-27 09:09 DEBUG  TaskList: ## Finished copy_installation_files
04-27 09:09 DEBUG  TaskList: ## Running get_iso...
04-27 09:09 DEBUG  TaskList: New task copy_file
04-27 09:09 DEBUG  TaskList: ### Running copy_file...  
04-27 09:12 DEBUG  TaskList: ### Finished copy_file
04-27 09:12 DEBUG  TaskList: New task check_iso  
04-27 09:12 DEBUG  TaskList: ### Running check_iso...
04-27 09:12 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
04-27 09:12 DEBUG  TaskList: New task get_metalink
04-27 09:12 DEBUG  TaskList: #### Running get_metalink...
04-27 09:12 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink) > C:\ubuntu\install
04-27 09:12 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.04-desktop-i386.metalink, url=http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.met>
04-27 09:12 DEBUG  downloader: download finished (read 19438 bytes)
04-27 09:12 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink](http://releases.ubuntu.com/9.04/MD5SUMS-metalink) > C:\ubuntu\install
04-27 09:12 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, >
04-27 09:12 DEBUG  downloader: download finished (read 413 bytes)
04-27 09:12 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
04-27 09:12 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-me>
04-27 09:12 DEBUG  downloader: download finished (read 189 bytes)
04-27 09:12 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-27 09:12 INFO   saplog: Checking block bindings..
04-27 09:12 INFO   saplog: Key verified successfully.
04-27 09:12 DEBUG  CommonBackend: metalink md5sums:
1ec553ada3a4a18fb977816ccac02dfc  ubuntu-9.04-alternate-amd64.metalink
5daf9cb57325672f0eb768d6c11888e8  ubuntu-9.04-alternate-i386.metalink
3df58e889d3613abc2347a6b0e8f4d04  ubuntu-9.04-desktop-amd64.metalink
542bc6d7988f1d2967d419c089b08f57  ubuntu-9.04-desktop-i386.metalink
ea0b13f00711ef4b2e5c772482033a1f  ubuntu-9.04-server-amd64.metalink
88e47c579eb587c8aae1a7d7737ab3f0  ubuntu-9.04-server-i386.metalink

04-27 09:12 DEBUG  TaskList: #### Finished get_metalink
04-27 09:12 DEBUG  TaskList: New task get_file_md5
04-27 09:12 DEBUG  TaskList: #### Running get_file_md5...
04-27 09:14 DEBUG  TaskList: #### Finished get_file_md5
04-27 09:14 DEBUG  TaskList: ### Finished check_iso
04-27 09:14 DEBUG  TaskList: ## Finished get_iso
04-27 09:14 DEBUG  TaskList: ## Running extract_kernel...
04-27 09:14 DEBUG  CommonBackend: Copying files from CD Z:\
04-27 09:14 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
04-27 09:14 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
04-27 09:14 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = da3a16e8bd2392c4eabf52d8fc22e947 == da3a16e8bd2392c4eabf52d8fc22e947
04-27 09:14 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.gz
04-27 09:14 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.gz md5 = c0b6de16a3614614b9543ce0f474e63c == c0b6de16a3614614b9543ce0f474e63c
04-27 09:14 DEBUG  TaskList: ## Finished extract_kernel
04-27 09:14 DEBUG  TaskList: ## Running choose_disk_sizes...
04-27 09:14 DEBUG  WindowsBackend: total size=7000  
  root=6744
  swap=256
  home=0
  usr=0
04-27 09:14 DEBUG  TaskList: ## Finished choose_disk_sizes
04-27 09:14 DEBUG  TaskList: ## Running create_preseed...
04-27 09:14 DEBUG  TaskList: ## Finished create_preseed
04-27 09:14 DEBUG  TaskList: ## Running modify_bootloader...
04-27 09:14 DEBUG  TaskList: New task modify_bootini
04-27 09:14 DEBUG  TaskList: ### Running modify_bootini...
04-27 09:14 DEBUG  WindowsBackend: modify_bootini C:
04-27 09:14 DEBUG  TaskList: ### Finished modify_bootini 
04-27 09:14 DEBUG  TaskList: ## Finished modify_bootloader
04-27 09:14 DEBUG  TaskList: ## Running modify_grub_configuration...
04-27 09:14 DEBUG  TaskList: ## Finished modify_grub_configuration
04-27 09:14 DEBUG  TaskList: ## Running create_virtual_disks...
04-27 09:14 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\root.disk of 6744MB
04-27 09:14 ERROR  Virtualdisk: Failed to extend file. Not enough free space?
None
04-27 09:14 ERROR  Virtualdisk: WriteFile() failed!

---

