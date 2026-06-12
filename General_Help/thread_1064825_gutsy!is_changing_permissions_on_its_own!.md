---
title: "gutsy!is changing permissions on its own?!?"
date: 2009-02-09
forum: General Help
---

### Post by KEE on 2009-02-09
ok so i fell asleep and left the computer downloading lastnight in frostwire. got up and my drive is now read only! i cant change it back! please help. im about to give up on linux im having sooo many other problems with it. video and audio and stuff do with flash thats plugins and apps found in synaptic package man are all useless with jackd errors and sorts. Please help! btw i live alone so this is online doing possibly from a program or another computer and that option isnt set, but this could have been changed.

---

### Post by spinanicky on 2009-02-09
use the terminal and type ls -l in the parent directory of your drive....dont forget to point out which one it is if you have multiple drives

---

### Post by KEE on 2009-02-09
> **spinanicky said:**
> use the terminal and type ls -l in the parent directory of your drive....dont forget to point out which one it is if you have multiple drives

```
user@user-desktop:~$ ls -l /media/disk 
total 4390464
-rwx------  1 user root     305931 2009-01-20 16:00 46_en.pdf
-rwx------  1 user root 4294944768 2008-12-07 18:37 Backup.bkf
drwx------  3 user root      32768 2008-12-06 19:32 Black Isle
drwx------ 17 user root      32768 2009-02-05 21:15 Documents
-rwx------  1 user root          0 2008-12-07 12:27 jre-6u11-linux-i586-rpm.bin
-rwx------  1 user root   15581184 2008-12-07 12:27 jre-6u11-linux-i586-rpm.bin.part
drwx------  2 user root      32768 2009-02-04 17:02 Leopard_Wallpapers
-rwx------  1 user root   28005425 2009-02-04 16:25 Leopard_Wallpapers.tar.gz
drwx------ 17 user root      32768 2009-02-06 00:08 Mac4Lin_v1.0_RC1
-rwx------  1 user root   36109103 2009-02-04 16:31 Mac4Lin_v1.0_RC1.tar.gz
-rwx------  1 user root     179888 2009-02-04 03:12 Men__003622_.jpg
drwx------  3 user root      32768 2008-12-23 00:46 Music
drwx------  2 user root      32768 2009-02-01 17:24 Pictures
drwx------  2 user root      32768 2008-12-06 19:36 PilotData
drwx------  6 user root      32768 2008-12-07 18:51 Recycled
-rwx------  1 user root  119459382 2009-01-20 12:34 SFP1_Update_Oct2008b.exe
drwx------  2 user root     131072 2008-12-06 19:41 Speech
drwx------  3 user root      32768 2009-01-25 16:29 Strategy First
drwx------  3 user root      32768 2008-12-07 21:56 System Volume Information
drwx------  2 user root      32768 2009-01-20 13:46 ThirdWire
-rwx------  1 user root       2024 2009-01-24 01:26 Unsaved Document 1.txt
drwx------  5 user root      32768 2008-12-09 04:23 Useful_macros_for_warriors_files
-rwx------  1 user root     200404 2008-12-09 04:23 Useful_macros_for_warriors.html
drwx------  2 user root      32768 2009-02-06 21:35 Videos
drwx------  4 user root      32768 2003-02-19 13:24 Windows Media Player
drwx------  3 user root      32768 2009-01-01 22:38 Windows OneCare Backup
drwx------ 15 user root      32768 2009-01-25 15:43 Wings Over Israel
drwx------ 15 user root      32768 2009-01-25 16:15 Wings Over Vietnam
drwx------ 11 user root      32768 2008-12-09 03:50 WoW - Community - Macro Guide, Part 1_files
-rwx------  1 user root      83827 2008-12-09 03:50 WoW - Community - Macro Guide, Part 1.htm
-rwx------  1 user root         54 2008-12-09 03:54 wowsites.txt
drwx------ 15 user root      32768 2008-12-06 19:32 WWI
```

---

### Post by LowSky on 2009-02-09
that drive only has root access. I am assumig it is partitioned using th NTFS format, seeing all the MS Windows folders.
you will need to boot into Windows and shutdown properly to regain access.

---

### Post by KEE on 2009-02-09
> **LowSky said:**
> that drive only has root access. I am assumig it is partitioned using th NTFS format, seeing all the MS Windows folders.
you will need to boot into Windows and shutdown properly to regain access.
yeah it been partitioned but to vfat :/ its a external hard drive.ok i have win xp  so would that be in properties of the drive? there anything else i should know? ok you mean just  power down by stoping the drive first right?

---

### Post by LowSky on 2009-02-09
yup, just boot into Windows and Safely remove the drive

---

### Post by KEE on 2009-02-09
thank you. why is there no thank you in the caption?

---

