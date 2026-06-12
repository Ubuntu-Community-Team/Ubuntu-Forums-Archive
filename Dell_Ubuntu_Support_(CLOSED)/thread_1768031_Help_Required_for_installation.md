---
title: "Help Required for installation"
date: 2011-05-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by parasitologist on 2011-05-26
[SIZE=3]I have a Dell Inspiron 14R with 64 bit Windows 7 home premium installed, 4 GB RAM, 500 GB HD (3 partitions- C- 80 GB, D- 188GB, E- 197 GB) I tried to install ubuntu 11.04 for 64 bit system. I wanted to create dual boot so downloaded Wubi and tried to install ubuntu in C drive with 10 GB allocation. But after 3 hrs of downloading and installing the installer showed a error messege and it didn,t install.
Please help me and give me detailed procedure as I am not so much techno expert.
Thank Guys
[/SIZE]

---

### Post by dyem1 on 2011-05-26
If you want to install ubuntu you can use a pendrive or a cd, it's not so difficult and there are many guides[ (http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/]("http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/")). Personally I don't know how wubi works and if it works, but installing ubuntu on other partition always worked for me. When you install ubuntu, it creates a menu in which you can decide what OS you want to use everytime you start your computer.
I was wondering, you are not trying to install ubuntu in the same partition that windows? That can't be done, you need to install it in another partition (I think, not very sure with wubi). I hope this helps.

---

### Post by bcbc on 2011-05-26
> **parasitologist said:**
> I have a Dell Inspiron 14R with 64 bit Windows 7 home premium installed, 4 GB RAM, 500 GB HD (3 partitions- C- 80 GB, D- 188GB, E- 197 GB) I tried to install ubuntu 11.04 for 64 bit system. I wanted to create dual boot so downloaded Wubi and tried to install ubuntu in C drive with 10 GB allocation. But after 3 hrs of downloading and installing the installer showed a error messege and it didn,t install.
Please help me and give me detailed procedure as I am not so much techno expert.
Thank Guys
The error message is contained in a log file wubi-11.04-rev211.log in the %temp% directory (just put %temp% in the address bar of windows explorer). You can post it here if you want some help. 
Or just follow the [Wubi Guide]("https://wiki.ubuntu.com/WubiGuide#How do I install Wubi on a machine with no Internet connection?") on how to install: downloading the desktop ISO yourself and placing it in the same folder as wubi.exe seems to work the best.

---

### Post by parasitologist on 2011-06-29
> **bcbc said:**
> The error message is contained in a log file wubi-11.04-rev211.log in the %temp% directory (just put %temp% in the address bar of windows explorer). You can post it here if you want some help. 
Or just follow the [Wubi Guide]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20install%20Wubi%20on%20a%20machine%20with%20no%20Internet%20connection?") on how to install: downloading the desktop ISO yourself and placing it in the same folder as wubi.exe seems to work the best.

