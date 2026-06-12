---
title: "how to install kernel source??"
date: 2009-06-07
forum: General Help
---

### Post by quixote on 2009-06-07
I'm running Jaunty, and trying to install VirtualBox 2.2.4.  It's complaining that it can't find my linux source files.  As one of the people caught in the ICH8/9 bug ([Bug #346691]("(https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all")), I had to install kernel 2.6.29 to avoid filesystem corruption.  However, the command I followed to do that didn't also put the source files where the standard kernel does (/usr/src with a link in /usr/lib/modules).  

How can I fix that?  I found a [thread that seems directly relevant]("http://www.uluga.ubuntuforums.org/showpost.php?p=5651938&postcount=2"), but I'm afraid to simply type in the command without being told that's what I need in my case.  I have no idea what I'm doing! :?

```
sudo apt-get install build-essential linux-headers-`uname -r` linux-source-`uname -r`
``` 

I'm scared to death to mess with the kernel itself, now that things are finally running, after the whole filesystem corruption nightmare.  I just need the sources in the right place so that Sun's stupid VirtualBox shuts up and behaves!  (And I do want the non-free version, sadly.  I need the USB support.)

---

### Post by philinux on 2009-06-07
How are you trying to install virtualbox.
I just installed the 9.04 64 bit deb
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

I just checked and linux source files are not listed as dependencies.

---

### Post by quixote on 2009-06-07
Interesting, that it's not a dependency.  What's the damn thing carping at me for?!  I used sudo dpkg -i, and downloaded the jaunty 64-bit version from the same site you link.  This is the error message:  ```

sudo dpkg -i VirtualBox_2.2.4_Ubuntu_jaunty.deb

Error! Your kernel source for kernel 2.6.29-02062904-generic cannot be found at
/lib/modules/2.6.29-02062904-generic/build or /lib/modules/2.6.29-02062904-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:145: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

```

I did install that DKMS, but got the error message when I tried to install after that anyway.  As I write this, it occurs to me that I didn't reboot after installing DKMS.  Could that be my problem?

---

### Post by quixote on 2009-06-08
Well, it's not a simple matter of rebooting.  VirtualBox installation still gives me the same error message.  When I upgraded my kernel, I installed only the image file, not the header file.  So, can I try the command in my original question without messing up my system?

??

Or not?

---

### Post by Yellow Pasque on 2009-06-09
build-essential and the headers for the kernel that came with Ubuntu are usually already installed by default. Installing the full source for the default Ubuntu kernel isn't dangerous (unless you're really low on free disk space), but it isn't going to help here.

You need the headers for the 2.6.29 kernel you're using, not the headers from the Ubuntu repo. Where did you get that kernel? Is it just the vanilla kernel from kernel.org?

---

### Post by quixote on 2009-06-09
> **Temüjin said:**
> build-essential and the headers for the kernel that came with Ubuntu are usually already installed by default.
Yes, all that stuff is there for the default 2.6.28 kernel that crashes my system and that I can't use. :(

I installed 2.6.29.4 using these two commands:```
$ wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-image-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb
$ sudo dpkg -i linux-image-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb
```so I have only the image, not the headers.  

What I don't know is whether installing the headers (linux-headers-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb) will interfere with my current 2.6.29 image install.  It's working and I don't want to touch it!

Also, can I use `uname -r` as in the command in my first question, or should I better just use the complete name?

Thanks for your help!

---

### Post by quixote on 2009-06-11
(Bump.  Anyone?  This is probably a simple question for an expert :D )

Also, I realize now, but I can't change it, that the subject should probably say "how to install kernel **headers**"

---

### Post by Yellow Pasque on 2009-06-11
Installing headers won't affect the kernel image.

---

### Post by quixote on 2009-06-11
Thanks a million!  Now I feel like I can charge ahead.

Update a day later: Yup.  Everything's working now.  Whee ! :-D

(I had a bit of a hiccup because I was still missing one of the header packages.  If you need to compile kernel modules -- which was the point of this whole exercise since VirtualBox wanted that for vboxdrv -- you need the plain old header file for all computers, plus the "generic" header package for your version (eg 64-bit), plus the source.  I hadn't realized I needed both the plain and the generic header packages, so for a while it was telling me I had broken dependencies in my linux-headers install.  Freaked me out, I can tell you!  But all's well that ends well.)

---

