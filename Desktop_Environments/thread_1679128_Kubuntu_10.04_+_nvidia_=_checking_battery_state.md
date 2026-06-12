---
title: "Kubuntu 10.04 + nvidia = checking battery state"
date: 2011-01-31
forum: Desktop Environments
---

### Post by lordemperor on 2011-01-31
[B]Edit: Disregarded NVidia's instructions and re-installed driver using the instructions [here]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia"). Has survived two reboots and 3D functions are restored.

Not the cutting-edge latest driver but I don't need that really.[/B] 

Leaving post up in case anyone else needs it.

My hardware:

Dell Vostro 230 (Provided by my employer)
CPU: E5400 @ 2.70GHz
RAM: 3GB
Video: NVidia Gefoce 310 512MB (Dell upgrade)

I have a fresh install of Kubuntu 10.04. Installation went fine and I installed the NVidia driver according to NVidia's directions, essentially:

```
stop kdm
./NVIDIA-Linux-x86-260.19.36.run
reboot
```Everything worked fine until Kubuntu installed some updates which required a reboot, there was probably a kernel update in there but I didn't take note at the time as there were not any problems then.

Upon reboot I go the dreaded *Checking battery state... [OK]*. With some furious googling it turned out to be the NVidia driver or a conflict with it.

I tried a couple of solutions including adding nouveau to several blacklists, to no avail. The "solution" which got the system running again was to disabled he NVidia driver by editing xorg.conf.

```
Section "Device"
    Identifier     "Device0"
[B]#    Driver         "nvidia"
    Driver         "nv"[/B]
    VendorName     "NVIDIA Corporation"
EndSection
```This I gather has disabled the NVidia driver in favour of the default nouveau driver.

At any rate, my desktop is working again but of course lacks compositing and 3d acceleration.

Did I do the NVidia install wrong?

Will reinstalling the NVidia driver get it working again?

How can I prevent this problem from cropping up again in the future?

---

### Post by inobe on 2011-01-31
glad that worked out for you.

you can mark your thread solved by clicking thread tools.

---

