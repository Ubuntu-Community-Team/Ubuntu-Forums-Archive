---
title: "Need to reinstall grub from install disk - Help please"
date: 2009-02-16
forum: General Help
---

### Post by goldstar1 on 2009-02-16
I screwed up...

I'm running x86_64 and was trying to improve the looks of my grub splash screen, using various methods on this forum.

I removed grub via package manager and now I don't have a boot loader.

I am right now communicating to this forum using my install disk and what I need to do is install grub onto my hard drive.

How do I do this?

TIA

---

### Post by unutbu on 2009-02-16
[list=1]
[*]Boot from the LiveCD.
[*]If you know the "device name" of your linux partition (e.g. /dev/sda1) then skip to step 3. Otherwise, open a terminal (Applications>Accessories>Terminal) and type
```
sudo fdisk -l
```
(note "-l" is a minus lowercase L).
You should see some output like this:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      112454       56196   de  Dell Utility
/dev/sda2          112455    10602899     5245222+   b  W95 FAT32
[COLOR="Red"]/dev/sda3[/COLOR]   *    10602900    51568649    20482875   83  Linux

```
The device name is in the first column, the partition type is on the right under the column entitled "System". Find the line with partition type "Linux" and then find the corresponding device name. In the above example, /dev/sda3 is the device name of the Linux partition.

[*]Type```

