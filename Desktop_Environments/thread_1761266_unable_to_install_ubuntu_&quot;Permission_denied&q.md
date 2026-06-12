---
title: "unable to install ubuntu &quot;Permission denied&quot;"
date: 2011-05-17
forum: Desktop Environments
---

### Post by aaudio9 on 2011-05-17
im using wubi to install ubuntu in Windows7 in a seperate partition. after a long installation (and nearly complete) i get an error says permission denied. whats wrong??please help me!!

---

### Post by Copper Bezel on 2011-05-18
I don't have any experience with Wubi, but the resulting system is just a regular dual boot machine, yes?

Do you remember what the error was exactly - what Wubi was writing when it said that permission was denied?

Are you using some earlier version, or the current 11.04? I've had trouble getting the most recent version to work as a USB boot disk, so I wonder if the problem is related.

Did Wubi successfully create the partition and such?

Depending on the above, what we'll probably end up doing here is to go ahead and create a LiveCD and install it over the partition Wubi created.

---

### Post by bcbc on 2011-05-18
> **aaudio9 said:**
> im using wubi to install ubuntu in Windows7 in a seperate partition. after a long installation (and nearly complete) i get an error says permission denied. whats wrong??please help me!!

Look for the log file. Open windows explorer, enter %temp% in the address bar. That will take you to your temp directory where you'll find the log file mentioned. Open it and look for the actual error, or just post it here between [CODE[SIZE="1"] [/SIZE]][/CODE] tags.

---

### Post by garvinrick4 on 2011-05-18
> **aaudio9 said:**
> im using wubi to install ubuntu in Windows7 in a seperate partition. after a long installation (and nearly complete) i get an error says permission denied. whats wrong??please help me!! Did you just slip an Ubuntu disk in and double click
the wubi icon and pick the size you wanted to use and your user name and password and click
install. Is this what you did? Just checking to see where you are at. Takes like 15 minutes.
 That is all there is to it. Wubi is a folder inside of Windows right next to Users called Ubuntu
in C: drive. It even attaches itself to Windows boot manager BCM I believe it is. 
A partition install is done with booting off of the Ubuntu disk and choosing to install and making selections
of how you want it installed on drive and such. directions below.
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")
[https://wiki.ubuntu.com/WubiGuide#Introduction](https://wiki.ubuntu.com/WubiGuide#Introduction)

If you have problems just go into add and remove programs in windows and remove Ubuntu and start over.
Or you can go to C: drive in Ubuntu folder right next to Users and open and uninstall. Start over.
That is one good thing about WUBI for new user is just uninstall like an Application and removed if want to start over.

---

### Post by garvinrick4 on 2011-05-18
Actually bcbc is pretty darn good with WUBI installs so I should leave this thread be.

---

### Post by bcbc on 2011-05-18
> **garvinrick4 said:**
> Actually bcbc is pretty darn good with WUBI installs so I should leave this thread be.

Thanks for the vote of confidence ;)
But I'm sure the OP appreciates more than one perspective.

---

### Post by aaudio9 on 2011-05-18
I don't have any experience with Wubi, but the resulting system is just a regular dual boot machine, yes?

> **Copper Bezel said:**
> Do you remember what the error was exactly - what Wubi was writing when it said that permission was denied?

I dont remember it,unfortunately.


> **Copper Bezel said:**
> 
Are you using some earlier version, or the current 11.04? I've had trouble getting the most recent version to work as a USB boot disk, so I wonder if the problem is related.

Its the latest 11.04.



> **Copper Bezel said:**
> 
Did Wubi successfully create the partition and such?

I made a partition myself about 10G of my HDD to install ubuntu.




this is just the end part or the installation log (the whole log is pretty long)

```
05-18 05:11 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
05-18 05:11 DEBUG  TaskList: ### Finished download
05-18 05:11 ERROR  TaskList: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-11.04-desktop-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-11.04-desktop-i386.iso'
05-18 05:11 DEBUG  TaskList: # Cancelling tasklist
05-18 05:11 DEBUG  TaskList: # Finished tasklist
05-18 05:11 ERROR  root: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-11.04-desktop-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-11.04-desktop-i386.iso'

```

---

### Post by aaudio9 on 2011-05-18
> **garvinrick4 said:**
> Did you just slip an Ubuntu disk in and double click
the wubi icon and pick the size you wanted to use and your user name and password and click
install. Is this what you did? Just checking to see where you are at. Takes like 15 minutes.
 That is all there is to it. Wubi is a folder inside of Windows right next to Users called Ubuntu
in C: drive. It even attaches itself to Windows boot manager BCM I believe it is. 
A partition install is done with booting off of the Ubuntu disk and choosing to install and making selections
of how you want it installed on drive and such. directions below.


i use POWER ISO to make an image of ubuntu iso i downloaded and double click the wubi icon inside the virtual disc and pick the size to use and put in my user name and password and click install.

---

### Post by bcbc on 2011-05-18
> **aaudio9 said:**
> I don't have any experience with Wubi, but the resulting system is just a regular dual boot machine, yes?

Not exactly. It's a dual boot but it uses a virtual disk that's hosted on the partition you chose to install (ntfs/fat32). Wubi is designed so that you don't have to partition. In your case, you created a 10GB partition already so perhaps Wubi is not what you want.

The log indicates that the bittorrent client Wubi uses (to download the desktop CD ISO) could not get access through a firewall (either Windows or some 3rd party firewall). You need to allow pyrun.exe (the python runtime) access to your firewall, but this could still be blocked by e.g. a corporate firewall.

It's kind of curious that it needs to download the ISO if you already had it. You can place wubi.exe and the desktop CD ISO in the same folder and it should use it instead of downloading a new one. (Unfortunately I need to see more of the log file to see what happened).

Anyway - if you want ubuntu on that 10GB partition (natively) then Wubi is not the way to go, unless:
1. you also have trouble booting from a live CD/USB
2. are not able to create full backups and are concerned about data loss (partitioning always has a little risk)
3. just want to try out Ubuntu and easily uninstall if you don't like it.

---

### Post by aaudio9 on 2011-05-18
> **bcbc said:**
> 
It's kind of curious that it needs to download the ISO if you already had it. You can place wubi.exe and the desktop CD ISO in the same folder and it should use it instead of downloading a new one. (Unfortunately I need to see more of the log file to see what happened).

Thnks bcbc for ur reply. I'll put the ISO n wubi in the same folder and install again (hope it works this time). Im installing right now.

I include the log of my previous installation.

