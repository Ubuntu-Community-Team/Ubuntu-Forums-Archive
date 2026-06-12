---
title: "Mplayer broken package error endless loop"
date: 2012-05-04
forum: Desktop Environments
---

### Post by tdlam on 2012-05-04
Hi folks...I am having a problem with mplayer installing/uninstalling on my xubuntu 12.04. The package is broken...but I can't uninstall it. I keep getting an error that reapeats over and over in a loop. Its also not letting me install other packages unril it is fixed. But all it does is keep looping to the same error over and over even when I press the cancel button.

Error is as follows:

```
installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 377846 files and directories currently installed.)
Unpacking mplayer (from .../mplayer_2%3a1.0~rc4.dfsg1+svn34540-1_i386.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: data error'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/mplayer_2%3a1.0~rc4.dfsg1+svn34540-1_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because MaxReports is reached already
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/mplayer_2%3a1.0~rc4.dfsg1+svn34540-1_i386.deb
Error in function: 
dpkg: dependency problems prevent configuration of electricsheep:
 electricsheep depends on mplayer; however:
  Package mplayer is not installed.
dpkg: error processing electricsheep (--configure):
 dependency problems - leaving unconfigured
```

anyway...any help that can be provided is as always appreciated. This forum is the best full of fine and helpful folks.

Thanks once again in advance.

---

### Post by SeijiSensei on 2012-05-04
It looks like your mplayer .deb package may be corrupt.

> dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: data error'

Try:

```

sudo apt-get purge mplayer
sudo apt-get update
sudo apt-get install mplayer

```

---

### Post by tdlam on 2012-05-04
The first purge command returns this:

```
tdlam@tdlam-Inspiron-6000:~$ sudo apt-get purge mplayer
[sudo] password for tdlam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mplayer is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 electricsheep : Depends: mplayer
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

apt get update went ok then the re install command returns this:
```
tdlam@tdlam-Inspiron-6000:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  mplayer-doc netselect fping
The following NEW packages will be installed:
  mplayer
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0 B/2,804 kB of archives.
After this operation, 5,588 kB of additional disk space will be used.
(Reading database ... 377846 files and directories currently installed.)
Unpacking mplayer (from .../mplayer_2%3a1.0~rc4.dfsg1+svn34540-1_i386.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: data error'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/mplayer_2%3a1.0~rc4.dfsg1+svn34540-1_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because the error message indicates an issue on the local system
         Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/mplayer_2%3a1.0~rc4.dfsg1+svn34540-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
tdlam@tdlam-Inspiron-6000:~$ 
```

Then I get the error dialogue box again and I hit cancel to close it and it keeps popping back up...sudo apt-get -f install doesn't work either...

---

### Post by tdlam on 2012-05-04
sorry for the double post but update manager just popped up...so when I tried to install the updates I got an error telling me that the package manager is broken. Here's the error read out:

```
The following packages have unmet dependencies:

electricsheep: Depends: mplayer but it is not installed
               Depends: flam3 (>= 2.7.19) but 3.0.1-2ubuntu1 is installed
               Depends: libavcodec-extra-53 (>= 4:0.7-1) but 4:0.8.1ubuntu1 is installed
               Depends: libavformat-extra-53 (>= 4:0.7-1) but it is not installed
               Depends: libc6 (>= 2.7) but 2.15-0ubuntu10 is installed
               Depends: libglade2-0 (>= 1:2.6.1) but 1:2.6.4-1ubuntu1 is installed
               Depends: libgtk2.0-0 (>= 2.8.0) but 2.24.10-0ubuntu6 is installed
               Depends: gconf2 (>= 2.28.1-2) but 3.2.5-0ubuntu2 is installed
```

---

### Post by mips on 2012-05-05
Post the contents of your **etc/apt/sources.list** file here.

---

### Post by tdlam on 2012-05-05
Well here is my sources list. 

```
# deb cdrom:[Xubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ precise-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main
# deb http://download.bitdefender.com/repos/deb/ bitdefender non-free # disabled on upgrade to precise
# deb-src http://download.bitdefender.com/repos/deb/ bitdefender non-free # disabled on upgrade to precise

```
I did a sudo apt-purge of a screensaver I was trying to install called electric sheep as it seems it was needing mplayer to work...that calmed the problem down a bit. I forgot to mention that I am running an xubuntu upgrade from 11.10 to 12.04...during the upgrade process I did get errors about MPLAYER...so I think something is up.

I tried to install mplayer again I get this error


```
installArchives() failed: Selecting previously unselected package fping.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 394807 files and directories currently installed.)
Unpacking fping (from .../fping_2.4b2-to-ipv6-16.1_i386.deb) ...
Selecting previously unselected package mplayer-skins.
Unpacking mplayer-skins (from .../mplayer-skins_3_all.deb) ...
Unpacking mplayer (from .../mplayer_2%3a1.0~rc4.dfsg1+svn34540-1_i386.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: data error'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/mplayer_2%3a1.0~rc4.dfsg1+svn34540-1_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because MaxReports is reached already
Selecting previously unselected package mplayer-doc.
Unpacking mplayer-doc (from .../mplayer-doc_2%3a1.0~rc4.dfsg1+svn34540-1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 8 added doc-base files...
Registering documents with scrollkeeper...
Errors were encountered while processing:
 /var/cache/apt/archives/mplayer_2%3a1.0~rc4.dfsg1+svn34540-1_i386.deb
Error in function: 
Setting up fping (2.4b2-to-ipv6-16.1) ...
Setting up mplayer-skins (3) ...
Setting up mplayer-doc (2:1.0~rc4.dfsg1+svn34540-1) ...

```

I ran sudo apt-get purge mplayer in therminal one more time and got this

```
tdlam@tdlam-Inspiron-6000:~$ sudo apt-get purge mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mplayer is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

ok thanks...it seems like at least Im not still getting that repeating error loop now but still dunno what is happening or if the problem is fixed or not...

---

### Post by mips on 2012-05-05
That mplayer file seems to be corrupted.

Post the output of **ls -l /var/cache/apt/archives/mplayer***

If you find any packages listed starting with the name mplayer then go into /var/cache/apt/archives/ and as root delete those packages using the rm command. You could also start nautilus using **gksu nautilus** and navigate to that location to delete the mplayer files. **Be VERY careful with using root access!!!**

Once you are done do a 
```
sudo apt-get -f install
sudo apt-get update
sudo apt-get install mplayer
```

---

### Post by SeijiSensei on 2012-05-05
> **mips said:**
> That mplayer file seems to be corrupted.

Post the output of **ls -l /var/cache/apt/archives/mplayer***

That deb package has these characteristics:

[B]Size 2803800
MD5  b4ca09a428e72260e0795305556abdcc
[/B]
OP, if your file has the same size, check its MD5 signature by running 

```
md5sum < /var/cache/apt/archives/mplayer_1.0~rc4.dfsg1+svn34540-1_i386.deb
```

If it's not the same size, or you get a different MD5 value, then you need to download it again.  Just click on [this link](http://security.ubuntu.com/ubuntu/pool/universe/m/mplayer/mplayer_1.0~rc4.dfsg1+svn34540-1_i386.deb), then run 
```
sudo dpkg -i /path/to/mplayer_1.0~rc4.dfsg1+svn34540-1_i386.deb
``` and let us know what happens.  It will probably be stored in your Downloads directory.  If that installs successfully, delete the one in the archives with
```
sudo rm -f /var/cache/apt/archives/mplayer_1.0~rc4.dfsg1+svn34540-1_i386.deb
```

---

### Post by tdlam on 2012-05-05
@ mips when I run ls -l /var/cache/apt/archives/mplayer* I get this:
```
-rw-r--r-- 1 root root 2803800 Jan 23 01:34 /var/cache/apt/archives/mplayer_2%3a1.0~rc4.dfsg1+svn34540-1_i386.deb
-rw-r--r-- 1 root root 2122350 Jan 23 01:34 /var/cache/apt/archives/mplayer-doc_2%3a1.0~rc4.dfsg1+svn34540-1_all.deb
-rw-r--r-- 1 root root  295342 Oct 16  2009 /var/cache/apt/archives/mplayer-skins_3_all.deb
```


"If you find any packages listed starting with the name mplayer then go into /var/cache/apt/archives/ and as root delete those packages using the rm command."
@ mips: sorry I am new and dont know how to go into a folder as 
root and dont know where I would find the folder you specified.

@SeijiSensei: when I run md5sum < /var/cache/apt/archives/mplayer_1.0~rc4.dfsg1+svn34540-1_i386.deb I get this:
```

bash: /var/cache/apt/archives/mplayer_1.0~rc4.dfsg1+svn34540-1_i386.deb: No such file or directory
```

---

### Post by dentaku65 on 2012-05-06
You can try dpkg command to force the mplayer removal.
```
sudo dpkg --force-all -P mplayer
```
Then:
```
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install mplayer
```

by

---

### Post by mips on 2012-05-06
> **tdlam said:**
> 


"If you find any packages listed starting with the name mplayer then go into /var/cache/apt/archives/ and as root delete those packages using the rm command."
@ mips: sorry I am new and dont know how to go into a folder as 
root and dont know where I would find the folder you specified.

Do what SeijiSensei said and do a,
```
rm -f /var/cache/apt/archives/mplayer*
```

---

### Post by tdlam on 2012-05-07
Welll thanks for all the advice...still couldnt figure out how to get into a folder as root...so I booted up this machine with linux puppy as a live cd...and went in and manually deleted the files...now the problem is gone.

SO I would say this thread is solved...still I would like to know how to get into a folder as root. Is there a command you need to run to do that so I know for the future?

Thanks in advance

---

### Post by mips on 2012-05-08
> **tdlam said:**
> 
SO I would say this thread is solved...still I would like to know how to get into a folder as root. Is there a command you need to run to do that so I know for the future?


The info is in the posts above but I will repeat in a more elaborate way.


You don't need to be root to access a folder, you do however need to use **sudo** to delete files **owned by root**.

To navigate to the folder:
```
cd /var/cache/apt/archives
```

To delete a file from inside a folder just specify the file name:
```
sudo rm -f *<filename>*
```

To delete a file from outside the folder specify it's full path :
```
sudo rm -f /var/cache/apt/archives/*<filename>*
```

Where **<filename>** is the full name of the file ie. "mplayer_2%3a1.0~rc4.dfsg1+svn34540-1_amd64.deb" which will only delete this one particular file...

..or you can specify a partial file name "mplayer*" where the * means ALL file names starting with 'mplayer' which will delete 3 files.

---

### Post by tdlam on 2012-05-12
Ok thank you very much for the info. 
That's a big help. 
I will post this thread as solved. All the best to you.

---

