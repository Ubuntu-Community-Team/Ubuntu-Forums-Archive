---
title: "ubuntu-desktop package error"
date: 2005-09-28
forum: Desktop Environments
---

### Post by CubanCorona on 2005-09-28
I just performed a new install of Hoary on my Sony Vaio PCG-R505.

The installer informed me that some packages did not install correctly.  However, Ubuntu seems to run fine.

Synaptic reports that the ubuntu-desktop package is broken.  When I try to reinstall it, I get the following output:


> Preconfiguring packages ...
(Reading database ... 57664 files and directories currently installed.)
Unpacking libopenh323-1.15.2 (from .../libopenh323-1.15.2_1.15.3-2_i386.deb) ...dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /cdrom//pool/main/o/openh323/libopenh323-1.15.2_1.15.3-2_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/doc/libopenh323-1.15.2/changelog.gz')
Unpacking ttf-baekmuk (from .../ttf-baekmuk_2.2-1ubuntu1_all.deb) ...
dpkg: error processing /cdrom//pool/main/t/ttf-baekmuk/ttf-baekmuk_2.2-1ubuntu1_all.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive: Success
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /cdrom//pool/main/o/openh323/libopenh323-1.15.2_1.15.3-2_i386.deb
 /cdrom//pool/main/t/ttf-baekmuk/ttf-baekmuk_2.2-1ubuntu1_all.deb

I would really appreciate some insight!

---

### Post by CubanCorona on 2005-09-28
bump

---

### Post by az on 2005-09-28
Your cd has some errors on it.  Some packages are currupted.

---

### Post by CubanCorona on 2005-09-28
How can I force corrupted packages to be re-downloaded?

Rather than trying to download them, it always wants the CD.

---

### Post by psychicdragon on 2005-09-28
sudo gedit /etc/apt/sources.list
Delete the first line that refers to the cd-rom.
sudo apt-get update
sudo apt-get install ubuntu-desktop

---

### Post by bfonseca on 2005-11-28
[QUOTE=psychicdragon]sudo gedit /etc/apt/sources.list
Delete the first line that refers to the cd-rom.
sudo apt-get update
sudo apt-get install ubuntu-desktop[/QUOTE]

I have the same problem as the guy up on top.. I tried your suggestion and it didnt work. I still get an error. The error is as follows:

/etc/defoma/hints/ttf-baekmuk (--configure):
 subprocess post-installation script returned error exit status 1
dpkg:  dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on ttf-baekmuk; however:
   package ttf-baekmuk is not configured yet

can you tell me where i need to go from here.
thanks 
brian

---

### Post by Xian on 2005-11-28
Does the following command help:

$ sudo dpkg --configure -a

---

### Post by bfonseca on 2005-11-28
[QUOTE=Xian]Does the following command help:

$ sudo dpkg --configure -a[/QUOTE]

hey thanks for the quick resonse. I got it to work by deleting the ttf-baekmuk package inside the archives and then I went into the sources.list and commented out the first few lines (the one that talks about the cdrom) just like psychicdragon said to do and then did the same thing for lock cause i was having a problem with that too.  So i deleted that.

Then I went into the synaptic and reinstalled both lock and ttf-baekmuk  and it worked. after this i did a :
 
sudo apt-get update
sudo apt-get -f install

It works just fine, now. Thanks for your quick response and help. I did try the sudo dpkg --configure -a like you sugested. It didnt say anything afterwords. So I am asuming everything is ok now. This is what I like about ubuntu, everybody willing to help out everybody else. Thanks for all, that helped.

Brian

---