05-09 18:53 INFO   root: === wubi 11.04 rev211 ===
05-09 18:53 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-09 18:53 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\audi bin marwoto\\Downloads\\Programs\\wubi.exe"']
05-09 18:53 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7196.tmp\data
05-09 18:53 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7196.tmp\bin\7z.exe
05-09 18:53 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-09 18:53 DEBUG  CommonBackend: Fetching basic info...
05-09 18:53 DEBUG  CommonBackend: original_exe=C:\Users\audi bin marwoto\Downloads\Programs\wubi.exe
05-09 18:53 DEBUG  CommonBackend: platform=win32
05-09 18:53 DEBUG  CommonBackend: osname=nt
05-09 18:53 DEBUG  CommonBackend: language=en_MY
05-09 18:53 DEBUG  CommonBackend: encoding=cp1252
05-09 18:53 DEBUG  WindowsBackend: arch=amd64
05-09 18:53 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7196.tmp\data\isolist.ini
05-09 18:53 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-09 18:53 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-09 18:53 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-09 18:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-09 18:53 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-09 18:53 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-09 18:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-09 18:53 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-09 18:53 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-09 18:53 DEBUG  WindowsBackend: Fetching host info...
05-09 18:53 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-09 18:53 DEBUG  WindowsBackend: windows version=vista
05-09 18:53 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-09 18:53 DEBUG  WindowsBackend: windows_sp=None
05-09 18:53 DEBUG  WindowsBackend: windows_build=7600
05-09 18:53 DEBUG  WindowsBackend: gmt=8
05-09 18:53 DEBUG  WindowsBackend: country=MY
05-09 18:53 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-09 18:53 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-09 18:53 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-09 18:53 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-09 18:53 DEBUG  WindowsBackend: windows_language_code=1033
05-09 18:53 DEBUG  WindowsBackend: windows_language=English
05-09 18:53 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-09 18:53 DEBUG  WindowsBackend: bootloader=vista
05-09 18:53 DEBUG  WindowsBackend: system_drive=Drive(C: hd 48928.1289063 mb free ntfs)
05-09 18:53 DEBUG  WindowsBackend: drive=Drive(C: hd 48928.1289063 mb free ntfs)
05-09 18:53 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.39453125 mb free ntfs)
05-09 18:53 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-09 18:53 DEBUG  WindowsBackend: uninstaller_path=None
05-09 18:53 DEBUG  WindowsBackend: previous_target_dir=None
05-09 18:53 DEBUG  WindowsBackend: previous_distro_name=None
05-09 18:53 DEBUG  WindowsBackend: keyboard_id=67699721
05-09 18:53 DEBUG  WindowsBackend: keyboard_layout=us
05-09 18:53 DEBUG  WindowsBackend: keyboard_variant=
05-09 18:53 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-09 18:53 DEBUG  CommonBackend: locale=en_US.UTF-8
05-09 18:53 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-09 18:53 DEBUG  CommonBackend: Searching ISOs on USB devices
05-09 18:53 DEBUG  CommonBackend: Searching for local CDs
05-09 18:53 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7196.tmp is a valid Ubuntu CD
05-09 18:53 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7196.tmp\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7196.tmp is a valid Ubuntu CD
05-09 18:53 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7196.tmp\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7196.tmp is a valid Ubuntu Netbook CD
05-09 18:53 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7196.tmp\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7196.tmp is a valid Kubuntu CD
05-09 18:53 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7196.tmp\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7196.tmp is a valid Kubuntu CD
05-09 18:53 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7196.tmp\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7196.tmp is a valid Xubuntu CD
05-09 18:53 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7196.tmp\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7196.tmp is a valid Xubuntu CD
05-09 18:53 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7196.tmp\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7196.tmp is a valid Mythbuntu CD
05-09 18:53 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7196.tmp\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7196.tmp is a valid Mythbuntu CD
05-09 18:53 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7196.tmp\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-09 18:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-09 18:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-09 18:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-09 18:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-09 18:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-09 18:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-09 18:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-09 18:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-09 18:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-09 18:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-09 18:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-09 18:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-09 18:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-09 18:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-09 18:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-09 18:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-09 18:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 18:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-09 18:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 18:53 INFO   root: Running the installer...
05-09 18:53 DEBUG  WindowsFrontend: __init__...
05-09 18:53 DEBUG  WindowsFrontend: on_init...
05-09 18:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7196.tmp\translations, languages=['en_US', 'en']
05-09 18:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7196.tmp\translations, languages=['en_US', 'en']
05-09 18:54 DEBUG  WindowsFrontend: frontend.on_quit
05-09 18:54 DEBUG  root: application.on_quit
05-09 18:54 INFO   root: sys.exit
05-09 19:41 INFO   root: === wubi 11.04 rev211 ===
05-09 19:41 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-09 19:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\audi bin marwoto\\Downloads\\Programs\\wubi.exe"']
05-09 19:41 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp\data
05-09 19:41 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp\bin\7z.exe
05-09 19:41 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-09 19:41 DEBUG  CommonBackend: Fetching basic info...
05-09 19:41 DEBUG  CommonBackend: original_exe=C:\Users\audi bin marwoto\Downloads\Programs\wubi.exe
05-09 19:41 DEBUG  CommonBackend: platform=win32
05-09 19:41 DEBUG  CommonBackend: osname=nt
05-09 19:41 DEBUG  CommonBackend: language=en_MY
05-09 19:41 DEBUG  CommonBackend: encoding=cp1252
05-09 19:41 DEBUG  WindowsBackend: arch=amd64
05-09 19:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp\data\isolist.ini
05-09 19:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-09 19:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-09 19:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-09 19:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-09 19:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-09 19:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-09 19:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-09 19:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-09 19:41 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-09 19:41 DEBUG  WindowsBackend: Fetching host info...
05-09 19:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-09 19:41 DEBUG  WindowsBackend: windows version=vista
05-09 19:41 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-09 19:41 DEBUG  WindowsBackend: windows_sp=None
05-09 19:41 DEBUG  WindowsBackend: windows_build=7600
05-09 19:41 DEBUG  WindowsBackend: gmt=8
05-09 19:41 DEBUG  WindowsBackend: country=MY
05-09 19:41 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-09 19:41 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-09 19:41 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-09 19:41 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-09 19:41 DEBUG  WindowsBackend: windows_language_code=1033
05-09 19:41 DEBUG  WindowsBackend: windows_language=English
05-09 19:41 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-09 19:41 DEBUG  WindowsBackend: bootloader=vista
05-09 19:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 48860.8671875 mb free ntfs)
05-09 19:41 DEBUG  WindowsBackend: drive=Drive(C: hd 48860.8671875 mb free ntfs)
05-09 19:41 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.22265625 mb free ntfs)
05-09 19:41 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-09 19:41 DEBUG  WindowsBackend: drive=Drive(F: hd 3078.3203125 mb free ntfs)
05-09 19:41 DEBUG  WindowsBackend: drive=Drive(G: hd 82960.3867188 mb free ntfs)
05-09 19:41 DEBUG  WindowsBackend: drive=Drive(H: hd 31194.2382813 mb free ntfs)
05-09 19:41 DEBUG  WindowsBackend: drive=Drive(I: removable 1849.96484375 mb free ntfs)
05-09 19:41 DEBUG  WindowsBackend: uninstaller_path=None
05-09 19:41 DEBUG  WindowsBackend: previous_target_dir=None
05-09 19:41 DEBUG  WindowsBackend: previous_distro_name=None
05-09 19:41 DEBUG  WindowsBackend: keyboard_id=67699721
05-09 19:41 DEBUG  WindowsBackend: keyboard_layout=us
05-09 19:41 DEBUG  WindowsBackend: keyboard_variant=
05-09 19:41 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-09 19:41 DEBUG  CommonBackend: locale=en_US.UTF-8
05-09 19:41 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-09 19:41 DEBUG  CommonBackend: Searching ISOs on USB devices
05-09 19:41 DEBUG  CommonBackend: Searching for local CDs
05-09 19:41 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp is a valid Ubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp is a valid Ubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp is a valid Ubuntu Netbook CD
05-09 19:41 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp is a valid Kubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp is a valid Kubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp is a valid Xubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp is a valid Xubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp is a valid Mythbuntu CD
05-09 19:41 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp is a valid Mythbuntu CD
05-09 19:41 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-09 19:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-09 19:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-09 19:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-09 19:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-09 19:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-09 19:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-09 19:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-09 19:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-09 19:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
05-09 19:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-09 19:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-09 19:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
05-09 19:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-09 19:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-09 19:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
05-09 19:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-09 19:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-09 19:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-09 19:41 INFO   root: Running the installer...
05-09 19:41 DEBUG  WindowsFrontend: __init__...
05-09 19:41 DEBUG  WindowsFrontend: on_init...
05-09 19:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp\translations, languages=['en_US', 'en']
05-09 19:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp\translations, languages=['en_US', 'en']
05-09 19:41 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=audibinmarwoto
05-09 19:41 INFO   root: Received settings
05-09 19:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp\translations, languages=['en_US', 'en']
05-09 19:41 DEBUG  TaskList: # Running tasklist...
05-09 19:41 DEBUG  TaskList: ## Running select_target_dir...
05-09 19:41 INFO   WindowsBackend: Installing into C:\ubuntu
05-09 19:41 DEBUG  TaskList: ## Finished select_target_dir
05-09 19:41 DEBUG  TaskList: ## Running create_dir_structure...
05-09 19:41 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-09 19:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-09 19:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-09 19:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-09 19:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-09 19:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-09 19:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-09 19:41 DEBUG  TaskList: ## Finished create_dir_structure
05-09 19:41 DEBUG  TaskList: ## Running uncompress_target_dir...
05-09 19:41 DEBUG  TaskList: ## Finished uncompress_target_dir
05-09 19:41 DEBUG  TaskList: ## Running create_uninstaller...
05-09 19:41 DEBUG  WindowsBackend: Copying uninstaller C:\Users\audi bin marwoto\Downloads\Programs\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-09 19:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-09 19:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-09 19:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-09 19:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-09 19:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-09 19:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-09 19:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-09 19:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-09 19:41 DEBUG  TaskList: ## Finished create_uninstaller
05-09 19:41 DEBUG  TaskList: ## Running copy_installation_files...
05-09 19:41 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-09 19:41 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp\winboot -> C:\ubuntu\winboot
05-09 19:41 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-09 19:41 DEBUG  TaskList: ## Finished copy_installation_files
05-09 19:41 DEBUG  TaskList: ## Running get_iso...
05-09 19:41 DEBUG  CommonBackend: Searching for local CD
05-09 19:41 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp is a valid Ubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl224F.tmp\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-09 19:41 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-09 19:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-09 19:41 DEBUG  CommonBackend: Searching for local ISO
05-09 19:41 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-09 19:41 DEBUG  TaskList: New task get_metalink
05-09 19:41 DEBUG  TaskList: ### Running get_metalink...
05-09 19:41 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > C:\ubuntu\install
05-09 19:41 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
05-09 19:41 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/natty-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/natty-desktop-amd64.metalink) > C:\ubuntu\install
05-09 19:41 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/natty-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/natty-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
05-09 19:41 DEBUG  TaskList: ### Finished get_metalink
05-09 19:41 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-09 19:41 DEBUG  TaskList: # Cancelling tasklist
05-09 19:41 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-09 19:41 DEBUG  TaskList: # Finished tasklist
05-09 19:42 INFO   root: === wubi 11.04 rev211 ===
05-09 19:42 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-09 19:42 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\audi bin marwoto\\Downloads\\Programs\\wubi.exe"']
05-09 19:42 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2E9E.tmp\data
05-09 19:42 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2E9E.tmp\bin\7z.exe
05-09 19:42 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-09 19:42 DEBUG  CommonBackend: Fetching basic info...
05-09 19:42 DEBUG  CommonBackend: original_exe=C:\Users\audi bin marwoto\Downloads\Programs\wubi.exe
05-09 19:42 DEBUG  CommonBackend: platform=win32
05-09 19:42 DEBUG  CommonBackend: osname=nt
05-09 19:42 DEBUG  CommonBackend: language=en_MY
05-09 19:42 DEBUG  CommonBackend: encoding=cp1252
05-09 19:42 DEBUG  WindowsBackend: arch=amd64
05-09 19:42 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2E9E.tmp\data\isolist.ini
05-09 19:42 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-09 19:42 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-09 19:42 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-09 19:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-09 19:42 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-09 19:42 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-09 19:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-09 19:42 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-09 19:42 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-09 19:42 DEBUG  WindowsBackend: Fetching host info...
05-09 19:42 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-09 19:42 DEBUG  WindowsBackend: windows version=vista
05-09 19:42 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-09 19:42 DEBUG  WindowsBackend: windows_sp=None
05-09 19:42 DEBUG  WindowsBackend: windows_build=7600
05-09 19:42 DEBUG  WindowsBackend: gmt=8
05-09 19:42 DEBUG  WindowsBackend: country=MY
05-09 19:42 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-09 19:42 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-09 19:42 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-09 19:42 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-09 19:42 DEBUG  WindowsBackend: windows_language_code=1033
05-09 19:42 DEBUG  WindowsBackend: windows_language=English
05-09 19:42 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-09 19:42 DEBUG  WindowsBackend: bootloader=vista
05-09 19:42 DEBUG  WindowsBackend: system_drive=Drive(C: hd 48859.3007813 mb free ntfs)
05-09 19:42 DEBUG  WindowsBackend: drive=Drive(C: hd 48859.3007813 mb free ntfs)
05-09 19:42 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.22265625 mb free ntfs)
05-09 19:42 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-09 19:42 DEBUG  WindowsBackend: drive=Drive(F: hd 3078.3203125 mb free ntfs)
05-09 19:42 DEBUG  WindowsBackend: drive=Drive(G: hd 82960.3867188 mb free ntfs)
05-09 19:42 DEBUG  WindowsBackend: drive=Drive(H: hd 31194.2382813 mb free ntfs)
05-09 19:42 DEBUG  WindowsBackend: drive=Drive(I: removable 1849.96484375 mb free ntfs)
05-09 19:42 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-09 19:42 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-09 19:42 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-09 19:42 DEBUG  WindowsBackend: keyboard_id=67699721
05-09 19:42 DEBUG  WindowsBackend: keyboard_layout=us
05-09 19:42 DEBUG  WindowsBackend: keyboard_variant=
05-09 19:42 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-09 19:42 DEBUG  CommonBackend: locale=en_US.UTF-8
05-09 19:42 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-09 19:42 DEBUG  CommonBackend: Searching ISOs on USB devices
05-09 19:42 DEBUG  CommonBackend: Searching for local CDs
05-09 19:42 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2E9E.tmp is a valid Ubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2E9E.tmp\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2E9E.tmp is a valid Ubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2E9E.tmp\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2E9E.tmp is a valid Ubuntu Netbook CD
05-09 19:42 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2E9E.tmp\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2E9E.tmp is a valid Kubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2E9E.tmp\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2E9E.tmp is a valid Kubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2E9E.tmp\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2E9E.tmp is a valid Xubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2E9E.tmp\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2E9E.tmp is a valid Xubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2E9E.tmp\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2E9E.tmp is a valid Mythbuntu CD
05-09 19:42 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2E9E.tmp\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2E9E.tmp is a valid Mythbuntu CD
05-09 19:42 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2E9E.tmp\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-09 19:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-09 19:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-09 19:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-09 19:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-09 19:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-09 19:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-09 19:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-09 19:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-09 19:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
05-09 19:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-09 19:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-09 19:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
05-09 19:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-09 19:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-09 19:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
05-09 19:42 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-09 19:42 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-09 19:42 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-09 19:42 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-09 19:42 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-09 19:42 INFO   root: Already installed, running the uninstaller...
05-09 19:42 INFO   root: Running the uninstaller...
05-09 19:42 INFO   CommonBackend: This is the uninstaller running
05-09 19:42 DEBUG  WindowsFrontend: __init__...
05-09 19:42 DEBUG  WindowsFrontend: on_init...
05-09 19:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2E9E.tmp\translations, languages=['en_US', 'en']
05-09 19:42 INFO   WindowsFrontend: Operation cancelled
05-09 19:42 DEBUG  WindowsFrontend: frontend.quit
05-09 19:42 DEBUG  WindowsFrontend: frontend.on_quit
05-09 19:42 DEBUG  root: application.on_quit
05-09 19:42 INFO   root: sys.exit
05-10 01:11 INFO   root: === wubi 11.04 rev211 ===
05-10 01:11 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-10 01:11 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
05-10 01:11 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylECF.tmp\data
05-10 01:11 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pylECF.tmp\bin\7z.exe
05-10 01:11 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-10 01:11 DEBUG  CommonBackend: Fetching basic info...
05-10 01:11 DEBUG  CommonBackend: original_exe=E:\wubi.exe
05-10 01:11 DEBUG  CommonBackend: platform=win32
05-10 01:11 DEBUG  CommonBackend: osname=nt
05-10 01:11 DEBUG  CommonBackend: language=en_MY
05-10 01:11 DEBUG  CommonBackend: encoding=cp1252
05-10 01:11 DEBUG  WindowsBackend: arch=amd64
05-10 01:11 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pylECF.tmp\data\isolist.ini
05-10 01:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-10 01:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-10 01:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-10 01:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-10 01:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-10 01:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-10 01:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-10 01:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-10 01:11 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-10 01:11 DEBUG  WindowsBackend: Fetching host info...
05-10 01:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-10 01:11 DEBUG  WindowsBackend: windows version=vista
05-10 01:11 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-10 01:11 DEBUG  WindowsBackend: windows_sp=None
05-10 01:11 DEBUG  WindowsBackend: windows_build=7600
05-10 01:11 DEBUG  WindowsBackend: gmt=8
05-10 01:11 DEBUG  WindowsBackend: country=MY
05-10 01:11 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-10 01:11 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-10 01:11 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-10 01:11 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-10 01:11 DEBUG  WindowsBackend: windows_language_code=1033
05-10 01:11 DEBUG  WindowsBackend: windows_language=English
05-10 01:11 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-10 01:11 DEBUG  WindowsBackend: bootloader=vista
05-10 01:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 48499.0546875 mb free ntfs)
05-10 01:11 DEBUG  WindowsBackend: drive=Drive(C: hd 48499.0546875 mb free ntfs)
05-10 01:11 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.22265625 mb free ntfs)
05-10 01:11 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-10 01:11 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-10 01:11 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-10 01:11 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-10 01:11 DEBUG  WindowsBackend: keyboard_id=67699721
05-10 01:11 DEBUG  WindowsBackend: keyboard_layout=us
05-10 01:11 DEBUG  WindowsBackend: keyboard_variant=
05-10 01:11 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-10 01:11 DEBUG  CommonBackend: locale=en_US.UTF-8
05-10 01:11 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-10 01:11 DEBUG  CommonBackend: Searching ISOs on USB devices
05-10 01:11 DEBUG  CommonBackend: Searching for local CDs
05-10 01:11 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylECF.tmp is a valid Ubuntu CD
05-10 01:11 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylECF.tmp\casper\filesystem.squashfs
05-10 01:11 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylECF.tmp is a valid Ubuntu CD
05-10 01:11 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylECF.tmp\casper\filesystem.squashfs
05-10 01:11 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylECF.tmp is a valid Ubuntu Netbook CD
05-10 01:11 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylECF.tmp\casper\filesystem.squashfs
05-10 01:11 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylECF.tmp is a valid Kubuntu CD
05-10 01:11 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylECF.tmp\casper\filesystem.squashfs
05-10 01:11 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylECF.tmp is a valid Kubuntu CD
05-10 01:11 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylECF.tmp\casper\filesystem.squashfs
05-10 01:11 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylECF.tmp is a valid Xubuntu CD
05-10 01:11 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylECF.tmp\casper\filesystem.squashfs
05-10 01:11 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylECF.tmp is a valid Xubuntu CD
05-10 01:11 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylECF.tmp\casper\filesystem.squashfs
05-10 01:11 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylECF.tmp is a valid Mythbuntu CD
05-10 01:11 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylECF.tmp\casper\filesystem.squashfs
05-10 01:11 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylECF.tmp is a valid Mythbuntu CD
05-10 01:11 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylECF.tmp\casper\filesystem.squashfs
05-10 01:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 01:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 01:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-10 01:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 01:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 01:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:11 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 01:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:11 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 01:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 01:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 01:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-10 01:11 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-10 01:11 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-10 01:11 INFO   Distro: Found a valid CD for Ubuntu: E:\
05-10 01:11 INFO   root: Running the CD menu...
05-10 01:11 DEBUG  WindowsFrontend: __init__...
05-10 01:11 DEBUG  WindowsFrontend: on_init...
05-10 01:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylECF.tmp\translations, languages=['en_US', 'en']
05-10 01:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylECF.tmp\translations, languages=['en_US', 'en']
05-10 01:11 INFO   root: CD menu finished
05-10 01:11 INFO   root: Rebooting
05-10 01:11 DEBUG  TaskList: # Running tasklist...
05-10 01:11 DEBUG  TaskList: ## Running reboot...
05-10 01:11 DEBUG  TaskList: ## Finished reboot
05-10 01:11 DEBUG  TaskList: # Finished tasklist
05-10 01:11 DEBUG  root: application.quit
05-10 01:11 DEBUG  WindowsFrontend: frontend.quit
05-10 01:11 DEBUG  WindowsFrontend: frontend.on_quit
05-10 01:11 DEBUG  root: application.on_quit
05-10 01:11 INFO   root: sys.exit
05-10 01:14 INFO   root: === wubi 11.04 rev211 ===
05-10 01:14 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-10 01:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
05-10 01:14 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\data
05-10 01:14 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\bin\7z.exe
05-10 01:14 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-10 01:14 DEBUG  CommonBackend: Fetching basic info...
05-10 01:14 DEBUG  CommonBackend: original_exe=E:\wubi.exe
05-10 01:14 DEBUG  CommonBackend: platform=win32
05-10 01:14 DEBUG  CommonBackend: osname=nt
05-10 01:14 DEBUG  CommonBackend: language=en_MY
05-10 01:14 DEBUG  CommonBackend: encoding=cp1252
05-10 01:14 DEBUG  WindowsBackend: arch=amd64
05-10 01:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\data\isolist.ini
05-10 01:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-10 01:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-10 01:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-10 01:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-10 01:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-10 01:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-10 01:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-10 01:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-10 01:14 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-10 01:14 DEBUG  WindowsBackend: Fetching host info...
05-10 01:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-10 01:14 DEBUG  WindowsBackend: windows version=vista
05-10 01:14 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-10 01:14 DEBUG  WindowsBackend: windows_sp=None
05-10 01:14 DEBUG  WindowsBackend: windows_build=7600
05-10 01:14 DEBUG  WindowsBackend: gmt=8
05-10 01:14 DEBUG  WindowsBackend: country=MY
05-10 01:14 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-10 01:14 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-10 01:14 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-10 01:14 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-10 01:14 DEBUG  WindowsBackend: windows_language_code=1033
05-10 01:14 DEBUG  WindowsBackend: windows_language=English
05-10 01:14 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-10 01:14 DEBUG  WindowsBackend: bootloader=vista
05-10 01:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 48492.78125 mb free ntfs)
05-10 01:14 DEBUG  WindowsBackend: drive=Drive(C: hd 48492.78125 mb free ntfs)
05-10 01:14 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.22265625 mb free ntfs)
05-10 01:14 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-10 01:14 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-10 01:14 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-10 01:14 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-10 01:14 DEBUG  WindowsBackend: keyboard_id=67699721
05-10 01:14 DEBUG  WindowsBackend: keyboard_layout=us
05-10 01:14 DEBUG  WindowsBackend: keyboard_variant=
05-10 01:14 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-10 01:14 DEBUG  CommonBackend: locale=en_US.UTF-8
05-10 01:14 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-10 01:14 DEBUG  CommonBackend: Searching ISOs on USB devices
05-10 01:14 DEBUG  CommonBackend: Searching for local CDs
05-10 01:14 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp is a valid Ubuntu CD
05-10 01:14 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp is a valid Ubuntu CD
05-10 01:14 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp is a valid Ubuntu Netbook CD
05-10 01:14 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp is a valid Kubuntu CD
05-10 01:14 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp is a valid Kubuntu CD
05-10 01:14 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp is a valid Xubuntu CD
05-10 01:14 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp is a valid Xubuntu CD
05-10 01:14 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp is a valid Mythbuntu CD
05-10 01:14 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp is a valid Mythbuntu CD
05-10 01:14 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-10 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-10 01:14 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-10 01:14 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-10 01:14 INFO   Distro: Found a valid CD for Ubuntu: E:\
05-10 01:14 INFO   root: Running the CD menu...
05-10 01:14 DEBUG  WindowsFrontend: __init__...
05-10 01:14 DEBUG  WindowsFrontend: on_init...
05-10 01:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\translations, languages=['en_US', 'en']
05-10 01:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\translations, languages=['en_US', 'en']
05-10 01:14 INFO   root: CD menu finished
05-10 01:14 INFO   root: Already installed, running the uninstaller...
05-10 01:14 INFO   root: Running the uninstaller...
05-10 01:14 INFO   CommonBackend: This is the uninstaller running
05-10 01:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\translations, languages=['en_US', 'en']
05-10 01:14 INFO   root: Received settings
05-10 01:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\translations, languages=['en_US', 'en']
05-10 01:14 DEBUG  TaskList: # Running tasklist...
05-10 01:14 DEBUG  TaskList: ## Running Backup ISO...
05-10 01:14 DEBUG  TaskList: ## Finished Backup ISO
05-10 01:14 DEBUG  TaskList: ## Running Remove bootloader entry...
05-10 01:14 DEBUG  WindowsBackend: Could not find bcd id
05-10 01:14 DEBUG  WindowsBackend: undo_bootini C:
05-10 01:14 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 48492.78125 mb free ntfs)
05-10 01:14 DEBUG  WindowsBackend: undo_bootini D:
05-10 01:14 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2105.22265625 mb free ntfs)
05-10 01:14 DEBUG  TaskList: ## Finished Remove bootloader entry
05-10 01:14 DEBUG  TaskList: ## Running Remove target dir...
05-10 01:14 DEBUG  CommonBackend: Deleting C:\ubuntu
05-10 01:14 DEBUG  TaskList: ## Finished Remove target dir
05-10 01:14 DEBUG  TaskList: ## Running Remove registry key...
05-10 01:14 DEBUG  TaskList: ## Finished Remove registry key
05-10 01:14 DEBUG  TaskList: # Finished tasklist
05-10 01:14 INFO   root: Almost finished uninstalling
05-10 01:14 INFO   root: Finished uninstallation
05-10 01:14 DEBUG  CommonBackend: Fetching basic info...
05-10 01:14 DEBUG  CommonBackend: original_exe=E:\wubi.exe
05-10 01:14 DEBUG  CommonBackend: platform=win32
05-10 01:14 DEBUG  CommonBackend: osname=nt
05-10 01:14 DEBUG  WindowsBackend: arch=amd64
05-10 01:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\data\isolist.ini
05-10 01:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-10 01:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-10 01:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-10 01:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-10 01:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-10 01:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-10 01:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-10 01:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-10 01:14 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-10 01:14 DEBUG  WindowsBackend: Fetching host info...
05-10 01:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-10 01:14 DEBUG  WindowsBackend: windows version=vista
05-10 01:14 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-10 01:14 DEBUG  WindowsBackend: windows_sp=None
05-10 01:14 DEBUG  WindowsBackend: windows_build=7600
05-10 01:14 DEBUG  WindowsBackend: gmt=8
05-10 01:14 DEBUG  WindowsBackend: country=MY
05-10 01:14 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-10 01:14 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-10 01:14 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-10 01:14 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-10 01:14 DEBUG  WindowsBackend: windows_language_code=1033
05-10 01:14 DEBUG  WindowsBackend: windows_language=English
05-10 01:14 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-10 01:14 DEBUG  WindowsBackend: bootloader=vista
05-10 01:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 48499.8125 mb free ntfs)
05-10 01:14 DEBUG  WindowsBackend: drive=Drive(C: hd 48499.8125 mb free ntfs)
05-10 01:14 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.22265625 mb free ntfs)
05-10 01:14 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-10 01:14 DEBUG  WindowsBackend: uninstaller_path=None
05-10 01:14 DEBUG  WindowsBackend: previous_target_dir=None
05-10 01:14 DEBUG  WindowsBackend: previous_distro_name=None
05-10 01:14 DEBUG  WindowsBackend: keyboard_id=67699721
05-10 01:14 DEBUG  WindowsBackend: keyboard_layout=us
05-10 01:14 DEBUG  WindowsBackend: keyboard_variant=
05-10 01:14 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-10 01:14 DEBUG  CommonBackend: Searching ISOs on USB devices
05-10 01:14 DEBUG  CommonBackend: Searching for local CDs
05-10 01:14 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp is a valid Ubuntu CD
05-10 01:14 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp is a valid Ubuntu CD
05-10 01:14 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp is a valid Ubuntu Netbook CD
05-10 01:14 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp is a valid Kubuntu CD
05-10 01:14 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp is a valid Kubuntu CD
05-10 01:14 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp is a valid Xubuntu CD
05-10 01:14 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp is a valid Xubuntu CD
05-10 01:14 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp is a valid Mythbuntu CD
05-10 01:14 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp is a valid Mythbuntu CD
05-10 01:14 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-10 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-10 01:14 INFO   Distro: Found a valid CD for Ubuntu: E:\
05-10 01:14 INFO   root: Running the installer...
05-10 01:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\translations, languages=['en_US', 'en']
05-10 01:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\translations, languages=['en_US', 'en']
05-10 01:14 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=audibinmarwoto
05-10 01:14 INFO   root: Received settings
05-10 01:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\translations, languages=['en_US', 'en']
05-10 01:14 DEBUG  TaskList: # Running tasklist...
05-10 01:14 DEBUG  TaskList: ## Running select_target_dir...
05-10 01:14 INFO   WindowsBackend: Installing into C:\ubuntu
05-10 01:14 DEBUG  TaskList: ## Finished select_target_dir
05-10 01:14 DEBUG  TaskList: ## Running create_dir_structure...
05-10 01:14 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-10 01:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-10 01:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-10 01:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-10 01:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-10 01:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-10 01:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-10 01:14 DEBUG  TaskList: ## Finished create_dir_structure
05-10 01:14 DEBUG  TaskList: ## Running uncompress_target_dir...
05-10 01:14 DEBUG  TaskList: ## Finished uncompress_target_dir
05-10 01:14 DEBUG  TaskList: ## Running create_uninstaller...
05-10 01:14 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-10 01:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-10 01:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-10 01:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-10 01:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-10 01:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-10 01:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-10 01:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-10 01:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-10 01:14 DEBUG  TaskList: ## Finished create_uninstaller
05-10 01:14 DEBUG  TaskList: ## Running copy_installation_files...
05-10 01:14 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-10 01:14 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\winboot -> C:\ubuntu\winboot
05-10 01:14 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-10 01:14 DEBUG  TaskList: ## Finished copy_installation_files
05-10 01:14 DEBUG  TaskList: ## Running get_iso...
05-10 01:14 DEBUG  TaskList: New task copy_file
05-10 01:14 DEBUG  TaskList: ### Running copy_file...
05-10 01:16 DEBUG  TaskList: ### Finished copy_file
05-10 01:16 DEBUG  TaskList: New task check_iso
05-10 01:16 DEBUG  TaskList: ### Running check_iso...
05-10 01:16 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
05-10 01:16 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
05-10 01:16 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
05-10 01:16 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-10 01:16 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-10 01:16 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
05-10 01:16 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
05-10 01:16 DEBUG  TaskList: New task get_metalink
05-10 01:16 DEBUG  TaskList: #### Running get_metalink...
05-10 01:16 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink) > C:\ubuntu\install
05-10 01:16 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
05-10 01:16 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.metalink) > C:\ubuntu\install
05-10 01:16 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
05-10 01:16 DEBUG  TaskList: #### Finished get_metalink
05-10 01:16 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for C:\ubuntu\install\installation.iso, ignoring
05-10 01:16 DEBUG  TaskList: ### Finished check_iso
05-10 01:16 DEBUG  TaskList: ## Finished get_iso
05-10 01:16 DEBUG  TaskList: ## Running extract_kernel...
05-10 01:16 DEBUG  CommonBackend: Copying files from CD E:\
05-10 01:16 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
05-10 01:16 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
05-10 01:16 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = db0104e80bc7e667344a14af3515de25 == db0104e80bc7e667344a14af3515de25
05-10 01:16 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
05-10 01:16 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = 4b776cdafb272064bb70e09ba212e4aa == 4b776cdafb272064bb70e09ba212e4aa
05-10 01:16 DEBUG  TaskList: ## Finished extract_kernel
05-10 01:16 DEBUG  TaskList: ## Running choose_disk_sizes...
05-10 01:16 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
05-10 01:16 DEBUG  TaskList: ## Finished choose_disk_sizes
05-10 01:16 DEBUG  TaskList: ## Running create_preseed...
05-10 01:16 DEBUG  TaskList: ## Finished create_preseed
05-10 01:16 DEBUG  TaskList: ## Running modify_bootloader...
05-10 01:16 DEBUG  TaskList: New task modify_bcd
05-10 01:16 DEBUG  TaskList: ### Running modify_bcd...
05-10 01:16 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 48499.8125 mb free ntfs)
05-10 01:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {633128b6-bc48-11df-a1e8-fd8ecb34e649}
05-10 01:16 DEBUG  TaskList: ### Finished modify_bcd
05-10 01:16 DEBUG  TaskList: New task modify_bcd
05-10 01:16 DEBUG  TaskList: ### Running modify_bcd...
05-10 01:16 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 2105.22265625 mb free ntfs)
05-10 01:16 DEBUG  WindowsBackend: BCD has already been modified
05-10 01:16 DEBUG  TaskList: ### Finished modify_bcd
05-10 01:16 DEBUG  TaskList: ## Finished modify_bootloader
05-10 01:16 DEBUG  TaskList: ## Running modify_grub_configuration...
05-10 01:16 DEBUG  TaskList: ## Finished modify_grub_configuration
05-10 01:16 DEBUG  TaskList: ## Running create_virtual_disks...
05-10 01:16 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\root.disk of 16744MB
05-10 01:16 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\swap.disk of 256MB
05-10 01:16 DEBUG  TaskList: ## Finished create_virtual_disks
05-10 01:16 DEBUG  TaskList: ## Running uncompress_files...
05-10 01:16 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
05-10 01:16 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
05-10 01:16 DEBUG  TaskList: ## Finished uncompress_files
05-10 01:16 DEBUG  TaskList: ## Running eject_cd...
05-10 01:16 DEBUG  TaskList: ## Finished eject_cd
05-10 01:16 DEBUG  TaskList: # Finished tasklist
05-10 01:16 INFO   root: Almost finished installing
05-10 01:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl7BF2.tmp\translations, languages=['en_US', 'en']
05-10 01:16 INFO   root: Finished installation
05-10 01:16 INFO   root: Rebooting
05-10 01:16 DEBUG  TaskList: # Running tasklist...
05-10 01:16 DEBUG  TaskList: ## Running reboot...
05-10 01:16 DEBUG  TaskList: ## Finished reboot
05-10 01:16 DEBUG  TaskList: # Finished tasklist
05-10 01:16 DEBUG  root: application.quit
05-10 01:16 DEBUG  WindowsFrontend: frontend.quit
05-10 01:16 DEBUG  WindowsFrontend: frontend.on_quit
05-10 01:16 DEBUG  root: application.on_quit
05-10 01:16 INFO   root: sys.exit
05-10 01:28 INFO   root: === wubi 11.04 rev211 ===
05-10 01:28 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-10 01:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
05-10 01:28 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl13AE.tmp\data
05-10 01:28 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl13AE.tmp\bin\7z.exe
05-10 01:28 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-10 01:28 DEBUG  CommonBackend: Fetching basic info...
05-10 01:28 DEBUG  CommonBackend: original_exe=E:\wubi.exe
05-10 01:28 DEBUG  CommonBackend: platform=win32
05-10 01:28 DEBUG  CommonBackend: osname=nt
05-10 01:28 DEBUG  CommonBackend: language=en_MY
05-10 01:28 DEBUG  CommonBackend: encoding=cp1252
05-10 01:28 DEBUG  WindowsBackend: arch=amd64
05-10 01:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl13AE.tmp\data\isolist.ini
05-10 01:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-10 01:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-10 01:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-10 01:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-10 01:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-10 01:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-10 01:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-10 01:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-10 01:28 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-10 01:28 DEBUG  WindowsBackend: Fetching host info...
05-10 01:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-10 01:28 DEBUG  WindowsBackend: windows version=vista
05-10 01:28 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-10 01:28 DEBUG  WindowsBackend: windows_sp=None
05-10 01:28 DEBUG  WindowsBackend: windows_build=7600
05-10 01:28 DEBUG  WindowsBackend: gmt=8
05-10 01:28 DEBUG  WindowsBackend: country=MY
05-10 01:28 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-10 01:28 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-10 01:28 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-10 01:28 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-10 01:28 DEBUG  WindowsBackend: windows_language_code=1033
05-10 01:28 DEBUG  WindowsBackend: windows_language=English
05-10 01:28 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-10 01:28 DEBUG  WindowsBackend: bootloader=vista
05-10 01:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 30571.5859375 mb free ntfs)
05-10 01:28 DEBUG  WindowsBackend: drive=Drive(C: hd 30571.5859375 mb free ntfs)
05-10 01:28 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.22265625 mb free ntfs)
05-10 01:28 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-10 01:28 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-10 01:28 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-10 01:28 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-10 01:28 DEBUG  WindowsBackend: keyboard_id=67699721
05-10 01:28 DEBUG  WindowsBackend: keyboard_layout=us
05-10 01:28 DEBUG  WindowsBackend: keyboard_variant=
05-10 01:28 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-10 01:28 DEBUG  CommonBackend: locale=en_US.UTF-8
05-10 01:28 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-10 01:28 DEBUG  CommonBackend: Searching ISOs on USB devices
05-10 01:28 DEBUG  CommonBackend: Searching for local CDs
05-10 01:28 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl13AE.tmp is a valid Ubuntu CD
05-10 01:28 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl13AE.tmp\casper\filesystem.squashfs
05-10 01:28 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl13AE.tmp is a valid Ubuntu CD
05-10 01:28 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl13AE.tmp\casper\filesystem.squashfs
05-10 01:28 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl13AE.tmp is a valid Ubuntu Netbook CD
05-10 01:28 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl13AE.tmp\casper\filesystem.squashfs
05-10 01:28 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl13AE.tmp is a valid Kubuntu CD
05-10 01:28 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl13AE.tmp\casper\filesystem.squashfs
05-10 01:28 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl13AE.tmp is a valid Kubuntu CD
05-10 01:28 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl13AE.tmp\casper\filesystem.squashfs
05-10 01:28 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl13AE.tmp is a valid Xubuntu CD
05-10 01:28 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl13AE.tmp\casper\filesystem.squashfs
05-10 01:28 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl13AE.tmp is a valid Xubuntu CD
05-10 01:28 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl13AE.tmp\casper\filesystem.squashfs
05-10 01:28 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl13AE.tmp is a valid Mythbuntu CD
05-10 01:28 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl13AE.tmp\casper\filesystem.squashfs
05-10 01:28 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl13AE.tmp is a valid Mythbuntu CD
05-10 01:28 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl13AE.tmp\casper\filesystem.squashfs
05-10 01:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 01:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 01:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-10 01:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 01:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 01:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 01:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 01:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 01:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 01:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-10 01:28 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-10 01:28 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-10 01:28 INFO   Distro: Found a valid CD for Ubuntu: E:\
05-10 01:28 INFO   root: Running the CD menu...
05-10 01:28 DEBUG  WindowsFrontend: __init__...
05-10 01:28 DEBUG  WindowsFrontend: on_init...
05-10 01:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl13AE.tmp\translations, languages=['en_US', 'en']
05-10 01:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl13AE.tmp\translations, languages=['en_US', 'en']
05-10 01:29 INFO   root: CD menu finished
05-10 01:29 DEBUG  CommonBackend: Showing info
05-10 01:29 DEBUG  root: application.quit
05-10 01:29 DEBUG  WindowsFrontend: frontend.quit
05-10 01:29 DEBUG  WindowsFrontend: frontend.on_quit
05-10 01:29 DEBUG  root: application.on_quit
05-10 01:29 INFO   root: sys.exit
05-10 01:29 INFO   root: === wubi 11.04 rev211 ===
05-10 01:29 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-10 01:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
05-10 01:29 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylC0CE.tmp\data
05-10 01:29 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pylC0CE.tmp\bin\7z.exe
05-10 01:29 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-10 01:29 DEBUG  CommonBackend: Fetching basic info...
05-10 01:29 DEBUG  CommonBackend: original_exe=E:\wubi.exe
05-10 01:29 DEBUG  CommonBackend: platform=win32
05-10 01:29 DEBUG  CommonBackend: osname=nt
05-10 01:29 DEBUG  CommonBackend: language=en_MY
05-10 01:29 DEBUG  CommonBackend: encoding=cp1252
05-10 01:29 DEBUG  WindowsBackend: arch=amd64
05-10 01:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pylC0CE.tmp\data\isolist.ini
05-10 01:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-10 01:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-10 01:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-10 01:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-10 01:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-10 01:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-10 01:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-10 01:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-10 01:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-10 01:29 DEBUG  WindowsBackend: Fetching host info...
05-10 01:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-10 01:29 DEBUG  WindowsBackend: windows version=vista
05-10 01:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-10 01:29 DEBUG  WindowsBackend: windows_sp=None
05-10 01:29 DEBUG  WindowsBackend: windows_build=7600
05-10 01:29 DEBUG  WindowsBackend: gmt=8
05-10 01:29 DEBUG  WindowsBackend: country=MY
05-10 01:29 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-10 01:29 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-10 01:29 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-10 01:29 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-10 01:29 DEBUG  WindowsBackend: windows_language_code=1033
05-10 01:29 DEBUG  WindowsBackend: windows_language=English
05-10 01:29 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-10 01:29 DEBUG  WindowsBackend: bootloader=vista
05-10 01:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 30570.3867188 mb free ntfs)
05-10 01:29 DEBUG  WindowsBackend: drive=Drive(C: hd 30570.3867188 mb free ntfs)
05-10 01:29 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.22265625 mb free ntfs)
05-10 01:29 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-10 01:29 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-10 01:29 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-10 01:29 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-10 01:29 DEBUG  WindowsBackend: keyboard_id=67699721
05-10 01:29 DEBUG  WindowsBackend: keyboard_layout=us
05-10 01:29 DEBUG  WindowsBackend: keyboard_variant=
05-10 01:29 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-10 01:29 DEBUG  CommonBackend: locale=en_US.UTF-8
05-10 01:29 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-10 01:29 DEBUG  CommonBackend: Searching ISOs on USB devices
05-10 01:29 DEBUG  CommonBackend: Searching for local CDs
05-10 01:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC0CE.tmp is a valid Ubuntu CD
05-10 01:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC0CE.tmp\casper\filesystem.squashfs
05-10 01:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC0CE.tmp is a valid Ubuntu CD
05-10 01:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC0CE.tmp\casper\filesystem.squashfs
05-10 01:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC0CE.tmp is a valid Ubuntu Netbook CD
05-10 01:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC0CE.tmp\casper\filesystem.squashfs
05-10 01:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC0CE.tmp is a valid Kubuntu CD
05-10 01:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC0CE.tmp\casper\filesystem.squashfs
05-10 01:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC0CE.tmp is a valid Kubuntu CD
05-10 01:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC0CE.tmp\casper\filesystem.squashfs
05-10 01:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC0CE.tmp is a valid Xubuntu CD
05-10 01:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC0CE.tmp\casper\filesystem.squashfs
05-10 01:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC0CE.tmp is a valid Xubuntu CD
05-10 01:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC0CE.tmp\casper\filesystem.squashfs
05-10 01:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC0CE.tmp is a valid Mythbuntu CD
05-10 01:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC0CE.tmp\casper\filesystem.squashfs
05-10 01:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC0CE.tmp is a valid Mythbuntu CD
05-10 01:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC0CE.tmp\casper\filesystem.squashfs
05-10 01:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 01:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 01:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-10 01:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 01:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 01:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 01:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 01:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 01:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 01:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 01:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-10 01:29 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-10 01:29 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-10 01:29 INFO   Distro: Found a valid CD for Ubuntu: E:\
05-10 01:29 INFO   root: Running the CD menu...
05-10 01:29 DEBUG  WindowsFrontend: __init__...
05-10 01:29 DEBUG  WindowsFrontend: on_init...
05-10 01:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylC0CE.tmp\translations, languages=['en_US', 'en']
05-10 01:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylC0CE.tmp\translations, languages=['en_US', 'en']
05-10 01:29 INFO   WindowsFrontend: Operation cancelled
05-10 01:29 DEBUG  WindowsFrontend: frontend.quit
05-10 01:29 DEBUG  WindowsFrontend: frontend.on_quit
05-10 01:29 DEBUG  root: application.on_quit
05-10 01:29 INFO   root: sys.exit
05-10 13:31 INFO   root: === wubi 11.04 rev211 ===
05-10 13:31 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-10 13:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
05-10 13:31 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylC11E.tmp\data
05-10 13:31 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pylC11E.tmp\bin\7z.exe
05-10 13:31 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-10 13:31 DEBUG  CommonBackend: Fetching basic info...
05-10 13:31 DEBUG  CommonBackend: original_exe=E:\wubi.exe
05-10 13:31 DEBUG  CommonBackend: platform=win32
05-10 13:31 DEBUG  CommonBackend: osname=nt
05-10 13:31 DEBUG  CommonBackend: language=en_MY
05-10 13:31 DEBUG  CommonBackend: encoding=cp1252
05-10 13:31 DEBUG  WindowsBackend: arch=amd64
05-10 13:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pylC11E.tmp\data\isolist.ini
05-10 13:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-10 13:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-10 13:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-10 13:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-10 13:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-10 13:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-10 13:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-10 13:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-10 13:31 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-10 13:31 DEBUG  WindowsBackend: Fetching host info...
05-10 13:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-10 13:31 DEBUG  WindowsBackend: windows version=vista
05-10 13:31 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-10 13:31 DEBUG  WindowsBackend: windows_sp=None
05-10 13:31 DEBUG  WindowsBackend: windows_build=7600
05-10 13:31 DEBUG  WindowsBackend: gmt=8
05-10 13:31 DEBUG  WindowsBackend: country=MY
05-10 13:31 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-10 13:31 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-10 13:31 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-10 13:31 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-10 13:31 DEBUG  WindowsBackend: windows_language_code=1033
05-10 13:31 DEBUG  WindowsBackend: windows_language=English
05-10 13:31 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-10 13:31 DEBUG  WindowsBackend: bootloader=vista
05-10 13:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 30551.2695313 mb free ntfs)
05-10 13:31 DEBUG  WindowsBackend: drive=Drive(C: hd 30551.2695313 mb free ntfs)
05-10 13:31 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.22265625 mb free ntfs)
05-10 13:31 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-10 13:31 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-10 13:31 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-10 13:31 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-10 13:31 DEBUG  WindowsBackend: keyboard_id=67699721
05-10 13:31 DEBUG  WindowsBackend: keyboard_layout=us
05-10 13:31 DEBUG  WindowsBackend: keyboard_variant=
05-10 13:31 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-10 13:31 DEBUG  CommonBackend: locale=en_US.UTF-8
05-10 13:31 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-10 13:31 DEBUG  CommonBackend: Searching ISOs on USB devices
05-10 13:31 DEBUG  CommonBackend: Searching for local CDs
05-10 13:31 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC11E.tmp is a valid Ubuntu CD
05-10 13:31 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC11E.tmp\casper\filesystem.squashfs
05-10 13:31 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC11E.tmp is a valid Ubuntu CD
05-10 13:31 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC11E.tmp\casper\filesystem.squashfs
05-10 13:31 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC11E.tmp is a valid Ubuntu Netbook CD
05-10 13:31 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC11E.tmp\casper\filesystem.squashfs
05-10 13:31 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC11E.tmp is a valid Kubuntu CD
05-10 13:31 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC11E.tmp\casper\filesystem.squashfs
05-10 13:31 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC11E.tmp is a valid Kubuntu CD
05-10 13:31 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC11E.tmp\casper\filesystem.squashfs
05-10 13:31 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC11E.tmp is a valid Xubuntu CD
05-10 13:31 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC11E.tmp\casper\filesystem.squashfs
05-10 13:31 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC11E.tmp is a valid Xubuntu CD
05-10 13:31 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC11E.tmp\casper\filesystem.squashfs
05-10 13:31 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC11E.tmp is a valid Mythbuntu CD
05-10 13:31 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC11E.tmp\casper\filesystem.squashfs
05-10 13:31 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC11E.tmp is a valid Mythbuntu CD
05-10 13:31 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC11E.tmp\casper\filesystem.squashfs
05-10 13:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 13:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 13:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 13:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 13:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-10 13:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 13:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 13:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 13:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 13:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 13:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 13:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 13:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 13:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 13:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 13:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 13:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 13:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 13:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-10 13:31 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-10 13:31 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-10 13:31 INFO   Distro: Found a valid CD for Ubuntu: E:\
05-10 13:31 INFO   root: Running the CD menu...
05-10 13:31 DEBUG  WindowsFrontend: __init__...
05-10 13:31 DEBUG  WindowsFrontend: on_init...
05-10 13:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylC11E.tmp\translations, languages=['en_US', 'en']
05-10 13:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylC11E.tmp\translations, languages=['en_US', 'en']
05-10 13:32 INFO   root: CD menu finished
05-10 13:32 INFO   root: Rebooting
05-10 13:32 DEBUG  TaskList: # Running tasklist...
05-10 13:32 DEBUG  TaskList: ## Running reboot...
05-10 13:32 DEBUG  TaskList: ## Finished reboot
05-10 13:32 DEBUG  TaskList: # Finished tasklist
05-10 13:32 DEBUG  root: application.quit
05-10 13:32 DEBUG  WindowsFrontend: frontend.quit
05-10 13:32 DEBUG  WindowsFrontend: frontend.on_quit
05-10 13:32 DEBUG  root: application.on_quit
05-10 13:32 INFO   root: sys.exit
05-10 16:29 INFO   root: === wubi 11.04 rev211 ===
05-10 16:29 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-10 16:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
05-10 16:29 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylC1B8.tmp\data
05-10 16:29 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pylC1B8.tmp\bin\7z.exe
05-10 16:29 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-10 16:29 DEBUG  CommonBackend: Fetching basic info...
05-10 16:29 DEBUG  CommonBackend: original_exe=E:\wubi.exe
05-10 16:29 DEBUG  CommonBackend: platform=win32
05-10 16:29 DEBUG  CommonBackend: osname=nt
05-10 16:29 DEBUG  CommonBackend: language=en_MY
05-10 16:29 DEBUG  CommonBackend: encoding=cp1252
05-10 16:29 DEBUG  WindowsBackend: arch=amd64
05-10 16:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pylC1B8.tmp\data\isolist.ini
05-10 16:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-10 16:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-10 16:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-10 16:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-10 16:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-10 16:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-10 16:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-10 16:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-10 16:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-10 16:29 DEBUG  WindowsBackend: Fetching host info...
05-10 16:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-10 16:29 DEBUG  WindowsBackend: windows version=vista
05-10 16:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-10 16:29 DEBUG  WindowsBackend: windows_sp=None
05-10 16:29 DEBUG  WindowsBackend: windows_build=7600
05-10 16:29 DEBUG  WindowsBackend: gmt=8
05-10 16:29 DEBUG  WindowsBackend: country=MY
05-10 16:29 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-10 16:29 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-10 16:29 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-10 16:29 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-10 16:29 DEBUG  WindowsBackend: windows_language_code=1033
05-10 16:29 DEBUG  WindowsBackend: windows_language=English
05-10 16:29 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-10 16:29 DEBUG  WindowsBackend: bootloader=vista
05-10 16:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 30555.1640625 mb free ntfs)
05-10 16:29 DEBUG  WindowsBackend: drive=Drive(C: hd 30555.1640625 mb free ntfs)
05-10 16:29 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.22265625 mb free ntfs)
05-10 16:29 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-10 16:29 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-10 16:29 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-10 16:29 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-10 16:29 DEBUG  WindowsBackend: keyboard_id=67699721
05-10 16:29 DEBUG  WindowsBackend: keyboard_layout=us
05-10 16:29 DEBUG  WindowsBackend: keyboard_variant=
05-10 16:29 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-10 16:29 DEBUG  CommonBackend: locale=en_US.UTF-8
05-10 16:29 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-10 16:29 DEBUG  CommonBackend: Searching ISOs on USB devices
05-10 16:29 DEBUG  CommonBackend: Searching for local CDs
05-10 16:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC1B8.tmp is a valid Ubuntu CD
05-10 16:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC1B8.tmp\casper\filesystem.squashfs
05-10 16:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC1B8.tmp is a valid Ubuntu CD
05-10 16:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC1B8.tmp\casper\filesystem.squashfs
05-10 16:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC1B8.tmp is a valid Ubuntu Netbook CD
05-10 16:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC1B8.tmp\casper\filesystem.squashfs
05-10 16:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC1B8.tmp is a valid Kubuntu CD
05-10 16:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC1B8.tmp\casper\filesystem.squashfs
05-10 16:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC1B8.tmp is a valid Kubuntu CD
05-10 16:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC1B8.tmp\casper\filesystem.squashfs
05-10 16:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC1B8.tmp is a valid Xubuntu CD
05-10 16:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC1B8.tmp\casper\filesystem.squashfs
05-10 16:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC1B8.tmp is a valid Xubuntu CD
05-10 16:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC1B8.tmp\casper\filesystem.squashfs
05-10 16:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC1B8.tmp is a valid Mythbuntu CD
05-10 16:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC1B8.tmp\casper\filesystem.squashfs
05-10 16:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC1B8.tmp is a valid Mythbuntu CD
05-10 16:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC1B8.tmp\casper\filesystem.squashfs
05-10 16:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 16:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 16:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-10 16:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 16:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 16:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 16:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 16:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 16:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 16:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-10 16:29 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-10 16:29 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-10 16:29 INFO   Distro: Found a valid CD for Ubuntu: E:\
05-10 16:29 INFO   root: Running the CD menu...
05-10 16:29 DEBUG  WindowsFrontend: __init__...
05-10 16:29 DEBUG  WindowsFrontend: on_init...
05-10 16:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylC1B8.tmp\translations, languages=['en_US', 'en']
05-10 16:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylC1B8.tmp\translations, languages=['en_US', 'en']
05-10 16:30 INFO   WindowsFrontend: Operation cancelled
05-10 16:30 DEBUG  WindowsFrontend: frontend.quit
05-10 16:30 DEBUG  WindowsFrontend: frontend.on_quit
05-10 16:30 DEBUG  root: application.on_quit
05-10 16:30 INFO   root: sys.exit
05-10 16:50 INFO   root: === wubi 11.04 rev211 ===
05-10 16:50 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-10 16:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
05-10 16:50 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66AE.tmp\data
05-10 16:50 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66AE.tmp\bin\7z.exe
05-10 16:50 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-10 16:50 DEBUG  CommonBackend: Fetching basic info...
05-10 16:50 DEBUG  CommonBackend: original_exe=E:\wubi.exe
05-10 16:50 DEBUG  CommonBackend: platform=win32
05-10 16:50 DEBUG  CommonBackend: osname=nt
05-10 16:50 DEBUG  CommonBackend: language=en_MY
05-10 16:50 DEBUG  CommonBackend: encoding=cp1252
05-10 16:50 DEBUG  WindowsBackend: arch=amd64
05-10 16:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66AE.tmp\data\isolist.ini
05-10 16:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-10 16:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-10 16:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-10 16:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-10 16:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-10 16:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-10 16:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-10 16:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-10 16:50 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-10 16:50 DEBUG  WindowsBackend: Fetching host info...
05-10 16:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-10 16:50 DEBUG  WindowsBackend: windows version=vista
05-10 16:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-10 16:50 DEBUG  WindowsBackend: windows_sp=None
05-10 16:50 DEBUG  WindowsBackend: windows_build=7600
05-10 16:50 DEBUG  WindowsBackend: gmt=8
05-10 16:50 DEBUG  WindowsBackend: country=MY
05-10 16:50 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-10 16:50 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-10 16:50 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-10 16:50 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-10 16:50 DEBUG  WindowsBackend: windows_language_code=1033
05-10 16:50 DEBUG  WindowsBackend: windows_language=English
05-10 16:50 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-10 16:50 DEBUG  WindowsBackend: bootloader=vista
05-10 16:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 30548.890625 mb free ntfs)
05-10 16:50 DEBUG  WindowsBackend: drive=Drive(C: hd 30548.890625 mb free ntfs)
05-10 16:50 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.22265625 mb free ntfs)
05-10 16:50 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-10 16:50 DEBUG  WindowsBackend: drive=Drive(I: removable 1865.76171875 mb free ntfs)
05-10 16:50 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-10 16:50 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-10 16:50 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-10 16:50 DEBUG  WindowsBackend: keyboard_id=67699721
05-10 16:50 DEBUG  WindowsBackend: keyboard_layout=us
05-10 16:50 DEBUG  WindowsBackend: keyboard_variant=
05-10 16:50 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-10 16:50 DEBUG  CommonBackend: locale=en_US.UTF-8
05-10 16:50 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-10 16:50 DEBUG  CommonBackend: Searching ISOs on USB devices
05-10 16:50 DEBUG  CommonBackend: Searching for local CDs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66AE.tmp is a valid Ubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66AE.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66AE.tmp is a valid Ubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66AE.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66AE.tmp is a valid Ubuntu Netbook CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66AE.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66AE.tmp is a valid Kubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66AE.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66AE.tmp is a valid Kubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66AE.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66AE.tmp is a valid Xubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66AE.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66AE.tmp is a valid Xubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66AE.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66AE.tmp is a valid Mythbuntu CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66AE.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66AE.tmp is a valid Mythbuntu CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66AE.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-10 16:50 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-10 16:50 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-10 16:50 INFO   Distro: Found a valid CD for Ubuntu: E:\
05-10 16:50 INFO   root: Running the CD menu...
05-10 16:50 DEBUG  WindowsFrontend: __init__...
05-10 16:50 DEBUG  WindowsFrontend: on_init...
05-10 16:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66AE.tmp\translations, languages=['en_US', 'en']
05-10 16:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66AE.tmp\translations, languages=['en_US', 'en']
05-10 16:50 INFO   root: === wubi 11.04 rev211 ===
05-10 16:50 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-10 16:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
05-10 16:50 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6FB3.tmp\data
05-10 16:50 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6FB3.tmp\bin\7z.exe
05-10 16:50 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-10 16:50 DEBUG  CommonBackend: Fetching basic info...
05-10 16:50 DEBUG  CommonBackend: original_exe=E:\wubi.exe
05-10 16:50 DEBUG  CommonBackend: platform=win32
05-10 16:50 DEBUG  CommonBackend: osname=nt
05-10 16:50 DEBUG  CommonBackend: language=en_MY
05-10 16:50 DEBUG  CommonBackend: encoding=cp1252
05-10 16:50 DEBUG  WindowsBackend: arch=amd64
05-10 16:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6FB3.tmp\data\isolist.ini
05-10 16:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-10 16:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-10 16:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-10 16:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-10 16:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-10 16:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-10 16:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-10 16:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-10 16:50 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-10 16:50 DEBUG  WindowsBackend: Fetching host info...
05-10 16:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-10 16:50 DEBUG  WindowsBackend: windows version=vista
05-10 16:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-10 16:50 DEBUG  WindowsBackend: windows_sp=None
05-10 16:50 DEBUG  WindowsBackend: windows_build=7600
05-10 16:50 DEBUG  WindowsBackend: gmt=8
05-10 16:50 DEBUG  WindowsBackend: country=MY
05-10 16:50 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-10 16:50 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-10 16:50 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-10 16:50 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-10 16:50 DEBUG  WindowsBackend: windows_language_code=1033
05-10 16:50 DEBUG  WindowsBackend: windows_language=English
05-10 16:50 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-10 16:50 DEBUG  WindowsBackend: bootloader=vista
05-10 16:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 30547.6796875 mb free ntfs)
05-10 16:50 DEBUG  WindowsBackend: drive=Drive(C: hd 30547.6796875 mb free ntfs)
05-10 16:50 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.22265625 mb free ntfs)
05-10 16:50 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-10 16:50 DEBUG  WindowsBackend: drive=Drive(I: removable 1865.76171875 mb free ntfs)
05-10 16:50 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-10 16:50 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-10 16:50 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-10 16:50 DEBUG  WindowsBackend: keyboard_id=67699721
05-10 16:50 DEBUG  WindowsBackend: keyboard_layout=us
05-10 16:50 DEBUG  WindowsBackend: keyboard_variant=
05-10 16:50 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-10 16:50 DEBUG  CommonBackend: locale=en_US.UTF-8
05-10 16:50 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-10 16:50 DEBUG  CommonBackend: Searching ISOs on USB devices
05-10 16:50 DEBUG  CommonBackend: Searching for local CDs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6FB3.tmp is a valid Ubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6FB3.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6FB3.tmp is a valid Ubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6FB3.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6FB3.tmp is a valid Ubuntu Netbook CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6FB3.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6FB3.tmp is a valid Kubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6FB3.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6FB3.tmp is a valid Kubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6FB3.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6FB3.tmp is a valid Xubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6FB3.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6FB3.tmp is a valid Xubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6FB3.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6FB3.tmp is a valid Mythbuntu CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6FB3.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6FB3.tmp is a valid Mythbuntu CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6FB3.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-10 16:50 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-10 16:50 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-10 16:50 INFO   Distro: Found a valid CD for Ubuntu: E:\
05-10 16:50 INFO   root: Running the CD menu...
05-10 16:50 DEBUG  WindowsFrontend: __init__...
05-10 16:50 DEBUG  WindowsFrontend: on_init...
05-10 16:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6FB3.tmp\translations, languages=['en_US', 'en']
05-10 16:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6FB3.tmp\translations, languages=['en_US', 'en']
05-10 16:50 INFO   WindowsFrontend: Operation cancelled
05-10 16:50 DEBUG  WindowsFrontend: frontend.quit
05-10 16:50 DEBUG  WindowsFrontend: frontend.on_quit
05-10 16:50 DEBUG  root: application.on_quit
05-10 16:50 INFO   root: sys.exit
05-10 16:50 INFO   WindowsFrontend: Operation cancelled
05-10 16:50 DEBUG  WindowsFrontend: frontend.quit
05-10 16:50 DEBUG  WindowsFrontend: frontend.on_quit
05-10 16:50 DEBUG  root: application.on_quit
05-10 16:50 INFO   root: sys.exit
05-10 16:50 INFO   root: === wubi 11.04 rev211 ===
05-10 16:50 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-10 16:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
05-10 16:50 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl9BE1.tmp\data
05-10 16:50 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl9BE1.tmp\bin\7z.exe
05-10 16:50 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-10 16:50 DEBUG  CommonBackend: Fetching basic info...
05-10 16:50 DEBUG  CommonBackend: original_exe=E:\wubi.exe
05-10 16:50 DEBUG  CommonBackend: platform=win32
05-10 16:50 DEBUG  CommonBackend: osname=nt
05-10 16:50 DEBUG  CommonBackend: language=en_MY
05-10 16:50 DEBUG  CommonBackend: encoding=cp1252
05-10 16:50 DEBUG  WindowsBackend: arch=amd64
05-10 16:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl9BE1.tmp\data\isolist.ini
05-10 16:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-10 16:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-10 16:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-10 16:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-10 16:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-10 16:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-10 16:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-10 16:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-10 16:50 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-10 16:50 DEBUG  WindowsBackend: Fetching host info...
05-10 16:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-10 16:50 DEBUG  WindowsBackend: windows version=vista
05-10 16:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-10 16:50 DEBUG  WindowsBackend: windows_sp=None
05-10 16:50 DEBUG  WindowsBackend: windows_build=7600
05-10 16:50 DEBUG  WindowsBackend: gmt=8
05-10 16:50 DEBUG  WindowsBackend: country=MY
05-10 16:50 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-10 16:50 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-10 16:50 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-10 16:50 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-10 16:50 DEBUG  WindowsBackend: windows_language_code=1033
05-10 16:50 DEBUG  WindowsBackend: windows_language=English
05-10 16:50 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-10 16:50 DEBUG  WindowsBackend: bootloader=vista
05-10 16:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 30549.2539063 mb free ntfs)
05-10 16:50 DEBUG  WindowsBackend: drive=Drive(C: hd 30549.2539063 mb free ntfs)
05-10 16:50 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.22265625 mb free ntfs)
05-10 16:50 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-10 16:50 DEBUG  WindowsBackend: drive=Drive(I: removable 1865.76171875 mb free ntfs)
05-10 16:50 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-10 16:50 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-10 16:50 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-10 16:50 DEBUG  WindowsBackend: keyboard_id=67699721
05-10 16:50 DEBUG  WindowsBackend: keyboard_layout=us
05-10 16:50 DEBUG  WindowsBackend: keyboard_variant=
05-10 16:50 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-10 16:50 DEBUG  CommonBackend: locale=en_US.UTF-8
05-10 16:50 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-10 16:50 DEBUG  CommonBackend: Searching ISOs on USB devices
05-10 16:50 DEBUG  CommonBackend: Searching for local CDs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl9BE1.tmp is a valid Ubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl9BE1.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl9BE1.tmp is a valid Ubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl9BE1.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl9BE1.tmp is a valid Ubuntu Netbook CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl9BE1.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl9BE1.tmp is a valid Kubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl9BE1.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl9BE1.tmp is a valid Kubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl9BE1.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl9BE1.tmp is a valid Xubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl9BE1.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl9BE1.tmp is a valid Xubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl9BE1.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl9BE1.tmp is a valid Mythbuntu CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl9BE1.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl9BE1.tmp is a valid Mythbuntu CD
05-10 16:50 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl9BE1.tmp\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 16:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 16:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-10 16:50 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-10 16:50 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-10 16:50 INFO   Distro: Found a valid CD for Ubuntu: E:\
05-10 16:50 INFO   root: Running the CD menu...
05-10 16:50 DEBUG  WindowsFrontend: __init__...
05-10 16:50 DEBUG  WindowsFrontend: on_init...
05-10 16:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl9BE1.tmp\translations, languages=['en_US', 'en']
05-10 16:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl9BE1.tmp\translations, languages=['en_US', 'en']
05-10 16:50 INFO   WindowsFrontend: Operation cancelled
05-10 16:50 DEBUG  WindowsFrontend: frontend.quit
05-10 16:50 DEBUG  WindowsFrontend: frontend.on_quit
05-10 16:50 DEBUG  root: application.on_quit
05-10 16:50 INFO   root: sys.exit
05-10 18:13 INFO   root: === wubi 11.04 rev211 ===
05-10 18:13 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-10 18:13 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
05-10 18:13 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\data
05-10 18:13 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\bin\7z.exe
05-10 18:13 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-10 18:13 DEBUG  CommonBackend: Fetching basic info...
05-10 18:13 DEBUG  CommonBackend: original_exe=E:\wubi.exe
05-10 18:13 DEBUG  CommonBackend: platform=win32
05-10 18:13 DEBUG  CommonBackend: osname=nt
05-10 18:13 DEBUG  CommonBackend: language=en_MY
05-10 18:13 DEBUG  CommonBackend: encoding=cp1252
05-10 18:13 DEBUG  WindowsBackend: arch=amd64
05-10 18:13 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\data\isolist.ini
05-10 18:13 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-10 18:13 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-10 18:13 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-10 18:13 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-10 18:13 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-10 18:13 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-10 18:13 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-10 18:13 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-10 18:13 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-10 18:13 DEBUG  WindowsBackend: Fetching host info...
05-10 18:13 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-10 18:13 DEBUG  WindowsBackend: windows version=vista
05-10 18:13 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-10 18:13 DEBUG  WindowsBackend: windows_sp=None
05-10 18:13 DEBUG  WindowsBackend: windows_build=7600
05-10 18:13 DEBUG  WindowsBackend: gmt=8
05-10 18:13 DEBUG  WindowsBackend: country=MY
05-10 18:13 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-10 18:13 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-10 18:13 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-10 18:13 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-10 18:13 DEBUG  WindowsBackend: windows_language_code=1033
05-10 18:13 DEBUG  WindowsBackend: windows_language=English
05-10 18:13 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-10 18:13 DEBUG  WindowsBackend: bootloader=vista
05-10 18:13 DEBUG  WindowsBackend: system_drive=Drive(C: hd 30542.1328125 mb free ntfs)
05-10 18:13 DEBUG  WindowsBackend: drive=Drive(C: hd 30542.1328125 mb free ntfs)
05-10 18:13 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.22265625 mb free ntfs)
05-10 18:13 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-10 18:13 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
05-10 18:13 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free ntfs)
05-10 18:13 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-10 18:13 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-10 18:13 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-10 18:13 DEBUG  WindowsBackend: keyboard_id=67699721
05-10 18:13 DEBUG  WindowsBackend: keyboard_layout=us
05-10 18:13 DEBUG  WindowsBackend: keyboard_variant=
05-10 18:13 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-10 18:13 DEBUG  CommonBackend: locale=en_US.UTF-8
05-10 18:13 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-10 18:13 DEBUG  CommonBackend: Searching ISOs on USB devices
05-10 18:13 DEBUG  CommonBackend: Searching for local CDs
05-10 18:13 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp is a valid Ubuntu CD
05-10 18:13 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp is a valid Ubuntu CD
05-10 18:13 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp is a valid Ubuntu Netbook CD
05-10 18:13 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp is a valid Kubuntu CD
05-10 18:13 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp is a valid Kubuntu CD
05-10 18:13 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp is a valid Xubuntu CD
05-10 18:13 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp is a valid Xubuntu CD
05-10 18:13 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp is a valid Mythbuntu CD
05-10 18:13 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp is a valid Mythbuntu CD
05-10 18:13 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-10 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-10 18:13 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-10 18:13 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-10 18:13 INFO   Distro: Found a valid CD for Ubuntu: E:\
05-10 18:13 INFO   root: Running the CD menu...
05-10 18:13 DEBUG  WindowsFrontend: __init__...
05-10 18:13 DEBUG  WindowsFrontend: on_init...
05-10 18:13 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\translations, languages=['en_US', 'en']
05-10 18:13 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\translations, languages=['en_US', 'en']
05-10 18:13 INFO   root: CD menu finished
05-10 18:13 INFO   root: Already installed, running the uninstaller...
05-10 18:13 INFO   root: Running the uninstaller...
05-10 18:13 INFO   CommonBackend: This is the uninstaller running
05-10 18:13 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\translations, languages=['en_US', 'en']
05-10 18:13 INFO   root: Received settings
05-10 18:13 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\translations, languages=['en_US', 'en']
05-10 18:13 DEBUG  TaskList: # Running tasklist...
05-10 18:13 DEBUG  TaskList: ## Running Backup ISO...
05-10 18:13 DEBUG  TaskList: ## Finished Backup ISO
05-10 18:13 DEBUG  TaskList: ## Running Remove bootloader entry...
05-10 18:13 DEBUG  WindowsBackend: Removing bcd entry {633128b6-bc48-11df-a1e8-fd8ecb34e649}
05-10 18:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
05-10 18:13 DEBUG  WindowsBackend: undo_bootini C:
05-10 18:13 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 30542.1328125 mb free ntfs)
05-10 18:13 DEBUG  WindowsBackend: undo_bootini D:
05-10 18:13 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2105.22265625 mb free ntfs)
05-10 18:13 DEBUG  WindowsBackend: undo_bootini F:
05-10 18:13 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
05-10 18:13 DEBUG  WindowsBackend: undo_bootini I:
05-10 18:13 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free ntfs)
05-10 18:13 DEBUG  TaskList: ## Finished Remove bootloader entry
05-10 18:13 DEBUG  TaskList: ## Running Remove target dir...
05-10 18:13 DEBUG  CommonBackend: Deleting C:\ubuntu
05-10 18:13 DEBUG  TaskList: ## Finished Remove target dir
05-10 18:13 DEBUG  TaskList: ## Running Remove registry key...
05-10 18:13 DEBUG  TaskList: ## Finished Remove registry key
05-10 18:13 DEBUG  TaskList: # Finished tasklist
05-10 18:13 INFO   root: Almost finished uninstalling
05-10 18:13 INFO   root: Finished uninstallation
05-10 18:13 DEBUG  CommonBackend: Fetching basic info...
05-10 18:13 DEBUG  CommonBackend: original_exe=E:\wubi.exe
05-10 18:13 DEBUG  CommonBackend: platform=win32
05-10 18:13 DEBUG  CommonBackend: osname=nt
05-10 18:13 DEBUG  WindowsBackend: arch=amd64
05-10 18:13 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\data\isolist.ini
05-10 18:13 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-10 18:13 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-10 18:13 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-10 18:13 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-10 18:13 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-10 18:13 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-10 18:13 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-10 18:13 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-10 18:13 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-10 18:13 DEBUG  WindowsBackend: Fetching host info...
05-10 18:13 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-10 18:13 DEBUG  WindowsBackend: windows version=vista
05-10 18:13 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-10 18:13 DEBUG  WindowsBackend: windows_sp=None
05-10 18:13 DEBUG  WindowsBackend: windows_build=7600
05-10 18:13 DEBUG  WindowsBackend: gmt=8
05-10 18:13 DEBUG  WindowsBackend: country=MY
05-10 18:13 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-10 18:13 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-10 18:13 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-10 18:13 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-10 18:13 DEBUG  WindowsBackend: windows_language_code=1033
05-10 18:13 DEBUG  WindowsBackend: windows_language=English
05-10 18:13 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-10 18:13 DEBUG  WindowsBackend: bootloader=vista
05-10 18:13 DEBUG  WindowsBackend: system_drive=Drive(C: hd 48246.3085938 mb free ntfs)
05-10 18:13 DEBUG  WindowsBackend: drive=Drive(C: hd 48246.3085938 mb free ntfs)
05-10 18:13 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.22265625 mb free ntfs)
05-10 18:13 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-10 18:13 DEBUG  WindowsBackend: uninstaller_path=None
05-10 18:13 DEBUG  WindowsBackend: previous_target_dir=None
05-10 18:13 DEBUG  WindowsBackend: previous_distro_name=None
05-10 18:13 DEBUG  WindowsBackend: keyboard_id=67699721
05-10 18:13 DEBUG  WindowsBackend: keyboard_layout=us
05-10 18:13 DEBUG  WindowsBackend: keyboard_variant=
05-10 18:13 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-10 18:13 DEBUG  CommonBackend: Searching ISOs on USB devices
05-10 18:13 DEBUG  CommonBackend: Searching for local CDs
05-10 18:13 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp is a valid Ubuntu CD
05-10 18:13 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp is a valid Ubuntu CD
05-10 18:13 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp is a valid Ubuntu Netbook CD
05-10 18:13 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp is a valid Kubuntu CD
05-10 18:13 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp is a valid Kubuntu CD
05-10 18:13 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp is a valid Xubuntu CD
05-10 18:13 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp is a valid Xubuntu CD
05-10 18:13 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp is a valid Mythbuntu CD
05-10 18:13 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp is a valid Mythbuntu CD
05-10 18:13 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-10 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:13 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-10 18:13 INFO   Distro: Found a valid CD for Ubuntu: E:\
05-10 18:13 INFO   root: Running the installer...
05-10 18:13 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\translations, languages=['en_US', 'en']
05-10 18:13 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\translations, languages=['en_US', 'en']
05-10 18:13 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=audibinmarwoto
05-10 18:13 INFO   root: Received settings
05-10 18:13 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\translations, languages=['en_US', 'en']
05-10 18:13 DEBUG  TaskList: # Running tasklist...
05-10 18:13 DEBUG  TaskList: ## Running select_target_dir...
05-10 18:13 INFO   WindowsBackend: Installing into C:\ubuntu
05-10 18:13 DEBUG  TaskList: ## Finished select_target_dir
05-10 18:13 DEBUG  TaskList: ## Running create_dir_structure...
05-10 18:13 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-10 18:13 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-10 18:13 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-10 18:13 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-10 18:13 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-10 18:13 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-10 18:13 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-10 18:13 DEBUG  TaskList: ## Finished create_dir_structure
05-10 18:13 DEBUG  TaskList: ## Running uncompress_target_dir...
05-10 18:13 DEBUG  TaskList: ## Finished uncompress_target_dir
05-10 18:13 DEBUG  TaskList: ## Running create_uninstaller...
05-10 18:13 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-10 18:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-10 18:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-10 18:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-10 18:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-10 18:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-10 18:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-10 18:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-10 18:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-10 18:13 DEBUG  TaskList: ## Finished create_uninstaller
05-10 18:13 DEBUG  TaskList: ## Running copy_installation_files...
05-10 18:13 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-10 18:13 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\winboot -> C:\ubuntu\winboot
05-10 18:13 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-10 18:13 DEBUG  TaskList: ## Finished copy_installation_files
05-10 18:13 DEBUG  TaskList: ## Running get_iso...
05-10 18:13 DEBUG  TaskList: New task copy_file
05-10 18:13 DEBUG  TaskList: ### Running copy_file...
05-10 18:14 DEBUG  TaskList: ### Finished copy_file
05-10 18:14 DEBUG  TaskList: New task check_iso
05-10 18:14 DEBUG  TaskList: ### Running check_iso...
05-10 18:14 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
05-10 18:14 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
05-10 18:14 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
05-10 18:14 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-10 18:14 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-10 18:14 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
05-10 18:14 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
05-10 18:14 DEBUG  TaskList: New task get_metalink
05-10 18:14 DEBUG  TaskList: #### Running get_metalink...
05-10 18:14 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink) > C:\ubuntu\install
05-10 18:14 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
05-10 18:14 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.metalink) > C:\ubuntu\install
05-10 18:14 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
05-10 18:14 DEBUG  TaskList: #### Finished get_metalink
05-10 18:14 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for C:\ubuntu\install\installation.iso, ignoring
05-10 18:14 DEBUG  TaskList: ### Finished check_iso
05-10 18:14 DEBUG  TaskList: ## Finished get_iso
05-10 18:14 DEBUG  TaskList: ## Running extract_kernel...
05-10 18:14 DEBUG  CommonBackend: Copying files from CD E:\
05-10 18:14 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
05-10 18:14 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
05-10 18:14 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = db0104e80bc7e667344a14af3515de25 == db0104e80bc7e667344a14af3515de25
05-10 18:14 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
05-10 18:14 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = 4b776cdafb272064bb70e09ba212e4aa == 4b776cdafb272064bb70e09ba212e4aa
05-10 18:14 DEBUG  TaskList: ## Finished extract_kernel
05-10 18:14 DEBUG  TaskList: ## Running choose_disk_sizes...
05-10 18:14 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
05-10 18:14 DEBUG  TaskList: ## Finished choose_disk_sizes
05-10 18:14 DEBUG  TaskList: ## Running create_preseed...
05-10 18:14 DEBUG  TaskList: ## Finished create_preseed
05-10 18:14 DEBUG  TaskList: ## Running modify_bootloader...
05-10 18:14 DEBUG  TaskList: New task modify_bcd
05-10 18:14 DEBUG  TaskList: ### Running modify_bcd...
05-10 18:14 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 48246.3085938 mb free ntfs)
05-10 18:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {633128b7-bc48-11df-a1e8-fd8ecb34e649}
05-10 18:14 DEBUG  TaskList: ### Finished modify_bcd
05-10 18:14 DEBUG  TaskList: New task modify_bcd
05-10 18:14 DEBUG  TaskList: ### Running modify_bcd...
05-10 18:14 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 2105.22265625 mb free ntfs)
05-10 18:14 DEBUG  WindowsBackend: BCD has already been modified
05-10 18:14 DEBUG  TaskList: ### Finished modify_bcd
05-10 18:14 DEBUG  TaskList: ## Finished modify_bootloader
05-10 18:14 DEBUG  TaskList: ## Running modify_grub_configuration...
05-10 18:14 DEBUG  TaskList: ## Finished modify_grub_configuration
05-10 18:14 DEBUG  TaskList: ## Running create_virtual_disks...
05-10 18:14 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\root.disk of 16744MB
05-10 18:14 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\swap.disk of 256MB
05-10 18:14 DEBUG  TaskList: ## Finished create_virtual_disks
05-10 18:14 DEBUG  TaskList: ## Running uncompress_files...
05-10 18:14 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
05-10 18:14 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
05-10 18:14 DEBUG  TaskList: ## Finished uncompress_files
05-10 18:14 DEBUG  TaskList: ## Running eject_cd...
05-10 18:14 DEBUG  TaskList: ## Finished eject_cd
05-10 18:14 DEBUG  TaskList: # Finished tasklist
05-10 18:14 INFO   root: Almost finished installing
05-10 18:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl8E89.tmp\translations, languages=['en_US', 'en']
05-10 18:14 INFO   root: Finished installation
05-10 18:14 DEBUG  root: application.quit
05-10 18:14 DEBUG  WindowsFrontend: frontend.quit
05-10 18:14 DEBUG  WindowsFrontend: frontend.on_quit
05-10 18:14 DEBUG  root: application.on_quit
05-10 18:14 INFO   root: sys.exit
05-10 18:49 INFO   root: === wubi 11.04 rev211 ===
05-10 18:49 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-10 18:49 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
05-10 18:49 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl22BC.tmp\data
05-10 18:49 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl22BC.tmp\bin\7z.exe
05-10 18:49 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-10 18:49 DEBUG  CommonBackend: Fetching basic info...
05-10 18:49 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
05-10 18:49 DEBUG  CommonBackend: platform=win32
05-10 18:49 DEBUG  CommonBackend: osname=nt
05-10 18:49 DEBUG  CommonBackend: language=en_MY
05-10 18:49 DEBUG  CommonBackend: encoding=cp1252
05-10 18:49 DEBUG  WindowsBackend: arch=amd64
05-10 18:49 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl22BC.tmp\data\isolist.ini
05-10 18:49 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-10 18:49 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-10 18:49 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-10 18:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-10 18:49 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-10 18:49 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-10 18:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-10 18:49 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-10 18:49 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-10 18:49 DEBUG  WindowsBackend: Fetching host info...
05-10 18:49 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-10 18:49 DEBUG  WindowsBackend: windows version=vista
05-10 18:49 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-10 18:49 DEBUG  WindowsBackend: windows_sp=None
05-10 18:49 DEBUG  WindowsBackend: windows_build=7600
05-10 18:49 DEBUG  WindowsBackend: gmt=8
05-10 18:49 DEBUG  WindowsBackend: country=MY
05-10 18:49 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-10 18:49 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-10 18:49 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-10 18:49 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-10 18:49 DEBUG  WindowsBackend: windows_language_code=1033
05-10 18:49 DEBUG  WindowsBackend: windows_language=English
05-10 18:49 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-10 18:49 DEBUG  WindowsBackend: bootloader=vista
05-10 18:49 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29437.4140625 mb free ntfs)
05-10 18:49 DEBUG  WindowsBackend: drive=Drive(C: hd 29437.4140625 mb free ntfs)
05-10 18:49 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.22265625 mb free ntfs)
05-10 18:49 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
05-10 18:49 DEBUG  WindowsBackend: drive=Drive(J: removable 2681.265625 mb free fat32)
05-10 18:49 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-10 18:49 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-10 18:49 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-10 18:49 DEBUG  WindowsBackend: keyboard_id=67699721
05-10 18:49 DEBUG  WindowsBackend: keyboard_layout=us
05-10 18:49 DEBUG  WindowsBackend: keyboard_variant=
05-10 18:49 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-10 18:49 DEBUG  CommonBackend: locale=en_US.UTF-8
05-10 18:49 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-10 18:49 DEBUG  CommonBackend: Searching ISOs on USB devices
05-10 18:49 DEBUG  CommonBackend: Searching for local CDs
05-10 18:49 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl22BC.tmp is a valid Ubuntu CD
05-10 18:49 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl22BC.tmp\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl22BC.tmp is a valid Ubuntu CD
05-10 18:49 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl22BC.tmp\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl22BC.tmp is a valid Ubuntu Netbook CD
05-10 18:49 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl22BC.tmp\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl22BC.tmp is a valid Kubuntu CD
05-10 18:49 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl22BC.tmp\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl22BC.tmp is a valid Kubuntu CD
05-10 18:49 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl22BC.tmp\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl22BC.tmp is a valid Xubuntu CD
05-10 18:49 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl22BC.tmp\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl22BC.tmp is a valid Xubuntu CD
05-10 18:49 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl22BC.tmp\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl22BC.tmp is a valid Mythbuntu CD
05-10 18:49 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl22BC.tmp\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl22BC.tmp is a valid Mythbuntu CD
05-10 18:49 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl22BC.tmp\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-10 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-10 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-10 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-10 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-10 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-10 18:49 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-10 18:49 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
05-10 18:49 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-10 18:49 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-10 18:49 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-10 18:49 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-10 18:49 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-10 18:49 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-10 18:49 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-10 18:49 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-10 18:49 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
05-10 18:49 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-10 18:49 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-10 18:49 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-10 18:49 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-10 18:49 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-10 18:49 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-10 18:49 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-10 18:49 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-10 18:49 INFO   root: Running the uninstaller...
05-10 18:49 INFO   CommonBackend: This is the uninstaller running
05-10 18:49 DEBUG  WindowsFrontend: __init__...
05-10 18:49 DEBUG  WindowsFrontend: on_init...
05-10 18:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl22BC.tmp\translations, languages=['en_US', 'en']
05-10 18:49 INFO   root: Received settings
05-10 18:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl22BC.tmp\translations, languages=['en_US', 'en']
05-10 18:49 DEBUG  TaskList: # Running tasklist...
05-10 18:49 DEBUG  TaskList: ## Running Backup ISO...
05-10 18:49 DEBUG  TaskList: ## Finished Backup ISO
05-10 18:49 DEBUG  TaskList: ## Running Remove bootloader entry...
05-10 18:49 DEBUG  WindowsBackend: Removing bcd entry {633128b7-bc48-11df-a1e8-fd8ecb34e649}
05-10 18:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
05-10 18:49 DEBUG  WindowsBackend: undo_bootini C:
05-10 18:49 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 29437.4140625 mb free ntfs)
05-10 18:49 DEBUG  WindowsBackend: undo_bootini D:
05-10 18:49 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2105.22265625 mb free ntfs)
05-10 18:49 DEBUG  WindowsBackend: undo_bootini J:
05-10 18:49 DEBUG  WindowsBackend: undo_configsys Drive(J: removable 2681.265625 mb free fat32)
05-10 18:49 DEBUG  TaskList: ## Finished Remove bootloader entry
05-10 18:49 DEBUG  TaskList: ## Running Remove target dir...
05-10 18:49 DEBUG  CommonBackend: Deleting C:\ubuntu
05-10 18:49 DEBUG  TaskList: ## Finished Remove target dir
05-10 18:49 DEBUG  TaskList: ## Running Remove registry key...
05-10 18:49 DEBUG  TaskList: ## Finished Remove registry key
05-10 18:49 DEBUG  TaskList: # Finished tasklist
05-10 18:49 INFO   root: Almost finished uninstalling
05-10 18:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl22BC.tmp\translations, languages=['en_US', 'en']
05-10 18:50 INFO   root: Finished uninstallation
05-10 18:50 DEBUG  root: application.quit
05-10 18:50 DEBUG  WindowsFrontend: frontend.quit
05-10 18:50 DEBUG  WindowsFrontend: frontend.on_quit
05-10 18:50 DEBUG  root: application.on_quit
05-10 18:50 INFO   root: sys.exit
05-13 04:18 INFO   root: === wubi 11.04 rev211 ===
05-13 04:18 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-13 04:18 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\audi bin marwoto\\Downloads\\Programs\\wubi.exe"']
05-13 04:18 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66A2.tmp\data
05-13 04:18 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66A2.tmp\bin\7z.exe
05-13 04:18 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-13 04:18 DEBUG  CommonBackend: Fetching basic info...
05-13 04:18 DEBUG  CommonBackend: original_exe=C:\Users\audi bin marwoto\Downloads\Programs\wubi.exe
05-13 04:18 DEBUG  CommonBackend: platform=win32
05-13 04:18 DEBUG  CommonBackend: osname=nt
05-13 04:18 DEBUG  CommonBackend: language=en_MY
05-13 04:18 DEBUG  CommonBackend: encoding=cp1252
05-13 04:18 DEBUG  WindowsBackend: arch=amd64
05-13 04:18 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66A2.tmp\data\isolist.ini
05-13 04:18 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-13 04:18 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-13 04:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-13 04:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-13 04:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-13 04:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-13 04:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-13 04:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-13 04:18 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-13 04:18 DEBUG  WindowsBackend: Fetching host info...
05-13 04:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-13 04:18 DEBUG  WindowsBackend: windows version=vista
05-13 04:18 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-13 04:18 DEBUG  WindowsBackend: windows_sp=None
05-13 04:18 DEBUG  WindowsBackend: windows_build=7600
05-13 04:18 DEBUG  WindowsBackend: gmt=8
05-13 04:18 DEBUG  WindowsBackend: country=MY
05-13 04:18 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-13 04:18 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-13 04:18 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-13 04:18 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-13 04:18 DEBUG  WindowsBackend: windows_language_code=1033
05-13 04:18 DEBUG  WindowsBackend: windows_language=English
05-13 04:18 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-13 04:18 DEBUG  WindowsBackend: bootloader=vista
05-13 04:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 59543.9609375 mb free ntfs)
05-13 04:18 DEBUG  WindowsBackend: drive=Drive(C: hd 59543.9609375 mb free ntfs)
05-13 04:18 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.22265625 mb free ntfs)
05-13 04:18 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-13 04:18 DEBUG  WindowsBackend: uninstaller_path=None
05-13 04:18 DEBUG  WindowsBackend: previous_target_dir=None
05-13 04:18 DEBUG  WindowsBackend: previous_distro_name=None
05-13 04:18 DEBUG  WindowsBackend: keyboard_id=67699721
05-13 04:18 DEBUG  WindowsBackend: keyboard_layout=us
05-13 04:18 DEBUG  WindowsBackend: keyboard_variant=
05-13 04:18 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-13 04:18 DEBUG  CommonBackend: locale=en_US.UTF-8
05-13 04:18 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-13 04:18 DEBUG  CommonBackend: Searching ISOs on USB devices
05-13 04:18 DEBUG  CommonBackend: Searching for local CDs
05-13 04:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66A2.tmp is a valid Ubuntu CD
05-13 04:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66A2.tmp\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66A2.tmp is a valid Ubuntu CD
05-13 04:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66A2.tmp\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66A2.tmp is a valid Ubuntu Netbook CD
05-13 04:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66A2.tmp\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66A2.tmp is a valid Kubuntu CD
05-13 04:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66A2.tmp\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66A2.tmp is a valid Kubuntu CD
05-13 04:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66A2.tmp\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66A2.tmp is a valid Xubuntu CD
05-13 04:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66A2.tmp\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66A2.tmp is a valid Xubuntu CD
05-13 04:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66A2.tmp\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66A2.tmp is a valid Mythbuntu CD
05-13 04:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66A2.tmp\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66A2.tmp is a valid Mythbuntu CD
05-13 04:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66A2.tmp\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-13 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-13 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-13 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-13 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-13 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-13 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-13 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-13 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-13 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-13 04:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-13 04:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-13 04:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-13 04:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-13 04:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-13 04:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-13 04:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-13 04:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 04:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-13 04:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 04:18 INFO   root: Running the installer...
05-13 04:18 DEBUG  WindowsFrontend: __init__...
05-13 04:18 DEBUG  WindowsFrontend: on_init...
05-13 04:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66A2.tmp\translations, languages=['en_US', 'en']
05-13 04:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl66A2.tmp\translations, languages=['en_US', 'en']
05-13 04:18 INFO   WindowsFrontend: Operation cancelled
05-13 04:18 DEBUG  WindowsFrontend: frontend.quit
05-13 04:18 DEBUG  WindowsFrontend: frontend.on_quit
05-13 04:18 DEBUG  root: application.on_quit
05-13 04:18 INFO   root: sys.exit
05-13 06:03 INFO   root: === wubi 11.04 rev211 ===
05-13 06:03 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-13 06:03 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\AUDIBI~1\\AppData\\Local\\Temp\\MagicISO_01CC10F05C41F175\\wubi.exe"']
05-13 06:03 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylB866.tmp\data
05-13 06:03 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pylB866.tmp\bin\7z.exe
05-13 06:03 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-13 06:03 DEBUG  CommonBackend: Fetching basic info...
05-13 06:03 DEBUG  CommonBackend: original_exe=C:\Users\AUDIBI~1\AppData\Local\Temp\MagicISO_01CC10F05C41F175\wubi.exe
05-13 06:03 DEBUG  CommonBackend: platform=win32
05-13 06:03 DEBUG  CommonBackend: osname=nt
05-13 06:03 DEBUG  CommonBackend: language=en_MY
05-13 06:03 DEBUG  CommonBackend: encoding=cp1252
05-13 06:03 DEBUG  WindowsBackend: arch=amd64
05-13 06:03 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pylB866.tmp\data\isolist.ini
05-13 06:03 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-13 06:03 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-13 06:03 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-13 06:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-13 06:03 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-13 06:03 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-13 06:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-13 06:03 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-13 06:03 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-13 06:03 DEBUG  WindowsBackend: Fetching host info...
05-13 06:03 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-13 06:03 DEBUG  WindowsBackend: windows version=vista
05-13 06:03 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-13 06:03 DEBUG  WindowsBackend: windows_sp=None
05-13 06:03 DEBUG  WindowsBackend: windows_build=7600
05-13 06:03 DEBUG  WindowsBackend: gmt=8
05-13 06:03 DEBUG  WindowsBackend: country=MY
05-13 06:03 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-13 06:03 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-13 06:03 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-13 06:03 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-13 06:03 DEBUG  WindowsBackend: windows_language_code=1033
05-13 06:03 DEBUG  WindowsBackend: windows_language=English
05-13 06:03 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-13 06:03 DEBUG  WindowsBackend: bootloader=vista
05-13 06:03 DEBUG  WindowsBackend: system_drive=Drive(C: hd 59592.9648438 mb free ntfs)
05-13 06:03 DEBUG  WindowsBackend: drive=Drive(C: hd 59592.9648438 mb free ntfs)
05-13 06:03 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.22265625 mb free ntfs)
05-13 06:03 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-13 06:03 DEBUG  WindowsBackend: uninstaller_path=None
05-13 06:03 DEBUG  WindowsBackend: previous_target_dir=None
05-13 06:03 DEBUG  WindowsBackend: previous_distro_name=None
05-13 06:03 DEBUG  WindowsBackend: keyboard_id=67699721
05-13 06:03 DEBUG  WindowsBackend: keyboard_layout=us
05-13 06:03 DEBUG  WindowsBackend: keyboard_variant=
05-13 06:03 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-13 06:03 DEBUG  CommonBackend: locale=en_US.UTF-8
05-13 06:03 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-13 06:03 DEBUG  CommonBackend: Searching ISOs on USB devices
05-13 06:03 DEBUG  CommonBackend: Searching for local CDs
05-13 06:03 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylB866.tmp is a valid Ubuntu CD
05-13 06:03 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylB866.tmp\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylB866.tmp is a valid Ubuntu CD
05-13 06:03 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylB866.tmp\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylB866.tmp is a valid Ubuntu Netbook CD
05-13 06:03 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylB866.tmp\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylB866.tmp is a valid Kubuntu CD
05-13 06:03 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylB866.tmp\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylB866.tmp is a valid Kubuntu CD
05-13 06:03 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylB866.tmp\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylB866.tmp is a valid Xubuntu CD
05-13 06:03 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylB866.tmp\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylB866.tmp is a valid Xubuntu CD
05-13 06:03 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylB866.tmp\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylB866.tmp is a valid Mythbuntu CD
05-13 06:03 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylB866.tmp\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylB866.tmp is a valid Mythbuntu CD
05-13 06:03 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylB866.tmp\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-13 06:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-13 06:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-13 06:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-13 06:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-13 06:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-13 06:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-13 06:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-13 06:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-13 06:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-13 06:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-13 06:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-13 06:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-13 06:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-13 06:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-13 06:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-13 06:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-13 06:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 06:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-13 06:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 06:03 INFO   root: Running the installer...
05-13 06:03 DEBUG  WindowsFrontend: __init__...
05-13 06:03 DEBUG  WindowsFrontend: on_init...
05-13 06:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylB866.tmp\translations, languages=['en_US', 'en']
05-13 06:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylB866.tmp\translations, languages=['en_US', 'en']
05-13 06:03 INFO   WindowsFrontend: Operation cancelled
05-13 06:03 DEBUG  WindowsFrontend: frontend.quit
05-13 06:03 DEBUG  WindowsFrontend: frontend.on_quit
05-13 06:03 DEBUG  root: application.on_quit
05-13 06:03 INFO   root: sys.exit
05-13 15:25 INFO   root: === wubi 11.04 rev211 ===
05-13 15:25 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-13 15:25 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\audi bin marwoto\\Downloads\\Programs\\wubi.exe"']
05-13 15:25 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp\data
05-13 15:25 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp\bin\7z.exe
05-13 15:25 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-13 15:25 DEBUG  CommonBackend: Fetching basic info...
05-13 15:25 DEBUG  CommonBackend: original_exe=C:\Users\audi bin marwoto\Downloads\Programs\wubi.exe
05-13 15:25 DEBUG  CommonBackend: platform=win32
05-13 15:25 DEBUG  CommonBackend: osname=nt
05-13 15:25 DEBUG  CommonBackend: language=en_MY
05-13 15:25 DEBUG  CommonBackend: encoding=cp1252
05-13 15:25 DEBUG  WindowsBackend: arch=amd64
05-13 15:25 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp\data\isolist.ini
05-13 15:25 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-13 15:25 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-13 15:25 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-13 15:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-13 15:25 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-13 15:25 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-13 15:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-13 15:25 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-13 15:25 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-13 15:25 DEBUG  WindowsBackend: Fetching host info...
05-13 15:25 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-13 15:25 DEBUG  WindowsBackend: windows version=vista
05-13 15:25 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-13 15:25 DEBUG  WindowsBackend: windows_sp=None
05-13 15:25 DEBUG  WindowsBackend: windows_build=7600
05-13 15:25 DEBUG  WindowsBackend: gmt=8
05-13 15:25 DEBUG  WindowsBackend: country=MY
05-13 15:25 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-13 15:25 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-13 15:25 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-13 15:25 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-13 15:25 DEBUG  WindowsBackend: windows_language_code=1033
05-13 15:25 DEBUG  WindowsBackend: windows_language=English
05-13 15:25 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-13 15:25 DEBUG  WindowsBackend: bootloader=vista
05-13 15:25 DEBUG  WindowsBackend: system_drive=Drive(C: hd 58870.8203125 mb free ntfs)
05-13 15:25 DEBUG  WindowsBackend: drive=Drive(C: hd 58870.8203125 mb free ntfs)
05-13 15:25 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.22265625 mb free ntfs)
05-13 15:25 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-13 15:25 DEBUG  WindowsBackend: uninstaller_path=None
05-13 15:25 DEBUG  WindowsBackend: previous_target_dir=None
05-13 15:25 DEBUG  WindowsBackend: previous_distro_name=None
05-13 15:25 DEBUG  WindowsBackend: keyboard_id=67699721
05-13 15:25 DEBUG  WindowsBackend: keyboard_layout=us
05-13 15:25 DEBUG  WindowsBackend: keyboard_variant=
05-13 15:25 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-13 15:25 DEBUG  CommonBackend: locale=en_US.UTF-8
05-13 15:25 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-13 15:25 DEBUG  CommonBackend: Searching ISOs on USB devices
05-13 15:25 DEBUG  CommonBackend: Searching for local CDs
05-13 15:25 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp is a valid Ubuntu CD
05-13 15:25 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp is a valid Ubuntu CD
05-13 15:25 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp is a valid Ubuntu Netbook CD
05-13 15:25 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp is a valid Kubuntu CD
05-13 15:25 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp is a valid Kubuntu CD
05-13 15:25 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp is a valid Xubuntu CD
05-13 15:25 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp is a valid Xubuntu CD
05-13 15:25 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp is a valid Mythbuntu CD
05-13 15:25 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp is a valid Mythbuntu CD
05-13 15:25 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-13 15:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-13 15:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-13 15:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-13 15:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-13 15:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-13 15:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-13 15:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-13 15:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-13 15:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-13 15:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-13 15:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-13 15:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-13 15:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-13 15:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-13 15:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-13 15:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-13 15:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-13 15:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:25 INFO   root: Running the installer...
05-13 15:25 DEBUG  WindowsFrontend: __init__...
05-13 15:25 DEBUG  WindowsFrontend: on_init...
05-13 15:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp\translations, languages=['en_US', 'en']
05-13 15:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp\translations, languages=['en_US', 'en']
05-13 15:25 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=audio9
05-13 15:25 INFO   root: Received settings
05-13 15:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp\translations, languages=['en_US', 'en']
05-13 15:25 DEBUG  TaskList: # Running tasklist...
05-13 15:25 DEBUG  TaskList: ## Running select_target_dir...
05-13 15:25 INFO   WindowsBackend: Installing into C:\ubuntu
05-13 15:25 DEBUG  TaskList: ## Finished select_target_dir
05-13 15:25 DEBUG  TaskList: ## Running create_dir_structure...
05-13 15:25 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-13 15:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-13 15:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-13 15:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-13 15:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-13 15:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-13 15:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-13 15:25 DEBUG  TaskList: ## Finished create_dir_structure
05-13 15:25 DEBUG  TaskList: ## Running uncompress_target_dir...
05-13 15:25 DEBUG  TaskList: ## Finished uncompress_target_dir
05-13 15:25 DEBUG  TaskList: ## Running create_uninstaller...
05-13 15:25 DEBUG  WindowsBackend: Copying uninstaller C:\Users\audi bin marwoto\Downloads\Programs\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-13 15:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-13 15:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-13 15:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-13 15:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-13 15:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-13 15:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-13 15:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-13 15:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-13 15:25 DEBUG  TaskList: ## Finished create_uninstaller
05-13 15:25 DEBUG  TaskList: ## Running copy_installation_files...
05-13 15:25 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-13 15:25 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp\winboot -> C:\ubuntu\winboot
05-13 15:25 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-13 15:25 DEBUG  TaskList: ## Finished copy_installation_files
05-13 15:25 DEBUG  TaskList: ## Running get_iso...
05-13 15:25 DEBUG  CommonBackend: Searching for local CD
05-13 15:25 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp is a valid Ubuntu CD
05-13 15:25 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl6ED9.tmp\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-13 15:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-13 15:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:25 DEBUG  CommonBackend: Searching for local ISO
05-13 15:25 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-13 15:25 DEBUG  TaskList: New task get_metalink
05-13 15:25 DEBUG  TaskList: ### Running get_metalink...
05-13 15:25 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > C:\ubuntu\install
05-13 15:26 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
05-13 15:26 DEBUG  downloader: download finished (read 28363 bytes)
05-13 15:26 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > C:\ubuntu\install
05-13 15:26 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-13 15:26 DEBUG  downloader: download finished (read 874 bytes)
05-13 15:26 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
05-13 15:26 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-13 15:26 DEBUG  downloader: download finished (read 198 bytes)
05-13 15:26 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-13 15:26 INFO   saplog: Checking block bindings..
05-13 15:26 INFO   saplog: Key verified successfully.
05-13 15:26 DEBUG  CommonBackend: metalink md5sums:
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

