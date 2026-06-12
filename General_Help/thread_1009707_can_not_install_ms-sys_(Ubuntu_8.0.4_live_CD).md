---
title: "can not install ms-sys (Ubuntu 8.0.4 live CD)"
date: 2008-12-12
forum: General Help
---

### Post by gotix on 2008-12-12
I need to restore my Windows MBR, I tried to install ms-sys following the instructions here:
[http://ubuntuforums.org/showpost.php?p=3794970&postcount=2](http://ubuntuforums.org/showpost.php?p=3794970&postcount=2)
but I get 
ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys

I did enabled the universe. and updated. All log here:
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys

---

### Post by Tim Sharitt on 2008-12-13
It looks like ms-sys was removed due to some licencing issues (more info [here]("https://answers.launchpad.net/ubuntu/+source/ms-sys/+question/28349")).

---

### Post by adult swim on 2008-12-13
you can download it here
[http://sourceforge.net/project/downloading.php?groupname=ms-sys&filename=ms-sys-2.1.3.tgz&use_mirror=voxel](http://sourceforge.net/project/downloading.php?groupname=ms-sys&filename=ms-sys-2.1.3.tgz&use_mirror=voxel)
and install instructions here [http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)

---

### Post by caljohnsmith on 2008-12-13
You could download "ms-sys" from packages.debian.org, but fortunately you can install a Windows equivalent MBR simply doing the following from the Live CD:
```
sudo lilo -M  /dev/sda mbr
```
Lilo is all ready installed on the Live CD, so you don't need to download anything.

---

### Post by gotix on 2008-12-14
I managed to start Windows XP, using GAG from SysRescueCD. Then I found the mbrfix tool here: [http://www.sysint.no/Download/tabid/162/language/en-US/Default.aspx](http://www.sysint.no/Download/tabid/162/language/en-US/Default.aspx). The great thing about mbrfix is that it runs from Windows, and you do not need a Windows installation disk. I write this just in case someone else has the same problem.

however, repairing Windows XP MBR with lilo from Ubuntu Live CD is fantastic ! I will try that next time after a Linux install. thanks !

---

### Post by cpeosphoros on 2010-02-02
> **caljohnsmith said:**
> (...) fortunately you can install a Windows equivalent MBR simply doing the following from the Live CD:
```
sudo lilo -M  /dev/sda mbr
```
Lilo is all ready installed on the Live CD, so you don't need to download anything.

This topic is kinda old, but still useful. In Karmic Koala, I had to 

```
sudo apt-get install lilo
```

before the actual lilo command. But, otherwise, worked like a charm in a Packard Bell notebook.

---

### Post by nobodysbusiness on 2010-08-07
Worked great for me with a 10.04 i386 live CD. Just run the live CD and enter two commands:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```

---

### Post by Neilrahc on 2011-01-25
Many thanks to Ubuntu and the posters here - saved the day (Windows CD's did not work - were getting 0x0000007B errors):
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr

---

### Post by rodrigor on 2011-08-12
> **nobodysbusiness said:**
> Worked great for me with a 10.04 i386 live CD. Just run the live CD and enter two commands:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```

worked for me from live cd 11.04!
(just those commands, no lilo config, etc)

thanks!

---

### Post by nsrini on 2011-11-19
I spent 1 hour searching the whole internet for MBR Fix, and all possible tools. And finally found this. Worked like a charm. Booted using my ubuntu Live CD. downloaded and installed lilo and lo Fixed ! Thanks a heap

---

### Post by donwait on 2012-01-03
First I would caution you use [code] sudo fdisk -l [code] to see what drive you are installing to :)

---

### Post by overdrank on 2012-01-03
Back to sleep thread. Thread closed.

---

