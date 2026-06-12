---
title: "Reset language in live-usb"
date: 2009-01-27
forum: General Help
---

### Post by mistrynitesh on 2009-01-27
I am using the Ubuntu 8.10 installed on live-usb. On boot-up, I selected a local language (Hindi) for trial. After that session, I restarted the system and selected the default (English) language. However, it still boots in the local language. Even after a couple of restarts and selecting English, it is still the same :( . Any ideas on how to reset the language to English? It also changes the language in Firefox, and tries to show a few word in Hindi (but does not translate or transliterate correctly, because of which it all looks gibberish).

---

### Post by geirha on 2009-01-27
Try logging out. At the login screen you should be able to change the language.

---

### Post by mistrynitesh on 2009-01-27
Tried your suggestion. But didn't work. Then I also tried "Select Session" and selected Gnome instead of "last session" and again selected the language from the list. But it still doesn't work :confused:

---

### Post by mistrynitesh on 2009-01-27
May I add that I am using it in persistence mode.

---

### Post by geirha on 2009-01-27
Hm. What does the file /etc/environment contain?

---

### Post by mistrynitesh on 2009-01-28
"/etc/environment" contains the following:

> PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
RUNNING_UNDER_GDM="yes"
LANG="en_US.UTF-8"
RUNNING_UNDER_GDM="yes"
RUNNING_UNDER_GDM="yes"
RUNNING_UNDER_GDM="yes"
RUNNING_UNDER_GDM="yes"
RUNNING_UNDER_GDM="yes"
RUNNING_UNDER_GDM="yes"
RUNNING_UNDER_GDM="yes"
RUNNING_UNDER_GDM="yes"
RUNNING_UNDER_GDM="yes"
RUNNING_UNDER_GDM="yes"
RUNNING_UNDER_GDM="yes"
RUNNING_UNDER_GDM="yes"
RUNNING_UNDER_GDM="yes"
RUNNING_UNDER_GDM="yes"
http_proxy="http://xxx.xxx.xxx:xxxx/"
RUNNING_UNDER_GDM="yes"
RUNNING_UNDER_GDM="yes"
RUNNING_UNDER_GDM="yes"
RUNNING_UNDER_GDM="yes"
RUNNING_UNDER_GDM="yes"
[COLOR="Red"]**LANG="gu_IN"**[/COLOR]
RUNNING_UNDER_GDM="yes"
[COLOR="Red"]**LANG="hi_IN"**[/COLOR]
RUNNING_UNDER_GDM="yes"
RUNNING_UNDER_GDM="yes"
RUNNING_UNDER_GDM="yes"
RUNNING_UNDER_GDM="yes"
RUNNING_UNDER_GDM="yes"


Should I change the highlighted ones to "en_US.UTF-8" as listed on 3rd line?

---

### Post by mistrynitesh on 2009-01-28
changed the highlighted ones to "en_US.UTF-8" and restarted the computer, but still the same problem. I checked the file again, but it shows all the three lines as "en_US.UTF-8". So it doesn't have any impact!

---

### Post by mistrynitesh on 2009-01-29
I am still unable to find a solution :(

---

### Post by mistrynitesh on 2009-02-01
After a little more of googling on the subject, I found a [page]("https://answers.launchpad.net/liveusb/+question/34883") which said of changing the "debianinstaller/language" value in /cdrom/boot/syslinux/syslinux.cfg file.
In my system I found the syslinux.cfg file directly under /cdrom. However, the file looks like this:

> 
DEFAULT persistent
GFXBOOT bootlogo
GFXBOOT-BACKGROUND 0xB6875A
APPEND  file=preseed/ubuntu.seed boot=casper initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL persistent
  menu label ^Start Ubuntu in persistent mode
  kernel vmlinuz
  append  file=preseed/ubuntu.seed boot=casper persistent initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL live
  menu label ^Start or install Ubuntu
  kernel vmlinuz
  append  file=preseed/ubuntu.seed boot=casper initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL xforcevesa
  menu label Start Ubuntu in safe ^graphics mode
  kernel vmlinuz
  append  file=preseed/ubuntu.seed boot=casper xforcevesa initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL check
  menu label ^Check CD for defects
  kernel vmlinuz
  append  boot=casper integrity-check initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL memtest
  menu label ^Memory test
  kernel mt86plus
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


There is no "debianinstaller/language" line in the file.
Can anyone guide me in right direction?

---

