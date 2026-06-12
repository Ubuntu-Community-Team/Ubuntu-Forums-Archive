---
title: "Dell Dimension 8300"
date: 2011-04-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lilmanbhb on 2011-04-05
So im sick of windows xp, but i need it for several applications i use. I need to dual boot ubuntu and xp. Im very new to the world of linux, and i have no idea how to solve this problem.
I have burned the ubuntu 10.10 iso on to a cd and it seems to work until i try to do anything with ubuntu. The screen shows up in windows that gives the instructions on booting/accesses the wubi installer. I have tried using the wubi installer, and always get an error during the extraction of the files that says "An error occured
Permission denied
Check log at (filepath)"
 
If i try to boot from the disk, it gets to the main loading screen with the 5 dots, but after about 30 seconds, the loading dots stop, and it freezes. I have left it for hours to check that im not being impatient.
 
If i can give any further info, lemme know. 
 
Here is the log for the wubi installer, for some reason i cant attatch it
 
 
03-27 16:57 INFO root: === wubi 10.10 rev197 ===
03-27 16:57 DEBUG root: Logfile is c:\docume~1\brando~1.djt\locals~1\temp\wubi-10.10-rev197.log
03-27 16:57 DEBUG root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
03-27 16:57 DEBUG CommonBackend: data_dir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp\data
03-27 16:57 DEBUG WindowsBackend: 7z=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp\bin\7z.exe
03-27 16:57 DEBUG CommonBackend: Fetching basic info...
03-27 16:57 DEBUG CommonBackend: original_exe=E:\wubi.exe
03-27 16:57 DEBUG CommonBackend: platform=win32
03-27 16:57 DEBUG CommonBackend: osname=nt
03-27 16:57 DEBUG CommonBackend: language=en_US
03-27 16:57 DEBUG CommonBackend: encoding=cp1252
03-27 16:57 DEBUG WindowsBackend: arch=i386
03-27 16:57 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp\data\isolist.ini
03-27 16:57 DEBUG CommonBackend: Adding distro Xubuntu-i386
03-27 16:57 DEBUG CommonBackend: Adding distro Xubuntu-amd64
03-27 16:57 DEBUG CommonBackend: Adding distro Kubuntu-amd64
03-27 16:57 DEBUG CommonBackend: Adding distro Mythbuntu-i386
03-27 16:57 DEBUG CommonBackend: Adding distro Ubuntu-amd64
03-27 16:57 DEBUG CommonBackend: Adding distro Ubuntu-i386
03-27 16:57 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
03-27 16:57 DEBUG CommonBackend: Adding distro Kubuntu-i386
03-27 16:57 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
03-27 16:57 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
03-27 16:57 DEBUG WindowsBackend: Fetching host info...
03-27 16:57 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-27 16:57 DEBUG WindowsBackend: windows version=xp
03-27 16:57 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
03-27 16:57 DEBUG WindowsBackend: windows_sp=Service Pack 3
03-27 16:57 DEBUG WindowsBackend: windows_build=2600
03-27 16:57 DEBUG WindowsBackend: gmt=-7
03-27 16:57 DEBUG WindowsBackend: country=US
03-27 16:57 DEBUG WindowsBackend: timezone=America/Denver
03-27 16:57 DEBUG WindowsBackend: windows_username=Brandon
03-27 16:57 DEBUG WindowsBackend: user_full_name=Brandon
03-27 16:57 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Brandon.DJT48W21
03-27 16:57 DEBUG WindowsBackend: windows_language_code=1033
03-27 16:57 DEBUG WindowsBackend: windows_language=English
03-27 16:57 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 3.00GHz
03-27 16:57 DEBUG WindowsBackend: bootloader=xp
03-27 16:57 DEBUG WindowsBackend: system_drive=Drive(C: hd 109986.042969 mb free ntfs)
03-27 16:57 DEBUG WindowsBackend: drive=Drive(C: hd 109986.042969 mb free ntfs)
03-27 16:57 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free )
03-27 16:57 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-27 16:57 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-27 16:57 DEBUG WindowsBackend: uninstaller_path=None
03-27 16:57 DEBUG WindowsBackend: previous_target_dir=None
03-27 16:57 DEBUG WindowsBackend: previous_distro_name=None
03-27 16:57 DEBUG WindowsBackend: keyboard_id=67699721
03-27 16:57 DEBUG WindowsBackend: keyboard_layout=us
03-27 16:57 DEBUG WindowsBackend: keyboard_variant=
03-27 16:57 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
03-27 16:57 DEBUG CommonBackend: locale=en_US.UTF-8
03-27 16:57 DEBUG WindowsBackend: total_memory_mb=1022.98828125
03-27 16:57 DEBUG CommonBackend: Searching ISOs on USB devices
03-27 16:57 DEBUG CommonBackend: Searching for local CDs
03-27 16:57 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
03-27 16:57 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
03-27 16:57 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
03-27 16:57 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
03-27 16:57 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu Netbook CD
03-27 16:57 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
03-27 16:57 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu CD
03-27 16:57 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
03-27 16:57 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu CD
03-27 16:57 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
03-27 16:57 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu Netbook CD
03-27 16:57 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
03-27 16:57 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp is a valid Xubuntu CD
03-27 16:57 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
03-27 16:57 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp is a valid Xubuntu CD
03-27 16:57 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
03-27 16:57 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp is a valid Mythbuntu CD
03-27 16:57 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
03-27 16:57 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp is a valid Mythbuntu CD
03-27 16:57 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
03-27 16:57 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
03-27 16:57 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
03-27 16:57 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
03-27 16:57 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
03-27 16:57 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook CD
03-27 16:57 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
03-27 16:57 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
03-27 16:57 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
03-27 16:57 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
03-27 16:57 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
03-27 16:57 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD
03-27 16:57 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
03-27 16:57 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
03-27 16:57 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
03-27 16:57 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
03-27 16:57 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
03-27 16:57 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
03-27 16:57 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
03-27 16:57 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
03-27 16:57 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
03-27 16:57 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
03-27 16:57 DEBUG Distro: parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-27 16:57 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-27 16:57 DEBUG Distro: wrong arch: i386 != amd64
03-27 16:57 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
03-27 16:57 INFO Distro: Found a valid CD for Ubuntu: E:\
03-27 16:57 INFO root: Running the CD menu...
03-27 16:57 DEBUG WindowsFrontend: __init__...
03-27 16:57 DEBUG WindowsFrontend: on_init...
03-27 16:57 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
03-27 16:57 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
03-27 16:57 INFO WindowsFrontend: Operation cancelled
03-27 16:57 DEBUG WindowsFrontend: frontend.quit
03-27 16:57 DEBUG WindowsFrontend: frontend.on_quit
03-27 16:57 DEBUG root: application.on_quit
03-27 16:57 INFO root: sys.exit
03-27 18:30 INFO root: === wubi 10.10 rev197 ===
03-27 18:30 DEBUG root: Logfile is c:\docume~1\brando~1.djt\locals~1\temp\wubi-10.10-rev197.log
03-27 18:30 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
03-27 18:30 DEBUG CommonBackend: data_dir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp\data
03-27 18:30 DEBUG WindowsBackend: 7z=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp\bin\7z.exe
03-27 18:30 DEBUG CommonBackend: Fetching basic info...
03-27 18:30 DEBUG CommonBackend: original_exe=D:\wubi.exe
03-27 18:30 DEBUG CommonBackend: platform=win32
03-27 18:30 DEBUG CommonBackend: osname=nt
03-27 18:30 DEBUG CommonBackend: language=en_US
03-27 18:30 DEBUG CommonBackend: encoding=cp1252
03-27 18:30 DEBUG WindowsBackend: arch=i386
03-27 18:30 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp\data\isolist.ini
03-27 18:30 DEBUG CommonBackend: Adding distro Xubuntu-i386
03-27 18:30 DEBUG CommonBackend: Adding distro Xubuntu-amd64
03-27 18:30 DEBUG CommonBackend: Adding distro Kubuntu-amd64
03-27 18:30 DEBUG CommonBackend: Adding distro Mythbuntu-i386
03-27 18:30 DEBUG CommonBackend: Adding distro Ubuntu-amd64
03-27 18:30 DEBUG CommonBackend: Adding distro Ubuntu-i386
03-27 18:30 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
03-27 18:30 DEBUG CommonBackend: Adding distro Kubuntu-i386
03-27 18:30 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
03-27 18:30 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
03-27 18:30 DEBUG WindowsBackend: Fetching host info...
03-27 18:30 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-27 18:30 DEBUG WindowsBackend: windows version=xp
03-27 18:30 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
03-27 18:30 DEBUG WindowsBackend: windows_sp=Service Pack 3
03-27 18:30 DEBUG WindowsBackend: windows_build=2600
03-27 18:30 DEBUG WindowsBackend: gmt=-7
03-27 18:30 DEBUG WindowsBackend: country=US
03-27 18:30 DEBUG WindowsBackend: timezone=America/Denver
03-27 18:30 DEBUG WindowsBackend: windows_username=Brandon
03-27 18:30 DEBUG WindowsBackend: user_full_name=Brandon
03-27 18:30 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Brandon.DJT48W21
03-27 18:30 DEBUG WindowsBackend: windows_language_code=1033
03-27 18:30 DEBUG WindowsBackend: windows_language=English
03-27 18:30 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 3.00GHz
03-27 18:30 DEBUG WindowsBackend: bootloader=xp
03-27 18:30 DEBUG WindowsBackend: system_drive=Drive(C: hd 109936.351563 mb free ntfs)
03-27 18:30 DEBUG WindowsBackend: drive=Drive(C: hd 109936.351563 mb free ntfs)
03-27 18:30 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-27 18:30 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
03-27 18:30 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-27 18:30 DEBUG WindowsBackend: uninstaller_path=None
03-27 18:30 DEBUG WindowsBackend: previous_target_dir=None
03-27 18:30 DEBUG WindowsBackend: previous_distro_name=None
03-27 18:30 DEBUG WindowsBackend: keyboard_id=67699721
03-27 18:30 DEBUG WindowsBackend: keyboard_layout=us
03-27 18:30 DEBUG WindowsBackend: keyboard_variant=
03-27 18:30 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
03-27 18:30 DEBUG CommonBackend: locale=en_US.UTF-8
03-27 18:30 DEBUG WindowsBackend: total_memory_mb=1022.98828125
03-27 18:30 DEBUG CommonBackend: Searching ISOs on USB devices
03-27 18:30 DEBUG CommonBackend: Searching for local CDs
03-27 18:30 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp is a valid Ubuntu CD
03-27 18:30 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
03-27 18:30 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp is a valid Ubuntu CD
03-27 18:30 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
03-27 18:30 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp is a valid Ubuntu Netbook CD
03-27 18:30 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
03-27 18:30 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp is a valid Kubuntu CD
03-27 18:30 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
03-27 18:30 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp is a valid Kubuntu CD
03-27 18:30 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
03-27 18:30 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp is a valid Kubuntu Netbook CD
03-27 18:30 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
03-27 18:30 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp is a valid Xubuntu CD
03-27 18:30 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
03-27 18:30 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp is a valid Xubuntu CD
03-27 18:30 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
03-27 18:30 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp is a valid Mythbuntu CD
03-27 18:30 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
03-27 18:30 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp is a valid Mythbuntu CD
03-27 18:30 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp\casper\filesystem.squashfs
03-27 18:30 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
03-27 18:30 DEBUG Distro: parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-27 18:30 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-27 18:30 DEBUG Distro: wrong arch: i386 != amd64
03-27 18:30 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
03-27 18:30 INFO Distro: Found a valid CD for Ubuntu: D:\
03-27 18:30 INFO root: Running the CD menu...
03-27 18:30 DEBUG WindowsFrontend: __init__...
03-27 18:30 DEBUG WindowsFrontend: on_init...
03-27 18:30 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp\translations, languages=['en_US', 'en']
03-27 18:30 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp\translations, languages=['en_US', 'en']
03-27 18:30 INFO root: === wubi 10.10 rev197 ===
03-27 18:30 DEBUG root: Logfile is c:\docume~1\brando~1.djt\locals~1\temp\wubi-10.10-rev197.log
03-27 18:30 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
03-27 18:30 DEBUG CommonBackend: data_dir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp\data
03-27 18:30 DEBUG WindowsBackend: 7z=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp\bin\7z.exe
03-27 18:30 DEBUG CommonBackend: Fetching basic info...
03-27 18:30 DEBUG CommonBackend: original_exe=D:\wubi.exe
03-27 18:30 DEBUG CommonBackend: platform=win32
03-27 18:30 DEBUG CommonBackend: osname=nt
03-27 18:30 DEBUG CommonBackend: language=en_US
03-27 18:30 DEBUG CommonBackend: encoding=cp1252
03-27 18:30 DEBUG WindowsBackend: arch=i386
03-27 18:30 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp\data\isolist.ini
03-27 18:30 DEBUG CommonBackend: Adding distro Xubuntu-i386
03-27 18:30 DEBUG CommonBackend: Adding distro Xubuntu-amd64
03-27 18:30 DEBUG CommonBackend: Adding distro Kubuntu-amd64
03-27 18:30 DEBUG CommonBackend: Adding distro Mythbuntu-i386
03-27 18:30 DEBUG CommonBackend: Adding distro Ubuntu-amd64
03-27 18:30 DEBUG CommonBackend: Adding distro Ubuntu-i386
03-27 18:30 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
03-27 18:30 DEBUG CommonBackend: Adding distro Kubuntu-i386
03-27 18:30 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
03-27 18:30 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
03-27 18:30 DEBUG WindowsBackend: Fetching host info...
03-27 18:30 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-27 18:30 DEBUG WindowsBackend: windows version=xp
03-27 18:30 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
03-27 18:30 DEBUG WindowsBackend: windows_sp=Service Pack 3
03-27 18:30 DEBUG WindowsBackend: windows_build=2600
03-27 18:30 DEBUG WindowsBackend: gmt=-7
03-27 18:30 DEBUG WindowsBackend: country=US
03-27 18:30 DEBUG WindowsBackend: timezone=America/Denver
03-27 18:30 DEBUG WindowsBackend: windows_username=Brandon
03-27 18:30 DEBUG WindowsBackend: user_full_name=Brandon
03-27 18:30 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Brandon.DJT48W21
03-27 18:30 DEBUG WindowsBackend: windows_language_code=1033
03-27 18:30 DEBUG WindowsBackend: windows_language=English
03-27 18:30 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 3.00GHz
03-27 18:30 DEBUG WindowsBackend: bootloader=xp
03-27 18:30 DEBUG WindowsBackend: system_drive=Drive(C: hd 109931.753906 mb free ntfs)
03-27 18:30 DEBUG WindowsBackend: drive=Drive(C: hd 109931.753906 mb free ntfs)
03-27 18:30 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
03-27 18:30 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
03-27 18:30 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-27 18:30 DEBUG WindowsBackend: uninstaller_path=None
03-27 18:30 DEBUG WindowsBackend: previous_target_dir=None
03-27 18:30 DEBUG WindowsBackend: previous_distro_name=None
03-27 18:30 DEBUG WindowsBackend: keyboard_id=67699721
03-27 18:30 DEBUG WindowsBackend: keyboard_layout=us
03-27 18:30 DEBUG WindowsBackend: keyboard_variant=
03-27 18:30 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
03-27 18:30 DEBUG CommonBackend: locale=en_US.UTF-8
03-27 18:30 DEBUG WindowsBackend: total_memory_mb=1022.98828125
03-27 18:30 DEBUG CommonBackend: Searching ISOs on USB devices
03-27 18:30 DEBUG CommonBackend: Searching for local CDs
03-27 18:30 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu CD
03-27 18:30 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-27 18:30 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu CD
03-27 18:30 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-27 18:30 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu Netbook CD
03-27 18:30 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-27 18:30 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp is a valid Kubuntu CD
03-27 18:30 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-27 18:30 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp is a valid Kubuntu CD
03-27 18:30 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-27 18:30 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp is a valid Kubuntu Netbook CD
03-27 18:30 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-27 18:30 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp is a valid Xubuntu CD
03-27 18:30 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-27 18:30 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp is a valid Xubuntu CD
03-27 18:30 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-27 18:30 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp is a valid Mythbuntu CD
03-27 18:30 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-27 18:30 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp is a valid Mythbuntu CD
03-27 18:30 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-27 18:30 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
03-27 18:30 DEBUG Distro: parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-27 18:30 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-27 18:30 DEBUG Distro: wrong arch: i386 != amd64
03-27 18:30 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
03-27 18:30 INFO Distro: Found a valid CD for Ubuntu: D:\
03-27 18:30 INFO root: Running the CD menu...
03-27 18:30 DEBUG WindowsFrontend: __init__...
03-27 18:30 DEBUG WindowsFrontend: on_init...
03-27 18:30 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp\translations, languages=['en_US', 'en']
03-27 18:30 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl15.tmp\translations, languages=['en_US', 'en']
03-27 18:30 INFO root: CD menu finished
03-27 18:30 INFO root: Running the installer...
03-27 18:30 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp\translations, languages=['en_US', 'en']
03-27 18:30 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp\translations, languages=['en_US', 'en']
03-27 18:31 DEBUG WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=brandon
03-27 18:31 INFO root: Received settings
03-27 18:31 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp\translations, languages=['en_US', 'en']
03-27 18:31 DEBUG TaskList: # Running tasklist...
03-27 18:31 DEBUG TaskList: ## Running select_target_dir...
03-27 18:31 INFO WindowsBackend: Installing into C:\ubuntu
03-27 18:31 DEBUG TaskList: ## Finished select_target_dir
03-27 18:31 DEBUG TaskList: ## Running create_dir_structure...
03-27 18:31 DEBUG CommonBackend: Creating dir C:\ubuntu
03-27 18:31 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
03-27 18:31 DEBUG CommonBackend: Creating dir C:\ubuntu\install
03-27 18:31 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
03-27 18:31 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
03-27 18:31 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-27 18:31 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-27 18:31 DEBUG TaskList: ## Finished create_dir_structure
03-27 18:31 DEBUG TaskList: ## Running uncompress_target_dir...
03-27 18:31 DEBUG TaskList: ## Finished uncompress_target_dir
03-27 18:31 DEBUG TaskList: ## Running create_uninstaller...
03-27 18:31 DEBUG WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-27 18:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-27 18:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-27 18:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-27 18:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-27 18:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-27 18:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-27 18:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-27 18:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-27 18:31 DEBUG TaskList: ## Finished create_uninstaller
03-27 18:31 DEBUG TaskList: ## Running copy_installation_files...
03-27 18:31 DEBUG WindowsBackend: Copying C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-27 18:31 DEBUG WindowsBackend: Copying C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp\winboot -> C:\ubuntu\winboot
03-27 18:31 DEBUG WindowsBackend: Copying C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl14.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-27 18:31 DEBUG TaskList: ## Finished copy_installation_files
03-27 18:31 DEBUG TaskList: ## Running get_iso...
03-27 18:31 DEBUG TaskList: New task copy_file
03-27 18:31 DEBUG TaskList: ### Running copy_file...
03-27 18:32 ERROR TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
03-27 18:32 DEBUG TaskList: # Cancelling tasklist
03-27 18:32 ERROR root: [Errno 13] Permission denied
Traceback (most recent call last):
File "\lib\wubi\application.py", line 56, in run
File "\lib\wubi\application.py", line 128, in select_task
File "\lib\wubi\application.py", line 194, in run_cd_menu
File "\lib\wubi\application.py", line 118, in select_task
File "\lib\wubi\application.py", line 156, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
03-27 18:32 DEBUG TaskList: New task check_iso
03-27 18:32 DEBUG CommonBackend: Searching for local ISO
03-27 18:32 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
03-27 18:32 DEBUG TaskList: New task get_metalink
03-27 18:32 ERROR TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
03-27 18:32 DEBUG TaskList: # Cancelling tasklist
03-27 18:32 DEBUG TaskList: # Finished tasklist
03-27 18:51 INFO root: === wubi 10.10 rev197 ===
03-27 18:51 DEBUG root: Logfile is c:\docume~1\brando~1.djt\locals~1\temp\wubi-10.10-rev197.log
03-27 18:51 DEBUG root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
03-27 18:51 DEBUG CommonBackend: data_dir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp\data
03-27 18:51 DEBUG WindowsBackend: 7z=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp\bin\7z.exe
03-27 18:51 DEBUG CommonBackend: Fetching basic info...
03-27 18:51 DEBUG CommonBackend: original_exe=E:\wubi.exe
03-27 18:51 DEBUG CommonBackend: platform=win32
03-27 18:51 DEBUG CommonBackend: osname=nt
03-27 18:51 DEBUG CommonBackend: language=en_US
03-27 18:51 DEBUG CommonBackend: encoding=cp1252
03-27 18:51 DEBUG WindowsBackend: arch=i386
03-27 18:51 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp\data\isolist.ini
03-27 18:51 DEBUG CommonBackend: Adding distro Xubuntu-i386
03-27 18:51 DEBUG CommonBackend: Adding distro Xubuntu-amd64
03-27 18:51 DEBUG CommonBackend: Adding distro Kubuntu-amd64
03-27 18:51 DEBUG CommonBackend: Adding distro Mythbuntu-i386
03-27 18:51 DEBUG CommonBackend: Adding distro Ubuntu-amd64
03-27 18:51 DEBUG CommonBackend: Adding distro Ubuntu-i386
03-27 18:51 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
03-27 18:51 DEBUG CommonBackend: Adding distro Kubuntu-i386
03-27 18:51 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
03-27 18:51 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
03-27 18:51 DEBUG WindowsBackend: Fetching host info...
03-27 18:51 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-27 18:51 DEBUG WindowsBackend: windows version=xp
03-27 18:51 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
03-27 18:51 DEBUG WindowsBackend: windows_sp=Service Pack 3
03-27 18:51 DEBUG WindowsBackend: windows_build=2600
03-27 18:51 DEBUG WindowsBackend: gmt=-7
03-27 18:51 DEBUG WindowsBackend: country=US
03-27 18:51 DEBUG WindowsBackend: timezone=America/Denver
03-27 18:51 DEBUG WindowsBackend: windows_username=Brandon
03-27 18:51 DEBUG WindowsBackend: user_full_name=Brandon
03-27 18:51 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Brandon.DJT48W21
03-27 18:51 DEBUG WindowsBackend: windows_language_code=1033
03-27 18:51 DEBUG WindowsBackend: windows_language=English
03-27 18:51 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 3.00GHz
03-27 18:51 DEBUG WindowsBackend: bootloader=xp
03-27 18:51 DEBUG WindowsBackend: system_drive=Drive(C: hd 109778.945313 mb free ntfs)
03-27 18:51 DEBUG WindowsBackend: drive=Drive(C: hd 109778.945313 mb free ntfs)
03-27 18:51 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free )
03-27 18:51 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-27 18:51 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-27 18:51 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-27 18:51 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
03-27 18:51 DEBUG WindowsBackend: previous_distro_name=Ubuntu
03-27 18:51 DEBUG WindowsBackend: keyboard_id=67699721
03-27 18:51 DEBUG WindowsBackend: keyboard_layout=us
03-27 18:51 DEBUG WindowsBackend: keyboard_variant=
03-27 18:51 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
03-27 18:51 DEBUG CommonBackend: locale=en_US.UTF-8
03-27 18:51 DEBUG WindowsBackend: total_memory_mb=1022.98828125
03-27 18:51 DEBUG CommonBackend: Searching ISOs on USB devices
03-27 18:51 DEBUG CommonBackend: Searching for local CDs
03-27 18:51 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
03-27 18:51 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
03-27 18:51 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
03-27 18:51 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
03-27 18:51 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu Netbook CD
03-27 18:51 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
03-27 18:51 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
03-27 18:51 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
03-27 18:51 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
03-27 18:51 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
03-27 18:51 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu Netbook CD
03-27 18:51 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
03-27 18:51 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
03-27 18:51 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
03-27 18:51 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
03-27 18:51 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
03-27 18:51 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
03-27 18:51 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
03-27 18:51 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
03-27 18:51 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
03-27 18:51 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
03-27 18:51 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
03-27 18:51 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
03-27 18:51 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
03-27 18:51 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook CD
03-27 18:51 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
03-27 18:51 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
03-27 18:51 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
03-27 18:51 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
03-27 18:51 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
03-27 18:51 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD
03-27 18:51 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
03-27 18:51 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
03-27 18:51 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
03-27 18:51 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
03-27 18:51 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
03-27 18:51 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
03-27 18:51 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
03-27 18:51 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
03-27 18:51 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
03-27 18:51 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
03-27 18:51 DEBUG Distro: parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-27 18:51 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-27 18:51 DEBUG Distro: wrong arch: i386 != amd64
03-27 18:51 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
03-27 18:51 INFO Distro: Found a valid CD for Ubuntu: E:\
03-27 18:51 INFO root: Running the CD menu...
03-27 18:51 DEBUG WindowsFrontend: __init__...
03-27 18:51 DEBUG WindowsFrontend: on_init...
03-27 18:51 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
03-27 18:51 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
03-27 18:51 INFO WindowsFrontend: Operation cancelled
03-27 18:51 DEBUG WindowsFrontend: frontend.quit
03-27 18:51 DEBUG WindowsFrontend: frontend.on_quit
03-27 18:51 DEBUG root: application.on_quit
03-27 18:51 INFO root: sys.exit
04-05 20:15 INFO root: === wubi 10.10 rev197 ===
04-05 20:15 DEBUG root: Logfile is c:\docume~1\brando~1.djt\locals~1\temp\wubi-10.10-rev197.log
04-05 20:15 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
04-05 20:15 DEBUG CommonBackend: data_dir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\data
04-05 20:15 DEBUG WindowsBackend: 7z=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\bin\7z.exe
04-05 20:15 DEBUG CommonBackend: Fetching basic info...
04-05 20:15 DEBUG CommonBackend: original_exe=D:\wubi.exe
04-05 20:15 DEBUG CommonBackend: platform=win32
04-05 20:15 DEBUG CommonBackend: osname=nt
04-05 20:15 DEBUG CommonBackend: language=en_US
04-05 20:15 DEBUG CommonBackend: encoding=cp1252
04-05 20:15 DEBUG WindowsBackend: arch=i386
04-05 20:15 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\data\isolist.ini
04-05 20:15 DEBUG CommonBackend: Adding distro Xubuntu-i386
04-05 20:15 DEBUG CommonBackend: Adding distro Xubuntu-amd64
04-05 20:15 DEBUG CommonBackend: Adding distro Kubuntu-amd64
04-05 20:15 DEBUG CommonBackend: Adding distro Mythbuntu-i386
04-05 20:15 DEBUG CommonBackend: Adding distro Ubuntu-amd64
04-05 20:15 DEBUG CommonBackend: Adding distro Ubuntu-i386
04-05 20:15 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
04-05 20:15 DEBUG CommonBackend: Adding distro Kubuntu-i386
04-05 20:15 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
04-05 20:15 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
04-05 20:15 DEBUG WindowsBackend: Fetching host info...
04-05 20:15 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-05 20:15 DEBUG WindowsBackend: windows version=xp
04-05 20:15 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
04-05 20:15 DEBUG WindowsBackend: windows_sp=Service Pack 3
04-05 20:15 DEBUG WindowsBackend: windows_build=2600
04-05 20:15 DEBUG WindowsBackend: gmt=-7
04-05 20:15 DEBUG WindowsBackend: country=US
04-05 20:15 DEBUG WindowsBackend: timezone=America/Denver
04-05 20:15 DEBUG WindowsBackend: windows_username=Brandon
04-05 20:15 DEBUG WindowsBackend: user_full_name=Brandon
04-05 20:15 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Brandon.DJT48W21
04-05 20:15 DEBUG WindowsBackend: windows_language_code=1033
04-05 20:15 DEBUG WindowsBackend: windows_language=English
04-05 20:15 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 3.00GHz
04-05 20:15 DEBUG WindowsBackend: bootloader=xp
04-05 20:15 DEBUG WindowsBackend: system_drive=Drive(C: hd 110772.648438 mb free ntfs)
04-05 20:15 DEBUG WindowsBackend: drive=Drive(C: hd 110772.648438 mb free ntfs)
04-05 20:15 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-05 20:15 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-05 20:15 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-05 20:15 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-05 20:15 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
04-05 20:15 DEBUG WindowsBackend: previous_distro_name=Ubuntu
04-05 20:15 DEBUG WindowsBackend: keyboard_id=67699721
04-05 20:15 DEBUG WindowsBackend: keyboard_layout=us
04-05 20:15 DEBUG WindowsBackend: keyboard_variant=
04-05 20:15 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
04-05 20:15 DEBUG CommonBackend: locale=en_US.UTF-8
04-05 20:15 DEBUG WindowsBackend: total_memory_mb=1022.98828125
04-05 20:15 DEBUG CommonBackend: Searching ISOs on USB devices
04-05 20:15 DEBUG CommonBackend: Searching for local CDs
04-05 20:15 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp is a valid Ubuntu CD
04-05 20:15 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\casper\filesystem.squashfs
04-05 20:15 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp is a valid Ubuntu CD
04-05 20:15 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\casper\filesystem.squashfs
04-05 20:15 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp is a valid Ubuntu Netbook CD
04-05 20:15 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\casper\filesystem.squashfs
04-05 20:15 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp is a valid Kubuntu CD
04-05 20:15 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\casper\filesystem.squashfs
04-05 20:15 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp is a valid Kubuntu CD
04-05 20:15 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\casper\filesystem.squashfs
04-05 20:15 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp is a valid Kubuntu Netbook CD
04-05 20:15 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\casper\filesystem.squashfs
04-05 20:15 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp is a valid Xubuntu CD
04-05 20:15 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\casper\filesystem.squashfs
04-05 20:15 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp is a valid Xubuntu CD
04-05 20:15 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\casper\filesystem.squashfs
04-05 20:15 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp is a valid Mythbuntu CD
04-05 20:15 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\casper\filesystem.squashfs
04-05 20:15 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp is a valid Mythbuntu CD
04-05 20:15 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\casper\filesystem.squashfs
04-05 20:15 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
04-05 20:16 DEBUG Distro: parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-05 20:16 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-05 20:16 DEBUG Distro: wrong arch: i386 != amd64
04-05 20:16 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
04-05 20:16 INFO Distro: Found a valid CD for Ubuntu: D:\
04-05 20:16 INFO root: Running the CD menu...
04-05 20:16 DEBUG WindowsFrontend: __init__...
04-05 20:16 DEBUG WindowsFrontend: on_init...
04-05 20:16 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\translations, languages=['en_US', 'en']
04-05 20:16 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\translations, languages=['en_US', 'en']
04-05 20:16 INFO root: CD menu finished
04-05 20:16 INFO root: Already installed, running the uninstaller...
04-05 20:16 INFO root: Running the uninstaller...
04-05 20:16 INFO CommonBackend: This is the uninstaller running
04-05 20:16 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\translations, languages=['en_US', 'en']
04-05 20:16 INFO root: Received settings
04-05 20:16 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\translations, languages=['en_US', 'en']
04-05 20:16 DEBUG TaskList: # Running tasklist...
04-05 20:16 DEBUG TaskList: ## Running Backup ISO...
04-05 20:16 DEBUG TaskList: ## Finished Backup ISO
04-05 20:16 DEBUG TaskList: ## Running Remove bootloader entry...
04-05 20:16 ERROR WindowsBackend: Cannot find bcdedit
04-05 20:16 DEBUG WindowsBackend: undo_bootini C:
04-05 20:16 DEBUG WindowsBackend: undo_configsys Drive(C: hd 110772.648438 mb free ntfs)
04-05 20:17 DEBUG TaskList: ## Finished Remove bootloader entry
04-05 20:17 DEBUG TaskList: ## Running Remove target dir...
04-05 20:17 DEBUG CommonBackend: Deleting C:\ubuntu
04-05 20:17 DEBUG TaskList: ## Finished Remove target dir
04-05 20:17 DEBUG TaskList: ## Running Remove registry key...
04-05 20:17 DEBUG TaskList: ## Finished Remove registry key
04-05 20:17 DEBUG TaskList: # Finished tasklist
04-05 20:17 INFO root: Almost finished uninstalling
04-05 20:17 INFO root: Finished uninstallation
04-05 20:17 DEBUG CommonBackend: Fetching basic info...
04-05 20:17 DEBUG CommonBackend: original_exe=D:\wubi.exe
04-05 20:17 DEBUG CommonBackend: platform=win32
04-05 20:17 DEBUG CommonBackend: osname=nt
04-05 20:17 DEBUG WindowsBackend: arch=i386
04-05 20:17 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\data\isolist.ini
04-05 20:17 DEBUG CommonBackend: Adding distro Xubuntu-i386
04-05 20:17 DEBUG CommonBackend: Adding distro Xubuntu-amd64
04-05 20:17 DEBUG CommonBackend: Adding distro Kubuntu-amd64
04-05 20:17 DEBUG CommonBackend: Adding distro Mythbuntu-i386
04-05 20:17 DEBUG CommonBackend: Adding distro Ubuntu-amd64
04-05 20:17 DEBUG CommonBackend: Adding distro Ubuntu-i386
04-05 20:17 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
04-05 20:17 DEBUG CommonBackend: Adding distro Kubuntu-i386
04-05 20:17 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
04-05 20:17 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
04-05 20:17 DEBUG WindowsBackend: Fetching host info...
04-05 20:17 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-05 20:17 DEBUG WindowsBackend: windows version=xp
04-05 20:17 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
04-05 20:17 DEBUG WindowsBackend: windows_sp=Service Pack 3
04-05 20:17 DEBUG WindowsBackend: windows_build=2600
04-05 20:17 DEBUG WindowsBackend: gmt=-7
04-05 20:17 DEBUG WindowsBackend: country=US
04-05 20:17 DEBUG WindowsBackend: timezone=America/Denver
04-05 20:17 DEBUG WindowsBackend: windows_username=Brandon
04-05 20:17 DEBUG WindowsBackend: user_full_name=Brandon
04-05 20:17 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Brandon.DJT48W21
04-05 20:17 DEBUG WindowsBackend: windows_language_code=1033
04-05 20:17 DEBUG WindowsBackend: windows_language=English
04-05 20:17 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 3.00GHz
04-05 20:17 DEBUG WindowsBackend: bootloader=xp
04-05 20:17 DEBUG WindowsBackend: system_drive=Drive(C: hd 110924.527344 mb free ntfs)
04-05 20:17 DEBUG WindowsBackend: drive=Drive(C: hd 110924.527344 mb free ntfs)
04-05 20:17 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-05 20:17 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-05 20:17 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-05 20:17 DEBUG WindowsBackend: uninstaller_path=None
04-05 20:17 DEBUG WindowsBackend: previous_target_dir=None
04-05 20:17 DEBUG WindowsBackend: previous_distro_name=None
04-05 20:17 DEBUG WindowsBackend: keyboard_id=67699721
04-05 20:17 DEBUG WindowsBackend: keyboard_layout=us
04-05 20:17 DEBUG WindowsBackend: keyboard_variant=
04-05 20:17 DEBUG WindowsBackend: total_memory_mb=1022.98828125
04-05 20:17 DEBUG CommonBackend: Searching ISOs on USB devices
04-05 20:17 DEBUG CommonBackend: Searching for local CDs
04-05 20:17 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp is a valid Ubuntu CD
04-05 20:17 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\casper\filesystem.squashfs
04-05 20:17 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp is a valid Ubuntu CD
04-05 20:17 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\casper\filesystem.squashfs
04-05 20:17 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp is a valid Ubuntu Netbook CD
04-05 20:17 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\casper\filesystem.squashfs
04-05 20:17 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp is a valid Kubuntu CD
04-05 20:17 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\casper\filesystem.squashfs
04-05 20:17 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp is a valid Kubuntu CD
04-05 20:17 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\casper\filesystem.squashfs
04-05 20:17 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp is a valid Kubuntu Netbook CD
04-05 20:17 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\casper\filesystem.squashfs
04-05 20:17 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp is a valid Xubuntu CD
04-05 20:17 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\casper\filesystem.squashfs
04-05 20:17 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp is a valid Xubuntu CD
04-05 20:17 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\casper\filesystem.squashfs
04-05 20:17 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp is a valid Mythbuntu CD
04-05 20:17 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\casper\filesystem.squashfs
04-05 20:17 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp is a valid Mythbuntu CD
04-05 20:17 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\casper\filesystem.squashfs
04-05 20:17 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
04-05 20:17 DEBUG Distro: wrong arch: i386 != amd64
04-05 20:17 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
04-05 20:17 INFO Distro: Found a valid CD for Ubuntu: D:\
04-05 20:17 INFO root: Running the CD boot helper...
04-05 20:17 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\translations, languages=['en_US', 'en']
04-05 20:17 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\translations, languages=['en_US', 'en']
04-05 20:17 INFO root: CD boot helper confirmed
04-05 20:17 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\translations, languages=['en_US', 'en']
04-05 20:17 DEBUG TaskList: # Running tasklist...
04-05 20:17 DEBUG TaskList: ## Running select_target_dir...
04-05 20:17 INFO WindowsBackend: Installing into C:\ubuntu
04-05 20:17 DEBUG TaskList: ## Finished select_target_dir
04-05 20:17 DEBUG TaskList: ## Running create_dir_structure...
04-05 20:17 DEBUG CommonBackend: Creating dir C:\ubuntu
04-05 20:17 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
04-05 20:17 DEBUG CommonBackend: Creating dir C:\ubuntu\install
04-05 20:17 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
04-05 20:17 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
04-05 20:17 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-05 20:17 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-05 20:17 DEBUG TaskList: ## Finished create_dir_structure
04-05 20:17 DEBUG TaskList: ## Running uncompress_target_dir...
04-05 20:17 DEBUG TaskList: ## Finished uncompress_target_dir
04-05 20:17 DEBUG TaskList: ## Running create_uninstaller...
04-05 20:17 DEBUG WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-05 20:17 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-05 20:17 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-05 20:17 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-05 20:17 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-05 20:17 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
04-05 20:17 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-05 20:17 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-05 20:17 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-05 20:17 DEBUG TaskList: ## Finished create_uninstaller
04-05 20:17 DEBUG TaskList: ## Running copy_installation_files...
04-05 20:17 DEBUG WindowsBackend: Copying C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-05 20:17 DEBUG WindowsBackend: Copying C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\winboot -> C:\ubuntu\winboot
04-05 20:17 DEBUG WindowsBackend: Copying C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl89.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-05 20:17 DEBUG TaskList: ## Finished copy_installation_files
04-05 20:17 DEBUG TaskList: ## Running use_cd...
04-05 20:17 DEBUG TaskList: New task copy_file
04-05 20:17 DEBUG TaskList: ### Running copy_file...
04-05 20:18 ERROR TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
04-05 20:18 DEBUG TaskList: # Cancelling tasklist
04-05 20:18 ERROR root: [Errno 13] Permission denied
Traceback (most recent call last):
File "\lib\wubi\application.py", line 56, in run
File "\lib\wubi\application.py", line 128, in select_task
File "\lib\wubi\application.py", line 194, in run_cd_menu
File "\lib\wubi\application.py", line 120, in select_task
File "\lib\wubi\application.py", line 217, in run_cd_boot
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
04-05 20:18 DEBUG TaskList: New task check_iso
04-05 20:18 DEBUG TaskList: ## Finished use_cd
04-05 20:18 DEBUG TaskList: # Finished tasklist
04-05 20:18 INFO root: === wubi 10.10 rev197 ===
04-05 20:18 DEBUG root: Logfile is c:\docume~1\brando~1.djt\locals~1\temp\wubi-10.10-rev197.log
04-05 20:18 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
04-05 20:18 DEBUG CommonBackend: data_dir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\data
04-05 20:18 DEBUG WindowsBackend: 7z=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\bin\7z.exe
04-05 20:18 DEBUG CommonBackend: Fetching basic info...
04-05 20:18 DEBUG CommonBackend: original_exe=D:\wubi.exe
04-05 20:18 DEBUG CommonBackend: platform=win32
04-05 20:18 DEBUG CommonBackend: osname=nt
04-05 20:18 DEBUG CommonBackend: language=en_US
04-05 20:18 DEBUG CommonBackend: encoding=cp1252
04-05 20:18 DEBUG WindowsBackend: arch=i386
04-05 20:18 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\data\isolist.ini
04-05 20:18 DEBUG CommonBackend: Adding distro Xubuntu-i386
04-05 20:18 DEBUG CommonBackend: Adding distro Xubuntu-amd64
04-05 20:18 DEBUG CommonBackend: Adding distro Kubuntu-amd64
04-05 20:18 DEBUG CommonBackend: Adding distro Mythbuntu-i386
04-05 20:18 DEBUG CommonBackend: Adding distro Ubuntu-amd64
04-05 20:18 DEBUG CommonBackend: Adding distro Ubuntu-i386
04-05 20:18 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
04-05 20:18 DEBUG CommonBackend: Adding distro Kubuntu-i386
04-05 20:18 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
04-05 20:18 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
04-05 20:18 DEBUG WindowsBackend: Fetching host info...
04-05 20:18 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-05 20:18 DEBUG WindowsBackend: windows version=xp
04-05 20:18 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
04-05 20:18 DEBUG WindowsBackend: windows_sp=Service Pack 3
04-05 20:18 DEBUG WindowsBackend: windows_build=2600
04-05 20:18 DEBUG WindowsBackend: gmt=-7
04-05 20:18 DEBUG WindowsBackend: country=US
04-05 20:18 DEBUG WindowsBackend: timezone=America/Denver
04-05 20:18 DEBUG WindowsBackend: windows_username=Brandon
04-05 20:18 DEBUG WindowsBackend: user_full_name=Brandon
04-05 20:18 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Brandon.DJT48W21
04-05 20:18 DEBUG WindowsBackend: windows_language_code=1033
04-05 20:18 DEBUG WindowsBackend: windows_language=English
04-05 20:18 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 3.00GHz
04-05 20:18 DEBUG WindowsBackend: bootloader=xp
04-05 20:18 DEBUG WindowsBackend: system_drive=Drive(C: hd 110801.945313 mb free ntfs)
04-05 20:18 DEBUG WindowsBackend: drive=Drive(C: hd 110801.945313 mb free ntfs)
04-05 20:18 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-05 20:18 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-05 20:18 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-05 20:18 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-05 20:18 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
04-05 20:18 DEBUG WindowsBackend: previous_distro_name=Ubuntu
04-05 20:18 DEBUG WindowsBackend: keyboard_id=67699721
04-05 20:18 DEBUG WindowsBackend: keyboard_layout=us
04-05 20:18 DEBUG WindowsBackend: keyboard_variant=
04-05 20:18 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
04-05 20:18 DEBUG CommonBackend: locale=en_US.UTF-8
04-05 20:18 DEBUG WindowsBackend: total_memory_mb=1022.98828125
04-05 20:18 DEBUG CommonBackend: Searching ISOs on USB devices
04-05 20:18 DEBUG CommonBackend: Searching for local CDs
04-05 20:18 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp is a valid Ubuntu CD
04-05 20:18 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-05 20:18 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp is a valid Ubuntu CD
04-05 20:18 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-05 20:18 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp is a valid Ubuntu Netbook CD
04-05 20:18 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-05 20:18 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp is a valid Kubuntu CD
04-05 20:18 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-05 20:18 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp is a valid Kubuntu CD
04-05 20:18 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-05 20:18 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp is a valid Kubuntu Netbook CD
04-05 20:18 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-05 20:18 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp is a valid Xubuntu CD
04-05 20:18 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-05 20:18 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp is a valid Xubuntu CD
04-05 20:18 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-05 20:18 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp is a valid Mythbuntu CD
04-05 20:18 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-05 20:18 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp is a valid Mythbuntu CD
04-05 20:18 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-05 20:18 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
04-05 20:18 DEBUG Distro: parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-05 20:18 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-05 20:18 DEBUG Distro: wrong arch: i386 != amd64
04-05 20:18 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
04-05 20:18 INFO Distro: Found a valid CD for Ubuntu: D:\
04-05 20:18 INFO root: Running the CD menu...
04-05 20:18 DEBUG WindowsFrontend: __init__...
04-05 20:18 DEBUG WindowsFrontend: on_init...
04-05 20:18 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\translations, languages=['en_US', 'en']
04-05 20:18 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\translations, languages=['en_US', 'en']
04-05 20:18 INFO root: CD menu finished
04-05 20:18 INFO root: Already installed, running the uninstaller...
04-05 20:18 INFO root: Running the uninstaller...
04-05 20:18 INFO CommonBackend: This is the uninstaller running
04-05 20:18 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\translations, languages=['en_US', 'en']
04-05 20:18 INFO root: Received settings
04-05 20:18 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\translations, languages=['en_US', 'en']
04-05 20:18 DEBUG TaskList: # Running tasklist...
04-05 20:18 DEBUG TaskList: ## Running Backup ISO...
04-05 20:18 DEBUG TaskList: ## Finished Backup ISO
04-05 20:18 DEBUG TaskList: ## Running Remove bootloader entry...
04-05 20:18 ERROR WindowsBackend: Cannot find bcdedit
04-05 20:18 DEBUG WindowsBackend: undo_bootini C:
04-05 20:18 DEBUG WindowsBackend: undo_configsys Drive(C: hd 110801.945313 mb free ntfs)
04-05 20:18 DEBUG TaskList: ## Finished Remove bootloader entry
04-05 20:18 DEBUG TaskList: ## Running Remove target dir...
04-05 20:18 DEBUG CommonBackend: Deleting C:\ubuntu
04-05 20:18 DEBUG TaskList: ## Finished Remove target dir
04-05 20:18 DEBUG TaskList: ## Running Remove registry key...
04-05 20:18 DEBUG TaskList: ## Finished Remove registry key
04-05 20:18 DEBUG TaskList: # Finished tasklist
04-05 20:18 INFO root: Almost finished uninstalling
04-05 20:18 INFO root: Finished uninstallation
04-05 20:18 DEBUG CommonBackend: Fetching basic info...
04-05 20:18 DEBUG CommonBackend: original_exe=D:\wubi.exe
04-05 20:18 DEBUG CommonBackend: platform=win32
04-05 20:18 DEBUG CommonBackend: osname=nt
04-05 20:18 DEBUG WindowsBackend: arch=i386
04-05 20:18 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\data\isolist.ini
04-05 20:18 DEBUG CommonBackend: Adding distro Xubuntu-i386
04-05 20:18 DEBUG CommonBackend: Adding distro Xubuntu-amd64
04-05 20:18 DEBUG CommonBackend: Adding distro Kubuntu-amd64
04-05 20:18 DEBUG CommonBackend: Adding distro Mythbuntu-i386
04-05 20:18 DEBUG CommonBackend: Adding distro Ubuntu-amd64
04-05 20:18 DEBUG CommonBackend: Adding distro Ubuntu-i386
04-05 20:18 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
04-05 20:18 DEBUG CommonBackend: Adding distro Kubuntu-i386
04-05 20:18 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
04-05 20:18 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
04-05 20:18 DEBUG WindowsBackend: Fetching host info...
04-05 20:18 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-05 20:18 DEBUG WindowsBackend: windows version=xp
04-05 20:18 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
04-05 20:18 DEBUG WindowsBackend: windows_sp=Service Pack 3
04-05 20:18 DEBUG WindowsBackend: windows_build=2600
04-05 20:18 DEBUG WindowsBackend: gmt=-7
04-05 20:18 DEBUG WindowsBackend: country=US
04-05 20:18 DEBUG WindowsBackend: timezone=America/Denver
04-05 20:18 DEBUG WindowsBackend: windows_username=Brandon
04-05 20:18 DEBUG WindowsBackend: user_full_name=Brandon
04-05 20:18 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Brandon.DJT48W21
04-05 20:18 DEBUG WindowsBackend: windows_language_code=1033
04-05 20:18 DEBUG WindowsBackend: windows_language=English
04-05 20:18 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 3.00GHz
04-05 20:18 DEBUG WindowsBackend: bootloader=xp
04-05 20:18 DEBUG WindowsBackend: system_drive=Drive(C: hd 110927.507813 mb free ntfs)
04-05 20:18 DEBUG WindowsBackend: drive=Drive(C: hd 110927.507813 mb free ntfs)
04-05 20:18 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-05 20:18 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-05 20:18 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-05 20:18 DEBUG WindowsBackend: uninstaller_path=None
04-05 20:18 DEBUG WindowsBackend: previous_target_dir=None
04-05 20:18 DEBUG WindowsBackend: previous_distro_name=None
04-05 20:18 DEBUG WindowsBackend: keyboard_id=67699721
04-05 20:18 DEBUG WindowsBackend: keyboard_layout=us
04-05 20:18 DEBUG WindowsBackend: keyboard_variant=
04-05 20:18 DEBUG WindowsBackend: total_memory_mb=1022.98828125
04-05 20:18 DEBUG CommonBackend: Searching ISOs on USB devices
04-05 20:18 DEBUG CommonBackend: Searching for local CDs
04-05 20:18 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp is a valid Ubuntu CD
04-05 20:18 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-05 20:18 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp is a valid Ubuntu CD
04-05 20:18 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-05 20:18 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp is a valid Ubuntu Netbook CD
04-05 20:18 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-05 20:18 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp is a valid Kubuntu CD
04-05 20:18 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-05 20:18 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp is a valid Kubuntu CD
04-05 20:18 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-05 20:18 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp is a valid Kubuntu Netbook CD
04-05 20:18 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-05 20:18 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp is a valid Xubuntu CD
04-05 20:18 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-05 20:18 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp is a valid Xubuntu CD
04-05 20:18 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-05 20:18 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp is a valid Mythbuntu CD
04-05 20:18 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-05 20:18 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp is a valid Mythbuntu CD
04-05 20:18 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-05 20:18 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
04-05 20:18 DEBUG Distro: wrong arch: i386 != amd64
04-05 20:18 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
04-05 20:18 INFO Distro: Found a valid CD for Ubuntu: D:\
04-05 20:18 INFO root: Running the CD boot helper...
04-05 20:18 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\translations, languages=['en_US', 'en']
04-05 20:18 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\translations, languages=['en_US', 'en']
04-05 20:19 INFO root: CD boot helper confirmed
04-05 20:19 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\translations, languages=['en_US', 'en']
04-05 20:19 DEBUG TaskList: # Running tasklist...
04-05 20:19 DEBUG TaskList: ## Running select_target_dir...
04-05 20:19 INFO WindowsBackend: Installing into C:\ubuntu
04-05 20:19 DEBUG TaskList: ## Finished select_target_dir
04-05 20:19 DEBUG TaskList: ## Running create_dir_structure...
04-05 20:19 DEBUG CommonBackend: Creating dir C:\ubuntu
04-05 20:19 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
04-05 20:19 DEBUG CommonBackend: Creating dir C:\ubuntu\install
04-05 20:19 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
04-05 20:19 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
04-05 20:19 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-05 20:19 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-05 20:19 DEBUG TaskList: ## Finished create_dir_structure
04-05 20:19 DEBUG TaskList: ## Running uncompress_target_dir...
04-05 20:19 DEBUG TaskList: ## Finished uncompress_target_dir
04-05 20:19 DEBUG TaskList: ## Running create_uninstaller...
04-05 20:19 DEBUG WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-05 20:19 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-05 20:19 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-05 20:19 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-05 20:19 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-05 20:19 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
04-05 20:19 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-05 20:19 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-05 20:19 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-05 20:19 DEBUG TaskList: ## Finished create_uninstaller
04-05 20:19 DEBUG TaskList: ## Running copy_installation_files...
04-05 20:19 DEBUG WindowsBackend: Copying C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-05 20:19 DEBUG WindowsBackend: Copying C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\winboot -> C:\ubuntu\winboot
04-05 20:19 DEBUG WindowsBackend: Copying C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8A.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-05 20:19 DEBUG TaskList: ## Finished copy_installation_files
04-05 20:19 DEBUG TaskList: ## Running use_cd...
04-05 20:19 DEBUG TaskList: New task copy_file
04-05 20:19 DEBUG TaskList: ### Running copy_file...
04-05 20:20 ERROR TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
04-05 20:20 DEBUG TaskList: # Cancelling tasklist
04-05 20:20 ERROR root: [Errno 13] Permission denied
Traceback (most recent call last):
File "\lib\wubi\application.py", line 56, in run
File "\lib\wubi\application.py", line 128, in select_task
File "\lib\wubi\application.py", line 194, in run_cd_menu
File "\lib\wubi\application.py", line 120, in select_task
File "\lib\wubi\application.py", line 217, in run_cd_boot
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
04-05 20:20 DEBUG TaskList: New task check_iso
04-05 20:20 DEBUG TaskList: ## Finished use_cd
04-05 20:20 DEBUG TaskList: # Finished tasklist
04-05 20:37 INFO root: === wubi 10.10 rev197 ===
04-05 20:37 DEBUG root: Logfile is c:\docume~1\brando~1.djt\locals~1\temp\wubi-10.10-rev197.log
04-05 20:37 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
04-05 20:37 DEBUG CommonBackend: data_dir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\data
04-05 20:37 DEBUG WindowsBackend: 7z=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\bin\7z.exe
04-05 20:37 DEBUG CommonBackend: Fetching basic info...
04-05 20:37 DEBUG CommonBackend: original_exe=D:\wubi.exe
04-05 20:37 DEBUG CommonBackend: platform=win32
04-05 20:37 DEBUG CommonBackend: osname=nt
04-05 20:37 DEBUG CommonBackend: language=en_US
04-05 20:37 DEBUG CommonBackend: encoding=cp1252
04-05 20:37 DEBUG WindowsBackend: arch=i386
04-05 20:37 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\data\isolist.ini
04-05 20:37 DEBUG CommonBackend: Adding distro Xubuntu-i386
04-05 20:37 DEBUG CommonBackend: Adding distro Xubuntu-amd64
04-05 20:37 DEBUG CommonBackend: Adding distro Kubuntu-amd64
04-05 20:37 DEBUG CommonBackend: Adding distro Mythbuntu-i386
04-05 20:37 DEBUG CommonBackend: Adding distro Ubuntu-amd64
04-05 20:37 DEBUG CommonBackend: Adding distro Ubuntu-i386
04-05 20:37 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
04-05 20:37 DEBUG CommonBackend: Adding distro Kubuntu-i386
04-05 20:37 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
04-05 20:37 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
04-05 20:37 DEBUG WindowsBackend: Fetching host info...
04-05 20:37 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-05 20:37 DEBUG WindowsBackend: windows version=xp
04-05 20:37 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
04-05 20:37 DEBUG WindowsBackend: windows_sp=Service Pack 3
04-05 20:37 DEBUG WindowsBackend: windows_build=2600
04-05 20:37 DEBUG WindowsBackend: gmt=-7
04-05 20:37 DEBUG WindowsBackend: country=US
04-05 20:37 DEBUG WindowsBackend: timezone=America/Denver
04-05 20:37 DEBUG WindowsBackend: windows_username=Brandon
04-05 20:37 DEBUG WindowsBackend: user_full_name=Brandon
04-05 20:37 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Brandon.DJT48W21
04-05 20:37 DEBUG WindowsBackend: windows_language_code=1033
04-05 20:37 DEBUG WindowsBackend: windows_language=English
04-05 20:37 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 3.00GHz
04-05 20:37 DEBUG WindowsBackend: bootloader=xp
04-05 20:37 DEBUG WindowsBackend: system_drive=Drive(C: hd 110796.183594 mb free ntfs)
04-05 20:37 DEBUG WindowsBackend: drive=Drive(C: hd 110796.183594 mb free ntfs)
04-05 20:37 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-05 20:37 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-05 20:37 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-05 20:37 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-05 20:37 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
04-05 20:37 DEBUG WindowsBackend: previous_distro_name=Ubuntu
04-05 20:37 DEBUG WindowsBackend: keyboard_id=67699721
04-05 20:37 DEBUG WindowsBackend: keyboard_layout=us
04-05 20:37 DEBUG WindowsBackend: keyboard_variant=
04-05 20:37 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
04-05 20:37 DEBUG CommonBackend: locale=en_US.UTF-8
04-05 20:37 DEBUG WindowsBackend: total_memory_mb=1022.98828125
04-05 20:37 DEBUG CommonBackend: Searching ISOs on USB devices
04-05 20:37 DEBUG CommonBackend: Searching for local CDs
04-05 20:37 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp is a valid Ubuntu CD
04-05 20:37 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-05 20:37 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp is a valid Ubuntu CD
04-05 20:37 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-05 20:37 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp is a valid Ubuntu Netbook CD
04-05 20:37 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-05 20:37 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp is a valid Kubuntu CD
04-05 20:37 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-05 20:37 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp is a valid Kubuntu CD
04-05 20:37 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-05 20:37 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp is a valid Kubuntu Netbook CD
04-05 20:37 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-05 20:37 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp is a valid Xubuntu CD
04-05 20:37 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-05 20:37 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp is a valid Xubuntu CD
04-05 20:37 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-05 20:37 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp is a valid Mythbuntu CD
04-05 20:37 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-05 20:37 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp is a valid Mythbuntu CD
04-05 20:37 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-05 20:37 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
04-05 20:37 DEBUG Distro: parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-05 20:37 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-05 20:37 DEBUG Distro: wrong arch: i386 != amd64
04-05 20:37 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
04-05 20:37 INFO Distro: Found a valid CD for Ubuntu: D:\
04-05 20:37 INFO root: Running the CD menu...
04-05 20:37 DEBUG WindowsFrontend: __init__...
04-05 20:37 DEBUG WindowsFrontend: on_init...
04-05 20:37 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\translations, languages=['en_US', 'en']
04-05 20:37 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\translations, languages=['en_US', 'en']
04-05 20:37 INFO root: CD menu finished
04-05 20:37 INFO root: Already installed, running the uninstaller...
04-05 20:37 INFO root: Running the uninstaller...
04-05 20:37 INFO CommonBackend: This is the uninstaller running
04-05 20:37 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\translations, languages=['en_US', 'en']
04-05 20:37 INFO root: Received settings
04-05 20:37 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\translations, languages=['en_US', 'en']
04-05 20:37 DEBUG TaskList: # Running tasklist...
04-05 20:37 DEBUG TaskList: ## Running Backup ISO...
04-05 20:37 DEBUG TaskList: ## Finished Backup ISO
04-05 20:37 DEBUG TaskList: ## Running Remove bootloader entry...
04-05 20:37 ERROR WindowsBackend: Cannot find bcdedit
04-05 20:37 DEBUG WindowsBackend: undo_bootini C:
04-05 20:37 DEBUG WindowsBackend: undo_configsys Drive(C: hd 110796.183594 mb free ntfs)
04-05 20:37 DEBUG TaskList: ## Finished Remove bootloader entry
04-05 20:37 DEBUG TaskList: ## Running Remove target dir...
04-05 20:37 DEBUG CommonBackend: Deleting C:\ubuntu
04-05 20:37 DEBUG TaskList: ## Finished Remove target dir
04-05 20:37 DEBUG TaskList: ## Running Remove registry key...
04-05 20:37 DEBUG TaskList: ## Finished Remove registry key
04-05 20:37 DEBUG TaskList: # Finished tasklist
04-05 20:37 INFO root: Almost finished uninstalling
04-05 20:37 INFO root: Finished uninstallation
04-05 20:37 DEBUG CommonBackend: Fetching basic info...
04-05 20:37 DEBUG CommonBackend: original_exe=D:\wubi.exe
04-05 20:37 DEBUG CommonBackend: platform=win32
04-05 20:37 DEBUG CommonBackend: osname=nt
04-05 20:37 DEBUG WindowsBackend: arch=i386
04-05 20:37 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\data\isolist.ini
04-05 20:37 DEBUG CommonBackend: Adding distro Xubuntu-i386
04-05 20:37 DEBUG CommonBackend: Adding distro Xubuntu-amd64
04-05 20:37 DEBUG CommonBackend: Adding distro Kubuntu-amd64
04-05 20:37 DEBUG CommonBackend: Adding distro Mythbuntu-i386
04-05 20:37 DEBUG CommonBackend: Adding distro Ubuntu-amd64
04-05 20:37 DEBUG CommonBackend: Adding distro Ubuntu-i386
04-05 20:37 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
04-05 20:37 DEBUG CommonBackend: Adding distro Kubuntu-i386
04-05 20:37 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
04-05 20:37 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
04-05 20:37 DEBUG WindowsBackend: Fetching host info...
04-05 20:37 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-05 20:37 DEBUG WindowsBackend: windows version=xp
04-05 20:37 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
04-05 20:37 DEBUG WindowsBackend: windows_sp=Service Pack 3
04-05 20:37 DEBUG WindowsBackend: windows_build=2600
04-05 20:37 DEBUG WindowsBackend: gmt=-7
04-05 20:37 DEBUG WindowsBackend: country=US
04-05 20:37 DEBUG WindowsBackend: timezone=America/Denver
04-05 20:37 DEBUG WindowsBackend: windows_username=Brandon
04-05 20:37 DEBUG WindowsBackend: user_full_name=Brandon
04-05 20:37 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Brandon.DJT48W21
04-05 20:37 DEBUG WindowsBackend: windows_language_code=1033
04-05 20:37 DEBUG WindowsBackend: windows_language=English
04-05 20:37 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 3.00GHz
04-05 20:37 DEBUG WindowsBackend: bootloader=xp
04-05 20:37 DEBUG WindowsBackend: system_drive=Drive(C: hd 110921.703125 mb free ntfs)
04-05 20:37 DEBUG WindowsBackend: drive=Drive(C: hd 110921.703125 mb free ntfs)
04-05 20:37 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-05 20:37 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-05 20:37 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-05 20:37 DEBUG WindowsBackend: uninstaller_path=None
04-05 20:37 DEBUG WindowsBackend: previous_target_dir=None
04-05 20:37 DEBUG WindowsBackend: previous_distro_name=None
04-05 20:37 DEBUG WindowsBackend: keyboard_id=67699721
04-05 20:37 DEBUG WindowsBackend: keyboard_layout=us
04-05 20:37 DEBUG WindowsBackend: keyboard_variant=
04-05 20:37 DEBUG WindowsBackend: total_memory_mb=1022.98828125
04-05 20:37 DEBUG CommonBackend: Searching ISOs on USB devices
04-05 20:37 DEBUG CommonBackend: Searching for local CDs
04-05 20:37 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp is a valid Ubuntu CD
04-05 20:37 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-05 20:37 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp is a valid Ubuntu CD
04-05 20:37 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-05 20:37 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp is a valid Ubuntu Netbook CD
04-05 20:37 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-05 20:37 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp is a valid Kubuntu CD
04-05 20:37 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-05 20:37 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp is a valid Kubuntu CD
04-05 20:37 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-05 20:37 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp is a valid Kubuntu Netbook CD
04-05 20:37 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-05 20:37 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp is a valid Xubuntu CD
04-05 20:37 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-05 20:37 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp is a valid Xubuntu CD
04-05 20:37 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-05 20:37 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp is a valid Mythbuntu CD
04-05 20:37 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-05 20:37 DEBUG Distro: checking whether C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp is a valid Mythbuntu CD
04-05 20:37 DEBUG Distro: does not contain C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-05 20:37 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
04-05 20:37 DEBUG Distro: wrong arch: i386 != amd64
04-05 20:37 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
04-05 20:37 INFO Distro: Found a valid CD for Ubuntu: D:\
04-05 20:37 INFO root: Running the installer...
04-05 20:37 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\translations, languages=['en_US', 'en']
04-05 20:37 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\translations, languages=['en_US', 'en']
04-05 20:37 DEBUG WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=brandon
04-05 20:37 INFO root: Received settings
04-05 20:37 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\translations, languages=['en_US', 'en']
04-05 20:37 DEBUG TaskList: # Running tasklist...
04-05 20:37 DEBUG TaskList: ## Running select_target_dir...
04-05 20:37 INFO WindowsBackend: Installing into C:\ubuntu
04-05 20:37 DEBUG TaskList: ## Finished select_target_dir
04-05 20:37 DEBUG TaskList: ## Running create_dir_structure...
04-05 20:37 DEBUG CommonBackend: Creating dir C:\ubuntu
04-05 20:37 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
04-05 20:37 DEBUG CommonBackend: Creating dir C:\ubuntu\install
04-05 20:37 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
04-05 20:37 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
04-05 20:37 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-05 20:37 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-05 20:37 DEBUG TaskList: ## Finished create_dir_structure
04-05 20:37 DEBUG TaskList: ## Running uncompress_target_dir...
04-05 20:37 DEBUG TaskList: ## Finished uncompress_target_dir
04-05 20:37 DEBUG TaskList: ## Running create_uninstaller...
04-05 20:37 DEBUG WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-05 20:37 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-05 20:37 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-05 20:37 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-05 20:37 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-05 20:37 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
04-05 20:37 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-05 20:37 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-05 20:37 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-05 20:37 DEBUG TaskList: ## Finished create_uninstaller
04-05 20:37 DEBUG TaskList: ## Running copy_installation_files...
04-05 20:37 DEBUG WindowsBackend: Copying C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-05 20:37 DEBUG WindowsBackend: Copying C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\winboot -> C:\ubuntu\winboot
04-05 20:37 DEBUG WindowsBackend: Copying C:\DOCUME~1\BRANDO~1.DJT\LOCALS~1\Temp\pyl8B.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-05 20:37 DEBUG TaskList: ## Finished copy_installation_files
04-05 20:37 DEBUG TaskList: ## Running get_iso...
04-05 20:37 DEBUG TaskList: New task copy_file
04-05 20:37 DEBUG TaskList: ### Running copy_file...
04-05 20:38 ERROR TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
04-05 20:38 DEBUG TaskList: # Cancelling tasklist
04-05 20:38 ERROR root: [Errno 13] Permission denied
Traceback (most recent call last):
File "\lib\wubi\application.py", line 56, in run
File "\lib\wubi\application.py", line 128, in select_task
File "\lib\wubi\application.py", line 194, in run_cd_menu
File "\lib\wubi\application.py", line 118, in select_task
File "\lib\wubi\application.py", line 156, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
04-05 20:38 DEBUG TaskList: New task check_iso
04-05 20:38 DEBUG CommonBackend: Searching for local ISO
04-05 20:38 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
04-05 20:38 DEBUG TaskList: New task get_metalink
04-05 20:38 ERROR TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
04-05 20:38 DEBUG TaskList: # Cancelling tasklist
04-05 20:38 DEBUG TaskList: # Finished tasklist

---

