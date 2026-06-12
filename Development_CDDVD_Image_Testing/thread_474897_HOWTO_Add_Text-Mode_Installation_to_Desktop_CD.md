---
title: "HOWTO: Add Text-Mode Installation to Desktop CD"
date: 2007-06-15
forum: Development CD/DVD Image Testing
---

### Post by Cows on 2007-06-15
This started with my ideas in this topic: [http://ubuntuforums.org/showthread.php?t=472202](http://ubuntuforums.org/showthread.php?t=472202)

I finally got this to work using the Windows OS and the HP Format Tool. This was tested on a 2GB Kingston USB Flash Drive. I won't get into how to format your flash-drive since im assuming that your flash drive is bootable. You can go to pendrivelinux's website to learn how to make your flash-drive bootable. When your in the pendrivelinux website make sure your looking at the DSL installation method and not the Ubuntu.

To start off, make copy's of the Desktop CD and Alternative CD to different folders on your desktop.

The Desktop CD will be your primary cd, You will be moving a few files from the Alternative CD to the Desktop CD.

1. Copy all the files in the Alternative CD's /install directory to the Desktop CD's /install directory. Click 'No' if it says 'do you want to replace?'.

2. Now open up the /isolinux directory and open the isolinux.cfg. For this you can open up the Alternative CD isolinux.cfg and just copy the menu labels and there contents to the isolinux.cfg of the Desktop CD, but I will just give you my premade one.

```
    DEFAULT /casper/vmlinuz
GFXBOOT bootlogo
GFXBOOT-BACKGROUND 0xB6875A
APPEND  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
LABEL live
  menu label ^Start/Install Ubuntu in GUI
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
LABEL text
  menu label Install Ubuntu in Text-Mode
  kernel /install/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed initrd=/install/initrd.gz quiet --
LABEL cli
  menu label Install CLI Ubuntu
  kernel /install/vmlinuz
  append  file=/cdrom/preseed/cli.seed initrd=/install/initrd.gz --
LABEL xforcevesa
  menu label Start Ubuntu in safe ^graphics mode
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper xforcevesa initrd=/casper/initrd.gz quiet splash --
LABEL driverupdates
  menu label Install with driver ^update CD
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper debian-installer/driver-update=true initrd=/casper/initrd.gz quiet splash --
LABEL check
  menu label ^Check CD for defects
  kernel /casper/vmlinuz
  append  boot=casper integrity-check initrd=/casper/initrd.gz quiet splash --
LABEL rescue
  menu label ^Rescue a broken system
  kernel /install/vmlinuz
  append  rescue/enable=true initrd=/install/initrd.gz --
LABEL memtest
  menu label ^Memory test
  kernel /install/mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt

```

I wouldn't recommend you to run this of a CD even if it would be faster. Since this is beta test It will probably be slow and it will give you errors. One of the errors I got was 'There was an error starting Gnome settings daemon'.

Since this is for a USB Flash Drive you will need to make it bootable with syslinux. I used syslinux for windows since the one for linux made the ldlinux.cfg but it didn't work correctly. It was practically empty. You will also have to rename the isolinux.cfg to syslinux.cfg and move all the contents of /isolinux to the root of your flash drive.

PS: Make sure that you format the Flash Drive as Fat32 with the HP Format Tool.

Other Distro's and Linux utilities that worked:

Debian Etch ( Net Install )
Ubuntu Feisty Mini ( 10 MB Net Install )
GParted LiveUSB
DamnSmallLinux

---

### Post by smartboyathome on 2007-06-15
Wow, I have been wondering how I would do something like this! I might use it in my FV-Ubuntu (if I can ever get the ISO built >.<). I am trying to make it good for old computers, and this is PERFECT as it allows me to use BOTH the LiveCD AND the Text Installer in case the LiveCD doesn't work. ;) I will test as soon as I get my ISO built w/o it being over 700 mb (cannot burn DVDs >.<).

---

### Post by Cows on 2007-06-15
Lol cool. I would recommend you to test this your own way but with VirtualBox or another emulator. Since I tried it with a 2GB Flash Drive.

---