Hey Thanks for your try here is %temp%
05-26 20:04 INFO   root: === wubi 11.04 rev211 ===
05-26 20:04 DEBUG  root: Logfile is c:\users\dell\appdata\local\temp\wubi-11.04-rev211.log
05-26 20:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\dell\\Downloads\\Programs\\wubi.exe"']
05-26 20:04 DEBUG  CommonBackend: data_dir=C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp\data
05-26 20:04 DEBUG  WindowsBackend: 7z=C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp\bin\7z.exe
05-26 20:04 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-26 20:04 DEBUG  CommonBackend: Fetching basic info...
05-26 20:04 DEBUG  CommonBackend: original_exe=C:\Users\dell\Downloads\Programs\wubi.exe
05-26 20:04 DEBUG  CommonBackend: platform=win32
05-26 20:04 DEBUG  CommonBackend: osname=nt
05-26 20:04 DEBUG  CommonBackend: language=en_US
05-26 20:04 DEBUG  CommonBackend: encoding=cp1252
05-26 20:04 DEBUG  WindowsBackend: arch=amd64
05-26 20:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp\data\isolist.ini
05-26 20:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-26 20:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-26 20:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-26 20:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-26 20:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-26 20:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-26 20:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-26 20:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-26 20:04 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-26 20:04 DEBUG  WindowsBackend: Fetching host info...
05-26 20:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-26 20:04 DEBUG  WindowsBackend: windows version=vista
05-26 20:04 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-26 20:04 DEBUG  WindowsBackend: windows_sp=None
05-26 20:04 DEBUG  WindowsBackend: windows_build=7600
05-26 20:04 DEBUG  WindowsBackend: gmt=5
05-26 20:04 DEBUG  WindowsBackend: country=US
05-26 20:04 DEBUG  WindowsBackend: timezone=America/New_York
05-26 20:04 DEBUG  WindowsBackend: windows_username=dell
05-26 20:04 DEBUG  WindowsBackend: user_full_name=dell
05-26 20:04 DEBUG  WindowsBackend: user_directory=C:\Users\dell
05-26 20:04 DEBUG  WindowsBackend: windows_language_code=1033
05-26 20:04 DEBUG  WindowsBackend: windows_language=English
05-26 20:04 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
05-26 20:04 DEBUG  WindowsBackend: bootloader=vista
05-26 20:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 51172.1132813 mb free ntfs)
05-26 20:04 DEBUG  WindowsBackend: drive=Drive(C: hd 51172.1132813 mb free ntfs)
05-26 20:04 DEBUG  WindowsBackend: drive=Drive(D: hd 152921.894531 mb free ntfs)
05-26 20:04 DEBUG  WindowsBackend: drive=Drive(E: hd 202322.820313 mb free ntfs)
05-26 20:04 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-26 20:04 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
05-26 20:04 DEBUG  WindowsBackend: uninstaller_path=None
05-26 20:04 DEBUG  WindowsBackend: previous_target_dir=None
05-26 20:04 DEBUG  WindowsBackend: previous_distro_name=None
05-26 20:04 DEBUG  WindowsBackend: keyboard_id=67699721
05-26 20:04 DEBUG  WindowsBackend: keyboard_layout=us
05-26 20:04 DEBUG  WindowsBackend: keyboard_variant=
05-26 20:04 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-26 20:04 DEBUG  CommonBackend: locale=en_US.UTF-8
05-26 20:04 DEBUG  WindowsBackend: total_memory_mb=3892.5234375
05-26 20:04 DEBUG  CommonBackend: Searching ISOs on USB devices
05-26 20:04 DEBUG  CommonBackend: Searching for local CDs
05-26 20:04 DEBUG  Distro:   checking whether C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp is a valid Ubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp is a valid Ubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp is a valid Ubuntu Netbook CD
05-26 20:04 DEBUG  Distro:     does not contain C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp is a valid Kubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp is a valid Kubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp is a valid Xubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp is a valid Xubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp is a valid Mythbuntu CD
05-26 20:04 DEBUG  Distro:     does not contain C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp is a valid Mythbuntu CD
05-26 20:04 DEBUG  Distro:     does not contain C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-26 20:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-26 20:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-26 20:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-26 20:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-26 20:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-26 20:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-26 20:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-26 20:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-26 20:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
05-26 20:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-26 20:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-26 20:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-26 20:04 INFO   root: Running the installer...
05-26 20:04 DEBUG  WindowsFrontend: __init__...
05-26 20:04 DEBUG  WindowsFrontend: on_init...
05-26 20:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp\translations, languages=['en_US', 'en']
05-26 20:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp\translations, languages=['en_US', 'en']
05-26 20:04 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=10000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=souvikrupa
05-26 20:04 INFO   root: Received settings
05-26 20:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp\translations, languages=['en_US', 'en']
05-26 20:04 DEBUG  TaskList: # Running tasklist...
05-26 20:04 DEBUG  TaskList: ## Running select_target_dir...
05-26 20:04 INFO   WindowsBackend: Installing into C:\ubuntu
05-26 20:04 DEBUG  TaskList: ## Finished select_target_dir
05-26 20:04 DEBUG  TaskList: ## Running create_dir_structure...
05-26 20:04 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-26 20:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-26 20:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-26 20:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-26 20:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-26 20:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-26 20:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-26 20:04 DEBUG  TaskList: ## Finished create_dir_structure
05-26 20:04 DEBUG  TaskList: ## Running uncompress_target_dir...
05-26 20:04 DEBUG  TaskList: ## Finished uncompress_target_dir
05-26 20:04 DEBUG  TaskList: ## Running create_uninstaller...
05-26 20:04 DEBUG  WindowsBackend: Copying uninstaller C:\Users\dell\Downloads\Programs\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-26 20:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-26 20:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-26 20:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-26 20:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-26 20:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-26 20:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-26 20:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-26 20:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-26 20:04 DEBUG  TaskList: ## Finished create_uninstaller
05-26 20:04 DEBUG  TaskList: ## Running copy_installation_files...
05-26 20:04 DEBUG  WindowsBackend: Copying C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-26 20:04 DEBUG  WindowsBackend: Copying C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp\winboot -> C:\ubuntu\winboot
05-26 20:04 DEBUG  WindowsBackend: Copying C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-26 20:04 DEBUG  TaskList: ## Finished copy_installation_files
05-26 20:04 DEBUG  TaskList: ## Running get_iso...
05-26 20:04 DEBUG  CommonBackend: Searching for local CD
05-26 20:04 DEBUG  Distro:   checking whether C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp is a valid Ubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain C:\Users\dell\AppData\Local\Temp\pylD6CE.tmp\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-26 20:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-26 20:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-26 20:04 DEBUG  CommonBackend: Searching for local ISO
05-26 20:04 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-26 20:04 DEBUG  TaskList: New task get_metalink
05-26 20:04 DEBUG  TaskList: ### Running get_metalink...
05-26 20:04 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > C:\ubuntu\install
05-26 20:04 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
05-26 20:04 DEBUG  downloader: download finished (read 28363 bytes)
05-26 20:04 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > C:\ubuntu\install
05-26 20:04 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-26 20:04 DEBUG  downloader: download finished (read 874 bytes)
05-26 20:04 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
05-26 20:04 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-26 20:04 DEBUG  downloader: download finished (read 198 bytes)
05-26 20:04 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-26 20:04 INFO   saplog: Checking block bindings..
05-26 20:04 INFO   saplog: Key verified successfully.
05-26 20:04 DEBUG  CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-11.04-server-i386.metalink

