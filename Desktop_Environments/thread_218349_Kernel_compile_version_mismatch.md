---
title: "Kernel compile version mismatch"
date: 2006-07-18
forum: Desktop Environments
---

### Post by jackpipe on 2006-07-18
Spot the difference.....
This is the output from a second run compiling the kernel.  This is the second time i've done this, so its reproducible. ie I install kernel sources, compile. test.  kernel fails.  Below is what I get when I try and compile a second time (actually without having altered anything, aside from adding the --initrd option to make-kpkg).
Any ideas?
I tried adding a debian/official - but that failed - I guess official kernels need to listed in a file somewhere ... etc.
frustrated.....


# sudo make-kpkg --initrd --revision=1 --append-to-version=mykerne1 kernel_image
Warning: The file include/linux/version.h exists
The contained UTS_VERSION string:
                        "2.6.15.7-ubuntu1mykernel"
does not match expectations:
                        "2.6.15.7-ubuntu1mykerne1"
I'll try and recover
Please ignore the warning about overriding and ignoring targets above.
These are harmless. They are only invoked in a part of the process
that tries to snarf variable values for the conf.vars file.
echo done >  stamp-configure
/usr/bin/make -f /usr/share/kernel-package/rules real_stamp_image
make[1]: Entering directory `/usr/src/linux-source-2.6.15'
The changelog says we are creating 2.6.15.7-ubuntu1mykernel, but I thought the version is 2.6.15.7-ubuntu1mykerne1
make[1]: *** [real_stamp_image] Error 1
make[1]: Leaving directory `/usr/src/linux-source-2.6.15'
make: *** [kernel-image-deb] Error 2

---

### Post by jackpipe on 2006-07-18
oops
A different font helps.
Now I can see the difference too.
Sorry.
Changing my default terminal font as we speak so I will be able to differentiate L and 1 in future

---

### Post by jackpipe on 2006-07-18
Actually, this does somewhat piss me off.
Here is the source of my error 
[http://ubuntuforums.org/archive/index.php/t-24853.html](http://ubuntuforums.org/archive/index.php/t-24853.html)
Notice the '1' instead of 'l'
Write 1000 times.... 
I will not cut and paste commands from websites, especially ubuntu forum posts.
I will not cut and paste commands from websites, especially ubuntu forum posts.
I will not cut and paste commands from websites, especially ubuntu forum posts.
etc

Aaaaarggghhhh.

---

