---
title: "Problem Installing Ansys CFX 10 in Ubuntu 7.10 alternate"
date: 2008-02-18
forum: Education &amp; Science
---

### Post by AlexVader on 2008-02-18
Hi World,

I have decided to quit WiDows once and for all, my laptop is no longer a dual booter.

I have tried to install ANSYS CFX 10.0 but there seens to be a problem with libXm.so.3 from lesstif...

I installed Ansys multiphysics 10.0 and i used the default libXm.so.3 from 7.10 gutsy... but with CFX i had no luck...

Does anyone have any hint on what may be happening here...?

I also installed MESA and DRI so as to use the GLX modules and DRI, because i use software like ProEngineer or Abaqus...

In my xorg conf i loaded glx module, and i have DRI enabled...

Thanks in advance

I would hate to have to get back to W....  :(

Alex

---

### Post by AlexVader on 2008-02-18
Ok, so i solved the graphic issue: it was related to the graphic driver, i uninstalled the restricted driver provided by ubuntu, and installed a previous one from ATI, problem solved;

Now i have a different one:

I can preprocess a problem in cfx, or postprocess, but the solver aborts with an error complaining that it cannot find the glibc in /usr/ansys_inc/cfx10/bin/linux package or it cannot find solver-pvm.exe or it is unreadable...

... both my glibc, and solver-pvm.exe are there, and i symlinked the libgc_s.so1 in /usr/ansys_inc/cfx/lib... whatever, against the one present in /lib, and still it complains and aborts the solver with an error...

Any hints...?

---

### Post by snogen on 2008-04-15
Anything new with regards to install ANSYS CFX on Ubuntu? Maybe CFX 11 and/or Ubuntu 8.04 ?

---

### Post by AlexVader on 2008-04-22
Hi Snogen

Thanks, i already had solved the issue, but i have stepped into CFX 11, it installs cleanly in Ubuntu 7.10...no problems at all...

The previous solution that i had found was way too complex...

Involved installing debootstrap for Ubuntu 6.10, and creating a chrooted environment in a folder like /usr/chroot_env where i installed a basic Ubuntu 6.10, symlinking /etc /dev /proc /sys and /var to my corresponding folders in /usr/chroot_env at boot time in /etc/fstab, and finally... entering my chroot jail with %schroot

... that allowed me to use all the programs in CFX 10 that had been compiled
for a previous version of GLIBC than the one present in 7.10...

...but i found out that this solution was way too "geeky"... and dangerous...  if by any chance you decide that you no longer want your chrooted environment, and rm -rf the folder /usr/chroot_env... the symlinks in /etc/fstab will ensure that ALL the foldere that you mounted in side this directory will vanish with the rm command... a bit unpleasant i think :(

Before doing that one must absolutely remove the lines in /etc/fstab with mount poits inside /etc/chroot_env, and reboot...   

it didn happen to me... but it can happen if someone is less focused

... thanks anyway...  :)... i find CFX 11 way more sophisticated than CFx 10...   specially that part that performs Fluid Structure Interaction...

Now i am facing a different problem...

I installed a Beowulf cluster with RHEL5 in CFD lab... i wanted to install CFX 11 in that cluster... but the license daemon cannot start TCP services...  so lmgrd never locks to the license...   :-(

I am using this cluster to send this email... so.. i do not get why the heck TCP won't start...

...   that is one of the reasons that i use Ubuntu in my PCs...

can you give me a hint here....?

Thanx

Alex

---

### Post by NeiNastran on 2008-04-22
You can always contact Ansys...

---

### Post by AlexVader on 2008-04-23
I did already...

They just say that 

RHEL 5.1 Client X86_64 architecture is not supported by Ansys products...

:-(

Thing is, the server is configured to use RHEL 5.1, all our engineering apps have been compiled under RHEL 5.1 glibc and kernel, and it would be way too hard to backport all those apps ( Finite volume solvers, visualizers, mesh converters, scripts...)

to RHEL 3.0 or 4.0... 

Why is it that those guys at ANSYS do not port their software to more recent versions of Linux Distros...?

... furthermore... the specific problem that i am reporting...

 - difficulty in starting TCP/IP - is not ansys related...

Alex

---

