---
title: "Can't install NVIDIA 180.27 drivers"
date: 2009-02-07
forum: General Help
---

### Post by TheLions on 2009-02-07
Ok problem is that i can't install new driver and i already removed drivers installed by "Hardware Drivers" applet so no-nice-grafix for me!:(

when i stop gnome and put this in terminal:[HTML]sudo su
./NVIDIA-Linux-x86_64-180.27-pkg2.run [/HTML]
i get
[HTML]./NVIDIA-Linux-x86_64-180.27-pkg2.run 
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86_64 180.27...........................................................................................................................................................
./NVIDIA-Linux-x86_64-180.27-pkg2.run: 870: ./nvidia-installer: Permission denied
[/HTML]

Please help!

EDIT:adding [SOLVED]

---

### Post by lswest on 2009-02-07
try running ```
sudo sh NVIDIA-Linux-x86_64-180.27-pkg2.run
``` instead.  If you're still running on an xserver change to the first virtual terminal (ctrl+alt+F1) and log in, then type ```
sudo /etc/init.d/gdm stop
``` and try the above again.

---

### Post by jocko on 2009-02-07
You probably need to make the installer executable.
Try this:```
chmod a+x NVIDIA-Linux-x86_64-180.27-pkg2.run
sudo ./NVIDIA-Linux-x86_64-180.27-pkg2.run
```

---

### Post by TheLions on 2009-02-07
Thanks for the replay!

ok i tried this:
[HTML]sudo su
/etc/init.d/gdm stop
chmod a+x NVIDIA-Linux-x86_64-180.27-pkg2.run
sudo sh NVIDIA-Linux-x86_64-180.27-pkg2.run[/HTML]

and no movement there, the same error persist:
[HTML]./NVIDIA-Linux-x86_64-180.27-pkg2.run: 870: ./nvidia-installer: Permission denied
[/HTML]

---

### Post by ju2wheels on 2009-02-07
> **TheLions said:**
> Thanks for the replay!

ok i tried this:
[HTML]sudo su
/etc/init.d/gdm stop
chmod a+x NVIDIA-Linux-x86_64-180.27-pkg2.run
sudo sh NVIDIA-Linux-x86_64-180.27-pkg2.run[/HTML]

and no movement there, the same error persist:
[HTML]./NVIDIA-Linux-x86_64-180.27-pkg2.run: 870: ./nvidia-installer: Permission denied
[/HTML]

Dont kill yourself doing this, there are debs already:

[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/)

You will want these 3:

[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-180-kernel-source_180.27-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-180-kernel-source_180.27-0ubuntu1_amd64.deb)

[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-180-libvdpau_180.27-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-180-libvdpau_180.27-0ubuntu1_amd64.deb)

[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-glx-180_180.27-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-glx-180_180.27-0ubuntu1_amd64.deb)

---

### Post by jocko on 2009-02-07
> **ju2wheels said:**
> Dont kill yourself doing this, there are debs already:

[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/)

You will want these 3:

[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-180-kernel-source_180.27-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-180-kernel-source_180.27-0ubuntu1_amd64.deb)

[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-180-libvdpau_180.27-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-180-libvdpau_180.27-0ubuntu1_amd64.deb)

[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-glx-180_180.27-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-glx-180_180.27-0ubuntu1_amd64.deb)

I'm pretty sure those packages are for jaunty, which have both newer kernel and newer xorg version than intrepid, so I think there is no way they will work in intrepid. But there are backported 180.11 drivers in the intrepid-updates repo.

---

### Post by ju2wheels on 2009-02-07
> **jocko said:**
> I'm pretty sure those packages are for jaunty, which have both newer kernel and newer xorg version than intrepid, so I think there is no way they will work in intrepid. But there are backported 180.11 drivers in the intrepid-updates repo.

No, those drivers were actually recommended to an Intrepid user on Launchpad bugs. And I can confirm they work as Im using them myself on my Intrepid.

---

### Post by TheLions on 2009-02-07
> **ju2wheels said:**
> Dont kill yourself doing this, there are debs already:

[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/)

You will want these 3:

[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-180-kernel-source_180.27-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-180-kernel-source_180.27-0ubuntu1_amd64.deb)

[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-180-libvdpau_180.27-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-180-libvdpau_180.27-0ubuntu1_amd64.deb)

[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-glx-180_180.27-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-glx-180_180.27-0ubuntu1_amd64.deb)

it worked like charm! [IMG]http://www.fer2.net/images/smilies/clap.gif[/IMG]
THANK YOU! [IMG]http://www.fer2.net/images/smilies/drunk.gif[/IMG]

---

### Post by jocko on 2009-02-07
> **ju2wheels said:**
> No, those drivers were actually recommended to an Intrepid user on Launchpad bugs. And I can confirm they work as Im using them myself on my Intrepid.
I stand corrected.

---

