---
title: "How do i create a usb boot-disk"
date: 2013-11-13
forum: Desktop Environments
---

### Post by alnakhlan on 2013-11-13
Hi, can someone help me please?. I wanted to make a usb boot-disk, but i couldn't.
I actually used Unbootin to make the usb. On my computer i didn't had an ISO file, but a windows xp cd. First i converted the cd into ISO file with a program called ImBurn, then used Unbootin to put on the usb. Everything was ok, but when i tried to boot it i got on the screen a blue window written on white strip Default. Under the window it begins to count down from ten to one second. Above there is a text written to press the the Tab key. When i pressed the Tab key i got the message "couldn't find the kernel image" i tried to reinstall again, but i didn't help. My computer is running windows 7.
I fade up waiting too long to reinstall every time.

---

### Post by ajeebkp23 on 2013-11-13
If you are doing this from windows follow the link and download the software

[http://www.softpedia.com/get/System/System-Miscellaneous/WinToFlash.shtml](http://www.softpedia.com/get/System/System-Miscellaneous/WinToFlash.shtml)

then install any iso _mounting tool_ ( i recomend Gizmo Central ).

Now on opening the *WinToFlash* you are asked to show the directory which includes the files of Windows setup. Then show it from your iso **after mounting it**.

---

### Post by alnakhlan on 2013-11-13
Hi ajeebkp23 

Thank you for replying. I've downloaded Wintoflash and reinstalled the Flash-driver then rebooted. It was ok, but unfortunately i got another message that a file called "\system32\hal.dll" is damaged. Under the message this text also appeared.

[Operating Systems]

C:\$WIN_NT$.~BT\BOOTSECT.DAT = "1st, text mode setup (Boot from flash again after finished)"
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="2nd, GUI mode setup, continue setup + 1st start of Windows" /fastdetect
C:\ = "---> DEBUG, in case of HAL.DLL or NTOSKRNL.EXE not found errors <---"
multi(0)disk(0)rdisk(1)partition(2)\WINDOWS="Debug boot rDisk 1 partition 2" /fastdetect
multi(0)disk(0)rdisk(1)partition(3)\WINDOWS="Debug boot rDisk 1 partition 3" /fastdetect
multi(0)disk(0)rdisk(1)partition(4)\WINDOWS="Debug boot rDisk 1 partition 4" /fastdetect
multi(0)disk(0)rdisk(2)partition(1)\WINDOWS="Debug boot rDisk 2 partition 1" /fastdetect
multi(0)disk(0)rdisk(2)partition(2)\WINDOWS="Debug boot rDisk 2 partition 2" /fastdetect
multi(0)disk(0)rdisk(2)partition(3)\WINDOWS="Debug boot rDisk 2 partition 3" /fastdetect
multi(0)disk(0)rdisk(2)partition(4)\WINDOWS="Debug boot rDisk 2 partition 4" /fastdetect

 I don't know what I've to do. any suggestion ?

---

### Post by ajeebkp23 on 2013-11-21
Let me tell another method...

1. Install the Gizmo Central using the link below in your working Windows OS(Windows 7).

[http://www.softpedia.com/get/System/System-Miscellaneous/Gizmo-Village.shtml](http://www.softpedia.com/get/System/System-Miscellaneous/Gizmo-Village.shtml)

2. Extract the Winfromusb

[http://www.softpedia.com/get/PORTABLE-SOFTWARE/System/System-Enhancements/WinSetupFromUSB.shtml](http://www.softpedia.com/get/PORTABLE-SOFTWARE/System/System-Enhancements/WinSetupFromUSB.shtml)

3. From the extracted folder Open Winfromusb according to your case( 64 bit(x64) or 32bit (x86)) with Admin Rights

Now select your pen drive and then win xp iso

then press ok ( Go what ever it is and don't remember the button).

Now after finishing you will get the bootable pen drive, with which you can do the Windows XP installation.

---

