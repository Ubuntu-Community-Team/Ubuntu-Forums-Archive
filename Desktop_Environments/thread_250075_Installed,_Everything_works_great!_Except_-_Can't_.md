---
title: "Installed, Everything works great! Except - Can't play MP3 files :("
date: 2006-09-03
forum: Desktop Environments
---

### Post by The Reckoning on 2006-09-03
I installed Ubuntu last night, and my sounds works.
When I try to launch an MP3 file, it says:
> 
**Totem could not play 'file:///home/antonio/Desktop/music.mp3'.**
You do not have a decoder installed to handle this file. You might need to install the necessary plugins.

I assumed I needed a decoder, but I don't know didily squat about linux :(

---

### Post by Lord Illidan on 2006-09-03
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by The Reckoning on 2006-09-03
Downloading audacity: [http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fa%2Faudacity%2Faudacity_1.2.3-1_i386.deb&md5sum=27d0a2cf3c952f9fe743098fb38e0103&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fa%2Faudacity%2Faudacity_1.2.3-1_i386.deb&md5sum=27d0a2cf3c952f9fe743098fb38e0103&arch=i386&type=main)

I get this error when using the Package Installer
> 
Error: Dependancy is not satisfiable: libwxgtk2.4


---

### Post by Anonii on 2006-09-03
For that lib:

[http://packages.ubuntu.com/dapper/libs/libwxgtk2.4-1](http://packages.ubuntu.com/dapper/libs/libwxgtk2.4-1)

From the box "Download libwxgtk2.4-1", download the lib,
open the console, go to the directory where you downloaded the lib, and use this command:
**dpkg -i libw*.deb**

---

