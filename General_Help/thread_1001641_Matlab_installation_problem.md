---
title: "Matlab installation problem"
date: 2008-12-04
forum: General Help
---

### Post by liskiewicz on 2008-12-04
Hello!

I'm trying to install native version of matlab. I've run the installation with no problems, then from matlab directory I've run script install_matlab. After running /bin/matlab script I'm getting:

```
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb555d7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb555d891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb5827494]
#3 /media/sda5/Matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so [0xaef562be]
#4 /media/sda5/Matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so [0xaef34ed7]
#5 /media/sda5/Matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so [0xaef35188]
#6 /media/sda5/Matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x2f) [0xaef3548f]
#7 [0xafba567e]
#8 [0xafb9de9d]
#9 [0xafb9de9d]
#10 [0xafb9b207]
#11 /media/sda5/Matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x6209a4d]
#12 /media/sda5/Matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x6305bc8]
#13 /media/sda5/Matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x62098e0]
#14 /media/sda5/Matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x34b) [0x625f77b]
#15 /media/sda5/Matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb1c2f96d]
#16 [0xafba567e]
#17 [0xafb9dd37]
#18 [0xafb9b207]
#19 /media/sda5/Matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x6209a4d]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb555d7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb555d96e]
#2 /usr/lib/libX11.so.6 [0xb5826619]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xb581c666]
#4 /media/sda5/Matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so [0xaef34189]
#5 /media/sda5/Matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so [0xaef343d5]
#6 /media/sda5/Matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so [0xaef35239]
#7 /media/sda5/Matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x2f) [0xaef3548f]
#8 [0xafba567e]
#9 [0xafb9de9d]
#10 [0xafb9de9d]
#11 [0xafb9b207]
#12 /media/sda5/Matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x6209a4d]
#13 /media/sda5/Matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x6305bc8]
#14 /media/sda5/Matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x62098e0]
#15 /media/sda5/Matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x34b) [0x625f77b]
#16 /media/sda5/Matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb1c2f96d]
#17 [0xafba567e]
#18 [0xafb9dd37]
#19 [0xafb9b207]
terminate called after throwing an instance of 'MathWorks::System::SimpleException'
Aborted

```

I can see the Matlab welcome screen, and the program window for about a second, then everything closes.

I've read on some forum that it is better idea to run matlab from sh /bin/scripts/matlab but from there it's even worse in my case. That's what I've got:

```
.: 199: Can't open /media/sda5/Matlab2008a/bin/bin/util/arch.sh

```

I've checked that such a file actualy does not exist. Actually there is no /bin/bin directory.

I've tried as well running matlab from metacity with the same effect. Oh I'm using Interpid, and Matlab version is 2008b.

---

### Post by colsandurz on 2008-12-04
How did you install matlab? Or have you not at all.  It looks like you're trying to install it from a flash drive or something (/media/sda).  If you can copy the image onto your hard drive then mount the image and install from there, you should be fine.  That's how I did it at least.

```

sudo mount -o loop matlab.iso /mnt/mountPoint
cd /mnt/mountPount
sudo ./install

```

Those are the commands I used to install.

---

### Post by orrinmb on 2008-12-10
its just from a downloaded taz file here is the install instructions

1. After untarring the original archive
(mit-matlab32-r2008a-student-full.tar), you can delete it.

2. Create a root directory for the installation in a location where
you have write permission; name it in a way that will let you
distinguish this installation from other Matlab versions
(/usr/local/matlabr2008a for example, though you may need to be root
for this location). In the steps below we denote this directory by
$MATLAB; replace $MATLAB below by the actual path you chose to and
including the root directory (/usr/local/matlabr2008a in the example
above).

3. Run the following from the shell prompt:
	cd $MATLAB
	zcat <path to>/lnx32-matlab-r2008a-student-full.tar.gz | tar xfp -

(replace <path to> by the path to where you downloaded
lnx32-matlab-r2008a-student-full.tar.gz). After this step you can delete
lnx32-matlab-r2008a-student-full.tar.gz.

4. Change directories to one that is on your path and writable where
you put binaries (such as /usr/local/bin, for example- you might need to be
root to do this). In that directory, run:
	ln -s $MATLAB/bin/matlab matlab
	ln -s $MATLAB/bin/mex mex
	ln -s $MATLAB/bin/mcc mcc
	ln -s $MATLAB/bin/mbuild mbuild
        
5. Launch Matlab by typing "matlab" at the shell prompt (or to run mex,
"mex <options> <file>", to run mcc, "mcc <options> <file>", to run
mbuild, "mbuild <options> <file>").

---

