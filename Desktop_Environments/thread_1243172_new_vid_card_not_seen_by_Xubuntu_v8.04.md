---
title: "new vid card not seen by Xubuntu v8.04"
date: 2009-08-18
forum: Desktop Environments
---

### Post by Skip Da Shu on 2009-08-18
I installed a nvidia 9600GSO card in a Xubuntu v8.04 system tonight thinking it would recognize the card and give me the option to install restricted driver (it had been using onboard Intel with VESA driver).  WRONG... My System-->Hardware Drivers just says no restricted drivers in use. Via Synaptic I installed first the nvidia-glx-new and nothing changed... sudo dpkg-reconfig xserver-xorg didn't buy me anything except to get me back to a decent resolution.  Following another thread I then installed nvidia-glx-new-envy but can't see what that changed and I've got no new entries in System--> 

I had this card working in a ubuntu Jaunty system but I really don't want to install that on this machine because it is my apt-cacher, samba server and backup machine... would prefer to not have to install and set all that up again.

How do I force the use of the nvidia driver since I'm getting no option to do so via Hardware Drivers?

PS: restricted linux headers are in place that match my 2.6.24-24 kernel.

---

### Post by khelben1979 on 2009-08-18
You can download the latest video driver directly from nVidia.com.

Get drivers [here]("http://www.nvidia.com/Download/index.aspx?lang=en-us").

---

### Post by Skip Da Shu on 2009-08-18
> **khelben1979 said:**
> You can download the latest video driver directly from nVidia.com.

Get drivers [here]("http://www.nvidia.com/Download/index.aspx?lang=en-us"). OK, will give that a whirl. Was hoping to be able to use the stuff in the repository.

EDIT: Downloaded their package to my desktop, stopped gdm, ssh'd into the machine and ran their script.  Said it had to compile a kernel and ended up finishing with what appeared to be good results.  My xorg.conf is updated but System-->Hardware Drivers still says there are now proprietary drivers in use and my BOINC application still says "no CUDA devices found".  So I don't think the driver is really working.

Any other suggestions?  Where should I look to see the driver?

EDIT2:
```
skip@crunch20:~$ sudo lspci | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0610 (rev a2)
```

```
skip@crunch20:~$ dmesg | grep -i nv
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[   41.545964] nvidia: module license 'NVIDIA' taints kernel.
[   41.800974] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.31  Tue Jul 28 17:52:27 PDT 2009
```

```
skip@crunch20:~$ lsmod | grep nvidia
nvidia              10321864  26 
i2c_core               28544  1 nvidia
```
```

skip@crunch20:~$ nvclock -s
Segmentation fault
```

and from BOINC:
> Tue 18 Aug 2009 01:38:58 PM CDT||Local time is UTC -5 hours
Tue 18 Aug 2009 01:38:58 PM CDT||Not using a proxy
Tue 18 Aug 2009 01:38:58 PM CDT||No CUDA devices found
Tue 18 Aug 2009 01:38:58 PM CDT||No coprocessors

However I just found the Nvidia xserver settings GUI app and it sees the 9600GSO (in settings instead of system on Xubuntu)

---

### Post by Skip Da Shu on 2009-08-18
Anybody know where "3D effects" is in Xubuntu?

---

### Post by Skip Da Shu on 2009-08-18
Got it working... thanx much.

See **[[COLOR="Blue"]here[/COLOR]]("http://boinc.berkeley.edu/dev/forum_thread.php?id=3564")**:

---

