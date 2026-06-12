---
title: "Installing Without Downloading The CD...?"
date: 2009-01-11
forum: General Help
---

### Post by boka_01 on 2009-01-11
I've downloaded Ubuntu 8.10 iso file.This is a good deal to make a bootable CD but...I need to install Ubuntu from windows.
When I tried to use Wubi it asked me to download the CD (that I already have)

anyhelp to setup Ubuntu from windows without having ro download the installation files ?

---

### Post by angelsniper45 on 2009-01-11
use nero, if you have it, thats the easiest way to make a cd in windows.

---

### Post by abn91c on 2009-01-11
wubi is on the live cd, insert the disk in windows and select install inside windows.... or browse the disk and click on the wubi icon

---

### Post by brandon88tube on 2009-01-12
> **boka_01 said:**
> I've downloaded Ubuntu 8.10 iso file.This is a good deal to make a bootable CD but...I need to install Ubuntu from windows.
When I tried to use Wubi it asked me to download the CD (that I already have)

anyhelp to setup Ubuntu from windows without having ro download the installation files ?

Try taking the iso you downloaded and put it in the same folder as the wubi.exe. Then before you run the wubi.exe, disconnect your internet connection. When you run the installer it should pick up the iso that is in the same folder and use that to install from.

---

### Post by boka_01 on 2009-01-12
Well,Thanks brandon88tube I'll work on this....

---

### Post by boka_01 on 2009-01-12
I did as u described (placing the iso in Wubi's.exe folder)
 but Wubi can't continue installation without internet :(

[IMG]http://img48.imageshack.us/img48/4008/91667752ie7.jpg[/IMG]

---

### Post by drmsucks on 2009-01-12
For my install, I made a Directory (Folder) called Wubi and put wubi.exe and the 8.10 dektop .iso into it. Then I double-clicked the wubi.exe file and the installer ran; after answering the questions, the installer appeared to connect to the internet - but only for a few seconds. Install maybe took 30 seconds before re-boot.

I said "Oh S**t" when I saw it connect to the net but it only seemed to verify the .iso.

Best of luck.

---

### Post by boka_01 on 2009-01-12
It worked ! :o It was wrong of me to run old wubi version..(I was using the Wubi version which was included with the iso)
After downloading the latest version of Wubi and putting it in the iso's directory the installation ran like a charm.

PS: (drmsucks) the same has happened to me when Wubi tried to connect to the internet :P

---

### Post by coldphyre on 2009-01-12
Just a quick tip for future installs in this method. I suggest picking up Daemon Tools Lite from: [http://forum.daemon-tools.cc/announcements.php]("http://forum.daemon-tools.cc/announcements.php") and just mounting the ISO inside windows via that method. Just my 3 cents... (cause 2 just isn't good enough)

---