05-26 20:04 DEBUG  TaskList: ### Finished get_metalink
05-26 20:04 DEBUG  TaskList: New task download
05-26 20:04 DEBUG  TaskList: ### Running download...
05-26 20:04 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-26 22:20 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request


05-26 22:20 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
05-26 22:20 DEBUG  TaskList: ### Finished download
05-26 22:20 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
05-26 22:20 DEBUG  TaskList: # Cancelling tasklist
05-26 22:20 DEBUG  TaskList: # Finished tasklist
05-26 22:20 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
05-26 22:59 INFO   root: === wubi 11.04 rev211 ===
05-26 22:59 DEBUG  root: Logfile is c:\users\dell\appdata\local\temp\wubi-11.04-rev211.log
05-26 22:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
05-26 22:59 DEBUG  CommonBackend: data_dir=C:\Users\dell\AppData\Local\Temp\pylC051.tmp\data
05-26 22:59 DEBUG  WindowsBackend: 7z=C:\Users\dell\AppData\Local\Temp\pylC051.tmp\bin\7z.exe
05-26 22:59 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-26 22:59 DEBUG  CommonBackend: Fetching basic info...
05-26 22:59 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
05-26 22:59 DEBUG  CommonBackend: platform=win32
05-26 22:59 DEBUG  CommonBackend: osname=nt
05-26 22:59 DEBUG  CommonBackend: language=en_US
05-26 22:59 DEBUG  CommonBackend: encoding=cp1252
05-26 22:59 DEBUG  WindowsBackend: arch=amd64
05-26 22:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\dell\AppData\Local\Temp\pylC051.tmp\data\isolist.ini
05-26 22:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-26 22:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-26 22:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-26 22:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-26 22:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-26 22:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-26 22:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-26 22:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-26 22:59 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-26 22:59 DEBUG  WindowsBackend: Fetching host info...
05-26 22:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-26 22:59 DEBUG  WindowsBackend: windows version=vista
05-26 22:59 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-26 22:59 DEBUG  WindowsBackend: windows_sp=None
05-26 22:59 DEBUG  WindowsBackend: windows_build=7600
05-26 22:59 DEBUG  WindowsBackend: gmt=5
05-26 22:59 DEBUG  WindowsBackend: country=US
05-26 22:59 DEBUG  WindowsBackend: timezone=America/New_York
05-26 22:59 DEBUG  WindowsBackend: windows_username=dell
05-26 22:59 DEBUG  WindowsBackend: user_full_name=dell
05-26 22:59 DEBUG  WindowsBackend: user_directory=C:\Users\dell
05-26 22:59 DEBUG  WindowsBackend: windows_language_code=1033
05-26 22:59 DEBUG  WindowsBackend: windows_language=English
05-26 22:59 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
05-26 22:59 DEBUG  WindowsBackend: bootloader=vista
05-26 22:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 52595.171875 mb free ntfs)
05-26 22:59 DEBUG  WindowsBackend: drive=Drive(C: hd 52595.171875 mb free ntfs)
05-26 22:59 DEBUG  WindowsBackend: drive=Drive(D: hd 152921.894531 mb free ntfs)
05-26 22:59 DEBUG  WindowsBackend: drive=Drive(E: hd 202322.820313 mb free ntfs)
05-26 22:59 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-26 22:59 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
05-26 22:59 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-26 22:59 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-26 22:59 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-26 22:59 DEBUG  WindowsBackend: keyboard_id=67699721
05-26 22:59 DEBUG  WindowsBackend: keyboard_layout=us
05-26 22:59 DEBUG  WindowsBackend: keyboard_variant=
05-26 22:59 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-26 22:59 DEBUG  CommonBackend: locale=en_US.UTF-8
05-26 22:59 DEBUG  WindowsBackend: total_memory_mb=3892.5234375
05-26 22:59 DEBUG  CommonBackend: Searching ISOs on USB devices
05-26 22:59 DEBUG  CommonBackend: Searching for local CDs
05-26 22:59 DEBUG  Distro:   checking whether C:\Users\dell\AppData\Local\Temp\pylC051.tmp is a valid Ubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain C:\Users\dell\AppData\Local\Temp\pylC051.tmp\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether C:\Users\dell\AppData\Local\Temp\pylC051.tmp is a valid Ubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain C:\Users\dell\AppData\Local\Temp\pylC051.tmp\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether C:\Users\dell\AppData\Local\Temp\pylC051.tmp is a valid Ubuntu Netbook CD
05-26 22:59 DEBUG  Distro:     does not contain C:\Users\dell\AppData\Local\Temp\pylC051.tmp\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether C:\Users\dell\AppData\Local\Temp\pylC051.tmp is a valid Kubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain C:\Users\dell\AppData\Local\Temp\pylC051.tmp\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether C:\Users\dell\AppData\Local\Temp\pylC051.tmp is a valid Kubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain C:\Users\dell\AppData\Local\Temp\pylC051.tmp\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether C:\Users\dell\AppData\Local\Temp\pylC051.tmp is a valid Xubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain C:\Users\dell\AppData\Local\Temp\pylC051.tmp\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether C:\Users\dell\AppData\Local\Temp\pylC051.tmp is a valid Xubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain C:\Users\dell\AppData\Local\Temp\pylC051.tmp\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether C:\Users\dell\AppData\Local\Temp\pylC051.tmp is a valid Mythbuntu CD
05-26 22:59 DEBUG  Distro:     does not contain C:\Users\dell\AppData\Local\Temp\pylC051.tmp\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether C:\Users\dell\AppData\Local\Temp\pylC051.tmp is a valid Mythbuntu CD
05-26 22:59 DEBUG  Distro:     does not contain C:\Users\dell\AppData\Local\Temp\pylC051.tmp\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-26 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-26 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-26 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-26 22:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-26 22:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-26 22:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-26 22:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-26 22:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-26 22:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
05-26 22:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-26 22:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-26 22:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-26 22:59 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-26 22:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-26 22:59 INFO   root: Running the uninstaller...
05-26 22:59 INFO   CommonBackend: This is the uninstaller running
05-26 22:59 DEBUG  WindowsFrontend: __init__...
05-26 22:59 DEBUG  WindowsFrontend: on_init...
05-26 22:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dell\AppData\Local\Temp\pylC051.tmp\translations, languages=['en_US', 'en']
05-26 22:59 INFO   root: Received settings
05-26 22:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dell\AppData\Local\Temp\pylC051.tmp\translations, languages=['en_US', 'en']
05-26 22:59 DEBUG  TaskList: # Running tasklist...
05-26 22:59 DEBUG  TaskList: ## Running Backup ISO...
05-26 22:59 DEBUG  TaskList: ## Finished Backup ISO
05-26 22:59 DEBUG  TaskList: ## Running Remove bootloader entry...
05-26 22:59 DEBUG  WindowsBackend: Could not find bcd id
05-26 22:59 DEBUG  WindowsBackend: undo_bootini C:
05-26 22:59 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 52595.171875 mb free ntfs)
05-26 22:59 DEBUG  WindowsBackend: undo_bootini D:
05-26 22:59 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 152921.894531 mb free ntfs)
05-26 22:59 DEBUG  WindowsBackend: undo_bootini E:
05-26 22:59 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 202322.820313 mb free ntfs)
05-26 22:59 DEBUG  WindowsBackend: undo_bootini G:
05-26 22:59 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
05-26 22:59 DEBUG  TaskList: ## Finished Remove bootloader entry
05-26 22:59 DEBUG  TaskList: ## Running Remove target dir...
05-26 22:59 DEBUG  CommonBackend: Deleting C:\ubuntu
05-26 22:59 DEBUG  TaskList: ## Finished Remove target dir
05-26 22:59 DEBUG  TaskList: ## Running Remove registry key...
05-26 22:59 DEBUG  TaskList: ## Finished Remove registry key
05-26 22:59 DEBUG  TaskList: # Finished tasklist
05-26 22:59 INFO   root: Almost finished uninstalling
05-26 22:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dell\AppData\Local\Temp\pylC051.tmp\translations, languages=['en_US', 'en']
05-26 22:59 INFO   root: Finished uninstallation
05-26 22:59 DEBUG  root: application.quit
05-26 22:59 DEBUG  WindowsFrontend: frontend.quit
05-26 22:59 DEBUG  WindowsFrontend: frontend.on_quit
05-26 22:59 DEBUG  root: application.on_quit
05-26 22:59 INFO   root: sys.exit

