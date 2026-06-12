---
title: "Ubuntu Feisty 20070131 i386 Desktop"
date: 2007-01-31
forum: Development CD/DVD Image Testing
---

### Post by canga on 2007-01-31
I have encountered significant problems with loading Feisty from the i386 Desktop CD released 31/1/2007.

Tried option 2 Guided partitioning using entire disk three (3) times, each time the install stopped before completion; there was a complete absence of CD reader or hard disk activity for 10-15 minutes.  

First time it stopped at Partition formatting 5%, creating ext3 filesystem for / in partition #1 of IDE1 Master ...

Second time it stopped at Installing system 22% Copying files ...

Third time it got to Installing system 99% Completely removed libglibmm-2.4-1c2a.

Fourth time I tried option 3 manual partitioning, and selected to format /dev/hda1.  Install stopped as this method didn't define a mount point for /.  The guided partitioning defined mount points for /media/hda1 and /media/hdd1

Fifth time I ran GParted from the live CD and reformatted /dev/hda1 to ext3 before starting the install.  This time the install worked.

I don't know if I can provide useful dumps, logs etc for a bug report as the install logs of all the unsuccessful attempts were lost.

Other observations:

The notification area on the Ubuntu loader screen uses a small blue font that is exceedingly difficult to read when your eyesight is challenged.

It seems to be necessary to move the mouse pointer off a button and then back over the button before a click is noticed when running the installer.

Note that the MD5Sum for the CD was correct and there were no checksum errors detected for the files on the CD.

Short testing on Live operation was as successful as one might expect.  I haven't run short testing on the installed system yet.

---

### Post by UBfusion on 2007-02-01
Interesting... this is a well-known bug (see e.g. [bug #76976]("https://launchpad.net/ubuntu/+source/ubiquity/+bug/76976") and [bug #81938]("https://launchpad.net/ubuntu/+source/ubiquity/+bug/81938") ) that should be gone in 20070131 (at least it's fixed in amd64 desktop which I tested).

Please have a look at the above bugs, and search Launchpad, for "ubiquity". A workaround exists as follows:

> Thanks for your report. This is also bug 76976, and has since been fixed; run 'sudo apt-get update; sudo apt-get install debconf ubiquity' from a terminal window before starting the installer to pick up the fix.

Please try the above fix and if possible try today's build and provide comments on your findings in Launchpad.

---

### Post by canga on 2007-02-02
I have just completed download of last night's version of ISO file and checked the MD5SUM.  Will burn CD and start testing of the new image.

---