05-13 15:26 DEBUG  TaskList: ### Finished get_metalink
05-13 15:26 DEBUG  TaskList: New task download
05-13 15:26 DEBUG  TaskList: ### Running download...
05-13 15:26 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-13 15:28 INFO   WindowsFrontend: Operation cancelled
05-13 15:28 DEBUG  WindowsFrontend: frontend.quit
05-13 15:28 DEBUG  WindowsFrontend: frontend.on_quit
05-13 15:28 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
05-13 15:28 DEBUG  TaskList: # Cancelling tasklist
05-13 15:28 DEBUG  TaskList: ### Finished download
05-13 15:28 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
05-13 15:28 DEBUG  root: application.on_quit
05-13 15:28 DEBUG  root: Forceful exit
05-13 15:28 INFO   root: sys.exit
05-13 15:29 INFO   root: === wubi 11.04 rev211 ===
05-13 15:29 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-13 15:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
05-13 15:29 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2175.tmp\data
05-13 15:29 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2175.tmp\bin\7z.exe
05-13 15:29 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-13 15:29 DEBUG  CommonBackend: Fetching basic info...
05-13 15:29 DEBUG  CommonBackend: original_exe=E:\wubi.exe
05-13 15:29 DEBUG  CommonBackend: platform=win32
05-13 15:29 DEBUG  CommonBackend: osname=nt
05-13 15:29 DEBUG  CommonBackend: language=en_MY
05-13 15:29 DEBUG  CommonBackend: encoding=cp1252
05-13 15:29 DEBUG  WindowsBackend: arch=amd64
05-13 15:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2175.tmp\data\isolist.ini
05-13 15:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-13 15:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-13 15:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-13 15:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-13 15:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-13 15:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-13 15:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-13 15:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-13 15:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-13 15:29 DEBUG  WindowsBackend: Fetching host info...
05-13 15:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-13 15:29 DEBUG  WindowsBackend: windows version=vista
05-13 15:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-13 15:29 DEBUG  WindowsBackend: windows_sp=None
05-13 15:29 DEBUG  WindowsBackend: windows_build=7600
05-13 15:29 DEBUG  WindowsBackend: gmt=8
05-13 15:29 DEBUG  WindowsBackend: country=MY
05-13 15:29 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-13 15:29 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-13 15:29 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-13 15:29 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-13 15:29 DEBUG  WindowsBackend: windows_language_code=1033
05-13 15:29 DEBUG  WindowsBackend: windows_language=English
05-13 15:29 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-13 15:29 DEBUG  WindowsBackend: bootloader=vista
05-13 15:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 58869.265625 mb free ntfs)
05-13 15:29 DEBUG  WindowsBackend: drive=Drive(C: hd 58869.265625 mb free ntfs)
05-13 15:29 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.22265625 mb free ntfs)
05-13 15:29 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-13 15:29 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-13 15:29 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-13 15:29 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-13 15:29 DEBUG  WindowsBackend: keyboard_id=67699721
05-13 15:29 DEBUG  WindowsBackend: keyboard_layout=us
05-13 15:29 DEBUG  WindowsBackend: keyboard_variant=
05-13 15:29 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-13 15:29 DEBUG  CommonBackend: locale=en_US.UTF-8
05-13 15:29 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-13 15:29 DEBUG  CommonBackend: Searching ISOs on USB devices
05-13 15:29 DEBUG  CommonBackend: Searching for local CDs
05-13 15:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2175.tmp is a valid Ubuntu CD
05-13 15:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2175.tmp\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2175.tmp is a valid Ubuntu CD
05-13 15:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2175.tmp\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2175.tmp is a valid Ubuntu Netbook CD
05-13 15:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2175.tmp\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2175.tmp is a valid Kubuntu CD
05-13 15:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2175.tmp\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2175.tmp is a valid Kubuntu CD
05-13 15:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2175.tmp\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2175.tmp is a valid Xubuntu CD
05-13 15:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2175.tmp\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2175.tmp is a valid Xubuntu CD
05-13 15:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2175.tmp\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2175.tmp is a valid Mythbuntu CD
05-13 15:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2175.tmp\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2175.tmp is a valid Mythbuntu CD
05-13 15:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2175.tmp\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-13 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-13 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-13 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-13 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-13 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-13 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-13 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-13 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-13 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-13 15:29 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-13 15:29 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-13 15:29 INFO   Distro: Found a valid CD for Ubuntu: E:\
05-13 15:29 INFO   root: Running the CD menu...
05-13 15:29 DEBUG  WindowsFrontend: __init__...
05-13 15:29 DEBUG  WindowsFrontend: on_init...
05-13 15:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2175.tmp\translations, languages=['en_US', 'en']
05-13 15:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl2175.tmp\translations, languages=['en_US', 'en']
05-13 15:29 INFO   root: CD menu finished
05-13 15:29 DEBUG  CommonBackend: Showing info
05-13 15:29 DEBUG  root: application.quit
05-13 15:29 DEBUG  WindowsFrontend: frontend.quit
05-13 15:29 DEBUG  WindowsFrontend: frontend.on_quit
05-13 15:29 DEBUG  root: application.on_quit
05-13 15:29 INFO   root: sys.exit
05-13 15:29 INFO   root: === wubi 11.04 rev211 ===
05-13 15:29 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-13 15:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
05-13 15:29 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\data
05-13 15:29 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\bin\7z.exe
05-13 15:29 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-13 15:29 DEBUG  CommonBackend: Fetching basic info...
05-13 15:29 DEBUG  CommonBackend: original_exe=E:\wubi.exe
05-13 15:29 DEBUG  CommonBackend: platform=win32
05-13 15:29 DEBUG  CommonBackend: osname=nt
05-13 15:29 DEBUG  CommonBackend: language=en_MY
05-13 15:29 DEBUG  CommonBackend: encoding=cp1252
05-13 15:29 DEBUG  WindowsBackend: arch=amd64
05-13 15:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\data\isolist.ini
05-13 15:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-13 15:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-13 15:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-13 15:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-13 15:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-13 15:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-13 15:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-13 15:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-13 15:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-13 15:29 DEBUG  WindowsBackend: Fetching host info...
05-13 15:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-13 15:29 DEBUG  WindowsBackend: windows version=vista
05-13 15:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-13 15:29 DEBUG  WindowsBackend: windows_sp=None
05-13 15:29 DEBUG  WindowsBackend: windows_build=7600
05-13 15:29 DEBUG  WindowsBackend: gmt=8
05-13 15:29 DEBUG  WindowsBackend: country=MY
05-13 15:29 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-13 15:29 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-13 15:29 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-13 15:29 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-13 15:29 DEBUG  WindowsBackend: windows_language_code=1033
05-13 15:29 DEBUG  WindowsBackend: windows_language=English
05-13 15:29 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-13 15:29 DEBUG  WindowsBackend: bootloader=vista
05-13 15:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 58869.2929688 mb free ntfs)
05-13 15:29 DEBUG  WindowsBackend: drive=Drive(C: hd 58869.2929688 mb free ntfs)
05-13 15:29 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.22265625 mb free ntfs)
05-13 15:29 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-13 15:29 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-13 15:29 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-13 15:29 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-13 15:29 DEBUG  WindowsBackend: keyboard_id=67699721
05-13 15:29 DEBUG  WindowsBackend: keyboard_layout=us
05-13 15:29 DEBUG  WindowsBackend: keyboard_variant=
05-13 15:29 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-13 15:29 DEBUG  CommonBackend: locale=en_US.UTF-8
05-13 15:29 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-13 15:29 DEBUG  CommonBackend: Searching ISOs on USB devices
05-13 15:29 DEBUG  CommonBackend: Searching for local CDs
05-13 15:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp is a valid Ubuntu CD
05-13 15:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp is a valid Ubuntu CD
05-13 15:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp is a valid Ubuntu Netbook CD
05-13 15:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp is a valid Kubuntu CD
05-13 15:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp is a valid Kubuntu CD
05-13 15:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp is a valid Xubuntu CD
05-13 15:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp is a valid Xubuntu CD
05-13 15:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp is a valid Mythbuntu CD
05-13 15:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp is a valid Mythbuntu CD
05-13 15:29 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-13 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-13 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-13 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-13 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-13 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-13 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-13 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-13 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-13 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-13 15:29 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-13 15:29 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-13 15:29 INFO   Distro: Found a valid CD for Ubuntu: E:\
05-13 15:29 INFO   root: Running the CD menu...
05-13 15:29 DEBUG  WindowsFrontend: __init__...
05-13 15:29 DEBUG  WindowsFrontend: on_init...
05-13 15:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\translations, languages=['en_US', 'en']
05-13 15:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\translations, languages=['en_US', 'en']
05-13 15:29 INFO   root: CD menu finished
05-13 15:29 INFO   root: Already installed, running the uninstaller...
05-13 15:29 INFO   root: Running the uninstaller...
05-13 15:29 INFO   CommonBackend: This is the uninstaller running
05-13 15:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\translations, languages=['en_US', 'en']
05-13 15:30 INFO   root: Received settings
05-13 15:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\translations, languages=['en_US', 'en']
05-13 15:30 DEBUG  TaskList: # Running tasklist...
05-13 15:30 DEBUG  TaskList: ## Running Backup ISO...
05-13 15:30 DEBUG  TaskList: ## Finished Backup ISO
05-13 15:30 DEBUG  TaskList: ## Running Remove bootloader entry...
05-13 15:30 DEBUG  WindowsBackend: Could not find bcd id
05-13 15:30 DEBUG  WindowsBackend: undo_bootini C:
05-13 15:30 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 58869.2929688 mb free ntfs)
05-13 15:30 DEBUG  WindowsBackend: undo_bootini D:
05-13 15:30 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2105.22265625 mb free ntfs)
05-13 15:30 DEBUG  TaskList: ## Finished Remove bootloader entry
05-13 15:30 DEBUG  TaskList: ## Running Remove target dir...
05-13 15:30 DEBUG  CommonBackend: Deleting C:\ubuntu
05-13 15:30 DEBUG  TaskList: ## Finished Remove target dir
05-13 15:30 DEBUG  TaskList: ## Running Remove registry key...
05-13 15:30 DEBUG  TaskList: ## Finished Remove registry key
05-13 15:30 DEBUG  TaskList: # Finished tasklist
05-13 15:30 INFO   root: Almost finished uninstalling
05-13 15:30 INFO   root: Finished uninstallation
05-13 15:30 DEBUG  CommonBackend: Fetching basic info...
05-13 15:30 DEBUG  CommonBackend: original_exe=E:\wubi.exe
05-13 15:30 DEBUG  CommonBackend: platform=win32
05-13 15:30 DEBUG  CommonBackend: osname=nt
05-13 15:30 DEBUG  WindowsBackend: arch=amd64
05-13 15:30 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\data\isolist.ini
05-13 15:30 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-13 15:30 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-13 15:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-13 15:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-13 15:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-13 15:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-13 15:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-13 15:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-13 15:30 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-13 15:30 DEBUG  WindowsBackend: Fetching host info...
05-13 15:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-13 15:30 DEBUG  WindowsBackend: windows version=vista
05-13 15:30 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-13 15:30 DEBUG  WindowsBackend: windows_sp=None
05-13 15:30 DEBUG  WindowsBackend: windows_build=7600
05-13 15:30 DEBUG  WindowsBackend: gmt=8
05-13 15:30 DEBUG  WindowsBackend: country=MY
05-13 15:30 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-13 15:30 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-13 15:30 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-13 15:30 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-13 15:30 DEBUG  WindowsBackend: windows_language_code=1033
05-13 15:30 DEBUG  WindowsBackend: windows_language=English
05-13 15:30 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-13 15:30 DEBUG  WindowsBackend: bootloader=vista
05-13 15:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 58871.1953125 mb free ntfs)
05-13 15:30 DEBUG  WindowsBackend: drive=Drive(C: hd 58871.1953125 mb free ntfs)
05-13 15:30 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.22265625 mb free ntfs)
05-13 15:30 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-13 15:30 DEBUG  WindowsBackend: uninstaller_path=None
05-13 15:30 DEBUG  WindowsBackend: previous_target_dir=None
05-13 15:30 DEBUG  WindowsBackend: previous_distro_name=None
05-13 15:30 DEBUG  WindowsBackend: keyboard_id=67699721
05-13 15:30 DEBUG  WindowsBackend: keyboard_layout=us
05-13 15:30 DEBUG  WindowsBackend: keyboard_variant=
05-13 15:30 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-13 15:30 DEBUG  CommonBackend: Searching ISOs on USB devices
05-13 15:30 DEBUG  CommonBackend: Searching for local CDs
05-13 15:30 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp is a valid Ubuntu CD
05-13 15:30 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\casper\filesystem.squashfs
05-13 15:30 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp is a valid Ubuntu CD
05-13 15:30 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\casper\filesystem.squashfs
05-13 15:30 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp is a valid Ubuntu Netbook CD
05-13 15:30 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\casper\filesystem.squashfs
05-13 15:30 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp is a valid Kubuntu CD
05-13 15:30 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\casper\filesystem.squashfs
05-13 15:30 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp is a valid Kubuntu CD
05-13 15:30 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\casper\filesystem.squashfs
05-13 15:30 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp is a valid Xubuntu CD
05-13 15:30 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\casper\filesystem.squashfs
05-13 15:30 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp is a valid Xubuntu CD
05-13 15:30 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\casper\filesystem.squashfs
05-13 15:30 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp is a valid Mythbuntu CD
05-13 15:30 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\casper\filesystem.squashfs
05-13 15:30 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp is a valid Mythbuntu CD
05-13 15:30 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\casper\filesystem.squashfs
05-13 15:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-13 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-13 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-13 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-13 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-13 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-13 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-13 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-13 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-13 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-13 15:30 INFO   Distro: Found a valid CD for Ubuntu: E:\
05-13 15:30 INFO   root: Running the installer...
05-13 15:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\translations, languages=['en_US', 'en']
05-13 15:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\translations, languages=['en_US', 'en']
05-13 15:30 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=audio9
05-13 15:30 INFO   root: Received settings
05-13 15:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\translations, languages=['en_US', 'en']
05-13 15:30 DEBUG  TaskList: # Running tasklist...
05-13 15:30 DEBUG  TaskList: ## Running select_target_dir...
05-13 15:30 INFO   WindowsBackend: Installing into C:\ubuntu
05-13 15:30 DEBUG  TaskList: ## Finished select_target_dir
05-13 15:30 DEBUG  TaskList: ## Running create_dir_structure...
05-13 15:30 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-13 15:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-13 15:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-13 15:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-13 15:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-13 15:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-13 15:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-13 15:30 DEBUG  TaskList: ## Finished create_dir_structure
05-13 15:30 DEBUG  TaskList: ## Running uncompress_target_dir...
05-13 15:30 DEBUG  TaskList: ## Finished uncompress_target_dir
05-13 15:30 DEBUG  TaskList: ## Running create_uninstaller...
05-13 15:30 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-13 15:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-13 15:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-13 15:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-13 15:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-13 15:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-13 15:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-13 15:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-13 15:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-13 15:30 DEBUG  TaskList: ## Finished create_uninstaller
05-13 15:30 DEBUG  TaskList: ## Running copy_installation_files...
05-13 15:30 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-13 15:30 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\winboot -> C:\ubuntu\winboot
05-13 15:30 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pyl96D3.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-13 15:30 DEBUG  TaskList: ## Finished copy_installation_files
05-13 15:30 DEBUG  TaskList: ## Running get_iso...
05-13 15:30 DEBUG  TaskList: New task copy_file
05-13 15:30 DEBUG  TaskList: ### Running copy_file...
05-13 15:31 DEBUG  TaskList: ### Finished copy_file
05-13 15:31 DEBUG  TaskList: New task check_iso
05-13 15:31 DEBUG  TaskList: ### Running check_iso...
05-13 15:31 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
05-13 15:31 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
05-13 15:31 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
05-13 15:31 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-13 15:31 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-13 15:31 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
05-13 15:31 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
05-13 15:31 DEBUG  TaskList: New task get_metalink
05-13 15:31 DEBUG  TaskList: #### Running get_metalink...
05-13 15:31 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink) > C:\ubuntu\install
05-13 15:31 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-i386.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink, basename=ubuntu-11.04-desktop-i386.metalink, length=28158, text=None
05-13 15:31 DEBUG  downloader: download finished (read 28158 bytes)
05-13 15:31 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > C:\ubuntu\install
05-13 15:31 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-13 15:31 DEBUG  downloader: download finished (read 874 bytes)
05-13 15:31 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
05-13 15:31 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-13 15:31 DEBUG  downloader: download finished (read 198 bytes)
05-13 15:31 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-13 15:31 INFO   saplog: Checking block bindings..
05-13 15:31 INFO   saplog: Key verified successfully.
05-13 15:31 DEBUG  CommonBackend: metalink md5sums:
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