There was a text doc file wubi-11.04 rev-211, i pasted whatever was written on it

---

### Post by bcbc on 2011-06-29
> 05-26 22:20 ERROR TaskList: Non fatal error Traceback (most recent call last):
File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
File "\lib\bittorrent\Rerequester.py", line 96, in fail
File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

The problem is the bittorrent downloader that wubi uses cannot connect. Either you're blocking pyrun.exe (the python runtime) from your firewall or it's another firewall somewhere.

You can either unblock pyrun.exe or just download the ISO yourself to the same folder as wubi.exe and run wubi from there.

See [https://wiki.ubuntu.com/WubiGuide#Installation](https://wiki.ubuntu.com/WubiGuide#Installation) for full installation options.

---

### Post by parasitologist on 2011-06-29
> **bcbc said:**
> The problem is the bittorrent downloader that wubi uses cannot connect. Either you're blocking pyrun.exe (the python runtime) from your firewall or it's another firewall somewhere.

You can either unblock pyrun.exe or just download the ISO yourself to the same folder as wubi.exe and run wubi from there.

See [https://wiki.ubuntu.com/WubiGuide#Installation](https://wiki.ubuntu.com/WubiGuide#Installation) for full installation options.



Thank You 
I am downloading the ubuntu 11.04 desktop.iso (as rar) and have downloaded wubi. So now what I have to do is extract the ubuntu 11.04files from the rar and paste the wubi in same folder and then run wubi?
Another thing can I install ubuntu in C drive, it already has Windows 7 installed in it,
how much allocation should I give to ubuntu

---

### Post by bcbc on 2011-06-29
> **parasitologist said:**
> Thank You 
I am downloading the ubuntu 11.04 desktop.iso (as rar) and have downloaded wubi. So now what I have to do is extract the ubuntu 11.04files from the rar and paste the wubi in same folder and then run wubi?
Another thing can I install ubuntu in C drive, it already has Windows 7 installed in it,
how much allocation should I give to ubuntu

No don't extract it. Just place it (the ISO) in the same folder as wubi.exe. (It's not a rar, rather you have assocaited .iso files with the winrar application, so Windows tells you it's a rar file).

You can install it in C: 

The size you need depends on what you want to do. When you first install, Ubuntu will take up about 2.6 GB. So if you just want to check out Ubuntu I'd say go for between 5GB and 10GB. 
But the size is fixed so if you're not sure it's better to aim high. If you intend to store or work with multimedia files the space goes quickly.
 

PS Wubi installs are vulnerable to forced shutdowns. If ubuntu appears to hang, try to reboot by holding down Alt+SysRQ and pressing R-E-I-S-U-B. Only if that fails, should you poweroff. Keep important data backed up outside the virtual disk (root.disk) e.g. on the windows host (under the /host directory)

---

