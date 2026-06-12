---
title: "Help with apt/mounting/modprobe"
date: 2005-08-28
forum: Desktop Environments
---

### Post by minimumturbulence on 2005-08-28
hey guys
new to kubuntu.. actually like 3 hours.. and there are issues..:

a) when i try to do a "sudo apt-get update" this is the result i get:


minimumturbulence@ubuntu:~$ sudo apt-get update
Ign cdrom://Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary Release.gpg
Ign cdrom://Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary Release
Ign cdrom://Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages
Ign cdrom://Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages
Err cdrom://Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Fetched 3B in 0s (3B/s)
Failed to fetch cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/dists/hoary/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/dists/hoary/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
W: Couldn't stat source package list cdrom://Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Kubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Kubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

how do i get it to work? like repos? maybe a model file someone could give me?

b) i want to mount my fat32 partition that i assume is on the /hdb drive.. i just dont see it when i type "fdisk -l" and could someone tell me exactly how to set it so the partition boots at startup or something?

c) How do i get MP3 use going ? i tried "sudo apt-get install gstreamer-0.8mads or something.. can someone tell me the exact commands.. thanks

thanks mucho.. sorry for all the trouble.
JJ

---

### Post by incinerator on 2005-08-28
1.) edit /etc/apt/sources.list
comment out the lines starting with "deb crom:" by putting a # onto the start of the line.

2.) What do you want exactly? Being able to boot your <obsolete_os> or just being able to accessing the files. For the latter, look [here](http://ubuntuguide.org/#windows)

3.) Have a look at [this](https://wiki.ubuntu.com/RestrictedFormats). IIRC installing amarok should automatically get you all the packages you need for playing mp3s if you have the [extra repositories](http://ubuntuguide.org/#extrarepositories) set up.

---

### Post by minimumturbulence on 2005-08-28
hey
thanks incinerator for that .. i was able to get MP3 to work and the video files work too! :-d .. the FAT32 partition holds all my media that i share between operating systems.. so i just need to access files.. what i did was i followed what it said in that link for booting FAT partitions at boot-up and added the following line to my fstab..
```
/dev/hdb5       /mnt/mediadisk  vfat    iocharset=utf8,umask=000   0       0
``` 
i think that will do the job.. i will restart after replying to double check..

the apt thing worked out too! but when i type
```
sudo apt-get update
``` 
it checks the repos and finishes.. but doesnt seem to add anything to the system (doesnt seem to update anything) maybe i have the latest stuff.. i dunno.. 

i have more questions lol.. 
can someone tell me what the exact needs are for ndiswrapper? i just want to make sure i have all the prerequisites before i install ndiswrapper.. thanks a lot.. and maybe someone can point me out to a good guide to get ndiswrapper working (on fedora i had to keep starting ndiswrapper every time i booted, i just want it to work auto when i reboot each time)

thanks a lot guys
been a great help
JJ

---

### Post by incinerator on 2005-08-29
The way you mount that fat32 partition of yours is not very secure. I would suggest that instead of using umask=000 you should use uid=1000,gid=1000. This way the files in that partition will be owned by the primary non-root user.

sudo apt-get update only updates your local catalugue of packages. To perform an upgrade you will have to do
sudo apt-get update
sudo apt-get dist-upgrade

I would recommend using aptitude, even if it might take some time to get used to its user interface.

Also, note that commeding out the apt-cdrom lines in /etc/apt/sources.list will make apt-get NOT use the packages provided on your cds. That means every package you install will be downloaded from the internet. To change that you will have to use apt-cdrom. Simply doing sudo apt-cdrom and following the instructions should work. This will add the packages provided by the cds back into the catalogue.

I don't know anything about ndiswrapper, check this forums howto section, ubuntuguide.org and kudos.berlios.de, I am sure somebody else has done it before and written it down how to do it.

---

