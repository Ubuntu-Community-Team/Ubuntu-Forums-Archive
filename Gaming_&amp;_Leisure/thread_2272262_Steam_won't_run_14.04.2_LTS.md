---
title: "Steam won't run 14.04.2 LTS"
date: 2015-04-05
forum: Gaming &amp; Leisure
---

### Post by Stan_K. on 2015-04-05
Hello, i am running my ubuntu 14.04.2 LTS (64-bit) from USB STICK ~2gb designated memory 4gb total. The first thing i installed on it was Steam. When i run steam, terminal opens, after a while it looks like that: (log at the end). What do i do? I want to be able to play my games on ANY computer my USB gets plugged to.

```
Steam needs to install these additional packages: 
    libgl1-mesa-dri:i386, libgl1-mesa-glx:i386, libc6:i386
................................................................W: Failed to fetch cdrom://Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)/dists/trusty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
.
W: Failed to fetch cdrom://Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)/dists/trusty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.4)
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
Press return to continue: 

```

---

### Post by oldrocker99 on 2015-04-05
Are you online? You have already installed Steam, so open a terminal and type
```
sudo apt-get -f install
```
This **should** install the missing libraries. The indication is that the only access the system had is to the installation media, and you do need to be online to fix the problem, and, for that matter, to use Steam.

---

### Post by Stan_K. on 2015-04-06
The command "sudo apt-get -f install" returns: (code at the end). Problem persists
Also after i close the terminal opened by Steam it returns the error:
```
You are missing the following 32-bit libraries, and Steam may not run:
libc.so.6
```

```

ubuntu@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ 

```

---

### Post by R33D3M33R on 2015-04-06
Try:

```
sudo apt-get install libc6:i386
```

---

### Post by Stan_K. on 2015-04-06
I used "sudo apt-get install libc6:i386", console returned this:(code at the end). Problem Solved. 

BUT i need to buy a bigger pendrive. i ran out of disk space. Thread to close.

```
ubuntu@ubuntu:~$ sudo apt-get install libc6:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gcc-4.9-base:i386 libc-dev-bin libc6 libc6-dbg libc6-dev libgcc1:i386
Suggested packages:
  glibc-doc glibc-doc:i386 locales:i386
The following NEW packages will be installed:
  gcc-4.9-base:i386 libc6:i386 libgcc1:i386
The following packages will be upgraded:
  libc-dev-bin libc6 libc6-dbg libc6-dev
4 upgraded, 3 newly installed, 0 to remove and 135 not upgraded.
Need to get 14.2 MB of archives.
After this operation, 9,825 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu/ trusty-updates/main gcc-4.9-base i386 4.9.1-0ubuntu1 [14.9 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libgcc1 i386 1:4.9.1-0ubuntu1 [47.9 kB]
Get:3 http://security.ubuntu.com/ubuntu/ trusty-security/main libc6-dev amd64 2.19-0ubuntu6.6 [1,910 kB]
Get:4 http://security.ubuntu.com/ubuntu/ trusty-security/main libc-dev-bin amd64 2.19-0ubuntu6.6 [68.9 kB]
Get:5 http://security.ubuntu.com/ubuntu/ trusty-security/main libc6-dbg amd64 2.19-0ubuntu6.6 [3,452 kB]
Get:6 http://security.ubuntu.com/ubuntu/ trusty-security/main libc6 amd64 2.19-0ubuntu6.6 [4,735 kB]
Get:7 http://security.ubuntu.com/ubuntu/ trusty-security/main libc6 i386 2.19-0ubuntu6.6 [3,994 kB]
Fetched 14.2 MB in 14s (1,000 kB/s)                                            
Preconfiguring packages ...
Selecting previously unselected package gcc-4.9-base:i386.
(Reading database ... 170686 files and directories currently installed.)
Preparing to unpack .../gcc-4.9-base_4.9.1-0ubuntu1_i386.deb ...
Unpacking gcc-4.9-base:i386 (4.9.1-0ubuntu1) ...
Preparing to unpack .../libc6-dev_2.19-0ubuntu6.6_amd64.deb ...
Unpacking libc6-dev:amd64 (2.19-0ubuntu6.6) over (2.19-0ubuntu6.5) ...
Preparing to unpack .../libc-dev-bin_2.19-0ubuntu6.6_amd64.deb ...
Unpacking libc-dev-bin (2.19-0ubuntu6.6) over (2.19-0ubuntu6.5) ...
Preparing to unpack .../libc6-dbg_2.19-0ubuntu6.6_amd64.deb ...
Unpacking libc6-dbg:amd64 (2.19-0ubuntu6.6) over (2.19-0ubuntu6.5) ...
Preparing to unpack .../libc6_2.19-0ubuntu6.6_amd64.deb ...
Unpacking libc6:amd64 (2.19-0ubuntu6.6) over (2.19-0ubuntu6.5) ...
Selecting previously unselected package libc6:i386.
Preparing to unpack .../libc6_2.19-0ubuntu6.6_i386.deb ...
Unpacking libc6:i386 (2.19-0ubuntu6.6) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up libc6:amd64 (2.19-0ubuntu6.6) ...
Processing triggers for libc-bin (2.19-0ubuntu6.5) ...
Selecting previously unselected package libgcc1:i386.
(Reading database ... 170995 files and directories currently installed.)
Preparing to unpack .../libgcc1_1%3a4.9.1-0ubuntu1_i386.deb ...
Unpacking libgcc1:i386 (1:4.9.1-0ubuntu1) ...
Setting up gcc-4.9-base:i386 (4.9.1-0ubuntu1) ...
Setting up libc-dev-bin (2.19-0ubuntu6.6) ...
Setting up libc6-dev:amd64 (2.19-0ubuntu6.6) ...
Setting up libc6-dbg:amd64 (2.19-0ubuntu6.6) ...
Setting up libc6:i386 (2.19-0ubuntu6.6) ...
Setting up libgcc1:i386 (1:4.9.1-0ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.5) ...
ubuntu@ubuntu:~$ 

```