05-13 15:31 DEBUG  TaskList: #### Finished get_metalink
05-13 15:31 DEBUG  TaskList: New task get_file_md5
05-13 15:31 DEBUG  TaskList: #### Running get_file_md5...
05-13 15:31 DEBUG  TaskList: #### Finished get_file_md5
05-13 15:31 ERROR  CommonBackend: Invalid md5 for ISO C:\ubuntu\install\installation.iso (8b1085bed498b82ef1485ef19074c281 != 775ecff4394449df5b7e83bb22d23fb8)
None
05-13 15:31 DEBUG  TaskList: ### Finished check_iso
05-13 15:31 DEBUG  CommonBackend: Searching for local ISO
05-13 15:31 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-13 15:31 DEBUG  TaskList: New task download
05-13 15:31 DEBUG  TaskList: ### Running download...
05-13 15:31 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent) > C:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
05-13 15:33 INFO   WindowsFrontend: Operation cancelled
05-13 15:34 DEBUG  WindowsFrontend: frontend.quit
05-13 15:34 DEBUG  WindowsFrontend: frontend.on_quit
05-13 15:34 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
05-13 15:34 DEBUG  TaskList: # Cancelling tasklist
05-13 15:34 DEBUG  TaskList: ### Finished download
05-13 15:34 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
05-13 15:34 DEBUG  root: application.on_quit
05-13 15:34 DEBUG  root: Forceful exit
05-13 15:34 INFO   root: sys.exit
05-13 15:39 INFO   root: === wubi 11.04 rev211 ===
05-13 15:39 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-13 15:39 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\audi bin marwoto\\Documents\\wubi.exe"']
05-13 15:39 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylB6D1.tmp\data
05-13 15:39 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pylB6D1.tmp\bin\7z.exe
05-13 15:39 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-13 15:39 DEBUG  CommonBackend: Fetching basic info...
05-13 15:39 DEBUG  CommonBackend: original_exe=C:\Users\audi bin marwoto\Documents\wubi.exe
05-13 15:39 DEBUG  CommonBackend: platform=win32
05-13 15:39 DEBUG  CommonBackend: osname=nt
05-13 15:39 DEBUG  CommonBackend: language=en_MY
05-13 15:39 DEBUG  CommonBackend: encoding=cp1252
05-13 15:39 DEBUG  WindowsBackend: arch=amd64
05-13 15:39 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pylB6D1.tmp\data\isolist.ini
05-13 15:39 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-13 15:39 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-13 15:39 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-13 15:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-13 15:39 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-13 15:39 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-13 15:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-13 15:39 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-13 15:39 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-13 15:39 DEBUG  WindowsBackend: Fetching host info...
05-13 15:39 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-13 15:39 DEBUG  WindowsBackend: windows version=vista
05-13 15:39 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-13 15:39 DEBUG  WindowsBackend: windows_sp=None
05-13 15:39 DEBUG  WindowsBackend: windows_build=7600
05-13 15:39 DEBUG  WindowsBackend: gmt=8
05-13 15:39 DEBUG  WindowsBackend: country=MY
05-13 15:39 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-13 15:39 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-13 15:39 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-13 15:39 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-13 15:39 DEBUG  WindowsBackend: windows_language_code=1033
05-13 15:39 DEBUG  WindowsBackend: windows_language=English
05-13 15:39 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-13 15:39 DEBUG  WindowsBackend: bootloader=vista
05-13 15:39 DEBUG  WindowsBackend: system_drive=Drive(C: hd 58183.453125 mb free ntfs)
05-13 15:39 DEBUG  WindowsBackend: drive=Drive(C: hd 58183.453125 mb free ntfs)
05-13 15:39 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.22265625 mb free ntfs)
05-13 15:39 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-13 15:39 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-13 15:39 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-13 15:39 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-13 15:39 DEBUG  WindowsBackend: keyboard_id=67699721
05-13 15:39 DEBUG  WindowsBackend: keyboard_layout=us
05-13 15:39 DEBUG  WindowsBackend: keyboard_variant=
05-13 15:39 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-13 15:39 DEBUG  CommonBackend: locale=en_US.UTF-8
05-13 15:39 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-13 15:39 DEBUG  CommonBackend: Searching ISOs on USB devices
05-13 15:39 DEBUG  CommonBackend: Searching for local CDs
05-13 15:39 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylB6D1.tmp is a valid Ubuntu CD
05-13 15:39 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylB6D1.tmp\casper\filesystem.squashfs
05-13 15:39 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylB6D1.tmp is a valid Ubuntu CD
05-13 15:39 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylB6D1.tmp\casper\filesystem.squashfs
05-13 15:39 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylB6D1.tmp is a valid Ubuntu Netbook CD
05-13 15:39 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylB6D1.tmp\casper\filesystem.squashfs
05-13 15:39 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylB6D1.tmp is a valid Kubuntu CD
05-13 15:39 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylB6D1.tmp\casper\filesystem.squashfs
05-13 15:39 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylB6D1.tmp is a valid Kubuntu CD
05-13 15:39 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylB6D1.tmp\casper\filesystem.squashfs
05-13 15:39 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylB6D1.tmp is a valid Xubuntu CD
05-13 15:39 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylB6D1.tmp\casper\filesystem.squashfs
05-13 15:39 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylB6D1.tmp is a valid Xubuntu CD
05-13 15:39 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylB6D1.tmp\casper\filesystem.squashfs
05-13 15:39 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylB6D1.tmp is a valid Mythbuntu CD
05-13 15:39 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylB6D1.tmp\casper\filesystem.squashfs
05-13 15:39 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylB6D1.tmp is a valid Mythbuntu CD
05-13 15:39 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylB6D1.tmp\casper\filesystem.squashfs
05-13 15:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-13 15:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-13 15:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-13 15:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-13 15:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-13 15:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-13 15:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-13 15:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-13 15:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-13 15:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-13 15:39 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-13 15:39 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-13 15:39 INFO   Distro: Found a valid CD for Ubuntu: E:\
05-13 15:39 INFO   root: Running the CD menu...
05-13 15:39 DEBUG  WindowsFrontend: __init__...
05-13 15:39 DEBUG  WindowsFrontend: on_init...
05-13 15:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylB6D1.tmp\translations, languages=['en_US', 'en']
05-13 15:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylB6D1.tmp\translations, languages=['en_US', 'en']
05-13 15:40 INFO   root: CD menu finished
05-13 15:40 INFO   root: Already installed, running the uninstaller...
05-13 15:40 INFO   root: Running the uninstaller...
05-13 15:40 INFO   CommonBackend: This is the uninstaller running
05-13 15:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylB6D1.tmp\translations, languages=['en_US', 'en']
05-13 15:40 INFO   WindowsFrontend: Operation cancelled
05-13 15:40 DEBUG  WindowsFrontend: frontend.quit
05-13 15:40 DEBUG  WindowsFrontend: frontend.on_quit
05-13 15:40 DEBUG  root: application.on_quit
05-13 15:40 INFO   root: sys.exit
05-13 15:44 INFO   root: === wubi 11.04 rev211 ===
05-13 15:44 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-13 15:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\audi bin marwoto\\Documents\\wubi.exe"']
05-13 15:44 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\data
05-13 15:44 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\bin\7z.exe
05-13 15:44 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-13 15:44 DEBUG  CommonBackend: Fetching basic info...
05-13 15:44 DEBUG  CommonBackend: original_exe=C:\Users\audi bin marwoto\Documents\wubi.exe
05-13 15:44 DEBUG  CommonBackend: platform=win32
05-13 15:44 DEBUG  CommonBackend: osname=nt
05-13 15:44 DEBUG  CommonBackend: language=en_MY
05-13 15:44 DEBUG  CommonBackend: encoding=cp1252
05-13 15:44 DEBUG  WindowsBackend: arch=amd64
05-13 15:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\data\isolist.ini
05-13 15:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-13 15:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-13 15:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-13 15:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-13 15:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-13 15:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-13 15:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-13 15:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-13 15:44 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-13 15:44 DEBUG  WindowsBackend: Fetching host info...
05-13 15:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-13 15:44 DEBUG  WindowsBackend: windows version=vista
05-13 15:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-13 15:44 DEBUG  WindowsBackend: windows_sp=None
05-13 15:44 DEBUG  WindowsBackend: windows_build=7600
05-13 15:44 DEBUG  WindowsBackend: gmt=8
05-13 15:44 DEBUG  WindowsBackend: country=MY
05-13 15:44 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-13 15:44 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-13 15:44 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-13 15:44 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-13 15:44 DEBUG  WindowsBackend: windows_language_code=1033
05-13 15:44 DEBUG  WindowsBackend: windows_language=English
05-13 15:44 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-13 15:44 DEBUG  WindowsBackend: bootloader=vista
05-13 15:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 58182.7109375 mb free ntfs)
05-13 15:44 DEBUG  WindowsBackend: drive=Drive(C: hd 58182.7109375 mb free ntfs)
05-13 15:44 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.22265625 mb free ntfs)
05-13 15:44 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-13 15:44 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-13 15:44 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-13 15:44 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-13 15:44 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-13 15:44 DEBUG  WindowsBackend: keyboard_id=67699721
05-13 15:44 DEBUG  WindowsBackend: keyboard_layout=us
05-13 15:44 DEBUG  WindowsBackend: keyboard_variant=
05-13 15:44 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-13 15:44 DEBUG  CommonBackend: locale=en_US.UTF-8
05-13 15:44 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-13 15:44 DEBUG  CommonBackend: Searching ISOs on USB devices
05-13 15:44 DEBUG  CommonBackend: Searching for local CDs
05-13 15:44 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp is a valid Ubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp is a valid Ubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp is a valid Ubuntu Netbook CD
05-13 15:44 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp is a valid Kubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp is a valid Kubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp is a valid Xubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp is a valid Xubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp is a valid Mythbuntu CD
05-13 15:44 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp is a valid Mythbuntu CD
05-13 15:44 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-13 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-13 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-13 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-13 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-13 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-13 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-13 15:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-13 15:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-13 15:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 15:44 INFO   root: Already installed, running the uninstaller...
05-13 15:44 INFO   root: Running the uninstaller...
05-13 15:44 INFO   CommonBackend: This is the uninstaller running
05-13 15:44 DEBUG  WindowsFrontend: __init__...
05-13 15:44 DEBUG  WindowsFrontend: on_init...
05-13 15:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\translations, languages=['en_US', 'en']
05-13 15:44 INFO   root: Received settings
05-13 15:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\translations, languages=['en_US', 'en']
05-13 15:44 DEBUG  TaskList: # Running tasklist...
05-13 15:44 DEBUG  TaskList: ## Running Backup ISO...
05-13 15:44 DEBUG  TaskList: ## Finished Backup ISO
05-13 15:44 DEBUG  TaskList: ## Running Remove bootloader entry...
05-13 15:44 DEBUG  WindowsBackend: Could not find bcd id
05-13 15:44 DEBUG  WindowsBackend: undo_bootini C:
05-13 15:44 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 58182.7109375 mb free ntfs)
05-13 15:44 DEBUG  WindowsBackend: undo_bootini D:
05-13 15:44 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2105.22265625 mb free ntfs)
05-13 15:44 DEBUG  TaskList: ## Finished Remove bootloader entry
05-13 15:44 DEBUG  TaskList: ## Running Remove target dir...
05-13 15:44 DEBUG  CommonBackend: Deleting C:\ubuntu
05-13 15:44 DEBUG  TaskList: ## Finished Remove target dir
05-13 15:44 DEBUG  TaskList: ## Running Remove registry key...
05-13 15:44 DEBUG  TaskList: ## Finished Remove registry key
05-13 15:44 DEBUG  TaskList: # Finished tasklist
05-13 15:44 INFO   root: Almost finished uninstalling
05-13 15:44 INFO   root: Finished uninstallation
05-13 15:44 DEBUG  CommonBackend: Fetching basic info...
05-13 15:44 DEBUG  CommonBackend: original_exe=C:\Users\audi bin marwoto\Documents\wubi.exe
05-13 15:44 DEBUG  CommonBackend: platform=win32
05-13 15:44 DEBUG  CommonBackend: osname=nt
05-13 15:44 DEBUG  WindowsBackend: arch=amd64
05-13 15:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\data\isolist.ini
05-13 15:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-13 15:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-13 15:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-13 15:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-13 15:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-13 15:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-13 15:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-13 15:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-13 15:44 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-13 15:44 DEBUG  WindowsBackend: Fetching host info...
05-13 15:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-13 15:44 DEBUG  WindowsBackend: windows version=vista
05-13 15:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-13 15:44 DEBUG  WindowsBackend: windows_sp=None
05-13 15:44 DEBUG  WindowsBackend: windows_build=7600
05-13 15:44 DEBUG  WindowsBackend: gmt=8
05-13 15:44 DEBUG  WindowsBackend: country=MY
05-13 15:44 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-13 15:44 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-13 15:44 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-13 15:44 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-13 15:44 DEBUG  WindowsBackend: windows_language_code=1033
05-13 15:44 DEBUG  WindowsBackend: windows_language=English
05-13 15:44 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-13 15:44 DEBUG  WindowsBackend: bootloader=vista
05-13 15:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 58870.2578125 mb free ntfs)
05-13 15:44 DEBUG  WindowsBackend: drive=Drive(C: hd 58870.2578125 mb free ntfs)
05-13 15:44 DEBUG  WindowsBackend: drive=Drive(D: hd 2105.22265625 mb free ntfs)
05-13 15:44 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-13 15:44 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-13 15:44 DEBUG  WindowsBackend: uninstaller_path=None
05-13 15:44 DEBUG  WindowsBackend: previous_target_dir=None
05-13 15:44 DEBUG  WindowsBackend: previous_distro_name=None
05-13 15:44 DEBUG  WindowsBackend: keyboard_id=67699721
05-13 15:44 DEBUG  WindowsBackend: keyboard_layout=us
05-13 15:44 DEBUG  WindowsBackend: keyboard_variant=
05-13 15:44 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-13 15:44 DEBUG  CommonBackend: Searching ISOs on USB devices
05-13 15:44 DEBUG  CommonBackend: Searching for local CDs
05-13 15:44 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp is a valid Ubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp is a valid Ubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp is a valid Ubuntu Netbook CD
05-13 15:44 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp is a valid Kubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp is a valid Kubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp is a valid Xubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp is a valid Xubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp is a valid Mythbuntu CD
05-13 15:44 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp is a valid Mythbuntu CD
05-13 15:44 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-13 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-13 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-13 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-13 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-13 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-13 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-13 15:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-13 15:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-13 15:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 15:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-13 15:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 15:44 INFO   root: Running the installer...
05-13 15:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\translations, languages=['en_US', 'en']
05-13 15:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylEFCB.tmp\translations, languages=['en_US', 'en']
05-13 15:45 INFO   WindowsFrontend: Operation cancelled
05-13 15:45 DEBUG  WindowsFrontend: frontend.quit
05-13 15:45 DEBUG  WindowsFrontend: frontend.on_quit
05-13 15:45 DEBUG  root: application.on_quit
05-13 15:45 INFO   root: sys.exit
05-15 19:43 INFO   root: === wubi 11.04 rev211 ===
05-15 19:43 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-15 19:43 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
05-15 19:43 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl40E6.tmp\data
05-15 19:43 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl40E6.tmp\bin\7z.exe
05-15 19:43 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-15 19:43 DEBUG  CommonBackend: Fetching basic info...
05-15 19:43 DEBUG  CommonBackend: original_exe=E:\wubi.exe
05-15 19:43 DEBUG  CommonBackend: platform=win32
05-15 19:43 DEBUG  CommonBackend: osname=nt
05-15 19:43 DEBUG  CommonBackend: language=en_MY
05-15 19:43 DEBUG  CommonBackend: encoding=cp1252
05-15 19:43 DEBUG  WindowsBackend: arch=amd64
05-15 19:43 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl40E6.tmp\data\isolist.ini
05-15 19:43 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-15 19:43 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-15 19:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-15 19:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-15 19:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-15 19:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-15 19:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-15 19:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-15 19:43 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-15 19:43 DEBUG  WindowsBackend: Fetching host info...
05-15 19:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-15 19:43 DEBUG  WindowsBackend: windows version=vista
05-15 19:43 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-15 19:43 DEBUG  WindowsBackend: windows_sp=None
05-15 19:43 DEBUG  WindowsBackend: windows_build=7600
05-15 19:43 DEBUG  WindowsBackend: gmt=8
05-15 19:43 DEBUG  WindowsBackend: country=MY
05-15 19:43 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-15 19:43 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-15 19:43 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-15 19:43 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-15 19:43 DEBUG  WindowsBackend: windows_language_code=1033
05-15 19:43 DEBUG  WindowsBackend: windows_language=English
05-15 19:43 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-15 19:43 DEBUG  WindowsBackend: bootloader=vista
05-15 19:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 57026.265625 mb free ntfs)
05-15 19:43 DEBUG  WindowsBackend: drive=Drive(C: hd 57026.265625 mb free ntfs)
05-15 19:43 DEBUG  WindowsBackend: drive=Drive(D: hd 2140.12109375 mb free ntfs)
05-15 19:43 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-15 19:43 DEBUG  WindowsBackend: uninstaller_path=None
05-15 19:43 DEBUG  WindowsBackend: previous_target_dir=None
05-15 19:43 DEBUG  WindowsBackend: previous_distro_name=None
05-15 19:43 DEBUG  WindowsBackend: keyboard_id=67699721
05-15 19:43 DEBUG  WindowsBackend: keyboard_layout=us
05-15 19:43 DEBUG  WindowsBackend: keyboard_variant=
05-15 19:43 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-15 19:43 DEBUG  CommonBackend: locale=en_US.UTF-8
05-15 19:43 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-15 19:43 DEBUG  CommonBackend: Searching ISOs on USB devices
05-15 19:43 DEBUG  CommonBackend: Searching for local CDs
05-15 19:43 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl40E6.tmp is a valid Ubuntu CD
05-15 19:43 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl40E6.tmp\casper\filesystem.squashfs
05-15 19:43 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl40E6.tmp is a valid Ubuntu CD
05-15 19:43 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl40E6.tmp\casper\filesystem.squashfs
05-15 19:43 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl40E6.tmp is a valid Ubuntu Netbook CD
05-15 19:43 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl40E6.tmp\casper\filesystem.squashfs
05-15 19:43 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl40E6.tmp is a valid Kubuntu CD
05-15 19:43 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl40E6.tmp\casper\filesystem.squashfs
05-15 19:43 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl40E6.tmp is a valid Kubuntu CD
05-15 19:43 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl40E6.tmp\casper\filesystem.squashfs
05-15 19:43 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl40E6.tmp is a valid Xubuntu CD
05-15 19:43 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl40E6.tmp\casper\filesystem.squashfs
05-15 19:43 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl40E6.tmp is a valid Xubuntu CD
05-15 19:43 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl40E6.tmp\casper\filesystem.squashfs
05-15 19:43 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl40E6.tmp is a valid Mythbuntu CD
05-15 19:43 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl40E6.tmp\casper\filesystem.squashfs
05-15 19:43 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl40E6.tmp is a valid Mythbuntu CD
05-15 19:43 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl40E6.tmp\casper\filesystem.squashfs
05-15 19:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-15 19:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-15 19:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-15 19:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-15 19:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-15 19:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-15 19:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-15 19:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-15 19:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-15 19:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-15 19:43 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-15 19:43 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-15 19:43 INFO   Distro: Found a valid CD for Ubuntu: E:\
05-15 19:43 INFO   root: Running the CD menu...
05-15 19:43 DEBUG  WindowsFrontend: __init__...
05-15 19:43 DEBUG  WindowsFrontend: on_init...
05-15 19:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl40E6.tmp\translations, languages=['en_US', 'en']
05-15 19:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl40E6.tmp\translations, languages=['en_US', 'en']
05-15 19:43 INFO   root: CD menu finished
05-15 19:43 INFO   root: Rebooting
05-15 19:43 DEBUG  TaskList: # Running tasklist...
05-15 19:43 DEBUG  TaskList: ## Running reboot...
05-15 19:43 DEBUG  TaskList: ## Finished reboot
05-15 19:43 DEBUG  TaskList: # Finished tasklist
05-15 19:43 DEBUG  root: application.quit
05-15 19:43 DEBUG  WindowsFrontend: frontend.quit
05-15 19:43 DEBUG  WindowsFrontend: frontend.on_quit
05-15 19:43 DEBUG  root: application.on_quit
05-15 19:43 INFO   root: sys.exit
05-15 19:47 INFO   root: === wubi 11.04 rev211 ===
05-15 19:47 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-15 19:47 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
05-15 19:47 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp\data
05-15 19:47 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp\bin\7z.exe
05-15 19:47 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-15 19:47 DEBUG  CommonBackend: Fetching basic info...
05-15 19:47 DEBUG  CommonBackend: original_exe=F:\wubi.exe
05-15 19:47 DEBUG  CommonBackend: platform=win32
05-15 19:47 DEBUG  CommonBackend: osname=nt
05-15 19:47 DEBUG  CommonBackend: language=en_MY
05-15 19:47 DEBUG  CommonBackend: encoding=cp1252
05-15 19:47 DEBUG  WindowsBackend: arch=amd64
05-15 19:47 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp\data\isolist.ini
05-15 19:47 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-15 19:47 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-15 19:47 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-15 19:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-15 19:47 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-15 19:47 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-15 19:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-15 19:47 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-15 19:47 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-15 19:47 DEBUG  WindowsBackend: Fetching host info...
05-15 19:47 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-15 19:47 DEBUG  WindowsBackend: windows version=vista
05-15 19:47 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-15 19:47 DEBUG  WindowsBackend: windows_sp=None
05-15 19:47 DEBUG  WindowsBackend: windows_build=7600
05-15 19:47 DEBUG  WindowsBackend: gmt=8
05-15 19:47 DEBUG  WindowsBackend: country=MY
05-15 19:47 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-15 19:47 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-15 19:47 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-15 19:47 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-15 19:47 DEBUG  WindowsBackend: windows_language_code=1033
05-15 19:47 DEBUG  WindowsBackend: windows_language=English
05-15 19:47 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-15 19:47 DEBUG  WindowsBackend: bootloader=vista
05-15 19:47 DEBUG  WindowsBackend: system_drive=Drive(C: hd 57043.4335938 mb free ntfs)
05-15 19:47 DEBUG  WindowsBackend: drive=Drive(C: hd 57043.4335938 mb free ntfs)
05-15 19:47 DEBUG  WindowsBackend: drive=Drive(D: hd 2140.12109375 mb free ntfs)
05-15 19:47 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-15 19:47 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
05-15 19:47 DEBUG  WindowsBackend: uninstaller_path=None
05-15 19:47 DEBUG  WindowsBackend: previous_target_dir=None
05-15 19:47 DEBUG  WindowsBackend: previous_distro_name=None
05-15 19:47 DEBUG  WindowsBackend: keyboard_id=67699721
05-15 19:47 DEBUG  WindowsBackend: keyboard_layout=us
05-15 19:47 DEBUG  WindowsBackend: keyboard_variant=
05-15 19:47 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-15 19:47 DEBUG  CommonBackend: locale=en_US.UTF-8
05-15 19:47 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-15 19:47 DEBUG  CommonBackend: Searching ISOs on USB devices
05-15 19:47 DEBUG  CommonBackend: Searching for local CDs
05-15 19:47 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp is a valid Ubuntu CD
05-15 19:47 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp is a valid Ubuntu CD
05-15 19:47 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp is a valid Ubuntu Netbook CD
05-15 19:47 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp is a valid Kubuntu CD
05-15 19:47 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp is a valid Kubuntu CD
05-15 19:47 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp is a valid Xubuntu CD
05-15 19:47 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp is a valid Xubuntu CD
05-15 19:47 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp is a valid Mythbuntu CD
05-15 19:47 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp is a valid Mythbuntu CD
05-15 19:47 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-15 19:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-15 19:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-15 19:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-15 19:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-15 19:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-15 19:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-15 19:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-15 19:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-15 19:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-15 19:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-15 19:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-15 19:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-15 19:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-15 19:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-15 19:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-15 19:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-15 19:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-15 19:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 19:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-15 19:47 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-15 19:47 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-15 19:47 INFO   Distro: Found a valid CD for Ubuntu: F:\
05-15 19:47 INFO   root: Running the CD menu...
05-15 19:47 DEBUG  WindowsFrontend: __init__...
05-15 19:47 DEBUG  WindowsFrontend: on_init...
05-15 19:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp\translations, languages=['en_US', 'en']
05-15 19:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp\translations, languages=['en_US', 'en']
05-15 19:47 INFO   root: CD menu finished
05-15 19:47 INFO   root: Running the installer...
05-15 19:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp\translations, languages=['en_US', 'en']
05-15 19:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp\translations, languages=['en_US', 'en']
05-15 19:47 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=audio9
05-15 19:47 INFO   root: Received settings
05-15 19:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp\translations, languages=['en_US', 'en']
05-15 19:47 DEBUG  TaskList: # Running tasklist...
05-15 19:47 DEBUG  TaskList: ## Running select_target_dir...
05-15 19:47 INFO   WindowsBackend: Installing into C:\ubuntu
05-15 19:47 DEBUG  TaskList: ## Finished select_target_dir
05-15 19:47 DEBUG  TaskList: ## Running create_dir_structure...
05-15 19:47 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-15 19:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-15 19:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-15 19:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-15 19:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-15 19:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-15 19:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-15 19:47 DEBUG  TaskList: ## Finished create_dir_structure
05-15 19:47 DEBUG  TaskList: ## Running uncompress_target_dir...
05-15 19:47 DEBUG  TaskList: ## Finished uncompress_target_dir
05-15 19:47 DEBUG  TaskList: ## Running create_uninstaller...
05-15 19:47 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-15 19:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-15 19:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-15 19:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-15 19:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-15 19:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-15 19:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-15 19:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-15 19:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-15 19:47 DEBUG  TaskList: ## Finished create_uninstaller
05-15 19:47 DEBUG  TaskList: ## Running copy_installation_files...
05-15 19:47 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-15 19:47 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp\winboot -> C:\ubuntu\winboot
05-15 19:47 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pylD3C2.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-15 19:47 DEBUG  TaskList: ## Finished copy_installation_files
05-15 19:47 DEBUG  TaskList: ## Running get_iso...
05-15 19:47 DEBUG  TaskList: New task copy_file
05-15 19:47 DEBUG  TaskList: ### Running copy_file...
05-15 19:48 DEBUG  TaskList: ### Finished copy_file
05-15 19:48 DEBUG  TaskList: New task check_iso
05-15 19:48 DEBUG  TaskList: ### Running check_iso...
05-15 19:48 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
05-15 19:48 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
05-15 19:48 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
05-15 19:48 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-15 19:48 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-15 19:48 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
05-15 19:48 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
05-15 19:48 DEBUG  TaskList: New task get_metalink
05-15 19:48 DEBUG  TaskList: #### Running get_metalink...
05-15 19:48 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink) > C:\ubuntu\install
05-15 19:48 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-i386.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink, basename=ubuntu-11.04-desktop-i386.metalink, length=28158, text=None
05-15 19:48 DEBUG  downloader: download finished (read 28158 bytes)
05-15 19:48 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > C:\ubuntu\install
05-15 19:48 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-15 19:48 DEBUG  downloader: download finished (read 874 bytes)
05-15 19:48 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
05-15 19:48 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-15 19:48 DEBUG  downloader: download finished (read 198 bytes)
05-15 19:48 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-15 19:48 INFO   saplog: Checking block bindings..
05-15 19:48 INFO   saplog: Key verified successfully.
05-15 19:48 DEBUG  CommonBackend: metalink md5sums:
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

