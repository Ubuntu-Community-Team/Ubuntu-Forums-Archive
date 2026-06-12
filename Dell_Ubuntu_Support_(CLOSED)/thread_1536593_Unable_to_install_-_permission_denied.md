---
title: "Unable to install - permission denied"
date: 2010-07-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by elasticsoul on 2010-07-22
Hi all,
 
 

I just bought a new-to-me Dell C640 with Win XP, with the intention of wiping it clean and going Ubuntu. Tired of Windows, and time to learn the future! Unfortunately, the future has been delayed due to installation issues. 
 
UPDATE: 
* System has: 1.7GHz processor, 1G RAM, 30G HD, 1024x768, CD/DVD drive
* Attempting a clean install of Ubuntu - bye, bye Windows
 
Here's what I did:[LIST=1]
[*]Burned a CD, checked the MD5, verified it, etc, on another computer.
[*]Attempted to boot from the CD on the 'new' Dell, but it never does.
[/LIST]There is much CD and hard drive activity, then nothing. The initial Ubuntu screen with the 5 dots (equivalent to hourglass) stays on the screen forever. When I reboot in Win XP and check the log, there are "permission denied errors" - no idea if this is the problem. 
 
The log file is below. Please help me dump Windows...
 
Thanks all,
Brian
 
07-21 21:28 INFO root: === wubi 10.04 rev189 ===
07-21 21:28 DEBUG root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-10.04-rev189.log
07-21 21:28 DEBUG root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
07-21 21:28 DEBUG CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\data
07-21 21:28 DEBUG WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\bin\7z.exe
07-21 21:28 DEBUG CommonBackend: Fetching basic info...
07-21 21:28 DEBUG CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
07-21 21:28 DEBUG CommonBackend: platform=win32
07-21 21:28 DEBUG CommonBackend: osname=nt
07-21 21:28 DEBUG CommonBackend: language=en_US
07-21 21:28 DEBUG CommonBackend: encoding=cp1252
07-21 21:28 DEBUG WindowsBackend: arch=i386
07-21 21:28 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\data\isolist.ini
07-21 21:28 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-21 21:28 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-21 21:28 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-21 21:28 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-21 21:28 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-21 21:28 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-21 21:28 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-21 21:28 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-21 21:28 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
07-21 21:28 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
07-21 21:28 DEBUG WindowsBackend: Fetching host info...
07-21 21:28 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-21 21:28 DEBUG WindowsBackend: windows version=xp
07-21 21:28 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
07-21 21:28 DEBUG WindowsBackend: windows_sp=Service Pack 3
07-21 21:28 DEBUG WindowsBackend: windows_build=2600
07-21 21:28 DEBUG WindowsBackend: gmt=-8
07-21 21:28 DEBUG WindowsBackend: country=US
07-21 21:28 DEBUG WindowsBackend: timezone=America/Los_Angeles
07-21 21:28 DEBUG WindowsBackend: windows_username=Administrator
07-21 21:28 DEBUG WindowsBackend: user_full_name=Administrator
07-21 21:28 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Administrator
07-21 21:28 DEBUG WindowsBackend: windows_language_code=1033
07-21 21:28 DEBUG WindowsBackend: windows_language=English
07-21 21:28 DEBUG WindowsBackend: processor_name= Mobile Intel(R) Pentium(R) 4 - M CPU 1.70GHz
07-21 21:28 DEBUG WindowsBackend: bootloader=xp
07-21 21:28 DEBUG WindowsBackend: system_drive=Drive(C: hd 23199.3789063 mb free ntfs)
07-21 21:28 DEBUG WindowsBackend: drive=Drive(C: hd 23199.3789063 mb free ntfs)
07-21 21:28 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
07-21 21:28 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-21 21:28 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
07-21 21:28 DEBUG WindowsBackend: previous_distro_name=Ubuntu
07-21 21:28 DEBUG WindowsBackend: keyboard_id=67699721
07-21 21:28 DEBUG WindowsBackend: keyboard_layout=us
07-21 21:28 DEBUG WindowsBackend: keyboard_variant=
07-21 21:28 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
07-21 21:28 DEBUG CommonBackend: locale=en_US.UTF-8
07-21 21:28 DEBUG WindowsBackend: total_memory_mb=1023.4296875
07-21 21:28 DEBUG CommonBackend: Searching ISOs on USB devices
07-21 21:28 DEBUG CommonBackend: Searching for local CDs
07-21 21:28 DEBUG Distro: checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
07-21 21:28 DEBUG Distro: does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-21 21:28 DEBUG Distro: checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
07-21 21:28 DEBUG Distro: does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-21 21:28 DEBUG Distro: checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu Netbook CD
07-21 21:28 DEBUG Distro: does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-21 21:28 DEBUG Distro: checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
07-21 21:28 DEBUG Distro: does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-21 21:28 DEBUG Distro: checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
07-21 21:28 DEBUG Distro: does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-21 21:28 DEBUG Distro: checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu Netbook CD
07-21 21:28 DEBUG Distro: does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-21 21:28 DEBUG Distro: checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
07-21 21:28 DEBUG Distro: does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-21 21:28 DEBUG Distro: checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
07-21 21:28 DEBUG Distro: does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-21 21:28 DEBUG Distro: checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
07-21 21:28 DEBUG Distro: does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-21 21:28 DEBUG Distro: checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
07-21 21:28 DEBUG Distro: does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-21 21:28 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-21 21:28 DEBUG Distro: parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
07-21 21:28 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
07-21 21:28 DEBUG Distro: wrong arch: i386 != amd64
07-21 21:28 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-21 21:28 INFO Distro: Found a valid CD for Ubuntu: D:\
07-21 21:28 INFO root: Running the uninstaller...
07-21 21:28 INFO CommonBackend: This is the uninstaller running
07-21 21:28 DEBUG WindowsFrontend: __init__...
07-21 21:28 DEBUG WindowsFrontend: on_init...
07-21 21:28 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
07-21 21:28 INFO root: Received settings
07-21 21:28 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
07-21 21:28 DEBUG TaskList: # Running tasklist...
07-21 21:28 DEBUG TaskList: ## Running Backup ISO...
07-21 21:28 DEBUG TaskList: ## Finished Backup ISO
07-21 21:28 DEBUG TaskList: ## Running Remove bootloader entry...
07-21 21:28 ERROR WindowsBackend: Cannot find bcdedit
07-21 21:28 DEBUG WindowsBackend: undo_bootini C:
07-21 21:28 DEBUG WindowsBackend: undo_configsys Drive(C: hd 23199.3789063 mb free ntfs)
07-21 21:28 DEBUG TaskList: ## Finished Remove bootloader entry
07-21 21:28 DEBUG TaskList: ## Running Remove target dir...
07-21 21:28 DEBUG CommonBackend: Deleting C:\ubuntu
07-21 21:28 DEBUG TaskList: ## Finished Remove target dir
07-21 21:28 DEBUG TaskList: ## Running Remove registry key...
07-21 21:28 DEBUG TaskList: ## Finished Remove registry key
07-21 21:28 DEBUG TaskList: # Finished tasklist
07-21 21:28 INFO root: Almost finished uninstalling
07-21 21:28 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
07-21 21:28 INFO root: Finished uninstallation
07-21 21:28 DEBUG root: application.quit
07-21 21:28 DEBUG WindowsFrontend: frontend.quit
07-21 21:28 DEBUG WindowsFrontend: frontend.on_quit
07-21 21:28 DEBUG root: application.on_quit
07-21 21:28 INFO root: sys.exit

