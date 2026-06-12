---
title: "strange errors trying to install nvidia-glx"
date: 2005-10-18
forum: Desktop Environments
---

### Post by biodiesel-bri on 2005-10-18
Hi all-

I'm getting some odd errors trying to install nvidia-glx.

```
root@dragon:/home/bri# apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  nvidia-settings nvidia-kernel-source
The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 3085kB of archives.
After unpacking 10.3MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  nvidia-glx
Install these packages without verification [y/N]? y
Err http://us.archive.ubuntu.com breezy/restricted nvidia-glx 1.0.7667-0ubuntu25
  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.12/nvidia-glx_1.0.7667-0ubuntu25_i386.deb  404 Not Found

```

Any ideas?  I checked the site and there isn't a file nvidia-glx 1.0.7667-0ubuntu25, but there is an nvidia-glx_1.0.7667-0ubuntu4_i386.deb.  Why is the file missing?  Why doesn't the repository update properly?  Why is the gpg sig broken?  Many mysteries.

Yes, I did apt-get update.  No joy.

---

### Post by Murgle on 2005-10-18
the us archives are being funky... remove all the us. infront of your archives and the reupdate and you should be golden

---

