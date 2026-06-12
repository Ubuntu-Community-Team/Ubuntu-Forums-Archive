---
title: "svgalib fails to compile"
date: 2006-05-24
forum: Desktop Environments
---

### Post by tytalus on 2006-05-24
Couple of starters here, I'm running kernel 2.6.12-9-386. The original gcc compiler used was gcc version 3.4.5 20050809 (prerelease) (That's what cat /proc/version returns anyways). The kernel source wasn't originally installed, so to get it installed I did the following 

$ uname -r
2.6.12-9-386
$ sudo apt-get install linux-source-2.6.10

This places linux-source-2.6.12.tar.bz2 in /usr/src.
2. Download the gcc compiler (if you installed ivtv in step 4 then you already did this):

$sudo apt-get install build-essential

3. Change to the directory /usr/src:

$ cd /usr/src

4. Uncompress the kernel source:

$ sudo tar xvjf linux-source-2.6.10.tar.bz2

5. Make a link called linux from the new source directory:

$ sudo ln -s /usr/src/linux-source-2.6.10 /usr/src/linux

6. We need the source directory to contain certain files (`version.h`, configuration files) for lirc to compile so:

$ cd linux
$ sudo make oldconfig --This should make the config file
$ sudo make include/linux/version.h --This creates the version.h file
$ sudo make modules -- WARNING: This may take a very long time to complete.

So I think it's setup correctly. So far what I've found is that I have some sort of rare problem with this chipset so I had to go into the makefile.cfg for svgalib & enable the "NO_ASM = y" string. Anyways, so when I go to install this, I use "sudo make CC=/usr/bin/gcc-3.4 install" to get it rolling, this is the last bit I get when it fails

make[1]: Leaving directory `/home/gamebox/svgalib-1.9.19/doc'
(cd kernel/svgalib_helper ; make default modules_install )
make[1]: Entering directory `/home/gamebox/svgalib-1.9.19/kernel/svgalib_helper'
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/gamebox/svgalib-1.9.19/kernel/svgalib_helper modules
make: *** /lib/modules/2.6.12-9-386/build: No such file or directory.  Stop.
make: Entering an unknown directorymake: Leaving an unknown directorymake[1]: *** [default] Error 2
make[1]: Leaving directory `/home/gamebox/svgalib-1.9.19/kernel/svgalib_helper'
make: *** [installmodule] Error 2


I went ahead and looked for the lib/modules/2.6.12-9-386/ for the build directory, but it doesn't exist? Not too sure what I need to do to fix this, but any suggestions or advice would be much appreciated. I turned up very little in my googling attempts. Also I'm a linux n00b.

Edit**
Ok, after more hunting around, I found this post
[http://ccrma-mail.stanford.edu/pipermail/planetccrma/2004-November/006769.html](http://ccrma-mail.stanford.edu/pipermail/planetccrma/2004-November/006769.html)
Which sort of showed that they had a symbolic link to /usr/src/ so I went ahead and created it that. It's now successfully installed. Proceeding with make demoprog etc. now, so that I can hopefully get Advancemame up & running :D

---

### Post by tytalus on 2006-05-24
Yargh. Bad news. Attempting to insmod the module results in:

gamebox@gamebox:~/svgalib-1.9.19$ sudo insmod /lib/modules/`uname -r`/kernel/misc/svgalib_helper.ko
insmod: error inserting '/lib/modules/2.6.12-9-386/kernel/misc/svgalib_helper.ko': -1 Unknown symbol in module


Anyone have any suggestions? I'm at my wits end with this.

---