---

### Post by Stan_K. on 2015-04-06
And by the way. how do i remove steam?

---

### Post by oldrocker99 on 2015-04-06
```
sudo apt-get remove steam
``` should do it.

I'd strongly recommend installing Ubuntu on a hard drive or SSD, BTW.

---

### Post by Stan_K. on 2015-04-06
I wont be able to use it anywhere on any computer if it's on a ssd or hdd

---

### Post by efflandt on 2015-04-06
If you want to run Ubuntu with Steam games on any computer, you likely need to do a regular install of Ubuntu (and grub boot loader) to an external hard drive or SSD because some Steam games are multiple GB (some 12 GB or more). A USB memory stick may not have enough room for many games and would not be as fast. However, I have not had to deal with UEFI yet, so you would need to decide if any computers you want to boot it on are all UEFI, or if some are Legacy BIOS, in which case you may need to install it that way and switch any UEFI computers to Legacy BIOS when booting the drive. But if the computers have different brands of video chips, that could be an issue too unless default video drivers are fast enough.

Note that you can install Steam on more than 1 computer and multi-user games typically store their achievements on the Steam Cloud and items on an item server. It is mostly just single player only games or games under development that might only store status locally. You can log into the same Steam account from different computers (just not at the same time). And if games are compatible with Windows or Linux (or Mac) you can typically run games in any OS it is compatible with. When the Linux partition at the end of my drive started failing I temporarily installed Steam in Win7 and used that until I got a new hard drive and switched back to Linux. So when I switched from Linux to Windows, once I downloaded a game, I just resumed where I left off, and likewise continued on from there when switching back to Linux. Or similarly if you have a desktop normally and use a gaming laptop for travel, it is not a problem for on-line games that store status on the Steam Cloud.

---

### Post by Mat_Bigelowe on 2015-12-12
It gave me the same thing about [COLOR=#000000][FONT=Ubuntu Mono]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. except it said I have 13 not updated sooooooo WHAT HAPPENED?!?!?!?!?!?!??!?!?!??!?!?!?!? Sorry for all the drama but I'm pretty new to Ubuntu and I have only been on steam for Linux for about a month now so I have no idea whats going on and I have a LAN on the 26th so if I don't get it up and running by then I'm screwed. Thanks, Mat[/FONT][/COLOR]

---