05-15 19:48 DEBUG  TaskList: #### Finished get_metalink
05-15 19:48 DEBUG  TaskList: New task get_file_md5
05-15 19:48 DEBUG  TaskList: #### Running get_file_md5...
05-15 19:48 DEBUG  TaskList: #### Finished get_file_md5
05-15 19:48 ERROR  CommonBackend: Invalid md5 for ISO C:\ubuntu\install\installation.iso (8b1085bed498b82ef1485ef19074c281 != 775ecff4394449df5b7e83bb22d23fb8)
None
05-15 19:48 DEBUG  TaskList: ### Finished check_iso
05-15 19:48 DEBUG  CommonBackend: Searching for local ISO
05-15 19:48 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-15 19:48 DEBUG  TaskList: New task download
05-15 19:48 DEBUG  TaskList: ### Running download...
05-15 19:48 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent) > C:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
05-15 19:51 INFO   WindowsFrontend: Operation cancelled
05-15 19:51 DEBUG  WindowsFrontend: frontend.quit
05-15 19:51 DEBUG  WindowsFrontend: frontend.on_quit
05-15 19:51 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
05-15 19:51 DEBUG  TaskList: # Cancelling tasklist
05-15 19:51 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
05-15 19:51 DEBUG  root: application.on_quit
05-15 19:51 DEBUG  root: Forceful exit
05-15 19:51 INFO   root: sys.exit
05-16 03:23 INFO   root: === wubi 11.04 rev211 ===
05-16 03:23 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-16 03:23 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
05-16 03:23 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylC65A.tmp\data
05-16 03:23 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pylC65A.tmp\bin\7z.exe
05-16 03:23 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-16 03:23 DEBUG  CommonBackend: Fetching basic info...
05-16 03:23 DEBUG  CommonBackend: original_exe=E:\wubi.exe
05-16 03:23 DEBUG  CommonBackend: platform=win32
05-16 03:23 DEBUG  CommonBackend: osname=nt
05-16 03:23 DEBUG  CommonBackend: language=en_MY
05-16 03:23 DEBUG  CommonBackend: encoding=cp1252
05-16 03:23 DEBUG  WindowsBackend: arch=amd64
05-16 03:23 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pylC65A.tmp\data\isolist.ini
05-16 03:23 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-16 03:23 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-16 03:23 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-16 03:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-16 03:23 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-16 03:23 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-16 03:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-16 03:23 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-16 03:23 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-16 03:23 DEBUG  WindowsBackend: Fetching host info...
05-16 03:23 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-16 03:23 DEBUG  WindowsBackend: windows version=vista
05-16 03:23 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-16 03:23 DEBUG  WindowsBackend: windows_sp=None
05-16 03:23 DEBUG  WindowsBackend: windows_build=7600
05-16 03:23 DEBUG  WindowsBackend: gmt=8
05-16 03:23 DEBUG  WindowsBackend: country=MY
05-16 03:23 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-16 03:23 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-16 03:23 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-16 03:23 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-16 03:23 DEBUG  WindowsBackend: windows_language_code=1033
05-16 03:23 DEBUG  WindowsBackend: windows_language=English
05-16 03:23 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-16 03:23 DEBUG  WindowsBackend: bootloader=vista
05-16 03:23 DEBUG  WindowsBackend: system_drive=Drive(C: hd 97254.6757813 mb free ntfs)
05-16 03:23 DEBUG  WindowsBackend: drive=Drive(C: hd 97254.6757813 mb free ntfs)
05-16 03:23 DEBUG  WindowsBackend: drive=Drive(D: hd 2.1015625 mb free ntfs)
05-16 03:23 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-16 03:23 DEBUG  WindowsBackend: drive=Drive(G: hd 17321.6914063 mb free ntfs)
05-16 03:23 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-16 03:23 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-16 03:23 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-16 03:23 DEBUG  WindowsBackend: keyboard_id=67699721
05-16 03:23 DEBUG  WindowsBackend: keyboard_layout=us
05-16 03:23 DEBUG  WindowsBackend: keyboard_variant=
05-16 03:23 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-16 03:23 DEBUG  CommonBackend: locale=en_US.UTF-8
05-16 03:23 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-16 03:23 DEBUG  CommonBackend: Searching ISOs on USB devices
05-16 03:23 DEBUG  CommonBackend: Searching for local CDs
05-16 03:23 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC65A.tmp is a valid Ubuntu CD
05-16 03:23 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
05-16 03:23 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC65A.tmp is a valid Ubuntu CD
05-16 03:23 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
05-16 03:23 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC65A.tmp is a valid Ubuntu Netbook CD
05-16 03:23 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
05-16 03:23 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC65A.tmp is a valid Kubuntu CD
05-16 03:23 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
05-16 03:23 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC65A.tmp is a valid Kubuntu CD
05-16 03:23 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
05-16 03:23 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC65A.tmp is a valid Xubuntu CD
05-16 03:23 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
05-16 03:23 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC65A.tmp is a valid Xubuntu CD
05-16 03:23 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
05-16 03:23 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC65A.tmp is a valid Mythbuntu CD
05-16 03:23 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
05-16 03:23 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylC65A.tmp is a valid Mythbuntu CD
05-16 03:23 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylC65A.tmp\casper\filesystem.squashfs
05-16 03:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 03:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 03:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-16 03:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 03:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 03:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:23 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 03:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:23 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 03:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 03:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 03:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 03:23 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-16 03:23 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-16 03:23 INFO   Distro: Found a valid CD for Ubuntu: E:\
05-16 03:23 INFO   root: Running the CD menu...
05-16 03:23 DEBUG  WindowsFrontend: __init__...
05-16 03:23 DEBUG  WindowsFrontend: on_init...
05-16 03:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylC65A.tmp\translations, languages=['en_US', 'en']
05-16 03:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylC65A.tmp\translations, languages=['en_US', 'en']
05-16 03:24 INFO   root: CD menu finished
05-16 03:24 INFO   root: Rebooting
05-16 03:24 DEBUG  TaskList: # Running tasklist...
05-16 03:24 DEBUG  TaskList: ## Running reboot...
05-16 03:24 DEBUG  TaskList: ## Finished reboot
05-16 03:24 DEBUG  TaskList: # Finished tasklist
05-16 03:24 DEBUG  root: application.quit
05-16 03:24 DEBUG  WindowsFrontend: frontend.quit
05-16 03:24 DEBUG  WindowsFrontend: frontend.on_quit
05-16 03:24 DEBUG  root: application.on_quit
05-16 03:24 INFO   root: sys.exit
05-16 03:26 INFO   root: === wubi 11.04 rev211 ===
05-16 03:26 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-16 03:26 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
05-16 03:26 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\data
05-16 03:26 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\bin\7z.exe
05-16 03:26 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-16 03:26 DEBUG  CommonBackend: Fetching basic info...
05-16 03:26 DEBUG  CommonBackend: original_exe=E:\wubi.exe
05-16 03:26 DEBUG  CommonBackend: platform=win32
05-16 03:26 DEBUG  CommonBackend: osname=nt
05-16 03:26 DEBUG  CommonBackend: language=en_MY
05-16 03:26 DEBUG  CommonBackend: encoding=cp1252
05-16 03:26 DEBUG  WindowsBackend: arch=amd64
05-16 03:26 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\data\isolist.ini
05-16 03:26 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-16 03:26 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-16 03:26 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-16 03:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-16 03:26 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-16 03:26 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-16 03:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-16 03:26 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-16 03:26 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-16 03:26 DEBUG  WindowsBackend: Fetching host info...
05-16 03:26 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-16 03:26 DEBUG  WindowsBackend: windows version=vista
05-16 03:26 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-16 03:26 DEBUG  WindowsBackend: windows_sp=None
05-16 03:26 DEBUG  WindowsBackend: windows_build=7600
05-16 03:26 DEBUG  WindowsBackend: gmt=8
05-16 03:26 DEBUG  WindowsBackend: country=MY
05-16 03:26 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-16 03:26 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-16 03:26 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-16 03:26 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-16 03:26 DEBUG  WindowsBackend: windows_language_code=1033
05-16 03:26 DEBUG  WindowsBackend: windows_language=English
05-16 03:26 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-16 03:26 DEBUG  WindowsBackend: bootloader=vista
05-16 03:26 DEBUG  WindowsBackend: system_drive=Drive(C: hd 97246.34375 mb free ntfs)
05-16 03:26 DEBUG  WindowsBackend: drive=Drive(C: hd 97246.34375 mb free ntfs)
05-16 03:26 DEBUG  WindowsBackend: drive=Drive(D: hd 2.1015625 mb free ntfs)
05-16 03:26 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-16 03:26 DEBUG  WindowsBackend: drive=Drive(G: hd 17321.6914063 mb free ntfs)
05-16 03:26 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-16 03:26 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-16 03:26 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-16 03:26 DEBUG  WindowsBackend: keyboard_id=67699721
05-16 03:26 DEBUG  WindowsBackend: keyboard_layout=us
05-16 03:26 DEBUG  WindowsBackend: keyboard_variant=
05-16 03:26 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-16 03:26 DEBUG  CommonBackend: locale=en_US.UTF-8
05-16 03:26 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-16 03:26 DEBUG  CommonBackend: Searching ISOs on USB devices
05-16 03:26 DEBUG  CommonBackend: Searching for local CDs
05-16 03:26 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp is a valid Ubuntu CD
05-16 03:26 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\casper\filesystem.squashfs
05-16 03:26 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp is a valid Ubuntu CD
05-16 03:26 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\casper\filesystem.squashfs
05-16 03:26 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp is a valid Ubuntu Netbook CD
05-16 03:26 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\casper\filesystem.squashfs
05-16 03:26 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp is a valid Kubuntu CD
05-16 03:26 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\casper\filesystem.squashfs
05-16 03:26 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp is a valid Kubuntu CD
05-16 03:26 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\casper\filesystem.squashfs
05-16 03:26 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp is a valid Xubuntu CD
05-16 03:26 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\casper\filesystem.squashfs
05-16 03:26 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp is a valid Xubuntu CD
05-16 03:26 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\casper\filesystem.squashfs
05-16 03:26 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp is a valid Mythbuntu CD
05-16 03:26 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\casper\filesystem.squashfs
05-16 03:26 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp is a valid Mythbuntu CD
05-16 03:26 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\casper\filesystem.squashfs
05-16 03:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 03:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 03:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-16 03:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 03:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 03:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 03:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 03:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 03:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 03:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 03:26 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-16 03:26 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-16 03:26 INFO   Distro: Found a valid CD for Ubuntu: E:\
05-16 03:26 INFO   root: Running the CD menu...
05-16 03:26 DEBUG  WindowsFrontend: __init__...
05-16 03:26 DEBUG  WindowsFrontend: on_init...
05-16 03:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\translations, languages=['en_US', 'en']
05-16 03:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\translations, languages=['en_US', 'en']
05-16 03:27 INFO   root: CD menu finished
05-16 03:27 INFO   root: Already installed, running the uninstaller...
05-16 03:27 INFO   root: Running the uninstaller...
05-16 03:27 INFO   CommonBackend: This is the uninstaller running
05-16 03:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\translations, languages=['en_US', 'en']
05-16 03:27 INFO   root: Received settings
05-16 03:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\translations, languages=['en_US', 'en']
05-16 03:27 DEBUG  TaskList: # Running tasklist...
05-16 03:27 DEBUG  TaskList: ## Running Backup ISO...
05-16 03:27 DEBUG  TaskList: ## Finished Backup ISO
05-16 03:27 DEBUG  TaskList: ## Running Remove bootloader entry...
05-16 03:27 DEBUG  WindowsBackend: Could not find bcd id
05-16 03:27 DEBUG  WindowsBackend: undo_bootini C:
05-16 03:27 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 97246.34375 mb free ntfs)
05-16 03:27 DEBUG  WindowsBackend: undo_bootini D:
05-16 03:27 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2.1015625 mb free ntfs)
05-16 03:27 DEBUG  WindowsBackend: undo_bootini G:
05-16 03:27 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 17321.6914063 mb free ntfs)
05-16 03:27 DEBUG  TaskList: ## Finished Remove bootloader entry
05-16 03:27 DEBUG  TaskList: ## Running Remove target dir...
05-16 03:27 DEBUG  CommonBackend: Deleting C:\ubuntu
05-16 03:27 DEBUG  TaskList: ## Finished Remove target dir
05-16 03:27 DEBUG  TaskList: ## Running Remove registry key...
05-16 03:27 DEBUG  TaskList: ## Finished Remove registry key
05-16 03:27 DEBUG  TaskList: # Finished tasklist
05-16 03:27 INFO   root: Almost finished uninstalling
05-16 03:27 INFO   root: Finished uninstallation
05-16 03:27 DEBUG  CommonBackend: Fetching basic info...
05-16 03:27 DEBUG  CommonBackend: original_exe=E:\wubi.exe
05-16 03:27 DEBUG  CommonBackend: platform=win32
05-16 03:27 DEBUG  CommonBackend: osname=nt
05-16 03:27 DEBUG  WindowsBackend: arch=amd64
05-16 03:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\data\isolist.ini
05-16 03:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-16 03:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-16 03:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-16 03:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-16 03:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-16 03:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-16 03:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-16 03:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-16 03:27 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-16 03:27 DEBUG  WindowsBackend: Fetching host info...
05-16 03:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-16 03:27 DEBUG  WindowsBackend: windows version=vista
05-16 03:27 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-16 03:27 DEBUG  WindowsBackend: windows_sp=None
05-16 03:27 DEBUG  WindowsBackend: windows_build=7600
05-16 03:27 DEBUG  WindowsBackend: gmt=8
05-16 03:27 DEBUG  WindowsBackend: country=MY
05-16 03:27 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-16 03:27 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-16 03:27 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-16 03:27 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-16 03:27 DEBUG  WindowsBackend: windows_language_code=1033
05-16 03:27 DEBUG  WindowsBackend: windows_language=English
05-16 03:27 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-16 03:27 DEBUG  WindowsBackend: bootloader=vista
05-16 03:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 97932.8984375 mb free ntfs)
05-16 03:27 DEBUG  WindowsBackend: drive=Drive(C: hd 97932.8984375 mb free ntfs)
05-16 03:27 DEBUG  WindowsBackend: drive=Drive(D: hd 2.1015625 mb free ntfs)
05-16 03:27 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
05-16 03:27 DEBUG  WindowsBackend: drive=Drive(G: hd 17321.6914063 mb free ntfs)
05-16 03:27 DEBUG  WindowsBackend: uninstaller_path=None
05-16 03:27 DEBUG  WindowsBackend: previous_target_dir=None
05-16 03:27 DEBUG  WindowsBackend: previous_distro_name=None
05-16 03:27 DEBUG  WindowsBackend: keyboard_id=67699721
05-16 03:27 DEBUG  WindowsBackend: keyboard_layout=us
05-16 03:27 DEBUG  WindowsBackend: keyboard_variant=
05-16 03:27 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-16 03:27 DEBUG  CommonBackend: Searching ISOs on USB devices
05-16 03:27 DEBUG  CommonBackend: Searching for local CDs
05-16 03:27 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp is a valid Ubuntu CD
05-16 03:27 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\casper\filesystem.squashfs
05-16 03:27 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp is a valid Ubuntu CD
05-16 03:27 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\casper\filesystem.squashfs
05-16 03:27 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp is a valid Ubuntu Netbook CD
05-16 03:27 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\casper\filesystem.squashfs
05-16 03:27 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp is a valid Kubuntu CD
05-16 03:27 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\casper\filesystem.squashfs
05-16 03:27 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp is a valid Kubuntu CD
05-16 03:27 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\casper\filesystem.squashfs
05-16 03:27 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp is a valid Xubuntu CD
05-16 03:27 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\casper\filesystem.squashfs
05-16 03:27 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp is a valid Xubuntu CD
05-16 03:27 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\casper\filesystem.squashfs
05-16 03:27 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp is a valid Mythbuntu CD
05-16 03:27 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\casper\filesystem.squashfs
05-16 03:27 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp is a valid Mythbuntu CD
05-16 03:27 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\casper\filesystem.squashfs
05-16 03:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 03:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 03:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-16 03:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 03:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 03:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 03:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 03:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 03:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 03:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 03:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 03:27 INFO   Distro: Found a valid CD for Ubuntu: E:\
05-16 03:27 INFO   root: Running the installer...
05-16 03:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\translations, languages=['en_US', 'en']
05-16 03:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylF5A4.tmp\translations, languages=['en_US', 'en']
05-16 03:28 INFO   WindowsFrontend: Operation cancelled
05-16 03:28 DEBUG  WindowsFrontend: frontend.quit
05-16 03:28 DEBUG  WindowsFrontend: frontend.on_quit
05-16 03:28 DEBUG  root: application.on_quit
05-16 03:28 INFO   root: sys.exit
05-16 04:08 INFO   root: === wubi 11.04 rev211 ===
05-16 04:08 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-16 04:08 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
05-16 04:08 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylDF09.tmp\data
05-16 04:08 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pylDF09.tmp\bin\7z.exe
05-16 04:08 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-16 04:08 DEBUG  CommonBackend: Fetching basic info...
05-16 04:08 DEBUG  CommonBackend: original_exe=F:\wubi.exe
05-16 04:08 DEBUG  CommonBackend: platform=win32
05-16 04:08 DEBUG  CommonBackend: osname=nt
05-16 04:08 DEBUG  CommonBackend: language=en_MY
05-16 04:08 DEBUG  CommonBackend: encoding=cp1252
05-16 04:08 DEBUG  WindowsBackend: arch=amd64
05-16 04:08 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pylDF09.tmp\data\isolist.ini
05-16 04:08 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-16 04:08 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-16 04:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-16 04:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-16 04:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-16 04:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-16 04:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-16 04:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-16 04:08 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-16 04:08 DEBUG  WindowsBackend: Fetching host info...
05-16 04:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-16 04:08 DEBUG  WindowsBackend: windows version=vista
05-16 04:08 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-16 04:08 DEBUG  WindowsBackend: windows_sp=None
05-16 04:08 DEBUG  WindowsBackend: windows_build=7600
05-16 04:08 DEBUG  WindowsBackend: gmt=8
05-16 04:08 DEBUG  WindowsBackend: country=MY
05-16 04:08 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-16 04:08 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-16 04:08 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-16 04:08 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-16 04:08 DEBUG  WindowsBackend: windows_language_code=1033
05-16 04:08 DEBUG  WindowsBackend: windows_language=English
05-16 04:08 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-16 04:08 DEBUG  WindowsBackend: bootloader=vista
05-16 04:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 97929.8125 mb free ntfs)
05-16 04:08 DEBUG  WindowsBackend: drive=Drive(C: hd 97929.7851563 mb free ntfs)
05-16 04:08 DEBUG  WindowsBackend: drive=Drive(D: hd 9881.96484375 mb free ntfs)
05-16 04:08 DEBUG  WindowsBackend: drive=Drive(E: hd 22246.5429688 mb free ntfs)
05-16 04:08 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
05-16 04:08 DEBUG  WindowsBackend: uninstaller_path=None
05-16 04:08 DEBUG  WindowsBackend: previous_target_dir=None
05-16 04:08 DEBUG  WindowsBackend: previous_distro_name=None
05-16 04:08 DEBUG  WindowsBackend: keyboard_id=67699721
05-16 04:08 DEBUG  WindowsBackend: keyboard_layout=us
05-16 04:08 DEBUG  WindowsBackend: keyboard_variant=
05-16 04:08 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-16 04:08 DEBUG  CommonBackend: locale=en_US.UTF-8
05-16 04:08 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-16 04:08 DEBUG  CommonBackend: Searching ISOs on USB devices
05-16 04:08 DEBUG  CommonBackend: Searching for local CDs
05-16 04:08 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylDF09.tmp is a valid Ubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylDF09.tmp\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylDF09.tmp is a valid Ubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylDF09.tmp\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylDF09.tmp is a valid Ubuntu Netbook CD
05-16 04:08 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylDF09.tmp\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylDF09.tmp is a valid Kubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylDF09.tmp\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylDF09.tmp is a valid Kubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylDF09.tmp\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylDF09.tmp is a valid Xubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylDF09.tmp\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylDF09.tmp is a valid Xubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylDF09.tmp\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylDF09.tmp is a valid Mythbuntu CD
05-16 04:08 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylDF09.tmp\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylDF09.tmp is a valid Mythbuntu CD
05-16 04:08 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylDF09.tmp\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-16 04:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 04:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 04:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-16 04:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 04:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 04:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-16 04:08 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-16 04:08 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-16 04:08 INFO   Distro: Found a valid CD for Ubuntu: F:\
05-16 04:08 INFO   root: Running the CD menu...
05-16 04:08 DEBUG  WindowsFrontend: __init__...
05-16 04:08 DEBUG  WindowsFrontend: on_init...
05-16 04:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylDF09.tmp\translations, languages=['en_US', 'en']
05-16 04:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylDF09.tmp\translations, languages=['en_US', 'en']
05-16 04:08 INFO   WindowsFrontend: Operation cancelled
05-16 04:08 DEBUG  WindowsFrontend: frontend.quit
05-16 04:08 DEBUG  WindowsFrontend: frontend.on_quit
05-16 04:08 DEBUG  root: application.on_quit
05-16 04:08 INFO   root: sys.exit
05-16 04:08 INFO   root: === wubi 11.04 rev211 ===
05-16 04:08 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-16 04:08 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
05-16 04:08 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp\data
05-16 04:08 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp\bin\7z.exe
05-16 04:08 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-16 04:08 DEBUG  CommonBackend: Fetching basic info...
05-16 04:08 DEBUG  CommonBackend: original_exe=F:\wubi.exe
05-16 04:08 DEBUG  CommonBackend: platform=win32
05-16 04:08 DEBUG  CommonBackend: osname=nt
05-16 04:08 DEBUG  CommonBackend: language=en_MY
05-16 04:08 DEBUG  CommonBackend: encoding=cp1252
05-16 04:08 DEBUG  WindowsBackend: arch=amd64
05-16 04:08 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp\data\isolist.ini
05-16 04:08 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-16 04:08 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-16 04:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-16 04:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-16 04:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-16 04:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-16 04:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-16 04:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-16 04:08 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-16 04:08 DEBUG  WindowsBackend: Fetching host info...
05-16 04:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-16 04:08 DEBUG  WindowsBackend: windows version=vista
05-16 04:08 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-16 04:08 DEBUG  WindowsBackend: windows_sp=None
05-16 04:08 DEBUG  WindowsBackend: windows_build=7600
05-16 04:08 DEBUG  WindowsBackend: gmt=8
05-16 04:08 DEBUG  WindowsBackend: country=MY
05-16 04:08 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-16 04:08 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-16 04:08 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-16 04:08 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-16 04:08 DEBUG  WindowsBackend: windows_language_code=1033
05-16 04:08 DEBUG  WindowsBackend: windows_language=English
05-16 04:08 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-16 04:08 DEBUG  WindowsBackend: bootloader=vista
05-16 04:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 97929.75 mb free ntfs)
05-16 04:08 DEBUG  WindowsBackend: drive=Drive(C: hd 97929.75 mb free ntfs)
05-16 04:08 DEBUG  WindowsBackend: drive=Drive(D: hd 9881.96484375 mb free ntfs)
05-16 04:08 DEBUG  WindowsBackend: drive=Drive(E: hd 22246.5429688 mb free ntfs)
05-16 04:08 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
05-16 04:08 DEBUG  WindowsBackend: uninstaller_path=None
05-16 04:08 DEBUG  WindowsBackend: previous_target_dir=None
05-16 04:08 DEBUG  WindowsBackend: previous_distro_name=None
05-16 04:08 DEBUG  WindowsBackend: keyboard_id=67699721
05-16 04:08 DEBUG  WindowsBackend: keyboard_layout=us
05-16 04:08 DEBUG  WindowsBackend: keyboard_variant=
05-16 04:08 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-16 04:08 DEBUG  CommonBackend: locale=en_US.UTF-8
05-16 04:08 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-16 04:08 DEBUG  CommonBackend: Searching ISOs on USB devices
05-16 04:08 DEBUG  CommonBackend: Searching for local CDs
05-16 04:08 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp is a valid Ubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp is a valid Ubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp is a valid Ubuntu Netbook CD
05-16 04:08 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp is a valid Kubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp is a valid Kubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp is a valid Xubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp is a valid Xubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp is a valid Mythbuntu CD
05-16 04:08 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp is a valid Mythbuntu CD
05-16 04:08 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-16 04:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 04:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 04:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-16 04:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 04:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 04:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 04:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 04:08 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-16 04:08 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-16 04:08 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-16 04:08 INFO   Distro: Found a valid CD for Ubuntu: F:\
05-16 04:08 INFO   root: Running the CD menu...
05-16 04:08 DEBUG  WindowsFrontend: __init__...
05-16 04:08 DEBUG  WindowsFrontend: on_init...
05-16 04:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp\translations, languages=['en_US', 'en']
05-16 04:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp\translations, languages=['en_US', 'en']
05-16 04:08 INFO   root: CD menu finished
05-16 04:08 INFO   root: Running the installer...
05-16 04:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp\translations, languages=['en_US', 'en']
05-16 04:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp\translations, languages=['en_US', 'en']
05-16 04:09 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=6000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=audio9
05-16 04:09 INFO   root: Received settings
05-16 04:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp\translations, languages=['en_US', 'en']
05-16 04:09 DEBUG  TaskList: # Running tasklist...
05-16 04:09 DEBUG  TaskList: ## Running select_target_dir...
05-16 04:09 INFO   WindowsBackend: Installing into D:\ubuntu
05-16 04:09 DEBUG  TaskList: ## Finished select_target_dir
05-16 04:09 DEBUG  TaskList: ## Running create_dir_structure...
05-16 04:09 DEBUG  CommonBackend: Creating dir D:\ubuntu
05-16 04:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
05-16 04:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
05-16 04:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
05-16 04:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
05-16 04:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
05-16 04:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
05-16 04:09 DEBUG  TaskList: ## Finished create_dir_structure
05-16 04:09 DEBUG  TaskList: ## Running uncompress_target_dir...
05-16 04:09 DEBUG  TaskList: ## Finished uncompress_target_dir
05-16 04:09 DEBUG  TaskList: ## Running create_uninstaller...
05-16 04:09 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
05-16 04:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
05-16 04:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
05-16 04:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-16 04:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
05-16 04:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-16 04:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-16 04:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-16 04:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-16 04:09 DEBUG  TaskList: ## Finished create_uninstaller
05-16 04:09 DEBUG  TaskList: ## Running copy_installation_files...
05-16 04:09 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
05-16 04:09 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp\winboot -> D:\ubuntu\winboot
05-16 04:09 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pylE72.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
05-16 04:09 DEBUG  TaskList: ## Finished copy_installation_files
05-16 04:09 DEBUG  TaskList: ## Running get_iso...
05-16 04:09 DEBUG  TaskList: New task copy_file
05-16 04:09 DEBUG  TaskList: ### Running copy_file...
05-16 04:09 DEBUG  TaskList: ### Finished copy_file
05-16 04:09 DEBUG  TaskList: New task check_iso
05-16 04:09 DEBUG  TaskList: ### Running check_iso...
05-16 04:09 DEBUG  CommonBackend: Checking D:\ubuntu\install\installation.iso
05-16 04:09 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu\install\installation.iso
05-16 04:09 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu\install\installation.iso
05-16 04:09 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-16 04:09 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-16 04:09 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu\install\installation.iso
05-16 04:09 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
05-16 04:09 DEBUG  TaskList: New task get_metalink
05-16 04:09 DEBUG  TaskList: #### Running get_metalink...
05-16 04:09 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink) > D:\ubuntu\install
05-16 04:09 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-11.04-desktop-i386.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink, basename=ubuntu-11.04-desktop-i386.metalink, length=28158, text=None
05-16 04:10 DEBUG  downloader: download finished (read 28158 bytes)
05-16 04:10 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > D:\ubuntu\install
05-16 04:10 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-16 04:10 DEBUG  downloader: download finished (read 874 bytes)
05-16 04:10 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
05-16 04:10 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-16 04:10 DEBUG  downloader: download finished (read 198 bytes)
05-16 04:10 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-16 04:10 INFO   saplog: Checking block bindings..
05-16 04:10 INFO   saplog: Key verified successfully.
05-16 04:10 DEBUG  CommonBackend: metalink md5sums:
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

