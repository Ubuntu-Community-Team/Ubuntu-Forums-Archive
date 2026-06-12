---
title: "nvidia-glx -- _nv001206gl"
date: 2006-01-10
forum: General Help
---

### Post by digger4ubuntu on 2006-01-10
OK - first background.

Moved to Kubuntu Breezy from SuSE 9.3 about 2 months ago.  X is not stable at all using the nvidia drivers from Nvidia's web site.  I get the "gettimeofday" loop errors and many others all basically resulting in this machine being unreliable in both 3d and 2d applications.  I can not have a workstation that locks up frequently and uncontrollably.  Might as well install a M$ product.

The nv drivers do not have 3d support.  Using mesa iis not an option as that the 3d is slow at best.  So I am trying the nvidia-glx packages now.

Hardware:
Athlon XP 1600+
Abit K7A Mobo (Via KT133A)
2x512MB PC133
PNY GeForce4 4200Ti

I have installed

dpkg -l | egrep -i "nvidia|2.6.12-10-k7"
ii  linux-headers-2.6.12-10-k7             2.6.12-10.25                       Linux kernel headers 2.6.12 on AMD K7
ii  linux-image-2.6.12-10-k7               2.6.12-10.25                       Linux kernel image for version 2.6.12 on AMD
ii  linux-restricted-modules-2.6.12-10-k7  2.6.12.4-11.1                      Non-free Linux 2.6.12 modules on AMD K7
ii  nvclock-gtk                            0.7-2ubuntu2                       Allows you to overclock your nVidia card und
ii  nvclock-qt                             0.7-2ubuntu2                       Allows you to overclock your nVidia card und
ii  nvidia-glx                             1.0.7667-0ubuntu25.1               NVIDIA binary XFree86 4.x/X.Org driver
ii  nvidia-kernel-common                   1.0.7667+1                         NVIDIA binary kernel module common files
ii  nvidia-settings                        1.0-3ubuntu6                       Tool of configuring the NVIDIA graphics driv

uname -a
Linux hostname 2.6.12-10-k7 #1 Thu Dec 22 12:32:10 UTC 2005 i686 GNU/Linux

I ran the nvidia-glx-config enable command and restarted X.  I have actually rebooted the entire machine to ensure a clean load of all kernel modules.  (I know - not needed - but willing to try anything at this point)

BTW - I did remove the Nvidia supplied drivers before I installed the packages.  I used the --uninstall option to the supplied install binary.

Now, whenever I start an application that requires 3D I get the following error:

glxgears: symbol lookup error: /usr/lib/libGL.so.1: undefined symbol: _nv001206gl

Google is giving me no love on that error and neither are my searches elsewhere.  Can anyone help?  I know I am probably just fried right now, but my searches are getting me no where; fast.

Thanks,

D

---

### Post by tonysathre on 2006-01-10
install them using synaptic or apt-get

---

### Post by digger4ubuntu on 2006-01-10
They were installed with "apt-get install pkgname"  All dependancies were allowed to auto-resolve.

---

