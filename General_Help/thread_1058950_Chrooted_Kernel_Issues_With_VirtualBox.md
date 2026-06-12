---
title: "Chrooted Kernel Issues With VirtualBox"
date: 2009-02-03
forum: General Help
---

### Post by nfox on 2009-02-03
***************************************************************************************
UPDATED: It's solved
***************************************************************************************

Since it was really hard for me to find this info, I'll post it for reference here:

rm ~/.config/Trolltech.conf
sudo /etc/init.d/vboxdrv setup && sudo -K
Virtualbox

Don't know why, but the Trolltech.conf file being removed fixes the "mixing QT versions" issue.

---

### Post by Titan8990 on 2009-02-03
> So since Intrepid is on a newer kernel than Hardy why is "uname -r" showing Intrepid's kernel under chroot?


Chroot does not use a different kernel. It uses your current kernel with the filesystem on your chroot environment. When you build something that is a module it builds it based on the headers of the same version of your currently running kernel. 

Chroot is not a virtual OS.....

---

### Post by nfox on 2009-02-03
> **Titan8990 said:**
> Chroot does not use a different kernel. It uses your current kernel with the filesystem on your chroot environment. When you build something that is a module it builds it based on the headers of the same version of your currently running kernel. 

Chroot is not a virtual OS.....

Right about the not being a virtual OS part but people can run AMD64 under x86 and vice versa. That's gotta indicate a different kernel right? Plus you can't get 2.6.27 on Hardy as far as I know(knew). 

More important to me is why VBoxDRV setup can't find my kernel to compile against? Seems like it should be able to handle mine as there is an Intrepid-specific download although I dl'ed the Hardy one. I've got KATE 3 running on my Intrepid X-session through the chroot and a slew of other apps so it should all be linked.. I can post my fstab if it helps.

It says "Specify KERN_DIR=<directory> and run Make again." How do I pass this if the setup is an /etc/init.d/ script?

---

### Post by Titan8990 on 2009-02-03
Usually when /etc/init.d/   contains a binary there is also a similar binary in something like /usr/bin. 

For this to work, at the least, you will need the linux header files in /usr/src/ for your currently running kernel. You shouldn't need to specify the directory.

---

### Post by nfox on 2009-02-03
Thanks for trying to help.
```
user@box:~$ ls /usr/src/
linux-headers-2.6.27-11  linux-headers-2.6.27-11-generic  rpm

```
It's there. VBoxDRV is not in "/usr/bin" but is a directory: "/var/lib/dkms/vboxdrv." The contents include two folders: "2.1.2" and "kernel-2.6.27-11-generic-i686" and I think that "generic-i686" may be a problem.

I'm looking at [http://forums.virtualbox.org/viewtopic.php?t=13107]("http://forums.virtualbox.org/viewtopic.php?t=13107") as it appears to be the same error. And:
```
(mychroot)user@box:/usr/bin$ dpkg -l |grep linux-headers-generic
ii  linux-headers-generic                  2.6.24.23.25                 Generic Linux kernel headers
```
Whereas my host Intrepid reports: 
```
user@box:~$ dpkg -l |grep linux-headers-generic
ii  linux-headers-generic                 2.6.27.11.14                            Generic Linux kernel headers
```

Seperate kernels. Why is "uname -r" not showing what "dpkg -l |grep linux-headers-generic" shows? It's not like I can get 2.6.27 on Hardy I don't believe.

---

### Post by Titan8990 on 2009-02-03
copy the headers from your intrepid filesystem to your hardy filesystem.

---

### Post by nfox on 2009-02-03
Your suggestions didn't work at least for me. I did as you said but no go.
I did however fix the problem and it's an easy fix:


I copied my APT's sources.list from Intrepid to Hardy's jail so it can properly obtain the headers and image. 
```
aptitude update && aptitude dist-upgrade && aptitude install linux-headers-`uname -r`
```

This properly put the system together as was required (as opposed to my meddling around with manually copying things...) and it works perfectly.

---

