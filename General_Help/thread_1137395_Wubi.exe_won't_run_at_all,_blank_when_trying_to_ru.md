---
title: "Wubi.exe won't run at all, blank when trying to run it"
date: 2009-04-25
forum: General Help
---

### Post by eBrY on 2009-04-25
I don't know what the hell happened, I had a previous wubi install from within XP, and uninstalled it, and now trying to install 9.04. But running Wubi.exe in all environments, I tried running it from a burnt CD, i tried running it by itself with and without ISO file in the same folder. In all cases, Wubi.exe is irresponsive. It doesn't have the menu or any prompt when running Wubi.exe I haven't found any posts about this problem. What can be causing wubi.exe to not load anything at all? Please help, thanks. I quad boot windows 7 (64-bit), XP (32-Bit), Mac OS X and now Ubuntu, I know theres nothing wrong with the different OSes, but I even tried to run wubi.exe in Windows 7 just to see if it would load, but it also didn't load anything in Windows 7 on CD, with and without the ISO in the same folder. I'm trying to install ubuntu 9.04 using winXP. What can be causing the wubi.exe to not run on my computer at all? I haven't seen this problem documented. Please help me fix this, thanks.

---

### Post by lisati on 2009-04-25
There seem to be some issues with Wubi these days, I even ran into problems myself on one machine....