sudo mount /dev/sda1  /mnt
```

Replace /dev/sda1 with the correct device name for your Linux partition.

[*]Mount the dev and proc directories:
```
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
```

[*]Change root to /mnt
```
sudo chroot /mnt 
```     
[*]Install the grub package 
```
apt-get install grub
```
[*]copy  GRUB  images  into  the  /mnt/boot directory and install the stage* files into the MBR and succeeding sectors
```
grub-install --recheck /dev/sda
```
[*]regenerate menu.lst
```
update-grub
```
[/list]

---

### Post by goldstar1 on 2009-02-16
Thanx for your quick reply --it seems that gfxboot is stopping me hold on...oops!



root@ubuntu:/# grub-install --recheck /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
The file /boot/grub/stage1 not read correctly.


Should I continue on here?

---

### Post by Phlee on 2009-02-16
I would just boot Ubuntu from the Live CD.  Once inside there:

```
sudo apt-get update || sudo apt-get purge grub || sudo apt-get install grub
```

---

### Post by goldstar1 on 2009-02-16
I'm getting some errors here...

root@ubuntu:/# apt-get reinstall grub
E: Invalid operation reinstall
root@ubuntu:/# apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-doc mdadm
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/907kB of archives.
After this operation, 2011kB of additional disk space will be used.
Preconfiguring packages ...
dpkg: regarding .../grub_0.97-29ubuntu45_amd64.deb containing grub:
 

>>>grub-gfxboot conflicts with grub
 
 grub (version 0.97-29ubuntu45) is to be installed.
dpkg: error processing /var/cache/apt/archives/grub_0.97-29ubuntu45_amd64.deb (--unpack):
 conflicting packages - not installing grub
Errors were encountered while processing:
 /var/cache/apt/archives/grub_0.97-29ubuntu45_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

root@ubuntu:/# sudo apt-get remove gfxboot

>>>>sudo: unable to resolve host ubuntu

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gfxboot is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/#

---

### Post by goldstar1 on 2009-02-16
Okay...I did the above and it seems I cannot get into my repositories...

root@ubuntu:/# sudo apt-get update || sudo apt-get purge grub || sudo apt-get install grub
sudo: unable to resolve host ubuntu
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg
  Could not resolve 'packages.medibuntu.org'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US
  Could not resolve 'packages.medibuntu.org'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US
  Could not resolve 'packages.medibuntu.org'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://packages.medibuntu.org/dists/gutsy/Release.gpg](http://packages.medibuntu.org/dists/gutsy/Release.gpg)  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch [http://packages.medibuntu.org/dists/gutsy/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/gutsy/free/i18n/Translation-en_US.bz2)  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch [http://packages.medibuntu.org/dists/gutsy/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/gutsy/non-free/i18n/Translation-en_US.bz2)  Could not resolve 'packages.medibuntu.org'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
root@ubuntu:/#

---

### Post by Phlee on 2009-02-16
You having DNS issues I bet.

```
cat /etc/resolv.conf
```

post your results please;)

---

### Post by caljohnsmith on 2009-02-16
Before you chroot, you should copy over your /etc/resolv.conf file into your chroot environment:
```
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
```
And then try chrooting. Let us know if that helps with your "unresolved host" problems.

---

### Post by goldstar1 on 2009-02-16
Hum...I don't know what this means...

root@ubuntu:/# apt-get remove gfxboot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
>>>Package gfxboot is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

root@ubuntu:/# apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-doc mdadm
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/907kB of archives.
After this operation, 2011kB of additional disk space will be used.
Preconfiguring packages ...
dpkg: regarding .../grub_0.97-29ubuntu45_amd64.deb containing grub:
 grub-gfxboot conflicts with grub
  grub (version 0.97-29ubuntu45) is to be installed.
dpkg: error processing /var/cache/apt/archives/grub_0.97-29ubuntu45_amd64.deb (--unpack):
 conflicting packages - not installing grub
Errors were encountered while processing:
 /var/cache/apt/archives/grub_0.97-29ubuntu45_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Phlee on 2009-02-16
Have you tried:

```
apt-get clean && apt-get autoremove grub
```

then:

```
apt-get install grub
```

---

### Post by goldstar1 on 2009-02-16
Here it is...

root@ubuntu:/# cat /etc/resolv.conf
# Generated by NetworkManager
root@ubuntu:/#

# Generated by NetworkManager
nameserver 192.168.1.1

---

### Post by goldstar1 on 2009-02-16
Here's the outcome of that...Is this a key thing?

root@ubuntu:/# apt-get clean && apt-get autoremove grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

root@ubuntu:/# apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-doc mdadm
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 907kB of archives.
After this operation, 2011kB of additional disk space will be used.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main grub 0.97-29ubuntu45
  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub/grub_0.97-29ubuntu45_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub/grub_0.97-29ubuntu45_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@ubuntu:/#

---

### Post by Phlee on 2009-02-16
It's a DNS issue.  Add your DNS servers inside your network manager.  It should do the trick.

---

### Post by goldstar1 on 2009-02-16
Okay here's what I've done and it seems we are getting closer...

ubuntu@ubuntu:~$ sudo mount /dev/sda1  /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# apt-get update || sudo apt-get purge grub || sudo apt-get install grub

All went very well to here, Then...

root@ubuntu:/# apt-get clean && apt-get autoremove grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.

root@ubuntu:/# apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-doc mdadm
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 0 to remove and 11 not upgraded.
Need to get 907kB of archives.
After this operation, 2011kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main grub 0.97-29ubuntu45 [907kB]
Fetched 907kB in 2s (336kB/s)
Preconfiguring packages ...
dpkg: regarding .../grub_0.97-29ubuntu45_amd64.deb containing grub:
 grub-gfxboot conflicts with grub
  grub (version 0.97-29ubuntu45) is to be installed.
dpkg: error processing /var/cache/apt/archives/grub_0.97-29ubuntu45_amd64.deb (--unpack):
 conflicting packages - not installing grub
Errors were encountered while processing:
 /var/cache/apt/archives/grub_0.97-29ubuntu45_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/#

---

### Post by goldstar1 on 2009-02-16
Okay here's what I've done and it seems we are getting closer...

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# apt-get update || sudo apt-get purge grub || sudo apt-get install grub

All went very well to here, Then...

root@ubuntu:/# apt-get clean && apt-get autoremove grub
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package grub is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.

root@ubuntu:/# apt-get install grub
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
grub-doc mdadm
The following NEW packages will be installed:
grub
0 upgraded, 1 newly installed, 0 to remove and 11 not upgraded.
Need to get 907kB of archives.
After this operation, 2011kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main grub 0.97-29ubuntu45 [907kB]
Fetched 907kB in 2s (336kB/s)
Preconfiguring packages ...
dpkg: regarding .../grub_0.97-29ubuntu45_amd64.deb containing grub:
grub-gfxboot conflicts with grub
grub (version 0.97-29ubuntu45) is to be installed.
dpkg: error processing /var/cache/apt/archives/grub_0.97-29ubuntu45_amd64.deb (--unpack):
conflicting packages - not installing grub
Errors were encountered while processing:
/var/cache/apt/archives/grub_0.97-29ubuntu45_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/#

---

