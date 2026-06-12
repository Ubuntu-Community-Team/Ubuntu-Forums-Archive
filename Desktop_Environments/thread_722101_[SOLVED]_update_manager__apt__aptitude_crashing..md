---
title: "[SOLVED] update manager / apt / aptitude crashing."
date: 2008-03-12
forum: Desktop Environments
---

### Post by endingexodus on 2008-03-12
I was doing an update for the first time in a while on my ubuntu 7.10 w/ gnome system as my comp had been dead for a while. after the update there was a seg fault, but I do not remember which file. This caused things to lock up so I rebooted and now when I run apt-get update, upgrade, an install or running update manager I get the error:

Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing xclIpboard (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

other than that the comp seems much less stable after being off for a couple weeks due to a blown PSU, which did certainly shut down the computer unsafely but it was in the middle of the night so it shouldn't have been doing much to cause corruption. 

Other than that sudo has been kinda funky, failing randomly with an error message about PAM? 
Anyways, any other information I can provide?
Thanks in advance.

---

### Post by sisco311 on 2008-03-12
try
```
sudo aptitude install -f
```
to fix the dependencies of broken packages.

---

### Post by endingexodus on 2008-03-12
Nope same error, but twice.

exodus@XD:~$ sudo aptitude install -f
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing xclIpboard (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing xclIpboard (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
exodus@XD:~$ 

Any other ideas?
Thanks

---

### Post by endingexodus on 2008-03-12
And... to make things worse, the problem mentioned above with sudo is kinda back, whenever I try to do something from gnome thats needs root authentication I get the error:

Failed to run time-admin as user root.
Unable to copy the user's Xauthorization file.

Thanks.

---

### Post by sisco311 on 2008-03-12
```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-backup
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo aptitude update
```

EDIT: Is something wrong with the /var/lib/dpkg/status file. It's a backup of the file in /var/lib/dpkg/status-old.

---

### Post by endingexodus on 2008-03-12
Whoops guess I should have searched around a bit for the Xauthority problem, I chowned the .Xauthority file and that at least works fine. But still having problems with the updating.
Thanks

---

### Post by endingexodus on 2008-03-12
Whew! Looks good!
Thanks sisco311

---

### Post by endingexodus on 2008-03-12
Shoot, I thought it was fixed.
but:

exodus@XD:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  evolution evolution-common evolution-plugins firefox firefox-gnome-support
  kdelibs-data kdelibs4c2a konsole libcdio6 libiso9660-4
  libnautilus-extension1 libpcre3 libpcrecpp0 libqt4-core libqt4-gui
  libvolume-id0 linux-headers-2.6.22-14 linux-headers-2.6.22-14-generic
  linux-libc-dev nautilus nautilus-data pcregrep udev volumeid
  xserver-xorg-video-intel
25 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0B/59.5MB of archives.
After unpacking 24.6kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/available' near line 4 package `python-bittorrent':
 field name `INstalled' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
exodus@XD:~$ 

thoughts?

---

### Post by endingexodus on 2008-03-12
My Linux genius of a roomate fixed it same problem but with the file available, so he copied  avaliable-old to available.
Thanks again

---

