---
title: "Why are apps not opening?"
date: 2006-03-30
forum: Desktop Environments
---

### Post by Sef on 2006-03-30
I have problems with apps not opening, command line not working, downloads, not working.  Have reinstalled a few times (reinstalled with different disks) because I thought it might be a software problem, but wondering if it is a hardware problem.  

If so, what could be the problem?

---

### Post by meborc on 2006-03-30
can you be more spesific... like what apps are you trying to run... what is the error meaasge in the terminal (if there is any)... what are your system specs etc

---

### Post by Sef on 2006-03-30
Just hangs in the terminal.  Tried to open OOo but just didn't open: said something about an internal error.  Time that is it so far, but other times, firefox failed to open and others did as well.

---

### Post by meborc on 2006-03-30
try running 

[B]sudo apt-get update
sudo apt-get upgrade[/B]

to update your computer...
but it seems like a mystery to me :-k

---

### Post by Sef on 2006-03-30
Got hung up updating last time...tried it again and this is what it says:

sef@jokat1:~$ sudo apt-get update
Password:
Sorry, try again.
Password:
Get:1 [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy Release
Get:4 [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-updates Release [30.9kB]
Get:5 [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports Release [19.6kB]
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy/main Packages
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy/restricted Packages
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy/main Sources
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy/restricted Sources
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy/universe Packages
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy/multiverse Packages
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy/universe Sources
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy/multiverse Sources
Get:6 [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-updates/main Packages [38.0kB]
Get:7 [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:8 [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-updates/main Sources [18.2kB]
Get:9 [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Get:10 [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/main Packages [14.0kB]
Ign [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/main Packages
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Error writing to output file - write (28 No space left on device)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Get:12 [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Ign [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/restricted Packages
Get:13 [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/universe Packages [26.1kB]
Ign [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/universe Packages
Ign [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/multiverse Packages
Get:14 [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/main Sources [1353B]
Ign [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/main Sources
Get:15 [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/restricted Sources [14B]
Ign [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/restricted Sources
Get:16 [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/universe Sources [10.2kB]
Ign [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/universe Sources
Get:17 [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/multiverse Sources [701B]
Ign [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/multiverse Sources
Get:18 [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/main Packages [14.4kB]
Err [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/main Packages
  Error writing to output file - write (28 No space left on device)
Get:19 [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/restricted Packages [20B]
Err [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/restricted Packages
  Error writing to output file - write (28 No space left on device)
Get:20 [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/universe Packages [29.3kB]
Err [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/universe Packages
  Error writing to output file - write (28 No space left on device)
Get:21 [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/multiverse Packages [1241B]Err [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/multiverse Packages
  Error writing to output file - write (28 No space left on device)
Get:22 [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/main Sources [5219B]
Err [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/main Sources
  Error writing to output file - write (28 No space left on device)
Get:23 [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/restricted Sources [20B]
Err [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/restricted Sources
  Error writing to output file - write (28 No space left on device)
Get:24 [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/universe Sources [11.1kB]
Err [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/universe Sources
  Error writing to output file - write (28 No space left on device)
Get:25 [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/multiverse Sources [593B]
Err [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) breezy-backports/multiverse Sources
  Error writing to output file - write (28 No space left on device)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages [3830B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources [1025B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
  Connection timed out
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4055B]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
  Error writing to output file - write (28 No space left on device)
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [15.2kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
  Error writing to output file - write (28 No space left on device)
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [899B]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
  Error writing to output file - write (28 No space left on device)
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [36.4kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
  Error writing to output file - write (28 No space left on device)
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages [3131B]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
  Error writing to output file - write (28 No space left on device)
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [5081B]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
  Error writing to output file - write (28 No space left on device)
Get:36 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources [907B]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
  Error writing to output file - write (28 No space left on device)
42% [6 Packages bzip2 0]

What partition is it writing to?

P3, 512 ram, 20 GB hd  (Replaced the motherboard a few months ago.)

---

### Post by Sef on 2006-03-30
I rebooted twice.  Second time everything went fine. However, the first time, I got this message:  Mounting Local Filesystem -  failed.

What does this mean?

---