05-16 04:10 DEBUG  TaskList: #### Finished get_metalink
05-16 04:10 DEBUG  TaskList: New task get_file_md5
05-16 04:10 DEBUG  TaskList: #### Running get_file_md5...
05-16 04:10 DEBUG  TaskList: #### Finished get_file_md5
05-16 04:10 ERROR  CommonBackend: Invalid md5 for ISO D:\ubuntu\install\installation.iso (8b1085bed498b82ef1485ef19074c281 != 775ecff4394449df5b7e83bb22d23fb8)
None
05-16 04:10 DEBUG  TaskList: ### Finished check_iso
05-16 04:10 DEBUG  CommonBackend: Searching for local ISO
05-16 04:10 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-16 04:10 DEBUG  TaskList: New task download
05-16 04:10 DEBUG  TaskList: ### Running download...
05-16 04:10 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent) > D:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
05-16 07:10 ERROR  TaskList: Traceback (most recent call last):
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


05-16 07:10 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
05-16 07:10 DEBUG  TaskList: ### Finished download
05-16 07:10 ERROR  TaskList: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-11.04-desktop-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-11.04-desktop-i386.iso'
05-16 07:10 DEBUG  TaskList: # Cancelling tasklist
05-16 07:10 DEBUG  TaskList: # Finished tasklist
05-16 07:10 ERROR  root: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-11.04-desktop-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-11.04-desktop-i386.iso'
05-16 12:33 INFO   root: === wubi 11.04 rev211 ===
05-16 12:33 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-16 12:33 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
05-16 12:33 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\data
05-16 12:33 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\bin\7z.exe
05-16 12:33 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-16 12:33 DEBUG  CommonBackend: Fetching basic info...
05-16 12:33 DEBUG  CommonBackend: original_exe=F:\wubi.exe
05-16 12:33 DEBUG  CommonBackend: platform=win32
05-16 12:33 DEBUG  CommonBackend: osname=nt
05-16 12:33 DEBUG  CommonBackend: language=en_MY
05-16 12:33 DEBUG  CommonBackend: encoding=cp1252
05-16 12:33 DEBUG  WindowsBackend: arch=amd64
05-16 12:33 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\data\isolist.ini
05-16 12:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-16 12:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-16 12:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-16 12:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-16 12:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-16 12:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-16 12:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-16 12:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-16 12:33 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-16 12:33 DEBUG  WindowsBackend: Fetching host info...
05-16 12:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-16 12:33 DEBUG  WindowsBackend: windows version=vista
05-16 12:33 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-16 12:33 DEBUG  WindowsBackend: windows_sp=None
05-16 12:33 DEBUG  WindowsBackend: windows_build=7600
05-16 12:33 DEBUG  WindowsBackend: gmt=8
05-16 12:33 DEBUG  WindowsBackend: country=MY
05-16 12:33 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-16 12:33 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-16 12:33 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-16 12:33 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-16 12:33 DEBUG  WindowsBackend: windows_language_code=1033
05-16 12:33 DEBUG  WindowsBackend: windows_language=English
05-16 12:33 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-16 12:33 DEBUG  WindowsBackend: bootloader=vista
05-16 12:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 98053.0507813 mb free ntfs)
05-16 12:33 DEBUG  WindowsBackend: drive=Drive(C: hd 98053.0507813 mb free ntfs)
05-16 12:33 DEBUG  WindowsBackend: drive=Drive(D: hd 9059.40234375 mb free ntfs)
05-16 12:33 DEBUG  WindowsBackend: drive=Drive(E: hd 22246.5429688 mb free ntfs)
05-16 12:33 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
05-16 12:33 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
05-16 12:33 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
05-16 12:33 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-16 12:33 DEBUG  WindowsBackend: keyboard_id=67699721
05-16 12:33 DEBUG  WindowsBackend: keyboard_layout=us
05-16 12:33 DEBUG  WindowsBackend: keyboard_variant=
05-16 12:33 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-16 12:33 DEBUG  CommonBackend: locale=en_US.UTF-8
05-16 12:33 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-16 12:33 DEBUG  CommonBackend: Searching ISOs on USB devices
05-16 12:33 DEBUG  CommonBackend: Searching for local CDs
05-16 12:33 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp is a valid Ubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp is a valid Ubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp is a valid Ubuntu Netbook CD
05-16 12:33 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp is a valid Kubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp is a valid Kubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp is a valid Xubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp is a valid Xubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp is a valid Mythbuntu CD
05-16 12:33 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp is a valid Mythbuntu CD
05-16 12:33 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-16 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-16 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-16 12:33 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-16 12:33 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-16 12:33 INFO   Distro: Found a valid CD for Ubuntu: F:\
05-16 12:33 INFO   root: Running the CD menu...
05-16 12:33 DEBUG  WindowsFrontend: __init__...
05-16 12:33 DEBUG  WindowsFrontend: on_init...
05-16 12:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\translations, languages=['en_US', 'en']
05-16 12:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\translations, languages=['en_US', 'en']
05-16 12:33 INFO   root: CD menu finished
05-16 12:33 INFO   root: Already installed, running the uninstaller...
05-16 12:33 INFO   root: Running the uninstaller...
05-16 12:33 INFO   CommonBackend: This is the uninstaller running
05-16 12:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\translations, languages=['en_US', 'en']
05-16 12:33 INFO   root: Received settings
05-16 12:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\translations, languages=['en_US', 'en']
05-16 12:33 DEBUG  TaskList: # Running tasklist...
05-16 12:33 DEBUG  TaskList: ## Running Backup ISO...
05-16 12:33 DEBUG  TaskList: ## Finished Backup ISO
05-16 12:33 DEBUG  TaskList: ## Running Remove bootloader entry...
05-16 12:33 DEBUG  WindowsBackend: Could not find bcd id
05-16 12:33 DEBUG  WindowsBackend: undo_bootini C:
05-16 12:33 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 98053.0507813 mb free ntfs)
05-16 12:33 DEBUG  WindowsBackend: undo_bootini D:
05-16 12:33 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 9059.40234375 mb free ntfs)
05-16 12:33 DEBUG  WindowsBackend: undo_bootini E:
05-16 12:33 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 22246.5429688 mb free ntfs)
05-16 12:33 DEBUG  TaskList: ## Finished Remove bootloader entry
05-16 12:33 DEBUG  TaskList: ## Running Remove target dir...
05-16 12:33 DEBUG  CommonBackend: Deleting D:\ubuntu
05-16 12:33 DEBUG  TaskList: ## Finished Remove target dir
05-16 12:33 DEBUG  TaskList: ## Running Remove registry key...
05-16 12:33 DEBUG  TaskList: ## Finished Remove registry key
05-16 12:33 DEBUG  TaskList: # Finished tasklist
05-16 12:33 INFO   root: Almost finished uninstalling
05-16 12:33 INFO   root: Finished uninstallation
05-16 12:33 DEBUG  CommonBackend: Fetching basic info...
05-16 12:33 DEBUG  CommonBackend: original_exe=F:\wubi.exe
05-16 12:33 DEBUG  CommonBackend: platform=win32
05-16 12:33 DEBUG  CommonBackend: osname=nt
05-16 12:33 DEBUG  WindowsBackend: arch=amd64
05-16 12:33 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\data\isolist.ini
05-16 12:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-16 12:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-16 12:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-16 12:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-16 12:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-16 12:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-16 12:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-16 12:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-16 12:33 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-16 12:33 DEBUG  WindowsBackend: Fetching host info...
05-16 12:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-16 12:33 DEBUG  WindowsBackend: windows version=vista
05-16 12:33 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-16 12:33 DEBUG  WindowsBackend: windows_sp=None
05-16 12:33 DEBUG  WindowsBackend: windows_build=7600
05-16 12:33 DEBUG  WindowsBackend: gmt=8
05-16 12:33 DEBUG  WindowsBackend: country=MY
05-16 12:33 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-16 12:33 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-16 12:33 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-16 12:33 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-16 12:33 DEBUG  WindowsBackend: windows_language_code=1033
05-16 12:33 DEBUG  WindowsBackend: windows_language=English
05-16 12:33 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-16 12:33 DEBUG  WindowsBackend: bootloader=vista
05-16 12:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 98053.515625 mb free ntfs)
05-16 12:33 DEBUG  WindowsBackend: drive=Drive(C: hd 98053.515625 mb free ntfs)
05-16 12:33 DEBUG  WindowsBackend: drive=Drive(D: hd 9881.4609375 mb free ntfs)
05-16 12:33 DEBUG  WindowsBackend: drive=Drive(E: hd 22246.5429688 mb free ntfs)
05-16 12:33 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
05-16 12:33 DEBUG  WindowsBackend: uninstaller_path=None
05-16 12:33 DEBUG  WindowsBackend: previous_target_dir=None
05-16 12:33 DEBUG  WindowsBackend: previous_distro_name=None
05-16 12:33 DEBUG  WindowsBackend: keyboard_id=67699721
05-16 12:33 DEBUG  WindowsBackend: keyboard_layout=us
05-16 12:33 DEBUG  WindowsBackend: keyboard_variant=
05-16 12:33 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-16 12:33 DEBUG  CommonBackend: Searching ISOs on USB devices
05-16 12:33 DEBUG  CommonBackend: Searching for local CDs
05-16 12:33 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp is a valid Ubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp is a valid Ubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp is a valid Ubuntu Netbook CD
05-16 12:33 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp is a valid Kubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp is a valid Kubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp is a valid Xubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp is a valid Xubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp is a valid Mythbuntu CD
05-16 12:33 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp is a valid Mythbuntu CD
05-16 12:33 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-16 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 12:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-16 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 12:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 12:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-16 12:33 INFO   Distro: Found a valid CD for Ubuntu: F:\
05-16 12:33 INFO   root: Running the installer...
05-16 12:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\translations, languages=['en_US', 'en']
05-16 12:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\translations, languages=['en_US', 'en']
05-16 12:34 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=6000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=audio9
05-16 12:34 INFO   root: Received settings
05-16 12:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\translations, languages=['en_US', 'en']
05-16 12:34 DEBUG  TaskList: # Running tasklist...
05-16 12:34 DEBUG  TaskList: ## Running select_target_dir...
05-16 12:34 INFO   WindowsBackend: Installing into D:\ubuntu
05-16 12:34 DEBUG  TaskList: ## Finished select_target_dir
05-16 12:34 DEBUG  TaskList: ## Running create_dir_structure...
05-16 12:34 DEBUG  CommonBackend: Creating dir D:\ubuntu
05-16 12:34 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
05-16 12:34 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
05-16 12:34 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
05-16 12:34 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
05-16 12:34 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
05-16 12:34 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
05-16 12:34 DEBUG  TaskList: ## Finished create_dir_structure
05-16 12:34 DEBUG  TaskList: ## Running uncompress_target_dir...
05-16 12:34 DEBUG  TaskList: ## Finished uncompress_target_dir
05-16 12:34 DEBUG  TaskList: ## Running create_uninstaller...
05-16 12:34 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
05-16 12:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
05-16 12:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
05-16 12:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-16 12:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
05-16 12:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-16 12:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-16 12:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-16 12:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-16 12:34 DEBUG  TaskList: ## Finished create_uninstaller
05-16 12:34 DEBUG  TaskList: ## Running copy_installation_files...
05-16 12:34 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
05-16 12:34 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\winboot -> D:\ubuntu\winboot
05-16 12:34 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pylAB27.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
05-16 12:34 DEBUG  TaskList: ## Finished copy_installation_files
05-16 12:34 DEBUG  TaskList: ## Running get_iso...
05-16 12:34 DEBUG  TaskList: New task copy_file
05-16 12:34 DEBUG  TaskList: ### Running copy_file...
05-16 12:35 DEBUG  TaskList: ### Finished copy_file
05-16 12:35 DEBUG  TaskList: New task check_iso
05-16 12:35 DEBUG  TaskList: ### Running check_iso...
05-16 12:35 DEBUG  CommonBackend: Checking D:\ubuntu\install\installation.iso
05-16 12:35 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu\install\installation.iso
05-16 12:35 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu\install\installation.iso
05-16 12:35 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-16 12:35 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-16 12:35 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu\install\installation.iso
05-16 12:35 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
05-16 12:35 DEBUG  TaskList: New task get_metalink
05-16 12:35 DEBUG  TaskList: #### Running get_metalink...
05-16 12:35 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink) > D:\ubuntu\install
05-16 12:35 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-11.04-desktop-i386.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink, basename=ubuntu-11.04-desktop-i386.metalink, length=28158, text=None
05-16 12:35 DEBUG  downloader: download finished (read 28158 bytes)
05-16 12:35 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > D:\ubuntu\install
05-16 12:35 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-16 12:35 DEBUG  downloader: download finished (read 874 bytes)
05-16 12:35 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
05-16 12:35 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-16 12:35 DEBUG  downloader: download finished (read 198 bytes)
05-16 12:35 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-16 12:35 INFO   saplog: Checking block bindings..
05-16 12:35 INFO   saplog: Key verified successfully.
05-16 12:35 DEBUG  CommonBackend: metalink md5sums:
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