A couple of discussion about it can be found here:
[http://ubuntuforums.org/showthread.php?t=1136534](http://ubuntuforums.org/showthread.php?t=1136534)
[http://ubuntuforums.org/showthread.php?p=7142388](http://ubuntuforums.org/showthread.php?p=7142388)

---

### Post by eBrY on 2009-04-25
Hi I've read those replies, but there is no solution. Actually, for me wubi.exe at first did run, but I was running it with the Ubuntu files extracted in a folder. This method didn't work for the previous version of Wubi, it would just close out before writing all the files. I tried it with this latest version of Wubi it did load the menu, now after a failed install it doesn't run anymore. The funny thing is i have win xp and 7 and Wubi won't run in windows 7 either with a different new environment. I also tried creating a new partition of Ubuntu and tried to install it from booting into the CD, but none of the menu options work except for selecting language. Presssing install option or the run from cd version doesn't work. only booting to primary OS menu the last option has any effect. Why is this happening please let me know thanks.

> **lisati said:**
> There seem to be some issues with Wubi these days, I even ran into problems myself on one machine....

A couple of discussion about it can be found here:
[http://ubuntuforums.org/showthread.php?t=1136534](http://ubuntuforums.org/showthread.php?t=1136534)
[http://ubuntuforums.org/showthread.php?p=7142388](http://ubuntuforums.org/showthread.php?p=7142388)

---

### Post by lisati on 2009-04-25
When I ran into trouble with Wubi I eventually skipped the Wubi and did a regular install by booting from the CD. 

I'm not sure how far away a solution is, and, other than making a note here in the forums where someone might be able to suggest something, I'm not sure what to advise.

---

### Post by eBrY on 2009-04-25
Thanks for your reply. I'm just wondering why I can't do a normal ubuntu install by booting with te CD. How do I manually enter the string to boot from the boot: prompt? Maybe I can get it to work that way, because the 1st 4 options does nothing when I press enter. I can't install through Wubi or normal method of installation at startup. Maybe my disc is defective?

> **lisati said:**
> When I ran into trouble with Wubi I eventually skipped the Wubi and did a regular install by booting from the CD. 

I'm not sure how far away a solution is, and, other than making a note here in the forums where someone might be able to suggest something, I'm not sure what to advise.

---

### Post by legendbb on 2009-08-17
I have the same issue under fresh installed Windows XP sp3.
Actually previous installation (before I cleaned up HD and load factory default XP) halt in the stage of building ISO.

No log file in ...\temp. just pyl#.exe, # increments with installation attempts.

Some threads recommended nonASCII volume name, that's definitely not my case.

Thanks,

---

### Post by adamwbb on 2011-09-06
same problem here i cant open wubi.
this ones 11.04 the latest version.
it pops up in the processes and dissapears quickly. the log is here below (i couldnt attach it its too big)
 
```
 
09-06 20:01 INFO   root: === wubi 11.04 rev211 ===
09-06 20:01 DEBUG  root: Logfile is c:\windows\temp\wubi-11.04-rev211.log
09-06 20:01 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
09-06 20:01 DEBUG  CommonBackend: data_dir=C:\WINDOWS\TEMP\pyl3.tmp\data
09-06 20:01 DEBUG  WindowsBackend: 7z=C:\WINDOWS\TEMP\pyl3.tmp\bin\7z.exe
09-06 20:01 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
09-06 20:01 DEBUG  CommonBackend: Fetching basic info...
09-06 20:01 DEBUG  CommonBackend: original_exe=D:\wubi.exe
09-06 20:01 DEBUG  CommonBackend: platform=win32
09-06 20:01 DEBUG  CommonBackend: osname=nt
09-06 20:01 DEBUG  CommonBackend: language=en_US
09-06 20:01 DEBUG  CommonBackend: encoding=cp1252
09-06 20:01 DEBUG  WindowsBackend: arch=amd64
09-06 20:01 DEBUG  CommonBackend: Parsing isolist=C:\WINDOWS\TEMP\pyl3.tmp\data\isolist.ini
09-06 20:01 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-06 20:01 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-06 20:01 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-06 20:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-06 20:01 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-06 20:01 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-06 20:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-06 20:01 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-06 20:01 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-06 20:01 DEBUG  WindowsBackend: Fetching host info...
09-06 20:01 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-06 20:01 DEBUG  WindowsBackend: windows version=xp
09-06 20:01 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
09-06 20:01 DEBUG  WindowsBackend: windows_sp=Service Pack 3
09-06 20:01 DEBUG  WindowsBackend: windows_build=2600
09-06 20:01 DEBUG  WindowsBackend: gmt=-5
09-06 20:01 DEBUG  WindowsBackend: country=US
09-06 20:01 DEBUG  WindowsBackend: timezone=America/New_York
09-06 20:01 ERROR  root: 'NoneType' object has no attribute 'decode'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\backends\common\backend.py", line 154, in fetch_basic_info
  File "\lib\wubi\backends\win32\backend.py", line 63, in fetch_host_info
  File "\lib\wubi\backends\win32\backend.py", line 360, in get_windows_username
AttributeError: 'NoneType' object has no attribute 'decode'
09-06 20:04 INFO   root: === wubi 11.04 rev211 ===
09-06 20:04 DEBUG  root: Logfile is c:\windows\temp\wubi-11.04-rev211.log
09-06 20:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
09-06 20:04 DEBUG  CommonBackend: data_dir=C:\WINDOWS\TEMP\pyl4.tmp\data
09-06 20:04 DEBUG  WindowsBackend: 7z=C:\WINDOWS\TEMP\pyl4.tmp\bin\7z.exe
09-06 20:04 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
09-06 20:04 DEBUG  CommonBackend: Fetching basic info...
09-06 20:04 DEBUG  CommonBackend: original_exe=D:\wubi.exe
09-06 20:04 DEBUG  CommonBackend: platform=win32
09-06 20:04 DEBUG  CommonBackend: osname=nt
09-06 20:04 DEBUG  CommonBackend: language=en_US
09-06 20:04 DEBUG  CommonBackend: encoding=cp1252
09-06 20:04 DEBUG  WindowsBackend: arch=amd64
09-06 20:04 DEBUG  CommonBackend: Parsing isolist=C:\WINDOWS\TEMP\pyl4.tmp\data\isolist.ini
09-06 20:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-06 20:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-06 20:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-06 20:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-06 20:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-06 20:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-06 20:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-06 20:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-06 20:04 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-06 20:04 DEBUG  WindowsBackend: Fetching host info...
09-06 20:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-06 20:04 DEBUG  WindowsBackend: windows version=xp
09-06 20:04 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
09-06 20:04 DEBUG  WindowsBackend: windows_sp=Service Pack 3
09-06 20:04 DEBUG  WindowsBackend: windows_build=2600
09-06 20:04 DEBUG  WindowsBackend: gmt=-5
09-06 20:04 DEBUG  WindowsBackend: country=US
09-06 20:04 DEBUG  WindowsBackend: timezone=America/New_York
09-06 20:04 ERROR  root: 'NoneType' object has no attribute 'decode'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\backends\common\backend.py", line 154, in fetch_basic_info
  File "\lib\wubi\backends\win32\backend.py", line 63, in fetch_host_info
  File "\lib\wubi\backends\win32\backend.py", line 360, in get_windows_username
AttributeError: 'NoneType' object has no attribute 'decode'
09-06 20:04 INFO   root: === wubi 11.04 rev211 ===
09-06 20:04 DEBUG  root: Logfile is c:\windows\temp\wubi-11.04-rev211.log
09-06 20:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
09-06 20:04 DEBUG  CommonBackend: data_dir=C:\WINDOWS\TEMP\pyl5.tmp\data
09-06 20:04 DEBUG  WindowsBackend: 7z=C:\WINDOWS\TEMP\pyl5.tmp\bin\7z.exe
09-06 20:04 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
09-06 20:04 DEBUG  CommonBackend: Fetching basic info...
09-06 20:04 DEBUG  CommonBackend: original_exe=D:\wubi.exe
09-06 20:04 DEBUG  CommonBackend: platform=win32
09-06 20:04 DEBUG  CommonBackend: osname=nt
09-06 20:04 DEBUG  CommonBackend: language=en_US
09-06 20:04 DEBUG  CommonBackend: encoding=cp1252
09-06 20:04 DEBUG  WindowsBackend: arch=amd64
09-06 20:04 DEBUG  CommonBackend: Parsing isolist=C:\WINDOWS\TEMP\pyl5.tmp\data\isolist.ini
09-06 20:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-06 20:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-06 20:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-06 20:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-06 20:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-06 20:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-06 20:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-06 20:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-06 20:04 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-06 20:04 DEBUG  WindowsBackend: Fetching host info...
09-06 20:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-06 20:04 DEBUG  WindowsBackend: windows version=xp
09-06 20:04 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
09-06 20:04 DEBUG  WindowsBackend: windows_sp=Service Pack 3
09-06 20:04 DEBUG  WindowsBackend: windows_build=2600
09-06 20:04 DEBUG  WindowsBackend: gmt=-5
09-06 20:04 DEBUG  WindowsBackend: country=US
09-06 20:04 DEBUG  WindowsBackend: timezone=America/New_York
09-06 20:04 ERROR  root: 'NoneType' object has no attribute 'decode'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\backends\common\backend.py", line 154, in fetch_basic_info
  File "\lib\wubi\backends\win32\backend.py", line 63, in fetch_host_info
  File "\lib\wubi\backends\win32\backend.py", line 360, in get_windows_username
AttributeError: 'NoneType' object has no attribute 'decode'
09-06 20:04 INFO   root: === wubi 11.04 rev211 ===
09-06 20:04 DEBUG  root: Logfile is c:\windows\temp\wubi-11.04-rev211.log
09-06 20:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
09-06 20:04 DEBUG  CommonBackend: data_dir=C:\WINDOWS\TEMP\pyl6.tmp\data
09-06 20:04 DEBUG  WindowsBackend: 7z=C:\WINDOWS\TEMP\pyl6.tmp\bin\7z.exe
09-06 20:04 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
09-06 20:04 DEBUG  CommonBackend: Fetching basic info...
09-06 20:04 DEBUG  CommonBackend: original_exe=D:\wubi.exe
09-06 20:04 DEBUG  CommonBackend: platform=win32
09-06 20:04 DEBUG  CommonBackend: osname=nt
09-06 20:04 DEBUG  CommonBackend: language=en_US
09-06 20:04 DEBUG  CommonBackend: encoding=cp1252
09-06 20:04 DEBUG  WindowsBackend: arch=amd64
09-06 20:04 DEBUG  CommonBackend: Parsing isolist=C:\WINDOWS\TEMP\pyl6.tmp\data\isolist.ini
09-06 20:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-06 20:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-06 20:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-06 20:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-06 20:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-06 20:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-06 20:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-06 20:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-06 20:04 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-06 20:04 DEBUG  WindowsBackend: Fetching host info...
09-06 20:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-06 20:04 DEBUG  WindowsBackend: windows version=xp
09-06 20:04 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
09-06 20:04 DEBUG  WindowsBackend: windows_sp=Service Pack 3
09-06 20:04 DEBUG  WindowsBackend: windows_build=2600
09-06 20:04 DEBUG  WindowsBackend: gmt=-5
09-06 20:04 DEBUG  WindowsBackend: country=US
09-06 20:04 DEBUG  WindowsBackend: timezone=America/New_York
09-06 20:04 ERROR  root: 'NoneType' object has no attribute 'decode'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\backends\common\backend.py", line 154, in fetch_basic_info
  File "\lib\wubi\backends\win32\backend.py", line 63, in fetch_host_info
  File "\lib\wubi\backends\win32\backend.py", line 360, in get_windows_username
AttributeError: 'NoneType' object has no attribute 'decode'
09-06 20:04 INFO   root: === wubi 11.04 rev211 ===
09-06 20:04 DEBUG  root: Logfile is c:\windows\temp\wubi-11.04-rev211.log
09-06 20:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
09-06 20:04 DEBUG  CommonBackend: data_dir=C:\WINDOWS\TEMP\pyl7.tmp\data
09-06 20:04 DEBUG  WindowsBackend: 7z=C:\WINDOWS\TEMP\pyl7.tmp\bin\7z.exe
09-06 20:04 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
09-06 20:04 DEBUG  CommonBackend: Fetching basic info...
09-06 20:04 DEBUG  CommonBackend: original_exe=D:\wubi.exe
09-06 20:04 DEBUG  CommonBackend: platform=win32
09-06 20:04 DEBUG  CommonBackend: osname=nt
09-06 20:04 DEBUG  CommonBackend: language=en_US
09-06 20:04 DEBUG  CommonBackend: encoding=cp1252
09-06 20:04 DEBUG  WindowsBackend: arch=amd64
09-06 20:04 DEBUG  CommonBackend: Parsing isolist=C:\WINDOWS\TEMP\pyl7.tmp\data\isolist.ini
09-06 20:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-06 20:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-06 20:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-06 20:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-06 20:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-06 20:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-06 20:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-06 20:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-06 20:04 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-06 20:04 DEBUG  WindowsBackend: Fetching host info...
09-06 20:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-06 20:04 DEBUG  WindowsBackend: windows version=xp
09-06 20:04 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
09-06 20:04 DEBUG  WindowsBackend: windows_sp=Service Pack 3
09-06 20:04 DEBUG  WindowsBackend: windows_build=2600
09-06 20:04 DEBUG  WindowsBackend: gmt=-5
09-06 20:04 DEBUG  WindowsBackend: country=US
09-06 20:04 DEBUG  WindowsBackend: timezone=America/New_York
09-06 20:04 ERROR  root: 'NoneType' object has no attribute 'decode'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\backends\common\backend.py", line 154, in fetch_basic_info
  File "\lib\wubi\backends\win32\backend.py", line 63, in fetch_host_info
  File "\lib\wubi\backends\win32\backend.py", line 360, in get_windows_username
AttributeError: 'NoneType' object has no attribute 'decode'
09-06 20:05 INFO   root: === wubi 11.04 rev211 ===
09-06 20:05 DEBUG  root: Logfile is c:\windows\temp\wubi-11.04-rev211.log
09-06 20:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
09-06 20:05 DEBUG  CommonBackend: data_dir=C:\WINDOWS\TEMP\pyl8.tmp\data
09-06 20:05 DEBUG  WindowsBackend: 7z=C:\WINDOWS\TEMP\pyl8.tmp\bin\7z.exe
09-06 20:05 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
09-06 20:05 DEBUG  CommonBackend: Fetching basic info...
09-06 20:05 DEBUG  CommonBackend: original_exe=D:\wubi.exe
09-06 20:05 DEBUG  CommonBackend: platform=win32
09-06 20:05 DEBUG  CommonBackend: osname=nt
09-06 20:05 DEBUG  CommonBackend: language=en_US
09-06 20:05 DEBUG  CommonBackend: encoding=cp1252
09-06 20:05 DEBUG  WindowsBackend: arch=amd64
09-06 20:05 DEBUG  CommonBackend: Parsing isolist=C:\WINDOWS\TEMP\pyl8.tmp\data\isolist.ini
09-06 20:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-06 20:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-06 20:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-06 20:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-06 20:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-06 20:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-06 20:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-06 20:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-06 20:05 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-06 20:05 DEBUG  WindowsBackend: Fetching host info...
09-06 20:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-06 20:05 DEBUG  WindowsBackend: windows version=xp
09-06 20:05 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
09-06 20:05 DEBUG  WindowsBackend: windows_sp=Service Pack 3
09-06 20:05 DEBUG  WindowsBackend: windows_build=2600
09-06 20:05 DEBUG  WindowsBackend: gmt=-5
09-06 20:05 DEBUG  WindowsBackend: country=US
09-06 20:05 DEBUG  WindowsBackend: timezone=America/New_York
09-06 20:05 ERROR  root: 'NoneType' object has no attribute 'decode'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\backends\common\backend.py", line 154, in fetch_basic_info
  File "\lib\wubi\backends\win32\backend.py", line 63, in fetch_host_info
  File "\lib\wubi\backends\win32\backend.py", line 360, in get_windows_username
AttributeError: 'NoneType' object has no attribute 'decode'
09-06 20:05 INFO   root: === wubi 11.04 rev211 ===
09-06 20:05 DEBUG  root: Logfile is c:\windows\temp\wubi-11.04-rev211.log
09-06 20:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
09-06 20:05 DEBUG  CommonBackend: data_dir=C:\WINDOWS\TEMP\pyl9.tmp\data
09-06 20:05 DEBUG  WindowsBackend: 7z=C:\WINDOWS\TEMP\pyl9.tmp\bin\7z.exe
09-06 20:05 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
09-06 20:05 DEBUG  CommonBackend: Fetching basic info...
09-06 20:05 DEBUG  CommonBackend: original_exe=D:\wubi.exe
09-06 20:05 DEBUG  CommonBackend: platform=win32
09-06 20:05 DEBUG  CommonBackend: osname=nt
09-06 20:05 DEBUG  CommonBackend: language=en_US
09-06 20:05 DEBUG  CommonBackend: encoding=cp1252
09-06 20:05 DEBUG  WindowsBackend: arch=amd64
09-06 20:05 DEBUG  CommonBackend: Parsing isolist=C:\WINDOWS\TEMP\pyl9.tmp\data\isolist.ini
09-06 20:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-06 20:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-06 20:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-06 20:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-06 20:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-06 20:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-06 20:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-06 20:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-06 20:05 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-06 20:05 DEBUG  WindowsBackend: Fetching host info...
09-06 20:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-06 20:05 DEBUG  WindowsBackend: windows version=xp
09-06 20:05 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
09-06 20:05 DEBUG  WindowsBackend: windows_sp=Service Pack 3
09-06 20:05 DEBUG  WindowsBackend: windows_build=2600
09-06 20:05 DEBUG  WindowsBackend: gmt=-5
09-06 20:05 DEBUG  WindowsBackend: country=US
09-06 20:05 DEBUG  WindowsBackend: timezone=America/New_York
09-06 20:05 ERROR  root: 'NoneType' object has no attribute 'decode'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\backends\common\backend.py", line 154, in fetch_basic_info
  File "\lib\wubi\backends\win32\backend.py", line 63, in fetch_host_info
  File "\lib\wubi\backends\win32\backend.py", line 360, in get_windows_username
AttributeError: 'NoneType' object has no attribute 'decode'
09-06 20:06 INFO   root: === wubi 11.04 rev211 ===
09-06 20:06 DEBUG  root: Logfile is c:\windows\temp\wubi-11.04-rev211.log
09-06 20:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
09-06 20:06 DEBUG  CommonBackend: data_dir=C:\WINDOWS\TEMP\pylA.tmp\data
09-06 20:06 DEBUG  WindowsBackend: 7z=C:\WINDOWS\TEMP\pylA.tmp\bin\7z.exe
09-06 20:06 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
09-06 20:06 DEBUG  CommonBackend: Fetching basic info...
09-06 20:06 DEBUG  CommonBackend: original_exe=D:\wubi.exe
09-06 20:06 DEBUG  CommonBackend: platform=win32
09-06 20:06 DEBUG  CommonBackend: osname=nt
09-06 20:06 DEBUG  CommonBackend: language=en_US
09-06 20:06 DEBUG  CommonBackend: encoding=cp1252
09-06 20:06 DEBUG  WindowsBackend: arch=amd64
09-06 20:06 DEBUG  CommonBackend: Parsing isolist=C:\WINDOWS\TEMP\pylA.tmp\data\isolist.ini
09-06 20:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-06 20:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-06 20:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-06 20:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-06 20:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-06 20:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-06 20:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-06 20:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-06 20:06 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-06 20:06 DEBUG  WindowsBackend: Fetching host info...
09-06 20:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-06 20:06 DEBUG  WindowsBackend: windows version=xp
09-06 20:06 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
09-06 20:06 DEBUG  WindowsBackend: windows_sp=Service Pack 3
09-06 20:06 DEBUG  WindowsBackend: windows_build=2600
09-06 20:06 DEBUG  WindowsBackend: gmt=-5
09-06 20:06 DEBUG  WindowsBackend: country=US
09-06 20:06 DEBUG  WindowsBackend: timezone=America/New_York
09-06 20:06 ERROR  root: 'NoneType' object has no attribute 'decode'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\backends\common\backend.py", line 154, in fetch_basic_info
  File "\lib\wubi\backends\win32\backend.py", line 63, in fetch_host_info
  File "\lib\wubi\backends\win32\backend.py", line 360, in get_windows_username
AttributeError: 'NoneType' object has no attribute 'decode'
09-06 20:06 INFO   root: === wubi 11.04 rev211 ===
09-06 20:06 DEBUG  root: Logfile is c:\windows\temp\wubi-11.04-rev211.log
09-06 20:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
09-06 20:06 DEBUG  CommonBackend: data_dir=C:\WINDOWS\TEMP\pylB.tmp\data
09-06 20:06 DEBUG  WindowsBackend: 7z=C:\WINDOWS\TEMP\pylB.tmp\bin\7z.exe
09-06 20:06 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
09-06 20:06 DEBUG  CommonBackend: Fetching basic info...
09-06 20:06 DEBUG  CommonBackend: original_exe=D:\wubi.exe
09-06 20:06 DEBUG  CommonBackend: platform=win32
09-06 20:06 DEBUG  CommonBackend: osname=nt
09-06 20:06 DEBUG  CommonBackend: language=en_US
09-06 20:06 DEBUG  CommonBackend: encoding=cp1252
09-06 20:06 DEBUG  WindowsBackend: arch=amd64
09-06 20:06 DEBUG  CommonBackend: Parsing isolist=C:\WINDOWS\TEMP\pylB.tmp\data\isolist.ini
09-06 20:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-06 20:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-06 20:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-06 20:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-06 20:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-06 20:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-06 20:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-06 20:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-06 20:06 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-06 20:06 DEBUG  WindowsBackend: Fetching host info...
09-06 20:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-06 20:06 DEBUG  WindowsBackend: windows version=xp
09-06 20:06 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
09-06 20:06 DEBUG  WindowsBackend: windows_sp=Service Pack 3
09-06 20:06 DEBUG  WindowsBackend: windows_build=2600
09-06 20:06 DEBUG  WindowsBackend: gmt=-5
09-06 20:06 DEBUG  WindowsBackend: country=US
09-06 20:06 DEBUG  WindowsBackend: timezone=America/New_York
09-06 20:06 ERROR  root: 'NoneType' object has no attribute 'decode'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\backends\common\backend.py", line 154, in fetch_basic_info
  File "\lib\wubi\backends\win32\backend.py", line 63, in fetch_host_info
  File "\lib\wubi\backends\win32\backend.py", line 360, in get_windows_username
AttributeError: 'NoneType' object has no attribute 'decode'
 

```
 
ive looked on the bugreports and ive seen nothing about this error how can i fix it?

---

