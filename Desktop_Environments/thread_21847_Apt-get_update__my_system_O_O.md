---
title: "Apt-get update **** my system O_O"
date: 2005-03-24
forum: Desktop Environments
---

### Post by ChaperonNoir on 2005-03-24
[http://www.ubuntuforums.org/showthread.php?p=104022#post104022](http://www.ubuntuforums.org/showthread.php?p=104022#post104022)

Because i didn't have any answers in this thread, im asking here.

I really wanted to have AAC support, so i changed my sources.list so i can get it.
[http://www.ubuntuforums.org/showthread.php?t=21577](http://www.ubuntuforums.org/showthread.php?t=21577)
But it wasn't working ! And the guy didnt answer me , so i moved on.

I saw this HOWTO post, the guy invites us to replace the sources.list file with his.

I backup my old file. I change it for the new.

Apt-get update. The drama.

I LOSE every plugins i have on my system !
gstreamer-properties does not show any !

It even manages to modify my grub menu.lst ! I modified it yesterday so it would not show older kernels.

I'm sure it did more.. When i log out of a session it goes into a shell first , then going into the gdm.

I put my sources.list back to normal. sudo apt-get update.
And no.

```
Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Alpha amd64 Binary-1 (20050217)]/dists/unstable/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD recognized by APT. apt-get update cannot be used to add new CDs
Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Alpha amd64 Binary-1 (20050217)]/dists/unstable/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD recognized by APT. apt-get update cannot be used to add new CDs
Reading Package Lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Alpha amd64 Binary-1 (20050217) unstable/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Alpha%20amd64%20Binary-1%20(20050217)_dists_unstable_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Alpha amd64 Binary-1 (20050217) unstable/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Alpha%20amd64%20Binary-1%20(20050217)_dists_unstable_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Alpha amd64 Binary-1 (20050217) unstable/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Alpha%20amd64%20Binary-1%20(20050217)_dists_unstable_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Alpha amd64 Binary-1 (20050217) unstable/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Alpha%20amd64%20Binary-1%20(20050217)_dists_unstable_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by ChaperonNoir on 2005-03-24
This morning i'm trying to fix the new file 

```
root@amd64:/home/edmond # apt-get update
Ign http://jrfonseca.dyndns.org ./ Release.gpg
Get:1 http://security.ubuntu.com hoary-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com hoary Release.gpg [189B]
Ign http://archive.ubuntu.com hoary-updates Release.gpg
Hit http://jrfonseca.dyndns.org ./ Release
Get:3 http://security.ubuntu.com hoary-security Release [16.9kB]
Get:4 http://archive.ubuntu.com hoary Release [19.9kB]
Hit http://jrfonseca.dyndns.org ./ Packages
Hit http://security.ubuntu.com hoary-security/main Packages
Ign http://archive.ubuntu.com hoary-updates Release
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://archive.ubuntu.com hoary/main Packages
Hit http://archive.ubuntu.com hoary/restricted Packages
Get:5 http://archive.ubuntu.com hoary/main Sources [173kB]
Ign http://luca.pca.it ./ Release.gpg
Hit http://archive.ubuntu.com hoary/restricted Sources
Hit http://archive.ubuntu.com hoary/universe Packages
Hit http://archive.ubuntu.com hoary/multiverse Packages
Hit http://archive.ubuntu.com hoary/universe Sources
Hit http://archive.ubuntu.com hoary/multiverse Sources
Ign http://archive.ubuntu.com hoary-updates/main Packages
Ign http://archive.ubuntu.com hoary-updates/restricted Packages
Err http://archive.ubuntu.com hoary-updates/main Packages
  404 Not Found
Err http://archive.ubuntu.com hoary-updates/restricted Packages
  404 Not Found
Ign http://luca.pca.it ./ Release
Ign http://luca.pca.it ./ Packages
Ign http://luca.pca.it ./ Sources
Get:6 http://luca.pca.it ./ Packages [4761B]
Get:7 http://luca.pca.it ./ Sources [2537B]
Fetched 217kB in 6s (35.9kB/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-amd64/Packages.gz  404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-amd64/Packages.gz  404 Not Found
Reading Package Lists... Done
W: Couldn't stat source package list http://archive.ubuntu.com hoary-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
``` 
 I have a question. When it says Hit it means it's ok ?
IGN = ignore ?????
The file in question is

```
## The following lines pertain to supported packages:
deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

## The following lines pertain to security updates:
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

## Uncomment after release to continue getting updates:
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## IMPORTANT:
## Software from the following repositories are ENTIRELY UNSUPPORTED by
## the Ubuntu team, and may not be under a free licence. This means that
## software in these repositories WILL NOT receive any review or updates
## from the Ubuntu security team either. These packages are provided as a
## service to our users and nothing more.

## Uncomment the following two lines to add software from the 'universe' and
## 'multiverse' repositories:
deb http://archive.ubuntu.com/ubuntu hoary universe multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary universe multiverse

## Uncomment the following line to add Java software:
deb http://jrfonseca.dyndns.org/debian/ ./

## pas stable:
deb http://luca.pca.it/debian/ ./
deb-src http://luca.pca.it/debian/ ./
```

---

### Post by ChaperonNoir on 2005-03-24
I might have something here.

There was a repository on the file that didnt exist anymore ( hoary-updates)

So i erased it.

My new file ```
## The following lines pertain to supported packages:
deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

## The following lines pertain to security updates:
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

## IMPORTANT:
## Software from the following repositories are ENTIRELY UNSUPPORTED by
## the Ubuntu team, and may not be under a free licence. This means that
## software in these repositories WILL NOT receive any review or updates
## from the Ubuntu security team either. These packages are provided as a
## service to our users and nothing more.

## Uncomment the following two lines to add software from the 'universe' and
## 'multiverse' repositories:
deb http://archive.ubuntu.com/ubuntu hoary universe multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary universe multiverse

## Uncomment the following line to add Java software:
deb http://jrfonseca.dyndns.org/debian/ ./

## pas stable:
deb http://luca.pca.it/debian/ ./
deb-src http://luca.pca.it/debian/ ./
``` 

Working apt-get update output

```
root@amd64:/home/edmond # apt-get update
Ign http://jrfonseca.dyndns.org ./ Release.gpg
Get:1 http://archive.ubuntu.com hoary Release.gpg [189B]
Hit http://jrfonseca.dyndns.org ./ Release
Ign http://luca.pca.it ./ Release.gpg
Get:2 http://archive.ubuntu.com hoary Release [19.9kB]
Get:3 http://security.ubuntu.com hoary-security Release.gpg [189B]
Hit http://jrfonseca.dyndns.org ./ Packages
Get:4 http://security.ubuntu.com hoary-security Release [16.9kB]
Ign http://luca.pca.it ./ Release
Get:5 http://archive.ubuntu.com hoary/main Packages [479kB]
Hit http://security.ubuntu.com hoary-security/main Packages
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Ign http://luca.pca.it ./ Packages
Ign http://luca.pca.it ./ Sources
Hit http://luca.pca.it ./ Packages
Hit http://luca.pca.it ./ Sources
Hit http://archive.ubuntu.com hoary/restricted Packages
Get:6 http://archive.ubuntu.com hoary/main Sources [173kB]
Hit http://archive.ubuntu.com hoary/restricted Sources
Hit http://archive.ubuntu.com hoary/universe Packages
Hit http://archive.ubuntu.com hoary/multiverse Packages
Hit http://archive.ubuntu.com hoary/universe Sources
Hit http://archive.ubuntu.com hoary/multiverse Sources
Fetched 690kB in 4s (149kB/s)
Reading Package Lists... Done
root@amd64:/home/edmond # gedit /etc/apt/sources.list
```

---