05-16 12:35 DEBUG  TaskList: #### Finished get_metalink
05-16 12:35 DEBUG  TaskList: New task get_file_md5
05-16 12:35 DEBUG  TaskList: #### Running get_file_md5...
05-16 12:35 DEBUG  TaskList: #### Finished get_file_md5
05-16 12:35 ERROR  CommonBackend: Invalid md5 for ISO D:\ubuntu\install\installation.iso (8b1085bed498b82ef1485ef19074c281 != 775ecff4394449df5b7e83bb22d23fb8)
None
05-16 12:35 DEBUG  TaskList: ### Finished check_iso
05-16 12:35 DEBUG  CommonBackend: Searching for local ISO
05-16 12:35 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-16 12:35 DEBUG  TaskList: New task download
05-16 12:35 DEBUG  TaskList: ### Running download...
05-16 12:35 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent) > D:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
05-16 12:50 INFO   WindowsFrontend: Operation cancelled
05-16 12:51 INFO   WindowsFrontend: Cancelled cancellation, resuming
05-16 13:09 INFO   WindowsFrontend: Operation cancelled
05-16 13:09 DEBUG  WindowsFrontend: frontend.quit
05-16 13:09 DEBUG  WindowsFrontend: frontend.on_quit
05-16 13:09 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
05-16 13:09 DEBUG  TaskList: # Cancelling tasklist
05-16 13:09 DEBUG  TaskList: ### Finished download
05-16 13:09 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
05-16 13:09 DEBUG  root: application.on_quit
05-16 13:09 DEBUG  root: Forceful exit
05-16 13:09 INFO   root: sys.exit
05-18 01:18 INFO   root: === wubi 11.04 rev211 ===
05-18 01:18 DEBUG  root: Logfile is c:\users\audibi~1\appdata\local\temp\wubi-11.04-rev211.log
05-18 01:18 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
05-18 01:18 DEBUG  CommonBackend: data_dir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\data
05-18 01:18 DEBUG  WindowsBackend: 7z=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\bin\7z.exe
05-18 01:18 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-18 01:18 DEBUG  CommonBackend: Fetching basic info...
05-18 01:18 DEBUG  CommonBackend: original_exe=F:\wubi.exe
05-18 01:18 DEBUG  CommonBackend: platform=win32
05-18 01:18 DEBUG  CommonBackend: osname=nt
05-18 01:18 DEBUG  CommonBackend: language=en_MY
05-18 01:18 DEBUG  CommonBackend: encoding=cp1252
05-18 01:18 DEBUG  WindowsBackend: arch=amd64
05-18 01:18 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\data\isolist.ini
05-18 01:18 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-18 01:18 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-18 01:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-18 01:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-18 01:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-18 01:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-18 01:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-18 01:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-18 01:18 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-18 01:18 DEBUG  WindowsBackend: Fetching host info...
05-18 01:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-18 01:18 DEBUG  WindowsBackend: windows version=vista
05-18 01:18 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-18 01:18 DEBUG  WindowsBackend: windows_sp=Service Pack 1
05-18 01:18 DEBUG  WindowsBackend: windows_build=7601
05-18 01:18 DEBUG  WindowsBackend: gmt=8
05-18 01:18 DEBUG  WindowsBackend: country=MY
05-18 01:18 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-18 01:18 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-18 01:18 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-18 01:18 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-18 01:18 DEBUG  WindowsBackend: windows_language_code=1033
05-18 01:18 DEBUG  WindowsBackend: windows_language=English
05-18 01:18 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-18 01:18 DEBUG  WindowsBackend: bootloader=vista
05-18 01:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 92891.2421875 mb free ntfs)
05-18 01:18 DEBUG  WindowsBackend: drive=Drive(C: hd 92891.2421875 mb free ntfs)
05-18 01:18 DEBUG  WindowsBackend: drive=Drive(D: hd 9191.87890625 mb free ntfs)
05-18 01:18 DEBUG  WindowsBackend: drive=Drive(E: hd 38730.4335938 mb free ntfs)
05-18 01:18 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
05-18 01:18 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
05-18 01:18 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
05-18 01:18 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-18 01:18 DEBUG  WindowsBackend: keyboard_id=67699721
05-18 01:18 DEBUG  WindowsBackend: keyboard_layout=us
05-18 01:18 DEBUG  WindowsBackend: keyboard_variant=
05-18 01:18 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
05-18 01:18 DEBUG  CommonBackend: locale=en_US.UTF-8
05-18 01:18 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-18 01:18 DEBUG  CommonBackend: Searching ISOs on USB devices
05-18 01:18 DEBUG  CommonBackend: Searching for local CDs
05-18 01:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp is a valid Ubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp is a valid Ubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp is a valid Ubuntu Netbook CD
05-18 01:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp is a valid Kubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp is a valid Kubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp is a valid Xubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp is a valid Xubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp is a valid Mythbuntu CD
05-18 01:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp is a valid Mythbuntu CD
05-18 01:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-18 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-18 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-18 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-18 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-18 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-18 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-18 01:18 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-18 01:18 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-18 01:18 INFO   Distro: Found a valid CD for Ubuntu: F:\
05-18 01:18 INFO   root: Running the CD menu...
05-18 01:18 DEBUG  WindowsFrontend: __init__...
05-18 01:18 DEBUG  WindowsFrontend: on_init...
05-18 01:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\translations, languages=['en_US', 'en']
05-18 01:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\translations, languages=['en_US', 'en']
05-18 01:18 INFO   root: CD menu finished
05-18 01:18 INFO   root: Already installed, running the uninstaller...
05-18 01:18 INFO   root: Running the uninstaller...
05-18 01:18 INFO   CommonBackend: This is the uninstaller running
05-18 01:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\translations, languages=['en_US', 'en']
05-18 01:18 INFO   root: Received settings
05-18 01:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\translations, languages=['en_US', 'en']
05-18 01:18 DEBUG  TaskList: # Running tasklist...
05-18 01:18 DEBUG  TaskList: ## Running Backup ISO...
05-18 01:18 DEBUG  TaskList: ## Finished Backup ISO
05-18 01:18 DEBUG  TaskList: ## Running Remove bootloader entry...
05-18 01:18 DEBUG  WindowsBackend: Could not find bcd id
05-18 01:18 DEBUG  WindowsBackend: undo_bootini C:
05-18 01:18 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 92891.2421875 mb free ntfs)
05-18 01:18 DEBUG  WindowsBackend: undo_bootini D:
05-18 01:18 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 9191.87890625 mb free ntfs)
05-18 01:18 DEBUG  WindowsBackend: undo_bootini E:
05-18 01:18 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 38730.4335938 mb free ntfs)
05-18 01:18 DEBUG  TaskList: ## Finished Remove bootloader entry
05-18 01:18 DEBUG  TaskList: ## Running Remove target dir...
05-18 01:18 DEBUG  CommonBackend: Deleting D:\ubuntu
05-18 01:18 DEBUG  TaskList: ## Finished Remove target dir
05-18 01:18 DEBUG  TaskList: ## Running Remove registry key...
05-18 01:18 DEBUG  TaskList: ## Finished Remove registry key
05-18 01:18 DEBUG  TaskList: # Finished tasklist
05-18 01:18 INFO   root: Almost finished uninstalling
05-18 01:18 INFO   root: Finished uninstallation
05-18 01:18 DEBUG  CommonBackend: Fetching basic info...
05-18 01:18 DEBUG  CommonBackend: original_exe=F:\wubi.exe
05-18 01:18 DEBUG  CommonBackend: platform=win32
05-18 01:18 DEBUG  CommonBackend: osname=nt
05-18 01:18 DEBUG  WindowsBackend: arch=amd64
05-18 01:18 DEBUG  CommonBackend: Parsing isolist=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\data\isolist.ini
05-18 01:18 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-18 01:18 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-18 01:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-18 01:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-18 01:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-18 01:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-18 01:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-18 01:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-18 01:18 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-18 01:18 DEBUG  WindowsBackend: Fetching host info...
05-18 01:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-18 01:18 DEBUG  WindowsBackend: windows version=vista
05-18 01:18 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-18 01:18 DEBUG  WindowsBackend: windows_sp=Service Pack 1
05-18 01:18 DEBUG  WindowsBackend: windows_build=7601
05-18 01:18 DEBUG  WindowsBackend: gmt=8
05-18 01:18 DEBUG  WindowsBackend: country=MY
05-18 01:18 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
05-18 01:18 DEBUG  WindowsBackend: windows_username=audi bin marwoto
05-18 01:18 DEBUG  WindowsBackend: user_full_name=audi bin marwoto
05-18 01:18 DEBUG  WindowsBackend: user_directory=C:\Users\audi bin marwoto
05-18 01:18 DEBUG  WindowsBackend: windows_language_code=1033
05-18 01:18 DEBUG  WindowsBackend: windows_language=English
05-18 01:18 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N475   @ 1.83GHz
05-18 01:18 DEBUG  WindowsBackend: bootloader=vista
05-18 01:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 92890.96875 mb free ntfs)
05-18 01:18 DEBUG  WindowsBackend: drive=Drive(C: hd 92890.96875 mb free ntfs)
05-18 01:18 DEBUG  WindowsBackend: drive=Drive(D: hd 9881.9375 mb free ntfs)
05-18 01:18 DEBUG  WindowsBackend: drive=Drive(E: hd 38730.4335938 mb free ntfs)
05-18 01:18 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
05-18 01:18 DEBUG  WindowsBackend: uninstaller_path=None
05-18 01:18 DEBUG  WindowsBackend: previous_target_dir=None
05-18 01:18 DEBUG  WindowsBackend: previous_distro_name=None
05-18 01:18 DEBUG  WindowsBackend: keyboard_id=67699721
05-18 01:18 DEBUG  WindowsBackend: keyboard_layout=us
05-18 01:18 DEBUG  WindowsBackend: keyboard_variant=
05-18 01:18 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-18 01:18 DEBUG  CommonBackend: Searching ISOs on USB devices
05-18 01:18 DEBUG  CommonBackend: Searching for local CDs
05-18 01:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp is a valid Ubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp is a valid Ubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp is a valid Ubuntu Netbook CD
05-18 01:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp is a valid Kubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp is a valid Kubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp is a valid Xubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp is a valid Xubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp is a valid Mythbuntu CD
05-18 01:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp is a valid Mythbuntu CD
05-18 01:18 DEBUG  Distro:     does not contain C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-18 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-18 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-18 01:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-18 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-18 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-18 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-18 01:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-18 01:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-18 01:18 INFO   Distro: Found a valid CD for Ubuntu: F:\
05-18 01:18 INFO   root: Running the installer...
05-18 01:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\translations, languages=['en_US', 'en']
05-18 01:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\translations, languages=['en_US', 'en']
05-18 01:18 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=6000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=audio9
05-18 01:18 INFO   root: Received settings
05-18 01:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\translations, languages=['en_US', 'en']
05-18 01:18 DEBUG  TaskList: # Running tasklist...
05-18 01:18 DEBUG  TaskList: ## Running select_target_dir...
05-18 01:18 INFO   WindowsBackend: Installing into D:\ubuntu
05-18 01:18 DEBUG  TaskList: ## Finished select_target_dir
05-18 01:18 DEBUG  TaskList: ## Running create_dir_structure...
05-18 01:18 DEBUG  CommonBackend: Creating dir D:\ubuntu
05-18 01:18 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
05-18 01:18 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
05-18 01:18 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
05-18 01:18 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
05-18 01:18 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
05-18 01:18 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
05-18 01:18 DEBUG  TaskList: ## Finished create_dir_structure
05-18 01:18 DEBUG  TaskList: ## Running uncompress_target_dir...
05-18 01:18 DEBUG  TaskList: ## Finished uncompress_target_dir
05-18 01:18 DEBUG  TaskList: ## Running create_uninstaller...
05-18 01:18 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
05-18 01:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
05-18 01:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
05-18 01:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-18 01:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
05-18 01:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-18 01:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-18 01:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-18 01:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-18 01:19 DEBUG  TaskList: ## Finished create_uninstaller
05-18 01:19 DEBUG  TaskList: ## Running copy_installation_files...
05-18 01:19 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
05-18 01:19 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\winboot -> D:\ubuntu\winboot
05-18 01:19 DEBUG  WindowsBackend: Copying C:\Users\AUDIBI~1\AppData\Local\Temp\pyl108B.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
05-18 01:19 DEBUG  TaskList: ## Finished copy_installation_files
05-18 01:19 DEBUG  TaskList: ## Running get_iso...
05-18 01:19 DEBUG  TaskList: New task copy_file
05-18 01:19 DEBUG  TaskList: ### Running copy_file...
05-18 01:20 DEBUG  TaskList: ### Finished copy_file
05-18 01:20 DEBUG  TaskList: New task check_iso
05-18 01:20 DEBUG  TaskList: ### Running check_iso...
05-18 01:20 DEBUG  CommonBackend: Checking D:\ubuntu\install\installation.iso
05-18 01:20 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu\install\installation.iso
05-18 01:20 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu\install\installation.iso
05-18 01:20 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-18 01:20 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-18 01:20 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu\install\installation.iso
05-18 01:20 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
05-18 01:20 DEBUG  TaskList: New task get_metalink
05-18 01:20 DEBUG  TaskList: #### Running get_metalink...
05-18 01:20 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink) > D:\ubuntu\install
05-18 01:20 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-11.04-desktop-i386.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink, basename=ubuntu-11.04-desktop-i386.metalink, length=28158, text=None
05-18 01:20 DEBUG  downloader: download finished (read 28158 bytes)
05-18 01:20 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > D:\ubuntu\install
05-18 01:20 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-18 01:20 DEBUG  downloader: download finished (read 874 bytes)
05-18 01:20 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
05-18 01:20 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-18 01:20 DEBUG  downloader: download finished (read 198 bytes)
05-18 01:20 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-18 01:20 INFO   saplog: Checking block bindings..
05-18 01:20 INFO   saplog: Key verified successfully.
05-18 01:20 DEBUG  CommonBackend: metalink md5sums:
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

