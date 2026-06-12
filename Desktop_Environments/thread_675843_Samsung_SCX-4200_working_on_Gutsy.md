---
title: "Samsung SCX-4200 working on Gutsy"
date: 2008-01-23
forum: Desktop Environments
---

### Post by minghai on 2008-01-23
Hi all,

      I had used the instructions on [http://ubuntuforums.org/showthread.php?t=245545](http://ubuntuforums.org/showthread.php?t=245545) to get my SCX-4200 working in Feisty.  I recently upgraded to Gutsy and there is a new Samsung Unified Linux driver and the instructions are somewhat different now so I documented the steps it took me to get it to work so here are the steps I took.

Printer
=====
Instructions from 
[http://news.u32.net/articles/2007/02/05/the-samsung-unified-linux-driver-installer-on-ubuntu](http://news.u32.net/articles/2007/02/05/the-samsung-unified-linux-driver-installer-on-ubuntu)

Download the latest driver from Samsung's site. Use the latest driver
for the SCX-4200 (2007072015943906_UnifiedLinuxDriver.tar.gz version
2.00.97)

$ tar zxf 2007072015943906_UnifiedLinuxDriver.tar.gz
$ cd cdroot
$ sudo ./autorun

Not sure if this step is needed: System -> Administration -> Printing
    Under "Server Settings" check "Show printers ...", "Share
published ..." and "Allow users ...".
    Under "Local Printers", for Device URI: choose "Samsung SCX-4200
Series USB"

Scanner
======
Instructions from
[http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian](http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian)

Run  "scanimage -L" and if its not installed, install it using "sudo
apt-get install sane-utils"

Fix for the scanning as normal user issue
------------------------------------------------------------
You have this problem if you run the command "scanimage -L" as a
normal user and something like this happens:

vcampus@vcampus-pc5:~$ scanimage -L
Segmentation fault (core dumped)

However, this happens if you run the command as root:

vcampus@vcampus-pc5:~$ sudo scanimage -L
device `smfp:SAMSUNG SCX-4200 Series on USB:0' is a SAMSUNG SCX-4200
Series on USB:0 Flatbed Scanner

The problem is that the driver is trying to access your computer's
parallel port to detect any printers there, but as a normal user you
cannot do it, so the system stops your program with a Segmentation
Fault signal.

I didn't see any way to set the driver up not to access the parallel
port, so I modified the binary driver to disable the parallel port
detection. This makes the driver not work with parallel port devices
anymore, so don't try this if you are using a parallel port device.

Download these files for the driver versions 2.00.95 and 2.00.97:

[http://jacobo.tarrio.org/files/soft/scx/fix-nopar-scx4200-2.00.95-2007061201.tar.gz](http://jacobo.tarrio.org/files/soft/scx/fix-nopar-scx4200-2.00.95-2007061201.tar.gz)
[http://jacobo.tarrio.org/files/soft/scx/fix-nopar-scx4200-2.00.95-2007061201.tar.gz.asc](http://jacobo.tarrio.org/files/soft/scx/fix-nopar-scx4200-2.00.95-2007061201.tar.gz.asc)

Use the md5sum command on the .tar.gz file and compare it to the MD5
sum supplied here. If they match, your file is probably correct.

# md5sum fix-nopar-scx4200-2.00.95-2007061201.tar.gz
f0deea1fb758332c0aa01e238857c043 fix-nopar-scx4200-2.00.95-2007061201.tar.gz

Then, run this:

# tar xvfz fix-nopar-sscx4200-2.00.95-2007061201.tar.gz
# cd fix-nopar

There are two versions of the fixed files: the "i386" one is for
32-bit x86 machines; the "x86_64" one is for 64-bit x86 machines. I
recommend that you run the "check.sh " script to make sure you know
which one you have to install:

# ./check.sh
The 32-bit library has been found at /usr/lib
You may replace it with the one in the "i386" directory

In this example, the script found the 32-bit version, so you would use
the fix in the "i386" directory. You might also have both versions
installed at the same time; in that case, you only have to follow the
instructions for both versions.

After you enter each directory, you'll find some useful information in
the README and differences.txt files. Read them as to be informed
about what's going on.

I recommend checking the MD5 sums against those that appear in the
README file, and aborting the procedure if they don't match:

# md5sum libmfp.so.1.0.1
090c0bf644399e5b4fef73506c64dd47  libmfp.so.1.0.1
# md5sum /usr/lib/libmfp.so.1.0.1
501cee139bc4b3b097f2d9789959abf6  /usr/lib/libmfp.so.1.0.1

They match, so now you can make a backup of the original, unmodified
file, and copy the fixed file over it:

# cp /usr/lib/libmfp.so.1.0.1 /usr/lib/oldlibmfp.so.1.0.1
# cp libmfp.so.1.0.1 /usr/lib

Now check that you can run "scanimage -L" as a normal user:

vcampus@vcampus-pc5:~$ sudo scanimage -L
device `smfp:SAMSUNG SCX-4200 Series on USB:0' is a SAMSUNG SCX-4200
Series on USB:0 Flatbed Scanner

If it doesn't work yet, try this:

# adduser YOUR_USER_NAME lp

Substitute your user name for YOUR_USER_NAME. And then, as a normal user:

$ newgrp lp

  Reboot for newgrp command to take effect on all shells.

vcampus@vcampus-pc5:~$ sudo scanimage -L
device `smfp:SAMSUNG SCX-4200 Series on USB:0' is a SAMSUNG SCX-4200
Series on USB:0 Flatbed Scanner

Now try xsane. If it complains for being ran as root, just reinstall
it. It should work.

If the fix doesn't work, you can undo it with:

# mv /usr/lib/oldlibmfp.so.1.0.1 /usr/lib/libmfp.so.1.0.1

---

