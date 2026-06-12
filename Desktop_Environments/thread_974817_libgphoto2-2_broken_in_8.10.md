---
title: "libgphoto2-2 broken in 8.10"
date: 2008-11-07
forum: Desktop Environments
---

### Post by mrkeef on 2008-11-07
The version of libgphoto2-2 which ships with Intrepid appears to be broken as some cameras can no longer connect correctly.

When using gthumb, digikam or F-Spot to import photos from my Canon Powershot S5-iS, I get this error message

> error occurred io-library could not lock device camera already in use

This seems to occur with several makes and models of camera, and in several other linux distros.

I found the solution is to "downgrade" libgphoto2-2 to an earlier version.

The process is as follows:

1. Dowload the package from:

[INDENT][https://launchpad.net/ubuntu/hardy/i386/libgphoto2-2/2.4.0-2ubuntu2](https://launchpad.net/ubuntu/hardy/i386/libgphoto2-2/2.4.0-2ubuntu2)[/INDENT]

2. Install the package

```
sudo dpkg -i Temp/libgphoto2-2_2.4.0-2ubuntu2_i386.deb
```

3. Lock the version so that Update Manager does not try to install the newer version.

[INDENT]Go to System- Administration-Synaptic
Search for libgphoto2-2 and select it
Click on Package and select "Lock Version"[/INDENT]

Hopefully, your camera should now connect as expected.

I expect that at some time in the near future this problem will be rectified by the libgphoto developers.

---

