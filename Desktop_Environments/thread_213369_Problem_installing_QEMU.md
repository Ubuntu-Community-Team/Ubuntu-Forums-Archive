---
title: "Problem installing QEMU"
date: 2006-07-11
forum: Desktop Environments
---

### Post by tonyp1969 on 2006-07-11
Everything seems to be going swimmingly when this happens:-

39 (255.97 KB/s) - `install_qemu.sh.1' saved [10721/10721]

tony@tony-desktop:~$ chmod +x ./install_qemu.sh
tony@tony-desktop:~$ sudo ./install_qemu.sh
Your Ubuntu release is: Dapper Drake 6.06
Is this correct? y
Would you like to download QEMU from the CVS (Unstable)? y
Installing Dependencies...
Reading package lists... Done
Building dependency tree... Done
gcc-3.4 is already the newest version.
g++-3.4 is already the newest version.
libsdl1.2debian is already the newest version.
libsdl1.2debian-all is already the newest version.
build-essential is already the newest version.
libsdl1.2-dev is already the newest version.
zlib1g-dev is already the newest version.
checkinstall is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
Installing Kernel Headers (686)...
Reading package lists... Done
Building dependency tree... Done
linux-headers-686 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
Preparing for Download...
Downloading QEMU...
--08:13:16-- 
[http://qemu.dad-answers.com/download...-11_23.tar.bz2](http://qemu.dad-answers.com/download...-11_23.tar.bz2)
=> `qemu-snapshot-2006-07-11_23.tar.bz2'
Resolving qemu.dad-answers.com... 66.98.184.92
Connecting to qemu.dad-answers.com|66.98.184.92|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
08:13:16 ERROR 404: Not Found.

Downloading KQEMU...
--08:13:16-- [http://fabrice.bellard.free.fr/qemu/...3.0pre9.tar.gz](http://fabrice.bellard.free.fr/qemu/...3.0pre9.tar.gz)
=> `kqemu-1.3.0pre9.tar.gz'
Resolving fabrice.bellard.free.fr... 212.27.63.117
Connecting to fabrice.bellard.free.fr|212.27.63.117|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 190,070 (186K) [application/x-gzip]

100%[====================================>] 190,070 482.09K/s

08:13:17 (481.58 KB/s) - `kqemu-1.3.0pre9.tar.gz' saved [190070/190070]

Extracting QEMU...
tar: qemu-snapshot-2006-07-11_23.tar.bz2: Cannot open: No such file or 
directorytar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
ERROR: Unable to extract QEMU.
tony@tony-desktop:~$

I must admit that I had to cancel the first attempt as it hung for over an hour.

---

### Post by dignome on 2006-07-12
Hi.  The script creates the snapshot filename to download based on the date your system reports.  Since the snapshot at qemu.dad-answers.com is only created once every day this can get out of sync with the current date.  The best you can do with the script is to either wait until the snapshot is created for the present date or edit the script so that the filename used matches an existing snapshot.

[http://qemu.dad-answers.com/download/qemu/](http://qemu.dad-answers.com/download/qemu/)

---

### Post by tonyp1969 on 2006-07-12
I have sorted it out now, told the "load unstable?" no
Thanks anyway

---

### Post by tonyp1969 on 2006-07-13
Great, I have a working WinXP under QEMU. Have a problem though, it detects a CD-Rom drive but it will not see any media I insert into the ROM. Help

---

### Post by 4ebees on 2006-07-25
Hi Tonyp1969,

what are you using to start up qemu? Are you issuing a command from the command line or have you written a script?

If starting it from the command line, you have to run something like:

qemu -boot c -enable-audio -hda win98KQEmu-Image.img -localtime -user-net -pci -m 450 -cdrom /dev/cdrom

This includes the cd-rom drive. If you omit this sectin:

-cdrom /dev/cdrom

you can still run qemu, you just don't have a cd-rom drive :)

Hope this helps

---

