---
title: "Error while loading shared libraries /lib/libsepl.so.1: cannot read file data"
date: 2011-07-12
forum: Desktop Environments
---

### Post by alex81 on 2011-07-12
Hello all, 

I've created quite a predicament with my desktop installation and would prefer to be able to salvage it instead of having to reformat/re-install Ubuntu. 

Quite a lot happened and here's my best recollection: 

- My Ubuntu installation stopped working and I could not get the desktop to load. 
- I backup up my entire home directory by creating a zip file along with other small zip files. I used Alt + Del + F1 to get the CLI to do this. 
- I then did different things trying to get the desktop to load. 
	- I did a apt-get upgrade, to try and get it to work; this was not sucessful. 
	- Working through several dependency issues I finally got sudo apt-get ubuntu-desktop upgrade to work, but it did not finish completely. I started to get out of memory errors. I am assuming this was because too much hard drive space was taken up by the zip files I had created
	-I could not boot and do anything properly after that.  Every attempt to modify the filesystem (to free up space) results in an error "Read Only File System". The root file system was not being mounted and I would see root@none on the CL
- Looking on the boot loader I now have Ubuntu 9.10 2.6.24-generic installed
- I burnt a new installation of Ubuntu 10.4 LTS 
	- Using Live CD I tried to see if I could free up some space and get the system back to more stable state, however this was NOT sucessful. I tried to mount my drive by sudo mount -t ext3 <dev> <dir> but I keep getting the following error: error while loading shared libraries: /lib/libsepol.so.1: cannot read file data: Input/output error


Does any one have any suggestions? It would be greatly appreciated! The only remaining option now I am looking at is a totaly re-install/reformat etc.,which I would prefer to avoid. 

Thanks much.

---

### Post by jerrrys on 2011-07-12
9.10 has reached EOL, have you been here

[https://lists.ubuntu.com/archives/ubuntu-security-announce/2011-March/001286.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2011-March/001286.html)

---

### Post by wildmanne39 on 2011-07-12
Hi, with the fact that 9.10 is no longer supported and everything you have done,you probably have some serious configuration issues I suggest a clean install of a supported version of ubuntu, I have helped a of of people fix there issues but I just do not know where to begin with yours.

---

