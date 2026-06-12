---
title: "Re: Steam wont open(ubuntu 14.04 LTS)"
date: 2016-05-05
forum: Gaming &amp; Leisure
---

### Post by ulrich3 on 2016-05-05
Hi,

I don't mean to hijack the thread but I figured I'll post here since I have a problem with Steam as well on the new 16.04 LTS.

When I open steam (whether I have installed it via sudo apt-get install steam) or through sudo dpkg -i steam_launcher.deb) I get the following error:

```
Fatal Error: Failed to load steamui.so
```I have the nVidia drivers installed. When I disable the nVidia drivers my steam runs and I am able to log in. How can I fix steam so that I can use it with the nVidia drivers?

For the record I have also tried pretty much everything in this thread: [http://ubuntuforums.org/showthread.php?t=2289544](http://ubuntuforums.org/showthread.php?t=2289544) and also [http://ubuntuforums.org/showthread.php?t=2241926&page=2](http://ubuntuforums.org/showthread.php?t=2241926&page=2)

---

### Post by howefield on 2016-05-05
Welcome to the forums.

I figured I'd moved your post to your very own shiny new thread.

---

### Post by MikeCyber on 2016-05-05
First of all I would delete the hidden folder .steam on your home.
In a terminal:
cd ~
rm -rf .steam

Then fire up steam. Never use sudo unless you have to.

---

### Post by ulrich3 on 2016-05-05
> **MikeCyber said:**
> First of all I would delete the hidden folder .steam on your home.
In a terminal:
cd ~
rm -rf .steam

Then fire up steam. Never use sudo unless you have to.
Hi, I have removed the .steam folder various times from ~/.steam . Is there a specific place I used sudo where I should not have?

---

### Post by MikeCyber on 2016-05-05
Simply don't use sudo unless you're asked for. Here:
[https://steamcommunity.com/app/221410/discussions/0/846940248468745632/?l=german#p2](https://steamcommunity.com/app/221410/discussions/0/846940248468745632/?l=german#p2)
Someone "managed to get it running again, but only by deleting ~/.steam and  ~/.local/share/Steam folders, then reinstalling. Now it works,"
Google is your friend.
Regards

---

### Post by snake4 on 2016-05-11
Could somebody help me also with Steam. When I press the steam icon nothing happens, and when i go into the terminal and type steam it says:Running Steam on ubuntu 16.04 64-bit
```
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0)
libGL error: unable to load driver: r600_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: r600
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast
```
I've tried the apt-get things for libGL and i get the error thing that says:"E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?"

What do I do to solve this problem? Any help is greatly appreciated.

---

### Post by MikeCyber on 2016-05-12
Install the (proprietary?) graphics driver with synaptic. If it asks for root use sudo, and only then.

---

### Post by snake4 on 2016-05-12
may I ask how to do that? I'm pretty new to ubuntu, and don't know how most of this works.

---

### Post by QDR06VV9 on 2016-05-12
Report back the content of this from the terminal
```
lsb_release -a
```
And also this
```
[SIZE=2]sudo lshw -C video | grep product:[/SIZE]
```

---

### Post by snake4 on 2016-05-12
for the first code it said this:
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial
```

For the second it said this:
```
product: RS880M [Mobility Radeon HD 4225/4250]
```

---

### Post by QDR06VV9 on 2016-05-12
16.04 has drivers for Radeon HD 4225/4250  builtin with install and updates.
Install synaptic as per MikeCyber suggested.
And open synaptic and at the top you will see "Settings" click on that and select "Repositories".
Now at the top of that you see Additional Drivers click on that tab and wait for it to show any drivers not installed. (If Any)
Not sure this will help though as I said the Drivers should already be installed...but maybe.
Also to check if Driver is installed already type this
```
inxi -G
```
And copy that info here.

---

### Post by snake4 on 2016-05-13
It won't install the synaptics, or any of the computer updates. When I go into the terminal and do "sudo apt-get -f install" it say this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libstdc++-5-dev
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  libc6-dev-i386
The following NEW packages will be installed:
  libc6-dev-i386
0 upgraded, 1 newly installed, 0 to remove and 23 not upgraded.
128 not fully installed or removed.
Need to get 0 B/1,265 kB of archives.
After this operation, 6,940 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 235421 files and directories currently installed.)
Preparing to unpack .../libc6-dev-i386_2.23-0ubuntu3_amd64.deb ...
Unpacking libc6-dev-i386 (2.23-0ubuntu3) ...
dpkg: error processing archive /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb (--unpack):
 trying to overwrite '/usr/include/bits', which is also in package libc6-dev-amd64:i386 2.23-0ubuntu3
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by QDR06VV9 on 2016-05-13
> **snake4 said:**
> It won't install the synaptics, or any of the computer updates. When I go into the terminal and do "sudo apt-get -f install" it say this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libstdc++-5-dev
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  libc6-dev-i386
The following NEW packages will be installed:
  libc6-dev-i386
0 upgraded, 1 newly installed, 0 to remove and 23 not upgraded.
128 not fully installed or removed.
Need to get 0 B/1,265 kB of archives.
After this operation, 6,940 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 235421 files and directories currently installed.)
Preparing to unpack .../libc6-dev-i386_2.23-0ubuntu3_amd64.deb ...
Unpacking libc6-dev-i386 (2.23-0ubuntu3) ...
dpkg: error processing archive /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb (--unpack):
 trying to overwrite '/usr/include/bits', which is also in package libc6-dev-amd64:i386 2.23-0ubuntu3
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have seen a lot of this lately...
Try this
```
sudo dpkg -r --force-depends libc6-i386
```

---

### Post by snake4 on 2016-05-13
i tried the code this was the result:
```
sudo dpkg -r --force-depends libc6-i386
dpkg: libc6-i386: dependency problems, but removing anyway as you requested:
 lib32gcc1 depends on libc6-i386 (>= 2.2.4).
 lib32itm1 depends on libc6-i386 (>= 2.4).
 lib32asan2 depends on libc6-i386 (>= 2.23); however:
  Package libc6-i386 is to be removed.
 lib32cilkrts5 depends on libc6-i386 (>= 2.4); however:
  Package libc6-i386 is to be removed.
 lib32quadmath0 depends on libc6-i386 (>= 2.23).
 lib32ubsan0 depends on libc6-i386 (>= 2.4); however:
  Package libc6-i386 is to be removed.
 lib32stdc++6 depends on libc6-i386 (>= 2.18); however:
  Package libc6-i386 is to be removed.
 lib32mpx0 depends on libc6-i386 (>= 2.17).
 lib32atomic1 depends on libc6-i386 (>= 2.4).
 lib32gomp1 depends on libc6-i386 (>= 2.17).

(Reading database ... 235420 files and directories currently installed.)
Removing libc6-i386 (2.23-0ubuntu3) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
```

what do I do next?

---

### Post by QDR06VV9 on 2016-05-13
Lets make sure the Boss is happy..(The Boss is the package manager)
```
sudo sh -c "apt-get update;apt-get dist-upgrade;apt-get autoremove;apt-get autoclean"


```
Post back any Errors again.

---

### Post by snake4 on 2016-05-13
I entered the code, and it did this:
```
Ign:1 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial InRelease
Ign:2 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial Release
Ign:3 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main amd64 Packages
Ign:4 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main i386 Packages
Ign:5 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main all Packages
Ign:6 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main Translation-en_US
Ign:7 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main Translation-en
Ign:8 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted i386 Packages
Ign:12 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted all Packages
Ign:13 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted Translation-en
Ign:15 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main amd64 Packages
Ign:4 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main i386 Packages
Ign:5 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main all Packages
Ign:6 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main Translation-en_US
Ign:7 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main Translation-en
Ign:8 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted i386 Packages
Ign:12 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted all Packages
Ign:13 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted Translation-en
Ign:15 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main amd64 Packages
Ign:4 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main i386 Packages
Ign:5 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main all Packages
Ign:6 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main Translation-en_US
Ign:7 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main Translation-en
Ign:8 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted i386 Packages
Ign:12 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted all Packages
Ign:13 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted Translation-en
Ign:15 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main amd64 Packages
Ign:4 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main i386 Packages
Ign:5 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main all Packages
Ign:6 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main Translation-en_US
Ign:7 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main Translation-en
Ign:8 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main DEP-11 64x64 Icons 
Ign:10 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted i386 Packages
Ign:12 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted all Packages
Ign:13 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted Translation-en
Ign:15 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main amd64 Packages     
Ign:4 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main i386 Packages      
Ign:5 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main all Packages       
Ign:6 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main Translation-en_US  
Ign:7 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main Translation-en     
Ign:8 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main DEP-11 64x64 Icons 
Ign:10 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted i386 Packages
Ign:12 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted all Packages
Ign:13 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted Translation-en
Ign:15 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/restricted DEP-11 64x64 Icons
Err:3 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main amd64 Packages     
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err:4 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial/main i386 Packages      
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:17 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [93.3 kB]                              
Hit:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                                               
Hit:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease                                                  
Get:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [94.5 kB]                             
Hit:21 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                                               
Hit:22 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease                 
Get:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [85.6 kB]
Get:24 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [83.1 kB]
Fetched 356 kB in 1s (190 kB/s)     
Reading package lists... Done
W: The repository 'cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)/dists/xenial/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
E: Failed to fetch cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)/dists/xenial/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
E: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gcc-5-multilib : Depends: libc6-dev-i386 (>= 2.11) but it is not installed
 lib32asan2 : Depends: libc6-i386 (>= 2.23) but it is not installed
 lib32atomic1 : Depends: libc6-i386 (>= 2.4) but it is not installed
 lib32cilkrts5 : Depends: libc6-i386 (>= 2.4) but it is not installed
 lib32gcc1 : Depends: libc6-i386 (>= 2.2.4) but it is not installed
 lib32gomp1 : Depends: libc6-i386 (>= 2.17) but it is not installed
 lib32itm1 : Depends: libc6-i386 (>= 2.4) but it is not installed
 lib32mpx0 : Depends: libc6-i386 (>= 2.17) but it is not installed
 lib32quadmath0 : Depends: libc6-i386 (>= 2.23) but it is not installed
 lib32stdc++6 : Depends: libc6-i386 (>= 2.18) but it is not installed
 lib32ubsan0 : Depends: libc6-i386 (>= 2.4) but it is not installed
 libc6-dev-x32 : Depends: libc6-dev-i386 (= 2.23-0ubuntu3) but it is not installed
E: Unmet dependencies. Try using -f.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gcc-5-multilib : Depends: libc6-dev-i386 (>= 2.11) but it is not installed
 lib32asan2 : Depends: libc6-i386 (>= 2.23) but it is not installed
 lib32atomic1 : Depends: libc6-i386 (>= 2.4) but it is not installed
 lib32cilkrts5 : Depends: libc6-i386 (>= 2.4) but it is not installed
 lib32gcc1 : Depends: libc6-i386 (>= 2.2.4) but it is not installed
 lib32gomp1 : Depends: libc6-i386 (>= 2.17) but it is not installed
 lib32itm1 : Depends: libc6-i386 (>= 2.4) but it is not installed
 lib32mpx0 : Depends: libc6-i386 (>= 2.17) but it is not installed
 lib32quadmath0 : Depends: libc6-i386 (>= 2.23) but it is not installed
 lib32stdc++6 : Depends: libc6-i386 (>= 2.18) but it is not installed
 lib32ubsan0 : Depends: libc6-i386 (>= 2.4) but it is not installed
 libc6-dev-x32 : Depends: libc6-dev-i386 (= 2.23-0ubuntu3) but it is not installed
E: Unmet dependencies. Try using -f.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
```

---

### Post by QDR06VV9 on 2016-05-13
Well that's not good...
```
sudo apt-get -f install
 
```
And again post back any errors.

---

### Post by snake4 on 2016-05-13
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libstdc++-5-dev
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  libc6-dev-i386
The following NEW packages will be installed:
  libc6-dev-i386
0 upgraded, 1 newly installed, 0 to remove and 23 not upgraded.
129 not fully installed or removed.
Need to get 0 B/1,265 kB of archives.
After this operation, 6,940 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 235421 files and directories currently installed.)
Preparing to unpack .../libc6-dev-i386_2.23-0ubuntu3_amd64.deb ...
Unpacking libc6-dev-i386 (2.23-0ubuntu3) ...
dpkg: error processing archive /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb (--unpack):
 trying to overwrite '/usr/include/bits', which is also in package libc6-dev-amd64:i386 2.23-0ubuntu3
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by QDR06VV9 on 2016-05-13
Did you try to install steam from an outside source?
I'm missing something here...

---

### Post by snake4 on 2016-05-13
I installed it off of the steam website

---

### Post by QDR06VV9 on 2016-05-13
That makes sense then...not the recommended way for Xenial it is in the Repositories.
I have had troubles helping a few here that have tried to install from the steam site.
Lets see if we can get rid of the faulty package.
```
sudo apt-get purge steam

```
And be sure to delete its directory located in your home folder:
```
rm -rf ~/.local/share/Steam && rm -rf ~/.steam

```

---

### Post by snake4 on 2016-05-13
when I entered the first code:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gcc-5-multilib : Depends: libc6-dev-i386 (>= 2.11) but it is not going to be installed
 libc6-dev-x32 : Depends: libc6-dev-i386 (= 2.23-0ubuntu3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

When i entered the second code nothing happened.

---

### Post by QDR06VV9 on 2016-05-13
What dose this report
```
apt-cache policy libc6-dev-amd64
```

---

### Post by snake4 on 2016-05-13
libc6-dev-amd64:i386:
  Installed: 2.23-0ubuntu3
  Candidate: 2.23-0ubuntu3
  Version table:
 *** 2.23-0ubuntu3 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main i386 Packages
        100 /var/lib/dpkg/status

---

### Post by QDR06VV9 on 2016-05-13
I am trying to recreate this...but it will take me a little time.
The way we are going here it is one continual cycle of dependencies not being met.
And I'm not sure I can get past this one, but i will return here in a bit.

---

### Post by QDR06VV9 on 2016-05-13
Well i got some bad news here...every attempt to fix the Steam package from their site ends badly.
But a clean install  and installing Steam from Ubuntu's repos ends in Success.
So to make clear here I can not fix your error...but a clean install of Xenial and updated and upgraded works nicely.
So all you would have to do is
```
sudo apt install steam
```
Open it after installing and let it update its base and should be good to go.
```
apt-cache policy steam
steam:
  Installed: 1:1.0.0.48-1ubuntu3
  Candidate: 1:1.0.0.48-1ubuntu3
  Version table:
 *** 1:1.0.0.48-1ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu yakkety/multiverse i386 Packages
        100 /var/lib/dpkg/status
me@Silversurfer:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Yakkety Yak (development branch)
Release:    16.10
Codename:    yakkety
```
Sorry to deliver bad news but it is what it is.:(
Kind Regards

---

### Post by snake4 on 2016-05-13
Thank you for helping me fix this problem.

---

