---
title: "Opencyc in Ubuntu?"
date: 2007-12-22
forum: Education &amp; Science
---

### Post by borgel on 2007-12-22
I have been trying to run [Opencyc]("http://www.opencyc.org/") on Gutsy, but I keep getting a segmentation fault error ( Error: Stack Overflow (signaled by signal 11 SIGSEGV (Segmentation violation)).  I didn't see an answer for this on Opencyc's forums so I thought I would check to see if anyone here has seen a solution for this problem.

---

### Post by SuperTrooper on 2007-12-29
EDIT: Ignore these instructions and look at my next post instead (the next post is much simpler)....

I too was pulling my hair out over OpenCyc for the last several days.  It works dandy on Windows.  But **I** absolutely do not work dandy under Windows.  Here's what I did to get it working in Ubuntu (essentially, I did a chroot install of CentOS underneath Ubuntu - rationale is near the bottom):

1. Download CentOS 3 ([http://www.centos.org/](http://www.centos.org/)) (I got the install DVD image .iso via BitTorrent)

2. Install qemu:
```
sudo aptitude install qemu
```

3. Setup a disk image:
```
qemu-img create -f raw /tmp/centos3_fresh_image.img 4G
```

4. Run qemu:
```
qemu -hda /tmp/centos3_fresh_image.img -cdrom CentOS-3.8-i386-binDVD.iso -boot d
```

5. (follow the steps in the QEMU window to install CentOS)

6. Find the sector offset of the partition by using fdisk.  Here is what my setup looked like:
```

fdisk -ul centos3_fresh_image.img 
You must set cylinders.
You can do this from the extra functions menu.

Disk centos3_fresh_image.img: 0 MB, 0 bytes
255 heads, 63 sectors/track, 0 cylinders, total 0 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

                  Device Boot      Start         End      Blocks   Id  System
centos3_fresh_image.img1   *          63      208844      104391   83  Linux
centos3_fresh_image.img2          208845     7871849     3831502+  83  Linux
centos3_fresh_image.img3         7871850     8385929      257040   82  Linux swap / Solaris

The sector offset for the root partition is: 208845.
Each sector is 512 bytes, so the byte offset is:
208845 * 512 = 106928640 bytes.

```

7. Use the byte offset (from above) to do a loopback mount of the partition:
```

sudo su # you need to be root from this point on...
mkdir /mnt/loop
mount -o loop,offset=106928640 /tmp/centos3_fresh_image.img /mnt/loop/

```

8. Copy all the data needed for the chroot:
```

mkdir /home/centos_cyc_chroot
cp -a /mnt/loop/. /home/centos_cyc_chroot/.

```

9. Untar/unzip the Cyc data (we are almost finished!):
```

mkdir /home/centos_cyc_chroot/home/cyc
tar xzvf opencyc-1.0.2-linux.tgz -C /home/centos_cyc_chroot/home/cyc

```

10. Now, the chroot magic happens (this is where we pretend like we are running CentOS while still running Ubuntu/Gentoo/Slackware/whatever):
```

# WARNING: you still need to be root for this to work!
chroot /home/centos_cyc_chroot
adduser cyc
chown -Rf cyc:users /home/cyc
su cyc
cd /home/cyc/opencyc-1.0/scripts/
echo RH-ES3-x86_32 > platform-override.txt
./run-cyc.sh
# Then you wait a very long time for Cyc to build a world file
# WARNING: you **might** see an error like this:
# ./run-cyc.sh: line 63:  2600 Segmentation fault      (core dumped) $CYC_EXE -w $CYC_WORLD
# HOWEVER!  That error is **not** fatal - things are okay (at least in my case they were)

# Now, if you did get a "Segmentation fault", just run this command again
# (try it several times until it succeeds ... it might fight a little, but eventually
# it should succeed):
./run-cyc.sh

# You should see an output that looks like this:
# bin/opencyc-RH-ES3-x86_32.bin -w world/kb-5006-RH-ES3-x86_32-local.load
# Loading statics.
# Mapping in the memory image.
# Running initializers ... PROCESS (47032), STREAM (47038), STREAM (47053), PROCESS (47064), done.
# Reconnected to shared object RED Library (auto-loaded).
# Cyc 10 (Linux 32-bit)
# Copyright (C) 1995 - 2006 Cycorp, Inc.  All rights reserved.
# RTL (Green Threads/ASM Contexts) initialized.
# CycL Initialized.
# The executable and world objects matched.
# Initializing HL backing store caches from units/5006/.
# Enabling base TCP services to port 3600.
#
# Ready for services.
# Process ID: 2681
# System 1.11058.2.20.2.3 KB 5006.
# CYC(1):

```

I was able to connect to [http://localhost:3602/cgi-bin/cyccgi/cg?cb-start](http://localhost:3602/cgi-bin/cyccgi/cg?cb-start) and get the Login page for Cyc.  Super!

I tried repeating these steps with vanilla Ubuntu (i.e. by *not* chrooting to CentOS), and kept getting failures that looked like this:

1.  ```

Mapping in the memory image.
./run-cyc.sh: line 63: 14473 Segmentation fault      (core dumped) $CYC_EXE -w $CYC_WORLD

```

2.  ```

Mapping in the memory image.
./run-cyc.sh: line 63: 14853 Illegal instruction     (core dumped) $CYC_EXE -w $CYC_WORLD

```

3. This is half-way failure: I can use the CYC shell (by choosing the "0" option), but the web server (on port 3602) is not available:
```

Mapping in the memory image.
Running initializers ... PROCESS (47028), STREAM (47034), STREAM (47049), PROCESS (47060), done.
Reconnected to shared object RED Library (auto-loaded).
Cyc 10 (Linux 32-bit)
Copyright (C) 1995 - 2006 Cycorp, Inc.  All rights reserved.
RTL (Green Threads/ASM Contexts) initialized.
CycL Initialized.
The executable and world objects matched.
Initializing HL backing store caches from units/5006/.
Enabling base TCP services to port 3600.

Ready for services.
Error: Received signal 7 SIGBUS (Bus error).
[Switching to single-threaded mode ....]

Select a restart:
  0: Recursive read loop.
  1: Exit program.
? 

```

...well, so there you have it...  If you or anyone else is brave enough to try all these steps, I would very much appreciate if at least one person could reply with a success or failure message so that these instructions can be modified if necessary.

EDIT: here is my system info, just in case:
```

uname -a
# Linux kikiliki 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux
RAM: 1 GB
Swap: 1 GB (maybe more would be recommended?)

```

EDIT: I also tried with Wine and CrossOver Linux, but failed, and here is a transcript of the failure:
```

dbaird@kikiliki (1229 03:32:07) scripts $ wine cmd
CMD Version 0.9.46

Z:\afs\goober.tld\user\dbaird\distfiles\tmp\opencyc-win\opencyc-1.0\scripts>run-cyc.bat
<...lots of noisy messages get printed...>
Loading statics.
Mapping in the memory image.

Implementation error: Could not create file mapping

OS-Err: 87: Invalid parameter

```

---

### Post by SuperTrooper on 2007-12-29
Hey, even better news!!!  I think Cyc was not getting along with the AFS filesystem (which contains my home directory).

So I moved off of AFS and then I was able to get Cyc running by doing the "run-cyc.sh" command (several times, because it crashes a lot) and eventually it just ran.  Like magic!!

Here is just a handful of the error messages it gives:

```

Mapping in the memory image.
./run-cyc.sh: line 63:  3224 Illegal instruction     (core dumped) $CYC_EXE -w $CYC_WORLD

```

```

Mapping in the memory image.
./run-cyc.sh: line 63:  3238 Segmentation fault      (core dumped) $CYC_EXE -w $CYC_WORLD

```

```

./run-cyc.sh: line 63:  3252 Segmentation fault      (core dumped) $CYC_EXE -w $CYC_WORLD

```

```

Mapping in the memory image.
bin/opencyc-RH-ES3-x86_32.bin: relocation error: bin/opencyc-RH-ES3-x86_32.bin: symbol munmap, version GLIBC_2.0 not defined in file libc.so.6 with link time reference

```

But that's okay!  It will work if you keep trying (for me, it usually takes like 5-10 tries.  Just don't run Cyc out of AFS!  (this might apply to NFS also ... maybe?)

Btw, don't forget to do
```

echo RH-ES3-x86_32 > platform-override.txt

```

I'll give this one more fresh test just to make sure I am not lying to you.

EDIT: Okay!  I just did one more fresh test!  It works:
```

tar xzvf opencyc-1.0.2-linux.tgz -C /tmp
cd /tmp/opencyc-1.0/scripts
echo RH-ES3-x86_32 > platform-override.txt
./run-cyc.sh
# Surprisingly, it worked on *the first try*...
# Confused, I restarted it and tried again ... and it *worked again*
# So, I restarted nearly 10 times and it worked every try
# Weird.  It mysteriously works great now (or so it seems.)

```

EDIT: Can someone else confirm this please?

---

### Post by tzarabagliu on 2008-04-11
I tried to run OpenCyc 1.0.2 on my Ubuntu 7.10 Gutsy Gibbon and got this error:

```
./run-cyc.sh: 28: [[: not found
Please run ./run-cyc.sh from opencyc-1.0/scripts
exit: 28: Illegal number: -1
```

it was because of the **bad interpreter** specified inside every script (/bin/sh which in gutsy points to the DASH shell)... See a solution to this problem here: [https://wiki.ubuntu.com/DashAsBinSh]("https://wiki.ubuntu.com/DashAsBinSh")

I changed the interpreter in each script to **/bin/bash** and it worked

---

### Post by zerwas on 2008-05-07
> **Jennifer-Botham said:**
> I would very much appreciate if at least one person could reply with a success or failure message so that these instructions can be modified if necessary.

**SUCCESS.**

Renaming the first line of all scripts from
```
#!/bin/sh
```
to
```
#! /bin/bash
```
(note the blank after "!") worked.

edit: But the initialization didn't work:
```
bin/opencyc-RH-ES3-x86_32.bin -w world/kb-5006-RH-ES3-x86_32-local.load
Loading statics.
Mapping in the memory image.
./run-cyc.sh: line 63: 14931 Segmentation fault      $CYC_EXE -w $CYC_WORLD
```

edit2: Simply try to start OpenCYC again and again and it will work after the 5th or 6th time. It's working now, thanks for the help.

-- zerwas

---

### Post by Big D on 2008-05-26
```

tar -xvf opencyc
cd opencyc/scripts
echo SuSE-9.2-x86_64 > platform-override.txt
./run.sh 

```
should work for 64 bit systems.

---

### Post by FaceLeg on 2008-11-08
```
tar -xvf opencyc
cd opencyc/scripts
```

Then renaming the first line of all scripts from
```
#!/bin/sh
```
to
```
SHELL = /bin/bash
```

Then
```
echo SuSE-9.2-x86_64 > platform-override.txt
./run.sh 

```

Worked for me in 8.10

It loads first try and hasn't crashed once for me - 2007 Macbook.

---

### Post by mjsantof on 2008-11-12
I had same problem (stack overflow), because I hadn't enabled cgi on tomcat. This link might help.

[http://cs.calstatela.edu/wiki/index.php/OpenCyc](http://cs.calstatela.edu/wiki/index.php/OpenCyc)

---

### Post by michaeljohn225 on 2008-11-12
I have been trying to run Opencyc on Gutsy, but I keep getting a segmentation fault error ( Error: Stack Overflow (signaled by signal 11 SIGSEGV (Segmentation violation)). I didn't see an answer for this on Opencyc's forums so I thought I would check to see if anyone here has seen a solution for this problem.

---

### Post by mjsantof on 2008-11-12
I've just have it working (although in Debian, but shouldn't be different in Gutsy). Have you configure Tomcat to run cgi? as explained in the link I post above?

---

### Post by omitt on 2008-11-25
[QUOTE=FaceLeg;6128994]```
tar -xvf opencyc
cd opencyc/scripts
```

Then renaming the first line of all scripts from
```
#!/bin/sh
```
to
```
SHELL = /bin/bash
```
That seemed to do the trick.  Now if only I can figure out how to open a local host.

---

### Post by sarahjohn on 2008-11-25
Just as background for other people. CGI is an interface specification between web server software (like IIS, Apache & Tomcat) and external applications, like our CGI search.

Some people assume that all CGI's are Perl scripts but this is incorrect. A CGI can be written in just about any scripting or programming language. In the case of our search.cgi, it is written in C++ and compiled to be a native executable file.

We don't have any direct experience with Tomcat but according to the Tomcat documentation, there are several servlet init parameters which can be used to configure the behaviour of the CGI servlet. One of them is; executable - The of the executable to be used to run the script. Default is perl.

---

