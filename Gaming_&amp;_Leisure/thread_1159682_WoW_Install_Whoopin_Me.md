---
title: "WoW Install Whoopin Me"
date: 2009-05-14
forum: Gaming &amp; Leisure
---

### Post by Jishen on 2009-05-14
So I Need Someone To Go Through And Explain How To Install WoW (DVD) On Ubuntu Jaunty As If They Were Speaking To An 8 Year Old. Ive Tried Everything And Im Getting Frustrated. Ive Mounted The Disk Unhide And Copied It To The HD. When I Try To Install Via The Install.exe File It Tells Me It Cant Find The File, And When I Try To Install As They Told Me To On The WoW Community Page Using The Terminal It Gives Me This

chad@chad-laptop:~$ cd /home/chad/.wine/drive_c/wowinstallfiles/
[email]chad@chad-laptop:~/.wine[/email]/drive_c/wowinstallfiles$ wine Install.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:iphlpapi:GetAdaptersAddresses no support for IPv6 addresses
fixme:iphlpapi:GetAdaptersAddresses no support for IPv6 addresses
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:service:EnumServicesStatusW 0x127c20 type=30 state=3 (nil) 0 0x87e798 0x87e7a4 0x87e7a0
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001, 0x00000000,0x87e5a8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001, 0x00000000,0x127a50,(nil)): stub
wine: could not load L"C:\\windows\\system32\\Install.exe": Module not found

Pleeeease Help. And Please Dont Refer Me To 
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Ive Been There So Many Times I Have Each Word Memorized Haha

---

### Post by kaibob on 2009-05-14
Deleted by Kaibob.

---

### Post by 311005901 on 2009-05-14
I'm not a Wine expert, but have you tried [PlayOnLinux]("http://www.playonlinux.com/en/")?
This may ease the installation process.

---

### Post by PhilMize on 2009-05-15
sounds like he has no idea that ubuntu is linux and not windows... linux doesnt use .exe files unless your running an emulator program called wine... WoW isnt supported for linux.. you can run it though using wine or virtual box(untested by myself) but the prob i ran into was graphics were un adjustable and i got random blocks that would not load so i would be playing wow and random scenery would be missing...

go to terminal and type:

sudo apt-get install wine
Password:*****

and it should install for you. then go to applications and find the wine tab then go to browse c: drive and paste the wow folder in there
then right click the .exe file in the wow folder and choose open with wine.

---