05-18 01:20 DEBUG  TaskList: #### Finished get_metalink
05-18 01:20 DEBUG  TaskList: New task get_file_md5
05-18 01:20 DEBUG  TaskList: #### Running get_file_md5...
05-18 01:21 DEBUG  TaskList: #### Finished get_file_md5
05-18 01:21 ERROR  CommonBackend: Invalid md5 for ISO D:\ubuntu\install\installation.iso (8b1085bed498b82ef1485ef19074c281 != 775ecff4394449df5b7e83bb22d23fb8)
None
05-18 01:21 DEBUG  TaskList: ### Finished check_iso
05-18 01:21 DEBUG  CommonBackend: Searching for local ISO
05-18 01:21 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-18 01:21 DEBUG  TaskList: New task download
05-18 01:21 DEBUG  TaskList: ### Running download...
05-18 01:21 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent) > D:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
05-18 05:11 ERROR  TaskList: Traceback (most recent call last):
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


05-18 05:11 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
05-18 05:11 DEBUG  TaskList: ### Finished download
05-18 05:11 ERROR  TaskList: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-11.04-desktop-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-11.04-desktop-i386.iso'
05-18 05:11 DEBUG  TaskList: # Cancelling tasklist
05-18 05:11 DEBUG  TaskList: # Finished tasklist
05-18 05:11 ERROR  root: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-11.04-desktop-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-11.04-desktop-i386.iso'

---

### Post by bcbc on 2011-05-18
> **aaudio9 said:**
> Thnks bcbc for ur reply. I'll put the ISO n wubi in the same folder and install again (hope it works this time). Im installing right now.

I include the log of my previous installation.

05-18 01:21 ERROR  CommonBackend: Invalid md5 for ISO D:\ubuntu\install\installation.iso (8b1085bed498b82ef1485ef19074c281 != 775ecff4394449df5b7e83bb22d23fb8)
None

The first error is an invalid md5sum on the iso.

---

### Post by aaudio9 on 2011-05-18
so how to fix this problem??i have to download another ISO?

---

### Post by bcbc on 2011-05-19
> **aaudio9 said:**
> so how to fix this problem??i have to download another ISO?

Yes. Download another ISO. Use something like bittorrent if you have a flaky connection. Check the md5sum manually (or let Wubi do it).

---

### Post by aaudio9 on 2011-05-19
how to check manually?? (im a noob):shy:

---

### Post by bcbc on 2011-05-19
Sorry should have added the link: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

That's the nice thing about Wubi as it does it for you - I think you'll find it easier: place wubi.exe in the same folder as the downloaded Desktop CD ISO and run wubi from there. Then just check the log file if it fails.

From the [Wubi Guide]("https://wiki.ubuntu.com/WubiGuide"):
> ...download both Wubi.exe and the required Desktop ISO from the same location (the release has to match):

For 10.04 use [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

For 10.10 use [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)

For 11.04 use [http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)

Copy both files into the same folder ... and run the Wubi executable.

---

### Post by aaudio9 on 2011-05-19
Thnks...the md5sum is different...but 

Why is that?the release is different??i have to dl the same release wubi and the ISO?

What is desktop environtment in wubi?is it like themes in windows?
i like the Xubuntu (coz of the cute mouse in the logo) hehe...

---

### Post by bcbc on 2011-05-19
> **aaudio9 said:**
> Thnks...the md5sum is different...but 

Why is that?the release is different??i have to dl the same release wubi and the ISO?

What is desktop environtment in wubi?is it like themes in windows?
i like the Xubuntu (coz of the cute mouse in the logo) hehe...
There's a long answer and there's a short answer. The short answer is that within wubi.exe there is specific code that checks the release of the Ubuntu desktop CD ISO and refuses to install with a different release. 

Wubi is the windows ubuntu installer. The desktop environment in Ubuntu is whichever one you choose to install. So if you use Wubi to install Xubuntu, you'll get Xubuntu. I tried that and it seems pretty decent - although I tend to stick with Ubuntu.

---

### Post by aaudio9 on 2011-05-22
i have safely install ubuntu on my laptop~
but it seems cant connect to the wireless :(

---

