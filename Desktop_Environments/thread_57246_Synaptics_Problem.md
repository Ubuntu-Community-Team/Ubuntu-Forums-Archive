---
title: "Synaptics Problem"
date: 2005-08-15
forum: Desktop Environments
---

### Post by OldSeaDog on 2005-08-15
I am a newbie, so excuse my ignorance.  Most of my computer knowledge is with Netware, and that was 10 years ago.  I then joined the hated ranks of the "users" :).

I have come a cropper with synaptics.  I have Dell Dimension 386, PIII running at 1GHz with 384MB of memory and I have 2 hard drives, a 20GB one which is the boot drive and has a small Linux partition (~500MB) used for /Home, as well as a 60GB drive with a 10GB Linux partition as root and ~1 GB for swap.

When I attempt to use Synaptics, it begins by reporting a set of errors where it is unable to stat a string of 8 package lists, including:
ca,archive.ubuntu.com hoary-updates/main and restricted, 
archive.ubuntu.com hoary/universe, main and restricted
security.ubuntu.com/main. restricted and universe
They are all shown in the order they occurred.

It then goes to a screen for Downloading package information, and stops at downloading file 5 of 8, with the following reported in the indicidual file progress:
Status: Failed	  Size: 0B	 Package: Release.gpg	URl: cdrom://Ubuntu 5.04_Hoary Hedgehog_-release i386(20050407) hoary Release.gpg.

Then it reports that it could not download all repository indexes.  a sample of two of the index errors are as follows:
[http://ca.archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg:](http://ca.archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg:) Connection failed
[http://ca.archive.ubuntu.com/ubuntu/dists/hoary-updates/Release.gpg:](http://ca.archive.ubuntu.com/ubuntu/dists/hoary-updates/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused).  There are 20 errors like this.

It then repeats the first error message and finally presents me with a list of the applications that have been installed, but nothing else.

My network connection appears to be fine, the CD is readable and I have no idea what to do next, short of going back to the beginning with a fresh installation.

Before I do that, does anyone have a simpler solution?

Thanks

---

### Post by amohanty on 2005-08-15
> following reported in the indicidual file progress:
Status: Failed Size: 0B Package: Release.gpg URl: cdrom://Ubuntu 5.04_Hoary Hedgehog_-release i386(20050407) hoary Release.gpg. 

I think that the relevant cd track got corrupted. The easiest way out is to burn a new CD.

HTH
AM

---