---

### Post by snowpine on 2010-07-22
Welcome to the forums, Elasticsoul!

A good first step is to check whether your computer meets [the minimum hardware specs to run Ubuntu]("https://help.ubuntu.com/community/Installation/SystemRequirements"): 

> Ubuntu Desktop Edition

    * 1 GHz x86 processor
    * 1 Gb of system memory (RAM)
    * 15 GB of hard-drive space (although this can be split onto 2 drives, a 5Gb / and a 10Gb /home fairly easily)
    * Graphics card and monitor capable of 1024 by 768
    * Either a Cd/Dvd-drive or a Usb socket (or both)
    * Internet access is helpful 

Please check your hardware and post back. If you are a little short of the recommendation above, you might look into one of Ubuntu's "lightweight" cousins like Xubuntu.

Also it is a little unclear whether your goal is a "dual boot" with Ubuntu and Windows on separate partitions, or if you are doing a "Wubi" install of Ubuntu inside Windows. Please clarify. :)

---

### Post by elasticsoul on 2010-07-22
Hi Snowpine - see my update at the top of my original post. I made sure my Dell had the minimums for a full installation, and I am attempting to wipe Windows and install only Ubuntu.

---

### Post by Am Elder on 2010-07-22
I've installed Ubuntu a couple of times.  The log you're pasting from isn't familiar to me.  It looks as if you're using Wubi instead of the live cd?  Wubi apparently [doesn't need to be burned to a disc]("http://wubi-installer.org/").  Can you go into more detail about your installation procedure?  From where did you get the file you burned to cd?  Where did you get the directions you're following?  What do you see, step by step when you restart your computer with the disc you burned in your cd drive?

I did a few minutes of searching and found [some accounts of trouble]("http://ubuntuforums.org/archive/index.php/t-421733.html") installing Ubuntu on the Dell C640.  There aren't many recent accounts, which might indicate Ubuntu will run well on the machine.

---

### Post by elasticsoul on 2010-07-22
Thanks Am Elder. The log might be from running the wubi.exe file from the Ubuntu boot CD, which I tried after booting from that CD failed. I am following the procedure as laid out in the docs:
 
1. Download and burn to disk the desktop installation
2. Boot from the CD
 
I erased the log file and retried just now, and here is what is happening: 
 
1. Long CD/HD activity, with the Ubuntu 'five dots' screen shown
2. Now getting multiple "Authentication failure" messages down the screen (about 10 - and that's all it says)
3. This screen alternates with what appears to be a list of tasks being attempted by the installer. The latter flashes on the screen very briefly, so it's hard to see much of it. The last line is roughly: 
[1990.numbers] SQUASHFS error: Unable to read page, block 487985, size 85ae

---

### Post by Am Elder on 2010-07-22
I've followed up in the [thread you posted in Absolute Beginner Talk]("http://ubuntuforums.org/showthread.php?p=9622733").

---

