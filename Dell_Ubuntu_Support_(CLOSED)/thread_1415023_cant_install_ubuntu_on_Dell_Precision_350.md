---
title: "cant install ubuntu on Dell Precision 350"
date: 2010-02-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by klitzsey on 2010-02-24
I just got a Dell Precision 350 from a friend and wanted to put Ubuntu 9.10 on it but every time I try to install I get to where x is loading for the install and everything just stops. can turn on and off the cap locks on the keyboard, can move the mouse but nothing else. I don't hear the CD spinning anymore. 

I saw the special iso for dell but its 1.8gb and this computer doesn't have a DVD on it just a regular CD. I don't have one to swap out at the present time either. 

Any suggestions one what is wrong?

---

### Post by bobcollard on 2010-02-24
> **klitzsey said:**
> I just got a Dell Precision 350 from a friend and wanted to put Ubuntu 9.10 on it but every time I try to install I get to where x is loading for the install and everything just stops. can turn on and off the cap locks on the keyboard, can move the mouse but nothing else. I don't hear the CD spinning anymore. 

I saw the special iso for dell but its 1.8gb and this computer doesn't have a DVD on it just a regular CD. I don't have one to swap out at the present time either. 

Any suggestions one what is wrong?
Did you check the MD5SUM of the .ISO before burning it to disk?   There is also a verification of the disk itself when you first start it.  No need for the Dell version, all it has is the drivers installed and you can do that after Ubuntu is installed.  Ubuntu is 690.8MB on a CD.

---

### Post by klitzsey on 2010-02-25
> **bobcollard said:**
> Did you check the MD5SUM of the .ISO before burning it to disk?   There is also a verification of the disk itself when you first start it.  No need for the Dell version, all it has is the drivers installed and you can do that after Ubuntu is installed.  Ubuntu is 690.8MB on a CD.

I ran the verification of the disk when I was unsuccessful the first time and it came back with no problems. I've also tried an 8.10 offical disk I had, Mint Linux, and OpenSolaris all with the same result. This computer has winxp installed and I can boot to that so I know nothing is wrong with the PC itself. 

I watched the msgs on screen as it was loading. this is everything that was on the screen before it froze. 

Scanning disc for indext files...
Found 2 packages indexes, 0 source indexes, 0 translation indexes and 1 signatures
Found label 'Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)'
This disc is called:
'Ubuntu 9.10 _Karmic Koala_ -Release i386 (20091028.5)'
Copying package lists... gpgv:Signature made Wed Oct 28 21:14:33 2009 UTC using DSA key ID FBB75451
gpgv:Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes....Done
Writing new source list
Source list entries for this disc are :
deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/karmic main restricted
Repeat this process for the rest of the CDs in your set.
W:Skipping non-existing file /cdrom/dists/karmic/main/binary-i386/Packages
W:Skipping non-existing file /cdrom/dists/karmic/restricted/binary-i386/Packages
Removing any system startup links for /etc/init.d/apparmor...
/etc/rcS.d/S37apparmor
(Reading database ... 120329 files and directories currently installed.)
Removing gdm-guest-session ...
Purging configuration files for gdm-guest-session ...

---

### Post by bobcollard on 2010-02-25
I have had to wait for X loading, sometimes it takes awhile.  Try again, and go get a cup of coffee.  Your computer may be unpacking a zip file and the drive would not be spinning.

---

### Post by klitzsey on 2010-02-26
> **bobcollard said:**
> I have had to wait for X loading, sometimes it takes awhile.  Try again, and go get a cup of coffee.  Your computer may be unpacking a zip file and the drive would not be spinning.


I let that computer sit for 3 hours and its still stops in the same place. The keyboard stopped functioning. I'm at the point of giving up. I'm going to look at the mobo and see if there is an arch situation but I guess I'll just leave winxp on it. Thanks for your help anyway.

---

